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
    * Do this EVERY TIME you start a new terminal to work on project, in Bash
        ```bash
        Windows Git Bash

        source .venv/Scripts/activate
        ```
        ```PowerShell
        Windows PowerShell

        .venv\Scripts\Activate.ps1
        ```


    * Every time you install a new package in that environment, **activate the environment again**