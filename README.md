# Backstage TechDocs Publishing

Reusable GitHub Actions workflow for publishing Backstage TechDocs to S3-compatible storage.

## Workflow Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `entity-name` | Yes | - | Name of the entity |
| `entity-kind` | No | Component | Kind of entity (Component, Service, etc.) |
| `entity-namespace` | No | default | Namespace of entity |
| `s3-endpoint` | Yes | - | S3-compatible endpoint URL |
| `bucket-name` | Yes | - | S3 bucket name |
| `aws-region` | No | us-east-1 | AWS region |

## Required Secrets

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

## Usage

Create a workflow that calls this reusable workflow:

```yaml
name: Publish TechDocs

on:
  push:
    branches:
      - main

jobs:
  publish:
    uses: Digitalist-Open-Cloud/BackstageTechDocs/.github/workflows/publish-techdocs.yml@main
    with:
      entity-name: my-entity
      entity-kind: Component
      entity-namespace: default
      s3-endpoint: https://storage.example.com
      bucket-name: my-bucket
      aws-region: us-east-1
    secrets:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

## Container

Uses `hub.dglive.net/public/backstage-tech-docs-generator:0.4`
