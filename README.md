# Commitizen

Commitizen offers more than just the ability to structure git commit messages. It's a powerful tool that, when combined with CI/CD pipelines like GitHub Actions, can automate version management and changelog creation. This guide provides a detailed, step-by-step walkthrough, from installation to versioned releases.

## 1. Installation

### 1.1. Python Installation

First, ensure you have Python and pip installed. If not, install them:

\```bash
sudo apt-get update
sudo apt-get install python3 python3-pip
\```

### 1.2. Install Commitizen

**Global Installation**:

\```bash
sudo pip3 install -U Commitizen
\```

**Local Project Installation**:

\```bash
pip3 install -U Commitizen
\```

## 2. Setup Your Project

### 2.1. Initialize a Git Repository

If your project isn't already a git repository, initialize it:

\```bash
git init
\```

### 2.2. Commitizen Configuration

Setting up Commitizen is straightforward thanks to the `cz init` command. This command will prompt you to select a configuration file and a commit convention.

1. **Initialize Configuration**:
   
   Run the following command to initiate the setup process:

\```bash
cz init
\```

2. **Select Configuration File**: 
   
   When prompted, choose `pyproject.toml` as the configuration file. We opt for `pyproject.toml` specifically because we are working on a Python project, and this file has become the standard for storing Python project configurations.

3. **Choose Commit Convention**:
   
   For the commit convention, select the "cz_conventional_commits" option to adhere to the conventional commits rule.

## 3. Making Commits Using Commitizen

### 3.1. Make Changes in Your Project

Make some changes in your project. This could be anything from adding a new feature, fixing a bug, or updating documentation.

### 3.2. Add Changes to Git

\```bash
git add .
\```

### 3.3. Commit Using Commitizen

Instead of the usual `git commit`, use:

\```bash
cz commit
\```

Follow the prompts to create a structured commit message.

## 4. Using Commitizen with a Branching Strategy

### 4.1. Create a Feature Branch

Before implementing a new feature or bugfix, create a separate branch:

\```bash
git checkout -b feature/your-feature-name
\```

### 4.2. Make Changes and Commit Using Commitizen

Repeat the steps from section 3 to make and commit your changes.

### 4.3. Push the Feature Branch to Remote

\```bash
git push origin feature/your-feature-name
\```

### 4.4. Create a Pull Request

Use your git platform (like GitHub or GitLab) to create a pull request to merge the feature branch into the main branch.

## 5. Automated Version Bumping with GitHub Actions

Upon merging a pull request, you can utilize GitHub Actions to automatically bump the version and generate a changelog.

### 5.1. GitHub Action Setup

In your repository, navigate to `.github/workflows` (create the directory if it doesn't exist). Create a new YAML file for the action, e.g., `bump_version.yml`. Populate it with:

```yaml
name: Bump version

on:
  pull_request:
    types: [closed]
    branches:
      - main

jobs:
  bump-version:
    if: "github.event.pull_request.merged == true && !startsWith(github.event.pull_request.title, 'bump:')"
    runs_on: ubuntu-latest
    steps:
      - name: Check out
        uses: actions/checkout@v3
        with:
          token: "${{ secrets.PERSONAL_ACCESS_TOKEN }}"
          fetch-depth: 0
      - name: Bump version and generate changelog
        uses: commitizen-tools/commitizen-action@master
        with:
          github_token: ${{ secrets.PERSONAL_ACCESS_TOKEN }}
```

### 5.2. Merging Pull Requests

When you merge a pull request, the action will automatically bump the version based on the commits. It will also generate a changelog for you.

## 6. Conclusion

With Commitizen and GitHub Actions, you can maintain a clean commit history, automatically manage versions, and generate changelogs effortlessly. This guide should equip you with the knowledge to integrate Commitizen into your workflow, but for more advanced configurations or details, refer to the official [Commitizen documentation](https://commitizen-tools.github.io/commitizen/).
