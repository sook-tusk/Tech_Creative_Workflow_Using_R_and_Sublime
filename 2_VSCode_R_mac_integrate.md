
# anaconda download
Follow the instructions here: <https://www.anaconda.com/download/success?reg=skipped>

Accept default settings and complete the installation process. We then activiate the conda environment.

In the Mac zsh terminal, type `. /Users/yourname/anaconda3/bin/activate && conda activate /Users/yourname/anaconda3; `.

For example:
```
(base) yourname@Mac ~ % . /Users/yourname/anaconda3/bin/activate && conda activate /Users/yourname/anaconda3; 
(base) yourname@Mac ~ % 
```
# to install radian, type this in the Terminal.
uv tool install radian

See details here: <https://github.com/randy3k/radian>

# in VSCode, install Extensions 
R by REditorSupport 

# configure VScode json 
```json
{
    "editor.fontSize": 15,
    "terminal.integrated.fontSize": 15,
    "workbench.colorTheme": "Atom One Dark",
    "workbench.iconTheme": "vscode-great-icons", 
    "r.bracketedPaste": true, 
    "r.alwaysUseActiveTerminal": true,
  // updated for VSCode version 1.143.1, Oct. 2026.
    "r.consolePath": "/Users/yourname/anaconda3/bin/radian",
    "r.executablePath": "/usr/local/bin/R",
  // These could cause an error.  
  // "r.rterm.option": [
  //    "--no-save",
  //    "--no-restore",
  //    "--r-binary=/usr/local/bin/R",
  //  ],
    "accessibility.signals.terminalQuickFix": {
        "announcement": "auto"
    },
}
```
# Configure VScode keybindings.json
Open the Command Palette with Cmd+Shift+P, then select Preferences: Open Keyboard Shortcuts (JSON).

In the existing keybindings.json file, add this entry:
```json
  {
    "key": "cmd+alt+r",
    "command": "r.createRTerm"
  },
  
```
If the r.createRTerm command does not work, install an extension, `Run in Terminal` by Kortina and set the shortcut as below.
```json
    {
    "key": "cmd+alt+r",
    "command": "runInTerminal.run",
    "args": {
        "cmd": "radian",
        "match": ".*"
     }
    }
```

Now, test running some lines of R code. First, press `cmd+alt+r` to open a Terminal. Then, press `cmd+enter` to send the R code to the Terminal.

Hopefully, these settings work. Some troubleshooting guide is provided in case of any issues.

# Troubleshoot issues caused by Path
Mac applies quarantine in VSCode repeatedly. To avoid it, do this:

In Mac, move VS Code from Downloads folder to Applications (or your own folder, e.g., Documents > PG_downloaded (I created this particular folder to house my own softwares).

In VSCode, 
1) Launch Visual Studio Code.
2) Press Cmd ⌘ + Shift ⇧ + P to open the Command Palette.
3) Type in 'shell' and select the 
 Shell command: Install ‘code’ command in PATH 


# Creating a task to launch an Radian terminal 
If none of methods triggers an Radian terminal, one can take advantage of the task feature in VSCode.

## Create a task to launch Radian automatically
tasks.json file is located in :

`"/Users/yourname/Library/Application Support/Code/User/tasks.json"`

Copy and paste the following into the tasks.json:
```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Open Radian",
      "type": "shell",
      "command": "radian",
      "problemMatcher": [],
      "presentation": {
        "reveal": "always",
        "focus": true,
        "panel": "dedicated",
        "clear": false
      },
      "runOptions": {
        "instanceLimit": 1
      }
    }
  ]
}
```

## Link the task to a shortcut, Cmd+Alt+R 
In the existing keybindings.json file, add this entry:
```json
{
  "key": "cmd+alt+r",
  "command": "workbench.action.tasks.runTask",
  "args": "Open Radian"
}
```
You should suppress some of the duplicate shortcuts and experiment with them youself to understand which shortcut is actually working!

# Extra: for graphics: 
VSCode shows plots, View also works without xqartz!

To install XQuartz: https://www.xquartz.org/

# Troubleshoot: OLD How to set shortcuts (avoid VSCode error: There are no open terminals).
For future ref only. No need.
Option 1: 
    1) Press Cmd ⌘ + Shift ⇧ + P to open the Command Palette.
    2) Type in 'R' and select the 
    R: Create R terminal
    3) Press Enter.

Option 2: set a shortcut

To set a shortcut to trigger radian,
    1) Press Cmd ⌘ + Shift ⇧ + P to open the Command Palette.
    2) Type in 'R' and select the 
        R: Create R terminal
    3) Instead of pressing Enter, click on the gear icon to lauch keyboard shortcut.
    4) Set as Cmd ⌘ + alt ⌥ + R

# Reference:

https://luongbui.com/r-and-radian-on-macos-and-vscode/

https://towardsdatascience.com/setting-up-python-julia-and-r-in-visual-studio-code-vscode-on-an-m1-mac-3e904a65b62b 

https://stackoverflow.com/questions/30065227/run-open-vscode-from-mac-terminal

Some of the info is dated. Some may still be useful.
https://francojc.github.io/posts/r-in-vscode/






























