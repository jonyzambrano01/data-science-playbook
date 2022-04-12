# Notebook Overview

- Description:
    - This notebook is focused on best practices related to codes and workflow.

- Table of contents:
    - [Notebook Overview](#notebook-overview)
        - [Git Workflow](#Git-workflow)
        - [Code Format and Structure](#syntax)
            - [Python](#python)
            - [SQL](#sql)
            - [Markdown](#markdown)

## Workflow

### Git Workflow

- Usage: use Git for all your projects, no matter the size.
- Commits:
    - Commit every time you have added a new piece of code (unit of work) that is working and compiles.
    - Run ```[bash] pre-commit``` before each commit to verify everything is working well.
    - If the `Gitlint` pre-commit fails run `[bash] git_last_msg` - which is an alias of `[bash]git log -1 --pretty=%B` - to retrieve the last message or run `[bash] git commit --amend` to try again.
- Push: only push when the feature/problem you are working on is done.
- Pull & fetch: every time you are going to start and before committing.
- Solo projects workflow:
    - Follow the [Git for solo development guide](https://rb.gy/ewfiap), the [Git quick guide](https://rb.gy/102pkh), and the [Git workflows documentation](https://rb.gy/a2arsk).
    - Create the following branches:
        - Main: public branch of the project. It can be altered only from the dev branch.
        - dev: development branch for maintenance, bug-fixing, or modifying features.
        - For complex enough projects that are production-oriented:
            - feature-name-branch: whenever there is a new big enough feature that can be developed independently from the dev branch.
    - Workflow representation:

        ```bash
        # Create a new dev branch
        git checkout -b dev
        # Check dev branch status
        git status
        # Add files
        git add -A
        # Commit - make sure to use a template
        git commit
        # Switch branches
        git checkout main
        # Merge branches into master
        git merge dev
        # Push to origin (remote)
        git push
        ```

- Documentation:
    - Commit:
        - Use [Gitlint](https://rb.gy/su7hjn).
        - use a template, e.g:

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

    - README file:
        - Follow the [make a README guide](https://rb.gy/z5nle8).
        - Follow the [choose an open source license guide](https://rb.gy/oektp5).
        - Use a template, e.g:

            ```file
            # <name of the project>
            
            <project description>
            
            ## Installation
            
            <installation instructions>
            
            ## Usage

            <usage instructions>
            
            ## Project structure

            <project structure explanation>
            
            ## Contributing

            [contribution instructions] - if it is an open-source project.

            ## TODOs

            <task on the pipeline> - use checkboxes.
            
            ## License

            <license url> - most of the time, it is MIT.
            ```

## Code Format and Structure

### Python

- Code formatting best practices:
    - Follow the [Python 3.7 documentation](https://rb.gy/dfwtqp).
    - Follow general [PEP8](https://rb.gy/cnobzx) standards (use [Flake8](https://rb.gy/x4x0yu) and [Pep8-naming](https://rb.gy/spqxo2)) and use [Black](https://rb.gy/tyturl) and [Isort](https://rb.gy/0krdc2) for auto-formatting.
    - Use correct typing ([Mypy](https://rb.gy/tdehcu)) and Docstrings documentation ([Pydocstyle](https://rb.gy/2efmp1)).
    - Use a 79 characters line limit. If continuation is not possible to ensure this, use line break lines `\`. If line breaking needs to occur around binary operators (e.g., `+` and `*`), it should be before the operator.
    - Use blank lines sparingly inside functions/blocks of code to show clear steps.
    - Following binary operators with a single space on either side (`=`, `+=`, `-=`, `==`, `!=`, `>`, `<`, `>=`, `<=`, `and`, `not`, `or`, etc.).
    - Don't use spaces before a comma, semicolon, or colon.
    - Prioritize double quotes `""` over single quotes `''`.
    - For `f-strings` use `{}` and `format()` instead of `%s`.
- Code logic best practices:
    - Don't compare booleans with `True` or `False`:
        - Incorrect: `[python] if my_bool == False`.
        - Correct: `[python] if not my_bool`.
    - Use only one return statement (if possible) in each function.
    - Use `*args` and `**kwargs` only when it is absolutely necessary.
    - Use ternary expressions when possible: `[python] reward = "1000 dollars" if score > 90 else "500 dollars"`.
    - Use list comprehensions: `[python] square_numbers = [number**2 for number in range(5)]`
    - When opening a file, always use the `with open()` statement.
- Naming conventions:
    - Variable and function names are in `lower_case` and `snake_case`.
    - Constant names are in `UPPER_CASE` and `SNAKE_CASE`.
    - Classes are in `CamelCase`.
    - Don't use names longer than 30 characters.
    - Names must begin with a letter and may not end with an underscore.
    - Use `__` for throwaway variables (e.g., unpacking or tuples results).
    - Variable names must describe the information represented by the variable.
    - Don't use **magic numbers** - variables/constants that are hardcoded and/or have a non-intuitive name:
        - Incorrect:

            ```python
            # loop the number of weeks
            w = 52
            for i in range(w):
            ```

        - Correct:

            ```python
            # loop the number of weeks
            NUMBER_OF_WEEKS = 52
            for week in range(NUMBER_OF_WEEKS):
            ```

    - Avoid abbreviations, but if used, document them properly.
    - Only use letters, numbers (try to avoid), and underscores in names. Avoid the use of multiple consecutive underscores.
- Comments:
    - Use blank lines sparingly (especially in-line ones) but don't use them to explain the obvious.
    - Limit the line length of comments and Docstrings to 72 characters.
    - Use complete sentences, starting with a capital letter and a space between the `#` and the first letter.
    - Indent block comments to the same level as the code they describe and separate paragraphs by a line containing a single `#`.
    - Separate in-line comments by two spaces from the statement.

### SQL

- Code formatting best practices:
    - Use the [SQLFluff auto-formatter](https://rb.gy/t8mv2t).
    - Follow the [SQL style guide](https://rb.gy/rzstqv).
    - Always declare aliases and avoid using `select *`.
    - Use a 79 characters line limit.
- Naming conventions:
    - Use always `lower_case` and `snake_case` for statements, columns names, and tables names declaration.
    - Aliases must describe the information represented by the tables - avoid abbreviations.
    - Avoid plural names for tables/columns.
    - Make sure that the name is not a reserved keyword.
    - Don't use names longer than 30 characters.
    - Names must begin with a letter and should not end with an underscore.
    - Never give a table the same name as one of its columns and vice versa.
    - Only use letters, numbers (try to avoid), and underscores in names. Avoid the use of multiple consecutive underscores.
    - Do not use prefixes for tables like `tab_` or stored procedures like `stp_`.
    - Stored procedures names must contain a verb.
    - Use `_id` suffix to define the unique identifier, such as a column that is a primary key.
- Code logic best practices:
    - Use `with()`, `between()` and `in()` statements as much as possible instead of nested tables, multiple `and`s or multiple `or`s.
    - Use abundant simple queries instead of fewer complex ones.
    - Where possible, do not use vendor-specific data types and functions.
- Comments:
    - Use `/*c style*/` comments for block-level comments and `--` for in-line comments.
    - Separate in-line comments by two spaces from the statement.
    - Use complete sentences, starting with a capital letter and a space between the `/*` and `--` characters.
    - Use comments only if necessary.

### Markdown

- Code formatting best practices:
    - Use the [Markdownlint-cli2 linter](https://rb.gy/lkdvma).
