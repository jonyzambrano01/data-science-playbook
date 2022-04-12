# Notebook Overview

- Description:
    - This notebook describes the setup of the proposed environment in `Linux`.
    - Non-command line installations are excluded from this notebook.

- Table of contents:
    - [Notebook Overview](#notebook-overview)
        - [Global Setup](#global-setup)
            - [Symlinks](#symlinks)
            - [VS Code](#vs-code)
            - [General Packages, Git, Pyenv, Pip, and Poetry](#general-packages-git-pyenv-pip-and-poetry)
        - [Project Setup](#project-setup)
            - [Pyenv and Poetry](#pyenv-and-poetry)
            - [VS Code Config](#vs-code-config)
            - [Git and GitHub](#git-and-github)
            - [Linting, Format, and Diffs](#linting-format-and-diffs)
                - [python Files](#python-files)
                - [Jupyter Notebooks](#jupyter-notebooks)
                - [Markdown Files](#markdown-files)

## Global Setup

### Symlinks

1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
2. Run `[bash] ln -s <folder path> <name of link>` to add a symbolic link to the `Windows` folders.

### VS Code

1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
2. Install the following extensions:
    - `ms-python.python`: `Python` support.
    - `ms-toolsai.jupyter`: `Jupyter` notebooks support.
    - `davidanson.vscode-markdownlint`:  `Markdown` linter support.
3. Add this to the user settings JSON: `[file] "editor.rulers": [79]` to set the ruler in `Python`.

### General Packages, Git, Pyenv, Pip, and Poetry

- Packages installation:
    1. From `VS Code` in a `Linux` session, open a new terminal.
    2. Run `[bash] sudo apt-get update` to update the `Aptitude package manager`.
    3. Run `[bash] sudo apt install make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl git` to install the dependencies.
- `Git`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
    2. Run `[bash] git config --global user.name "<user name>"` to set up the name.
    3. Run `[bash] git config --global github.user <user>` to set up the user.
    4. Run `[bash] git config --global user.email <email>` to set up the email.
    5. Run `[bash] git config --global core.editor "code -w"` to make `VS Code` the standard `Git` code editor.
    6. Run `[bash] mkdir $HOME/git-config` to create the `Git` config folder in your user and cd to the folder.
    7. Run `[bash] touch .gitmessage` to create a `.gitmessage` file.
    8. Run `[bash] code .gitmessage` to open the file and add the following content. Save and close.

        ```file
        # Structure:
        #
        # --- Start
        # ------------------------------------------------
        # <type>: <description> - no more than 50 chars (check line above)
        # - Type: check type options on the bottom and .gitlint config file
        # - Description: summary, imperative, if it is solving an issue it must start
        #   with fix #<issue number>
        # --- Blank line between tittle and optional body
        # ----------------------------------------------------------------------
        # [optional body] - no more than 72 chars (check line above)
        # - Explain *what* and *why* (not *how*)
        # --- end
        #
        # Types:
        # - feature: new feature
        # - fix: any bug fix you put in place
        # - data: change on the data
        # - docs: changes on documentation
        # - refactor: neither fixes a bug nor adds a feature
        ```

    9. Run `[bash] git config --global commit.template /home/<linux user name>/git-config/.gitmessage` to setup the default commit template.

- `Pyenv`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
    2. Run `[bash] curl https://pyenv.run | bash`.
    3. Run `[bash] code $HOME/.bashrc` to open the `Bash shell script`.
    4. Add the following to the file to include `Pyenv` and the local libraries in the load path:

         ```[file]
            # Pyenv
            export PATH="$HOME/.pyenv/bin:$PATH"
            eval "$(pyenv init -)"
            eval "$(pyenv virtualenv-init -)"
            
            # User-level installed libraries
            export PATH="$HOME/.local/bin:$PATH"
         ```

    5. Run `[bash] source $HOME/.bashrc` to apply the changes on the `Bash shell script`.
    6. Run `[bash] pyenv install -v <python version>` to install an specific `Python` version.
    7. Run `[bash] pyenv global <python version>` to activate the installed `Python` version.
    8. Run `[bash] python3 -m site --user-base` to extract the user base's binary directory.
    9. Run `[bash] code $HOME/.bashrc` to open the `Bash shell script`.
    10. Add `[file] export PATH="$PATH:<user base binary directory>/bin"` to the file and save it to locate the user-level installed libraries going forward.
    11. Add `[file] alias python=python3` to the file and save to use `Python 3` as default going forward.
    12. Run `[bash] source $HOME/.bashrc` to apply the changes on the `Bash shell script`.
    13. Repeat the same installation process `[bash] pyenv install -v <python version>` for each `Python` version that needs to be installed.
- `Pip`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
    2. Run `[bash] pyenv global <python version>` to activate an specific `Python` version.
    3. Run `[bash] wget https://bootstrap.pypa.io/get-pip.py` to apply the changes on the `Bash shell script`.
    4. Run `[bash] sudo python ./get-pip.py` to install `Pip`.
    5. Run `[bash] rm get-pip.py` to remove the `Python` file.
- `Poetry`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
    2. Run `[bash] pyenv global <python version>` to activate an specific `Python` version.
    3. Run `[bash] pip install --user poetry` to install `Poetry`.

## Project Setup

### Pyenv and Poetry

1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
2. Cd to the desired location of the project and run `[bash] mkdir <project name>` to create a new project folder (check standard project name syntax) and cd to the folder.
3. Run `[bash] pyenv local <python version>` to set the version of the project. Remember to use `[bash] pyenv versions` to check the installed `Python` versions.
4. Run `[bash] poetry init` to initialize `Poetry`. Fill the fields (use defaults except for interactive dependencies (type no)).
5. Run `[bash] poetry env use <path to local python>`. The `Python` path can be extracted from running `[bash] pyenv which python`
6. Run `[bash] poetry shell` to activate the environment.
7. Run `[bash] poetry add ipykernel jupyter` to add `Ipykernel` and `Jupyter` and use the same command to include any extra packages.
8. Run `[bash] poetry install` to install all the libraries in the environment.

### VS Code Config

1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux project` folder.
2. Run `[bash] poetry shell` to activate the environment and extract the virtual environment path.
3. Add the next setting to the `VS Code` setting JSON `[file] "python.defaultInterpreterPath": "<virtual environment path>/bin/python"` to add the virtual environment to the settings. Get the path running `[bash] poetry show -v`.
4. Cd to the `.vscode` folder and run `[bash] touch .gitignore` to exclude the `VS Code` config from the `Git` workflow.

### Git and GitHub

1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
2. Run `[bash] git init` to initialize the `Git` files.
3. Setup the user name, user, and email locally depending on the project needs. Don't use the `--global` option.
4. Create a tailored `.gitmessage` depending on the project needs.
5. Run `[bash] git config commit.template .gitmessage` to set up the default commit template.
6. Create the project structure depending on the project needs.
7. Run `[bash] touch .gitignore` to create a `.gitignore` file.
8. Run `[bash] code .gitignore` to open the file and add the rules following the next format. Save and close.

    ```file
    # <path description>
    <path>
    ```

9. Run `[bash] touch .gitkeep` on the empty folders that are necessary to keep.
10. Connect to `GitHub`:
    1. Create a new empty repository on `GitHub`.
    2. Run `[bash] git commit` to commit for the first time.
    3. Run `[bash] git branch -M main` to create the `main` branch.
    4. Run `[bash] git remote add origin <github repository url>`.
    5. Run `[bash] git push -u origin main` to push.
11. Create additional branches and do the workflow setup.
12. Aliases:
    1. Run `[bash] code $HOME/.bashrc` to open the `Bash shell script`.
    2. Add `[file] alias git_last_msg="git log -1 --pretty=%B"` to the file and save it to create an alias to get the last `Git`  commit message.
    3. Run `[bash] source $HOME/.bashrc` to apply the changes on the `Bash shell script`.
13. Pre-commits:
    1. Run `[bash] poetry add gitlint` to install `Gitlint`.
    2. Run `[bash] touch .gitlint` to create a new `Gitlint` configuration file.
    3. Run `[bash] code .gitlint`  to open the file and add the following text to config `Gitlint`:

        ```file
            [general]
            # Ignore certain rules
            ignore=body-is-missing

            # Verbosity
            verbosity = 2

            # Enable community contributed rules
            contrib=contrib-title-conventional-commits

            # Set the line-length
            [title-max-length]
            line-length=50

            # Set the body-length
            [body-max-line-length]
            line-length=72

            # Conventional commits
            [contrib-title-conventional-commits]
            types = feature,fix,data,docs,refactor
        ```

    4. Run `[bash] poetry add pre-commit` to install `Pre-commit`.
    5. Run `[bash] touch .pre-commit-config.yaml` to create a new `Pre-commit` config file.
    6. Run `[bash] code .pre-commit-config.yaml` to open the config file and add the hooks in the following format. `<github tag>` refers to the tag on `GitHub` that corresponds to the version of the package that was installed locally (the versions can be checked on `pyproject.toml`):

        ```file
            repos:
            -   repo: https://github.com/jorisroovers/gitlint
                rev: <github tag>
                hooks:
                - id: gitlint             
            default_language_version:
                python: python<python version>
        ```

    7. Run `[bash] pre-commit install --hook-type commit-msg` to set up the `Git hook` scripts. This specific `Pre-commit` requires a different setup as it is related to commit messages.

### Linting, Format, and Diffs

#### python Files

- Local installation:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
    2. Cd to project home directory.
    3. Run `[bash] poetry shell` to activate the environment.
    4. Run `[bash] poetry add black isort flake8 pep8-naming mypy pydocstyle` to install `Isort`, `Flake8`, `Black`, `Mypy`, `Pep8-naming`, and `Pydocstyle`.
- Config files:
    - `Flake8` (to make it work with the other tools):
        1. From `VS Code` in a `Linux` session, open a new terminal.
        2. Cd to project home directory.
        3. Run `[bash] touch .flake8` to create a new `Flake8` config file.
        4. Run `[bash] code .flake8` to open the file and add the following text. These changes are required to make the library compatible with the rest of the format/linter tools.

            ```file
                [flake8]
                ignore = E302 <notebooks path>/*
                max-line-length = 79
                max-complexity = 18
                select = B,C,E,F,W,T4,B9
                enable-extensions = pep8-naming
            ```

    - `Black`:
        1. Run `[bash] code pyproject.toml` to open the `pyproject` file and add the following text. These changes are required to make the library compatible with the rest of the format/linter tools.

            ```[file]
                [tool.black]
                line-length = 79
                include = '\.pyi?$'
                exclude = '''
                /(
                    \.git
                | \.hg
                | \.mypy_cache
                | \.tox
                | \.venv
                | _build
                | buck-out
                | build
                | dist
                )/
                '''
            ```

- `VS Code`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
    2. Add the following settings to the `VS Code` setting JSON to activate the linters:

        ```file
            "python.linting.enabled": true,
            "python.linting.flake8Enabled": true,
            "python.linting.mypyEnabled": true,
            "python.linting.pydocstyleEnabled": true
        ```

- `Git hooks`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
    2. Run `[bash] code .pre-commit-config.yaml` to open the config file and add the hooks in the following format. `<github tag>` refers to the tag on `GitHub` that corresponds to the version of the package that was installed locally (the versions can be checked on `pyproject.toml`):

        ```file
            -   repo: https://github.com/psf/black
                rev: <github tag>
                hooks:
                - id: black
            -   repo: https://gitlab.com/pycqa/flake8
                rev: <github tag>
                hooks:
                - id: flake8
                additional_dependencies:
                    - pep8-naming==<github tag>
            -   repo: https://github.com/pre-commit/mirrors-mypy
                rev: <github tag>
                hooks:
                - id: mypy
            -   repo: https://github.com/PyCQA/isort
                rev: <github tag>
                hooks:
                - id: isort
            -   repo: https://github.com/PyCQA/pydocstyle
                rev: <github tag>
                hooks:
                - id: pydocstyle
        ```

    3. Run `[bash] pre-commit install` to set up the `Git hook` scripts.

#### Jupyter Notebooks

- Local installation:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` user folder.
    2. Run `[bash] poetry shell` to activate the environment.
    3. Run `[bash] poetry add nbstripout` to install `Nbstripout`.
    4. Run `[bash] poetry add jupytext` to install `Jupytext`. Don't change the metadata config for `Jupytext` as this could cause problems in the `Pre-commit`.
- `Git hooks`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` project folder.
    2. Run `[bash] code .pre-commit-config.yaml` to open the config file and add the hooks in the following format. `<github tag>` refers to the tag on `GitHub` that corresponds to the version of the package that was installed locally (the versions can be checked on `pyproject.toml`):

        ```file
             -   repo: https://github.com/kynan/nbstripout
                 rev: <github tag>
                 hooks:
                 - id: nbstripout
             -   repo: https://github.com/mwouts/jupytext
                 rev: <github tag>
                 hooks:
                 - id: jupytext
                   args: [--sync]
        ```

    3. Run `[bash] pre-commit install` to set up the `Git hook` scripts.

#### Markdown Files

- Local installation:
    - Local installation of `Markdownlint-cli2` is not necessary as it is already included in the `VS Code extensions`.
    1. Run `[bash] touch .mardownlint-cli2.jsonc` to create a new config file.
    2. Run `[bash] code .mardownlint-cli2.jsonc` to open the file and add the following text to configure the rules.

        ```file
            {
                "config":{
                    "default": true,
                    "MD007": {"indent": 4},
                    "MD033": false,
                    "MD013": false}
            }
        ```

- `VS Code`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` project folder.
    2. Add the next settings to the `VS Code` setting JSON to setup the `Markdown` rules:

        ```file
            "markdownlint.config": {
                "default": true,
                "MD007": {"indent": 4},
                "MD033": false,
                "MD013": false
            }
        ```

- `Git hooks`:
    1. From `VS Code` in a `Linux` session, open a new terminal in your `Linux` project folder.
    2. Run `[bash] code .pre-commit-config.yaml` to open the config file and add the hooks in the following format. `<latest version tag>` refers to the recommended version in the `GitHub` repository webpage.

        ```file
            - repo: https://gitbub.com/DavidAnson/markdownlint-cli2
              rev: <latest version tag>
              hooks:
              - id: markdownlint-cli2
        ```
