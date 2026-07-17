# Installation

## Python

1. Install Python3:

   ```
   sudo apt update;
   sudo apt install python3 python3-env python3 pip
   ```

1. Check the installed Python version: `python3 --version`
1. Create project directory.
1. create venv in the project directory: `python3 -m venv .venv`

## VSCode

1. Activate the Python venv: `source .venv/bin/activate`
1. Install the Misrosoft Python VSCode extension.
1. Configure the Python interpreter:
   1. `Ctrl + Shift + P`
   1. Selecte "Python: Select Interpreter"
   1. Select `.venv/bin/python`
1. Activate Python venv on VSCode startup:
   Add to .vscode/settings.json
   ```json
   {
     "python.defaultInterpreterPath": "${workspaceFolder}/.venv/bin/python",
     "python.terminal.activateEnvironment": true
   }
   ```
1. Create `requirements.txt` and add required libraries to it.
1. Install the required libraries: `pip install -r requirements.txt`

## Install Nimpy
1. Activate venv
1. `sudo apt update; sudo apt install nim`
1. `nimble install nimpy`