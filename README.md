# GitHub-Actions-101

## Extract version from branch name

Say we have a workflow which is triggered by branches named `release-*.*.*`.
Now we want to extract version from the branch name, and later we will use it (e.g. as image tag).

Here is an example:
```yml
on:
  push:
    branches:
      - 'release-*.*.*'
jobs:
  extract:
    steps:
      - run: |
          echo "${GITHUB_REF_NAME#release-}"
          echo "VERSION=${GITHUB_REF_NAME#release-}" >> $GITHUB_ENV
      - run: echo ${{ env.VERSION }}
```

Its running result: https://github.com/qsliu2017/GitHub-Actions-101/actions/runs/1723929312
