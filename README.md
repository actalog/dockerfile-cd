# Dockerfile CD

```yml
name: CD

on:
  workflow_run:
    workflows: ['CI']
    types:
      - completed
    branches:
      - main

jobs:
  dockerfile-cd:
    name: Dockerfile CD
    runs-on: ubuntu-latest
    steps:
      - uses: actalog/check-ci@main
      - uses: actions/checkout@v4
      - uses: actalog/dockerfile-cd@main
        with:
          image-name: actalog/some-software
          image-version: v1.0.0
          registry-username: actalog
          registry-token: ${{ secrets.DOCKER_HUB_TOKEN }}
```
