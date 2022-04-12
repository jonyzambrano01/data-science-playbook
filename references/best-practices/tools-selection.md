# Notebook Overview

- Description:
    - This notebook is focused on tools selection for an optimal Data Science workflow.
    - Some tools may be excluded based on:
        - (pop) popularity: unpopular tools that are not widely used or are not very well documented/maintained.
        - (osy) operating system: unsupported on `Windows`, `Linux` or `macOS` - prioritize tools that are OS agnostic.
        - (int) integration: difficult to integrate with other tools.
        - (dep) dependencies: requires extra dependencies or tools to work.
        - (wfl) workflow: does not follow the desired workflow.
        - (old) old/low-performance tools: old tools that, despite being powerful, have newer and better competitors.
        - (sco) scope or complexity: the tool is too comprehensive/complex or too simple for the defined scope.
- Table of contents:
    - [Notebook Overview](#notebook-overview)
        - [Tools Selection](#tools-selection)
            - [Summary](#summary)
            - [Data Science Core Tools](#data-science-core-tools)
                - [Script Formatting](#script-formatting)
                    - [Python](#python)
                    - [SQL](#sql)
                    - [Markdown](#markdown)
                - [Package Management, Virtual Environments, and Different Python Versions](#package-management-virtual-environments-and-different-python-versions)
                - [Versioning Control](#versioning-control)
                - [Data Science Projects Folder Structure And Workflow](#data-science-projects-folder-structure-and-workflow)

## Tools Selection

### Summary

- Data Science core tools:
    - Script formatting:
        - Python:
            - `Flake8` due to its versatility, plugins, and fewer false positives.
            - `Black` due to its popularity and simplicity (less to choose is better in this context).
            - `Mypy`, `Pep8-naming`, `Pydocstyle`, and `Isort` were the only good tools of their type.
        - SQL: `SQLFluff` is the only good tool of its type.
        - Markdown: `Markdownlint-cli2` is the only good tool of its type.
        - Package management, virtual environments, and different `Python` versions: `Poetry` due to its capabilities (environments and package management) and works great along with `Pyenv`.
        - Versioning Control:
            - `Git` is the only good tool of its type.
            - `DVC` should suffice for most projects.
            - `Delta Lake` could be useful on very complex projects in which there is a necessary integration with big data tools along with `MLflow`.
        - Data Science projects folder structure And workflow: `Cookiecutter` is the only good tool of its type.

### Data Science Core Tools

#### Script Formatting

##### Python

- Linters (`PEP8` enforcement, typing, and consistency checks):
    - General errors and conventions:
        - [Flake8](https://rb.gy/x4x0yu):
            - (+) checks inconsistencies and `PEP8` guidelines.
            - (+) wide usage and integration with useful plugins:
                - [Pep8-naming](https://rb.gy/spqxo2): ensure naming conventions.
            - (-) not as comprehensive in errors detection as other options.
        - [Pylint](https://rb.gy/arzkkk):
            - (+) check inconsistencies and `PEP8` guidelines.
            - (+) very comprehensive set of errors.
            - (-) many false positives.
            - (-) very whiny and difficult to get a perfect code without errors.
        - Excluded options: [YALA](https://rb.gy/quuzlr) (pop), [Coala](https://rb.gy/wxwf49) (pop), [Pylama](https://rb.gy/ydzqz0) (pop).
    - Naming conventions:
        - [Pep8-naming](https://rb.gy/spqxo2): only good option available.
    - Typing:
        - [Mypy](https://rb.gy/tdehcu): only good option available.
        - Excluded options: [Pytype](https://rb.gy/avt21t), [Pyre](https://rb.gy/hmqufk) (osy - does not support `Windows`), [pyright](https://rb.gy/q34dvi) (dep - requires `Node JS` to be installed).
    - Docstrings (`PEP257` enforcement):
        - [Pydocstyle](https://rb.gy/2efmp1): only good option available.
- Auto-formatters:
    - General use:
        - [YAPF](https://rb.gy/xrtts3):
            - (+) high flexibility and styles.
            - (-) variable - the same file can be formatted in different ways at different iterations.
            - (-) does not organize imports.
        - [Black](https://rb.gy/tyturl):
            - (+) deterministic.
            - (+) static (low flexibility) - focused on consistency.
            - (-) just beautifies the code. Do not fix the code to follow `PEP8` guidelines.
            - (-) does not organize imports.
        - [Autopep8](https://rb.gy/qtkmxm):
            - (+) wide usage in the community.
            - (+) fixes the code to follow the `PEP8` guidelines.
            - (-) does not check any inconsistency on the code.
            - (-) does not beautify the code.
    - Format imports:
        - [Isort](https://rb.gy/0krdc2): only good option available.
        - Excluded options: [Flake8-import-order](https://rb.gy/xb260m) (wfl - auto-formatters make a better job here in the workflow).

##### SQL

- Linters/auto-formatters:
    - [SQLFluff](https://rb.gy/t8mv2t): only good option available.

##### Markdown

- Linters/auto-formatters:
    - [Markdownlint-cli2](https://rb.gy/lkdvma): only good option available.
    - Excluded options: [Markdownlint](https://rb.gy/pe28pg), [markdownlint-cli](https://rb.gy/dvhllh) (wfl - not easy to integrate with `Pre-commit` or not easy to integrate with code editors), [Pymarkdown](https://rb.gy/mwu3l9) (pop).

#### Package Management, Virtual Environments, and Different Python Versions

- [Pyenv](https://rb.gy/w9oegv):
    - (+) best tool to manage `Python` versions.
    - (+) very popular option.
    - (+) good documentation.
    - (-) not optimal to manage virtual environments and packages.
- [Virtualenv](https://rb.gy/oyhe6a) and [Virtualenvwrapper](https://rb.gy/lmaxrk):
    - (+) more control over the installed libraries.
    - (+) free even for commercial use.
    - (+) recommended by PyPa (`Python` Packaging Authority) for versions < 3.5.
    - (-) can be more complicated to set up than other options `Python`.
    - (-) copy the `Python` interpreter to another location.
    - (-) less capable package management than other options.
- [Venv](https://rb.gy/xa4nyl):
    - (+) native tool in `Python` - no need to install extra libraries.
    - (+) recommended by PyPa (Python packaging authority) for versions >=3.5.
    - (-) not available for versions < 3.3.
    - (-) less capable package management than other options.
- [Pipenv](https://rb.gy/wzpoku):
    - (+) wide usage.
    - (+) can be used to manage multiple `Python` versions as well.
    - (+) recommended by PyPa (Python packaging authority) for environments and packages management.
    - (-) more difficult to set up and manage than other tools.
    - (-) integration problems with `WSL`.
- [Poetry](https://rb.gy/vddgaa):
    - (+) increasing momentum in the community.
    - (+) more flexible and powerful than other options (locations and interpreters are easily changed, dev and prod dependencies are managed separately).
    - (+) recommended by PyPa (Python packaging authority) for environments and packages management.
    - (-) more recent development - adoption is not enough yet.
- Excluded options: [PEW](https://rb.gy/oaz5mu) (pop - last development was in 2018), [Conda](https://rb.gy/ulzwvv) (dep).

#### Versioning Control

- Code version management:
    - [Git](https://rb.gy/zd2fk5): only good option available.
    - Excluded options: [Mercurial](https://rb.gy/dg94co) (pop).
- Pre-commits setup:
    - [Pre-commit](https://rb.gy/pcglja):
        - (+) easy to use and integrate with most of the linters and auto-formatters.
        - (+) easy to integrate with `Python`.
        - (-) less flexible than other options.
    - [Git hooks](https://rb.gy/twm9ev):
        - (+) high flexibility.
        - (-) high complexity.
        - (-) popular, but not as much as other options.
    - Excluded options: [Husky](https://rb.gy/7b2sjb) (int - more focused on web development).
- Commit messages linters:
    - [Gitlint](https://rb.gy/su7hjn): only good option available.
    - Excluded options: [Commitlint](https://rb.gy/wdctqm) and [Committizen](https://rb.gy/vov41w) (sco - too complex tools, int - more focused on web development).
- Data management and experiments tracking:
    - [DVC](https://rb.gy/syihvp):
        - (+) wide usage.
        - (+) framework agnostic and easy to implement.
        - (+) functionalities beyond data version management - ML models tracking.
        - (+) experiments tracking is not as good as other options.
        - (-) not good supporting big data projects.
    - [Delta Lake](https://rb.gy/troxx6):
        - (+) big data support - `Spark`.
        - (+) integration with cloud services like `Azure`.
        - (-) not flexible
        - (-) complex to use.
        - (-) no ML models tracking.
    - [MLflow](https://rb.gy/kude3g):
        - (+) powerful features for ML models tracking.
        - (+) wide usage.
        - (-) does not have data versioning control.
    - Excluded options: [Git LFS](https://rb.gy/tzrbu5) (wfl - requires dedicated servers that over-complicate the workflow), [Pachyderm](https://rb.gy/jxaxsi) (pop), [LakeFS](https://rb.gy/aupi9r) (pop), [Metaflow](https://metaflow.org/) (dep - dependency on aws), [Kedro](https://rb.gy/9wqbwk) (pop).

#### Data Science Projects Folder Structure and Workflow

- Project structure:
    - [Cookiecutter](https://rb.gy/ixcfnk) and [Cookiecutter-Data-Science](https://rb.gy/ycjiyx) template: only good option available. Some changes may be required depending on the other selected tools and configurations.
    - Excluded options: [Boilr](https://github.com/tmrts/boilrS) (pop).
