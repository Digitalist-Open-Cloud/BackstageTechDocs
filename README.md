# Publish TechDocs for Backstage

For any S3-compatible storage.

## Usage

Needed secrets:

```shell
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
TECHDOCS_S3_BUCKET_NAME
S3_ENDPOINT
AWS_REGION
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
    secrets:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
      TECHDOCS_S3_BUCKET_NAME: ${{ secrets.TECHDOCS_S3_BUCKET_NAME }}
      S3_ENDPOINT: ${{ secrets.S3_ENDPOINT }}
      AWS_REGION: ${{ secrets.AWS_REGION }}
```
