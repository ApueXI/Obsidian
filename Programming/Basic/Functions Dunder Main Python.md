---
Created: 2025-06-05T06:37
---
if _name ==_main_: (this script can be imported OR run standalone)  
Functions and classes in this module can be reused  
without the main block of code executing

```Python
# gawin mo to sa json file
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "My script 1",
            "type": "debugpy",
            "request": "launch",
            "program": "${workspaceFolder}/functions_TheDunderMain_Script1.py",
            "console": "integratedTerminal"
        },
        {
            "name": "My Script 2",
            "type": "debugpy",
            "request": "launch",
            "program": "${workspaceFolder}/functions_TheDunderMain_Script2.py",
            "console": "integratedTerminal"
        }
    ]
}
```