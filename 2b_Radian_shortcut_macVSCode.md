
Use a shortcut to run R in Radian terminal
(See below if json user settings do not lauch an r radian terminal)

# 1. Via Extension: Run in Terminal 

## Install an extention
Install the extension, Run in Terminal by Kortina

## Link the task to a shortcut, Cmd+Alt+R 
Open the Command Palette with Cmd+Shift+P, then select Preferences: Open Keyboard Shortcuts (JSON).

In the existing keybindings.json file, add this entry:
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

# 2. Creating a task 

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
_The script above was created by AI._

## Link the task to a shortcut, Cmd+Alt+R 
Open the Command Palette with Ctrl+Shift+P, then select Preferences: Open Keyboard Shortcuts (JSON).

In the existing keybindings.json file, add this entry:
```json
{
  "key": "cmd+alt+r",
  "command": "workbench.action.tasks.runTask",
  "args": "Open Radian"
}
```

