# `web-template-vue`

GitHub repo template for generating a web component repo with a Vue project, for a similar
Next.js-React template see sibling repo [`web-template-react`](https://github.com/mkdevops-se/web-template-react).

## Getting Started

Hit the [Use this template](https://github.com/mkdevops-se/web-template-vue/generate) button
to create your own Vue 2.x repository. After your repository is created, allow for a few minutes
to pass while the _Template Cleanup_ GitHub Actions Workflow perform setup of the repo
([example](https://github.com/mblomdahl/mats-web-project/actions/runs/3256048235/jobs/5346008221)).

## Developing the Template

Have a Python 3 virtual environment and `cookiecutter`:

    python3 -m venv venv
    . venv/bin/activate
    pip install cookiecutter

Set intended repo name and GitHub owner:

    export REPO_NAME=mats-vue-project
    export GITHUB_USERNAME=mblomdahl

Generate project from template:

    cookiecutter --no-input --output-dir . archetype/web_vue2 \
      repo_name=$REPO_NAME github_username=$GITHUB_USERNAME

Remove Cookiecutter templating, move generated project into repo root and commit:

    rm -rvf archetype/ .github/
    mv -v $REPO_NAME/* .
    mv -v $REPO_NAME/.github .
    mv -v $REPO_NAME/.gitignore .
    rm -rvf $REPO_NAME/
    git add .
    git commit -m"Generated $REPO_NAME from Cookiecutter"

Review the generated project, run the project setup steps from the re-created root README:

    yarn install && yarn build && yarn lint

Finally, reset your branch to the origin state:

    git reset --hard origin HEAD
