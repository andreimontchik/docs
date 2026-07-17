# Install
  * Linux:
    1. [Download deb archive](https://code.visualstudio.com/download)
    1. Install: `sudo apt update; sudo dpkg -i code_xxx.deb`
  * MacOS:
    1. Download: https://code.visualstudio.com/
    1. Extract from the downloaded archive and move to the Applications folder. 

# Configure
1. Linux: make sure that the "Fractional Scaling" is disabled in Displays configuration, otherwise fonts might be blury.
1. Create or replace the `settings.json` file contents with the following to set fonts, disable annoying suggestions etc. File location:
   * Linux: `~/.config/Code/User/`
   * MacOS: `/Users/andrei/Library/Application Support/Code/User/`
```
{
    "workbench.colorTheme": "Default Light Modern",
    "workbench.colorCustomizations": {
        "editor.lineHighlightBackground": "#F3EFEE",
        "editor.background": "#FFFFFF", // Set to white for a lighter background
        "editor.foreground": "#000000"
    },
    "editor.rulers": [],
    "editor.hover.enabled": false,
    "editor.suggest.preview": false,
    "editor.quickSuggestions": {
        "other": false,
        "comments": false,
        "strings": false
    },
    "editor.suggestOnTriggerCharacters": false,
    "editor.suggest.showWords": false,
    "rust-analyzer.hover.actions.enable": false,
    "rust-analyzer.hover.actions.updateTest.enable": false,
    "rust-analyzer.hover.actions.debug.enable": false,
    "rust-analyzer.hover.actions.gotoTypeDef.enable": false,
    "rust-analyzer.hover.actions.implementations.enable": false,
    "editor.fontFamily": "'Fira Code', monospace",
    "editor.fontLigatures": true,
    "editor.fontWeight": "400",
    "editor.fontSize": 14,
    "editor.formatOnSave": true,
    "git.enableSmartCommit": true,
    "git.confirmSync": false,
    "terminal.integrated.fontWeight": "normal",
    "terminal.integrated.fontFamily": "Courier New",
    "lldb.useBundled": true,
    "lldb.verboseLogging": true,
}
```
1. Configure the keyboard shortcut to manually request CoPilot suggestions: 
   1. Open the Keyboard Shortcuts: `Ctrl+K Ctrl+s`.
   1. Search for "GitHub Copilot: Open Completions Panel".
   1. Assign the `Ctrl+Shift+0` key sequence.
1. Restart VSCode.

# Support Rust
## Install and configure Rust extensions
* Install the `rust-analyzer` extension to support Rust.
* Install the following system libraries are installed, they are required by `codelldb`: `sudo apt install build-essential libstdc++-12-dev libclang-dev
`
* Install the CodeLLDB plugin by Vadim Chugunov for debugging.
* Restart VSCode.

## Debug Rust library
Create Launch configuration to run application that uses the library. Example: 
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "LQE",
            "type": "lldb",
            "request": "launch",
            "program": "${workspaceFolder}/target/debug/lqe",
            "args": [],
            "cwd": "${workspaceFolder}",
            "envFile": "${workspaceFolder}/dev.env",
            "stopOnEntry": false
        }
    ]
}
```

# Support Typescript
1. Install and configure [NodeJS and TypeScript](JavaScript/#nodejs).
1. Install Prettier: `npm install --save-dev prettier`
1. Install the Prettier VSCode extension, required for formatting the TypeScript files.
1. Add the following to settings.json: 
   ```
   {
     "editor.defaultFormatter": "esbenp.prettier-vscode",
     "editor.formatOnSave": true
   }

```


