# Check labels in PR

Checks that one of the following labels is present on the pull request: `change: standard`, `change:emergency`, `change:impactful`.
If not the action automatically assigns `change: standard`

## Setup

Create a `.yml` file under the `.github/workflows/` directory in your repository with the following contents:

```
name: Expect labels
on:
  pull_request:
   types: [opened, labeled, unlabeled, synchronize]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: transferwise/tw-check-label@1.0.1
      with:
        github-token: '${{ secrets.GITHUB_TOKEN }}'
```

Then, enable the corresponding status check in the branch protection rules of your repo.
