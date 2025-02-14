# Lab 3

This lab guides you through the process of creating, setting up, documenting, and publishing a Python package for geospatial applications. By the end of this lab, you will have a structured package with version control, automated checks, and online documentation.

## Exercise 1: Create a Python Package Using Cookiecutter

**Objective:**
Generate a well-structured Python package using a standardized template.

**Instructions:**

1. Install Cookiecutter if you haven't already:
   ```bash
   pip install cookiecutter bump-my-version
   ```
2. Use the following template to create your package:
   ```bash
   cookiecutter gh:opengeos/cookiecutter-pypackage
   ```
3. Follow the prompts to customize your package.
4. Create a new repository on GitHub and push your package code to it.

**References:**

- [Cookiecutter instructions](https://geog-510.gishub.org/book/software/cookiecutter.html)
- [Python package Template](https://github.com/opengeos/cookiecutter-pypackage)

---

## Exercise 2: Set Up Pre-Commit Hooks

**Objective:**
Automate code quality checks using pre-commit hooks to enforce best practices.

**Instructions:**

1. Navigate to https://pre-commit.ci and sign in with your GitHub account.
2. Add your package repository to pre-commit.ci.
3. Create a `.pre-commit-config.yaml` file in your repository or use an example configuration:
   [Example Pre-Commit Config](https://github.com/giswqs/geodev/blob/main/.pre-commit-config.yaml)
4. Install the pre-commit hooks:
   ```bash
   pre-commit install
   ```
5. Test the hooks by running:
   ```bash
   pre-commit run --all-files
   ```
6. Commit the `.pre-commit-config.yaml` file and push it to GitHub.

---

## Exercise 3: Enable MkDocs for Documentation

**Objective:**
Set up an online documentation site for your package using MkDocs. The cookiecutter template already includes MkDocs, so you can start writing documentation right away.

**Instructions:**

1. Install required packages for documentation:
   ```bash
   cd YOUR-PACKAGE-REPO
   conda activate YOUR-ENV-NAME
   pip install -r requirements_dev.txt
   ```
2. Update Markdown files in the `docs/` directory.
3. Serve the documentation locally:
   ```bash
   mkdocs serve
   ```
4. Commit and push the changes to GitHub.
5. Enable GitHub Pages and use the `gh-pages` branch for the source.

**Reference:**
[Example MkDocs Website](https://geodev.gishub.org)

---

## Exercise 4: Make a GitHub Release and Publish on PyPI

**Objective:**
Create a package release and distribute it to PyPI.

**Instructions:**

1. Bump the package version using `bump-my-version`:
   ```bash
   bump-my-version bump patch/minor/major
   ```
2. Commit the version change and push it to GitHub.
   ```
   git push
   git push --tags
   ```
3. Create a GitHub release:
   - Go to the "Releases" tab on GitHub.
   - Click "Draft a new release."
   - Select the tag version from the dropdown.
   - Click "Generate release notes."
   - Click "Publish release."
4. Make sure your package is automatically published on PyPI using GitHub Actions.

**Reference:**
[Example GitHub Release](https://github.com/giswqs/geodev/releases/tag/0.0.1)

---

## Submission Requirements

Submit the following information:

1. A link to your package repository on GitHub.
2. A link to the pre-commit yaml file in your repository.
3. A link to the online documentation site for your package.
4. A link to the GitHub release page for your package.
5. A link to your package on PyPI.

## Summary

In this lab, you have:

✅ Created a Python package using Cookiecutter

✅ Set up pre-commit hooks for automated code quality checks

✅ Enabled MkDocs for documentation

✅ Released and published your package on PyPI

Now, your package is ready for distribution and use by the geospatial community! 🚀
