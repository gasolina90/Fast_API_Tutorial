## Creating a virtual environment with Python
1. Create a virtual environment ONCE PER PROJECT
    * Run in bash, terminal, or CMD:

        ```bash
        python -m venv .venv
        ```
        * What it means:
        
        `python`: use the program called python
        
        `-m`: call a module as a script, we'll tell it which module next

        `venv`: use the module called venv that normally comes installed with Python

        `.venv`: create the virtual environment in the new directory .venv

2. Activate the virtual environment
    * Do this EVERY TIME you start a new terminal to work on project, navigate to project directory within Windows Powershell

        **FOR THE FIRST TIME**
        ```PowerShell
        Windows PowerShell

        .venv\Scripts\Activate.ps1
        ```
    * Every time you install a new package in that environment, **activate the environment again** with this command:
        ```PowerShell
        activate
        ```

3. Check the Virtual Environment is active, navigate to project directory, if not there already:
    * Open new terminal > Launch profile > PowerShell
        ```PowerShell
        Windows PowerShell
        
        Get-Command python
        ```
    * If it shows the python binary at .venv\Scripts\python, inside of your project, then it worked
        ![venv active confirmation][Fast_API_Tutorial\Images\Screenshot 2026-05-31 154521.png]

4. Upgrade PIP
    * Many package installation errors ocur because of an outdated PIP
        ```Bash
        python -m pip install --upgrade pip
        ```

5. Add .gitignore
    * Add a .gitignore to exclude everything in your `.venv` directory from Git
        ```Bash
        echo "*" > .venv/.gitignore
        ```

    * What it means:

        `echo "*"`: will print the text * in the terminal

        `>`: anything printed to the terminal by the command to the left of > should not be printed but instead written to the file that goes to the right of >

        `.gitignore`: the name of the file where the text should be written

        And * for Git means "everything". So, it will ignore everything in the .venv directory.

        That command will create a file .gitignore with the content: `*`

6. Install Packages
    * ONLY after activating the environment
    * Installing them directly if time is very limited
        ```Bash
        pip install "fastapi[standard]"
        ```
    * Installing them from requirements.txt

7. Deactivate the Virtual Environment
    * Deactivate the venv when done working with:
        ```Bash
        deactivate
        ```

## Configuring the app entrypoint:
1. Recommended to configure the `entrypoint` in a `.toml` file for when the project grows/scales up.
    * Create `.toml` file in the root folder of your project (`Fast_API_Tutorial`)
    * Write in it:
        ```TOML
        [tool.fastapi]
        entrypoint = "main:app"
        ```
        * Only if the .toml is within another directory, such as backend, then write `entrypoint = backend.main:app`

    * Otherwise, for small projects you can configure the entrypoint in the command while in the .venv with:
        ```Bash
        fastapi dev --entrypoint main:app
        ```
        * You MUST ALWAYS remember to pass the correct path/entrypoint every time you call the `fastapi` command if using this technique