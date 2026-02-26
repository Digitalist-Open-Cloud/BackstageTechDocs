# Publish TechDocs for Backstage

For any S3-compatible storage.

## Usage

Needed secrets:

```shell
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
```

Create file like:

```shell
.github/workflows/techdocs.yml
```

In the file:

```shell
name: Publish TechDocs

on:
  push:
    branches:
      - main

jobs:
  publish:
    uses: github.com/Digitalist-Open-Cloud/BackstageTechDocs/platform-workflows/.github/workflows/publish-techdocs.yml@main
    with:
      entity-name: my-doc-entity
      entity-kind: Component
      entity-namespace: default
      s3-endpoint: https://fk2.storage.com
      bucket-name: foobar
      aws-region: us-east1
    secrets:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```
