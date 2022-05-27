# Data Science Playbook

This project focuses on sharing the best practices to create Data Science and Analytics products. It suggests several best-in-class tools, but as tools and standards flexibility is a natural part of any Data Science project, we encourage people to take and adapt whatever piece of this project is useful for their Data Science projects. The following tools are suggested as part of the optimal Data Science workflow:

- `Python`
- `SQL - PostgreSQL`
- `VS Code`
- `Linux - WSL`
- `Spark - PySpark`

## Installation

- Clone the project.
- Run `[Bash] Poetry shell` to create the Poetry virtual environment.
- Run `[Bash] Poetry install` to install all the dependencies.
- Run `[Bash] pre-commit install --hook-type commit-msg` and `[Bash] pre-commit install` to install the pre-commits.

## Usage

- Please refer to the references folder to access the best practices and cheat sheets documentation.

## Project structure

```file

├── .flake8                                  <- Flake8 config file
├── .gitignore                               <- Git .gitignore file
├── .gitlint                                 <- Gitlint config file
├── .gitmessage                              <- Git commit message template
├── .markdown.yaml                           <- Markdownlint-cli2 config file
├── .pre-commit-config.yaml                  <- Pre-commit config file
├── .python-version                          <- Pyenv config file
├── LICENSE                                  <- Project license
├── Poetry.lock                              <- Poetry lock file
├── .pydocstyle                              <- Pydocstyle config file
├── pyproject.toml                           <- Project config file
├── README.md                                <- The top-level README for developers using this project
│
└── references                               <- Data dictionaries, manuals, and all other explanatory materials
    ├── best-practices                       <- Best practices documentation
    |   ├── codes-and-workflow.md            <- Codes and workflow best practices documentation
    |   ├── environment-setup.md             <- Environment setup using suggested tools documentation
    |   └── tools-selection.md               <- Optimal tools selection documentation
    └── cheat-sheets                         <- Selected tools cheat sheets
        └── python-core-elements.md          <- Python core elements cheat sheet
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## TODOs

- [ ] Cheat-sheets:
    - [ ] Python - core elements (WIP)
    - [ ] Python - Scikit-learn
    - [ ] Python - PySpark
    - [ ] Python - visualization and dashboarding
    - [ ] SQL - core elements
    - [ ] SQL - administration and DB optimization
- [ ] Best practices documentation:
    - [ ] Codes and workflow (WIP)
    - [ ] Environment setup (WIP)
    - [ ] Tools selection (WIP)
- [ ] Key concepts documentation:
    - [ ] Data Science and ML
    - [ ] SQL and DB architecture
    - [ ] Big data
- [ ] Jupyter notebooks and scripts:
    - [ ] Standard data preparation and analysis
    - [ ] Segmentation modeling
    - [ ] Classification modeling

## License

[MIT](https://choosealicense.com/licenses/mit/)
