[

// Rterm open (radian opens Rterm to run R codes)
// To make two columns, go to View > Layout > Columns:2. Put the cursor in Column2: 
    { "keys": ["ctrl+alt+r"],
        "command": "terminus_open",
        "args": {
            "post_window_hooks": [
                ["carry_file_to_pane", {"direction": "right"}]
            ],
            "cmd" : "radian"
        }
    },


]

