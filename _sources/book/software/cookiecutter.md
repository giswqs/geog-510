# Cookiecutter

## Introduction

[Cookiecutter](https://github.com/cookiecutter/cookiecutter) is a command-line utility that generates projects from templates. It automates the creation of a project structure with predefined files and directories, ensuring consistency and saving time when starting new projects. This tool is particularly useful for developers who want to maintain a standardized setup across multiple projects.

**Example Python Package Template:** [opengeos/cookiecutter-pypackage](https://github.com/opengeos/cookiecutter-pypackage)

## Usage

This guide provides a step-by-step walkthrough for creating a Python package, configuring it for distribution, and managing versioning and releases. Follow these instructions to streamline your workflow.

## Prerequisites

Before proceeding, install the required tools using pip or conda:

### Use pip

```bash
pip install cookiecutter bump-my-version
```

### Use conda

```bash
conda install -c conda-forge cookiecutter bump-my-version
```

## Step-by-Step Instructions

### 1. Generate the Package Structure

Use Cookiecutter to create the initial structure of your Python package. This command clones a template repository and sets up the necessary files and directories. Follow the prompts to customize your package:

```bash
cookiecutter gh:opengeos/cookiecutter-pypackage
```

### 2. Create a Repository on GitHub

1. Go to [GitHub](https://github.com) and create a new empty repository. Makre the repository name the same as your package name.
2. Do NOT initialize it with a README, license, or .gitignore file.

### 3. Configure GitHub Actions Permissions

Enable GitHub Actions to perform read and write operations for your repository:

1. Go to your repository on GitHub.
2. Navigate to `Settings` > `Actions` > `General` > `Workflow permissions`.
3. Adjust the settings to allow **read and write operations**.

### 4. Clone the Repository

Clone the newly created GitHub repository to your local machine:

```bash
git clone [your-repository-url]
```

### 5. Copy Files from the Cookiecutter Template

Copy the generated files from the Cookiecutter template into your cloned repository.

### 6. Commit and Push Changes

Commit the changes and push them to your GitHub repository:

```bash
git add .
git commit -m "Initial commit"
git push origin main
```

### 7. Create a PyPI API Token

1. Visit [pypi.org](https://pypi.org) and log in or create an account.
2. Navigate to `Account Settings` > `API Tokens`.
3. Create a new API token with the `Entire account` scope. Copy the token for later use.

### 8. Add PyPI Credentials to GitHub Secrets

Store your PyPI credentials securely in your GitHub repository:

1. Go to your repository on GitHub.
2. Navigate to `Settings` > `Secrets` > `New repository secret`.
3. Add the following secrets:

- `PYPI_USERNAME`: Use `__token__` as the value.
- `PYPI_PASSWORD`: Use the API token you copied earlier.

### 9. Create a GitHub Release

Trigger the deployment of your package by creating a release on GitHub:

1. Go to the `Releases` section in your GitHub repository.
2. Click `Draft a new release`.
3. Follow the prompts to create the release.

### 10. Enable GitHub Pages

To host documentation or other static content, enable GitHub Pages:

1. Navigate to `Settings` > `Pages`.
2. Select the `gh-pages` branch as the source.
3. Click `Save`.

### 11. Manage Versioning with bump-my-version

Use `bump-my-version` to handle version updates for your package:

1. Perform a dry run to preview changes:

```bash
bump-my-version bump [patch/minor/major] --dry-run --verbose
```

2. Apply the version bump:

```bash
bump-my-version bump [patch/minor/major]
```

### 12. Push Version Tags and Changes

After updating the version, push the changes and tags to GitHub:

```bash
git push --tags
git push
```

### 13. Create a New GitHub Release

Finally, create a new release on GitHub to reflect the updated version:

1. Repeat the process described in **Step 9**.

## Conclusion

By following this guide, you can efficiently set up, configure, and manage a Python package using Cookiecutter and related tools. This workflow ensures consistency, automates repetitive tasks, and simplifies the process of distributing your package.

For more information, refer to the official documentation of [Cookiecutter](https://github.com/cookiecutter/cookiecutter) and [bump-my-version](https://github.com/callowayproject/bump-my-version).
