
# Integrate VSCode with R to run R code (Windows)

## Install anaconda, Radian (skip if already done)
To install Radian,
download and install Anaconda3, https://www.anaconda.com/

in anaconda navigator>environments>base(root)>upsidetriangle>Open Terminal)
and execute the following command:

pip3 install -U radian

## Environment setting (skip if already done)
add anaconda3 in Environment.
add R in env. C:\Program Files\R\R-4.1.1\bin\
Do not add r.exe at the end of the path. Won't work!
Restart PC after env is changed.

## in RStudio (skip if already done)
install.packages("languageserver")

## Install VSCode extension for for python
R

Python (Microsoft)

Python Extension pack(Don Jayamanne).

## Configure VSCode json
In VSCode, press `F1 > type Preferences: Open User Settings (JSON)` to open the json file.

```json
{

    "r.bracketedPaste": true,
    // "r.rterm.windows": "C:\\ProgramData\\anaconda3\\Scripts\\radian.exe",
    "r.rterm.windows": "C:\\Users\\yourname\\anaconda3\\Scripts\\radian.exe",
    "r.rpath.windows": "C:\\Program Files\\R\\R-4.3.1\\bin\\R.exe",
    "r.lsp.debug": true,
    "r.lsp.diagnostics": true,
    "r.rterm.option": [
        "--no-save",
        "--no-restore",
        "--r-binary=C:\\Program Files\\R\\R-4.3.1\\bin\\R.exe"
    ],

    "terminal.integrated.fontSize": 15,
    "terminal.integrated.lineHeight": 1.2,
}
```

## Complete the setup by configuring VSCode shortcut keys
R Create Terminal
: Set as ctrl+alt+r (consistent with Sublime)

In VSCode, press `F1 > type Preferences: Open Keyboard Shortcuts (JSON)` to open the shortcut keys json file. Copy the following and paste at the end of the file inside the square brackets, `[]`.
```
[
  // ========= R =======
  {
    "key": "ctrl+enter",
    "command": "-r.runSelection",
    "when": "editorTextFocus && !editorReadonly && editorLangId == 'r'"
  },
  {
    "key": "ctrl+enter",
    "command": "-r.runSelection",
    "when": "editorTextFocus && !editorReadonly && editorLangId == 'rmd'"
  },
  // Same as Sublime's shortcut. Radian R terminal
  {
    "key": "ctrl+alt+r",
    "command": "r.createRTerm"
  },

]
```

## Tips
### VSCode Keybidnings location
C:\Users\yourname\AppData\Roaming\Code\User

## TROUBLESHOOT

### 18/2/2024 FIX TO RUN R CODE  ===============
0. Installed Rtools43 (R>4.3) compatible with R version. 
needed in Windows PC??
Checked .libPaths() then installed languageserver again.
install.packages("languageserver")

1.  .Rprofile is empty in other desktop PC but works...

2. json config updated 18/2/2024
in Rpath, R-4.3.1\\bin\\64x causes issues in laptop.
Removed it and  R-4.3.1\\bin\\R.exe seems to work ok.


// Linux requires alwaysUseActiveTerminal. No need in Windows.
    //"r.alwaysUseActiveTerminal": true,

3. to run R code: (DATED, IGNORE, for future ref only)

- Open the R scipt.
VSCode command palette, select 
  R:Create R Terminal 
Set the shortcut as Ctrl+Shift+T 

- Open R Termial by pressing Ctrl+Shift+T as you do in Sublime.
(VSCode MEnu option New Terminal will open PowerShell, AVOID)

To send the R code, use the shortcut, Ctrl+Enter.
It didn't work initially. So I checked VSCode command palette.
In VSCode command palette, choose 
	R: Run Selection/Line 
We need to use this. Set the shortcut as Ctrl+Enter 
If there are multiple shortcut set as Ctrl+Enter,
temporarily assign Alt+Enter and change it back to Ctrl+Enter.
These shortcuts overwrite existing ones. Accept it's okay.

4. VSCode Keybidnings customised
R Create Terminal
Set as ctrl+alt+r (same as Sublime)

5. Done.
