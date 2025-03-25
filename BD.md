# Changes made for Brad's Deals

Changes made to the fork:
  - Ignores all lambda packages changes and the version tag since we update via GHAs rather than through terraform.

## Updating

If cloning through the `gh` cli, it will automatically setup an `upstream` remote.  Otherwise, one will need to add the upstream remote:

```bash
git remote add upstream https://github.com/terraform-aws-modules/terraform-aws-lambda.git
```

Sync the master branch to our `bd` branch.  Note that this can be done through the UI with the "Sync fork" button.  Otherwise, via command line:

<!-- TODO: Does the sync rebase or merge? -->
```bash
```

Pull the latest tag and push up to our fork:

```bash
git pull upstream $RELEASE_TAG
git push origin $RELEASE_TAG
```

Checkout onto the tag that we are upgrading, checkout to a new branch, merge in the `bd` branch, and push a new tag:

```bash
git checkout $RELEASE_TAG
git checkout -b bd-release/$RELEASE_TAG
git pull --no-rebase origin bd
git tag $RELEASE_TAG-bd
git push origin $RELEASE_TAG-bd
```

Optional: Cut a new release from the tag.