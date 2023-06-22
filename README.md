# test-build-vite-action
Builds a NPM Vite project and comments any errors on a pull request.

## Summary
This action is intended to run on pull requests.
It only works for NPM, yarn and pnpm are not supported.
If it detects errors, the action will fail and leave a comment under the PR with the error, making sure the production CI/CD pipeline won't fail.

### Usage
```yml
on:
  pull_request:
    types: [opened, synchronize]

jobs:
  test:
    runs-on: ubuntu-latest

    permissions:
      pull-requests: write
      contents: write

    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3

      - name: Test Build
        uses: Lenni009/test-build-vite-action@main
        with:
          node-version: 18
```

### Paramters
- `node-version`: Allows you to specify a node version to use. Defaults to `latest`.
