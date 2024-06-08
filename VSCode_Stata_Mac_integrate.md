
== Stata - VSCode Integration ==

# Step 1: Install VSCode extension
- Install `Stata Enhanced` by Kyle Barron.

This extension allows Stata code highlights. 

To run Stata code, we need `stataRun`.
- Install `stataRun` by Yeaoh Media Inc.

# Step 2: Configure VSCode
In settings.json file, add the following:
Customise as necessary. Yours may be "stataMP".
```json
    // ============= Stata ==================
    "stataRun.whichApp": "stataIC",
```

# Step 3: Complete. Test running Stata code now
Restart VSCode.
Open a do file. No need to select the current line.
To run the code, press Cmd+Shift+S.
Customise the shortcut as necessary.

# Issues 
- The cursor is left in Stata window, not back in VSCode. Can look in future. 
- If Stata window is not triggered, try restarting VSCode several times at each stage.

