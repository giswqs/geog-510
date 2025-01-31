# Lab 1

This lab will guide you through creating a Python environment, working with Git and GitHub, and using GitHub features such as issues and discussions.

## Exercise 1: Create a New Python Environment

1. Create a new vairtual environment named `test` using conda, mamba, or uv.
2. Activate the environment.
3. Install a Python package of named [geospatial](https://geospatial.gishub.org).
4. Run `conda list` or `pip list` to verify the package is installed.
5. Run `python -c "import geospatial; print(geospatial.__version__)"` to verify the package is working correctly.
6. Deactivate the environment.
7. Remove the environment using `conda remove --name test --all`.

## Exercise 2: Create a New Git Repository

1. Create a new GitHub repository named `geog510-test` using the GitHub website.
2. Set the repository to public and initialize it with a README file.
3. Clone the repository to your local machine using Git.
4. Create a new file named `test.txt` in the repository and add some text to it.
5. Commit the changes and push them to the remote repository.
6. Create a new branch named `test-branch` and switch to it.
7. Make some changes to the `test.txt` file and commit them.
8. Push the new branch to the remote repository.
9. Create a pull request (PR) on GitHub to merge the changes from `test-branch` into the `main` branch.
10. Merge the PR and delete the `test-branch` branch.

## Exercise 3: Create a New Markdown File

1. Create a new branch named `test-markdown` in the local `geog510-test` repository.
2. Create a new file named `test.md` in the `test-markdown` branch.
3. Add a title to the file using the `#` symbol.
4. Add various sections to the file using headers (`##`, `###`, etc.).
5. Add vairous types of content to the file, such as text, lists, links, images, and code blocks.
6. Commit the changes and push the branch to the remote repository.
7. Create a PR to merge the changes from `test-markdown` into the `main` branch.
8. Merge the PR and delete the `test-markdown` branch.
9. View the rendered Markdown file on GitHub.

## Exercise 4: Create a GitHub Issue

1. Navigate to your `geog510-test` repository on GitHub.
2. Go to the **Issues** tab and click **New issue**.
3. Provide a title and a detailed description.
4. Make sure the description includes various types of content, such as text, lists, links, images, and code blocks.
5. Assign the issue to yourself and add a label.
6. Submit the issue.
7. Add a comment to the issue, then close it.

## Exercise 5: Use GitHub Discussions

1. Enable **GitHub Discussions** for your `geog510-test` repository.
2. Create a new discussion topic under the **Q&A** category.
3. Add a title and description to the discussion.
4. Make sure the description includes various types of content, such as text, lists, links, images, and code blocks.
5. Post the discussion and reply to it.
6. Mark a reply as the accepted answer.
7. Close the discussion.

## What to Submit

1. Exercise 1: Write the output of `python -c "import geospatial; print(geospatial.__version__)"`.
2. Exercise 2: A link to the GitHub pull request.
3. Exercise 3: A link to the Markdown file on GitHub.
4. Exercise 4: A link to the GitHub issue.
5. Exercise 5: A link to the GitHub discussion.
