# Croissant Metadata Validator

[![GitHub Actions](https://github.com/iulusoy/verify-croissant-schema/workflows/Test%20Error%20Handling/badge.svg)](https://github.com/iulusoy/verify-croissant-schema/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/downloads/)

A GitHub Action to validate Croissant metadata files using the [mlcroissant](https://github.com/mlcommons/croissant) Python package.

## Usage

### Basic Usage

```yaml
name: Validate Croissant Metadata

on: [push, pull_request]

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: iulusoy/verify-croissant-schema
        with:
          file: 'path/to/metadata.json'
```

### Advanced Usage

```yaml
name: Validate Croissant Metadata

on: [push, pull_request]

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: iulusoy/verify-croissant-schema
        with:
          file: 'croissant.json'
          python-version: '3.11'
```

### Using from GitHub Marketplace

You can use this action from the GitHub Marketplace:

```yaml
- uses: iulusoy/verify-croissant-schema@v1
  with:
    file: 'path/to/metadata.json'
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `file` | Path to the Croissant metadata file to validate | `true` | - |
| `python-version` | Python version to use | `false` | `3.10` |

## Features

- ✅ Validates Croissant metadata files
- ✅ Uses the official mlcroissant Python package
- ✅ Configurable Python version
- ✅ Fails the workflow if validation fails

## Requirements

- Python 3.10 or higher
- The specified file must exist in the repository

## Example Workflow

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Validate Croissant metadata
        uses: iulusoy/verify-croissant-schema
        with:
          file: 'metadata/croissant.json'
          python-version: '3.10'
```



