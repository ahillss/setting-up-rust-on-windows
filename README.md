# Rust On Windows Guide

Quick guide to setting up rust development on Windows, since information I found was very confusing.

## Installing

* **rust up** - x86_64-pc-windows-msvc from [Other Rust Installation Methods](https://forge.rust-lang.org/infra/other-installation-methods.html)

* **vs build tools** - *rust up* should download this for you, select and install **Desktop Development with C++**

* **vs code** - from [vscode website](https://code.visualstudio.com/Download). The **Zip** verson can be made portable by creating a folder called **data** inside its directory (instead of using the windows users "roaming" folder).

* **vs code extensions** - [better toml](https://marketplace.visualstudio.com/items?itemName=bungcip.better-toml), [CodeLLDB](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb) and [rust analyzer](https://marketplace.visualstudio.com/items?itemName=matklad.rust-analyzer) (the alternate [rust](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust) extension wasn't showing inferred types for me)

## Rust up

By default it is installed in ```%USERPROFILE%\.cargo``` and ```%USERPROFILE%\.rustup```. You move it to a more convient location by adding/modifying the windows environment variables:

* ```CARGO_HOME```
* ```RUSTUP_HOME```
* ```PATH```

## Project Config

### workspace

In vs code, goto file, save workspace as, and save to your project's directory. eg ```c:\Projects\hello\workspace.code-workspace```.

### compile using tasks (optional)

Create a ```tasks.json``` for your project (eg ```c:\Projects\hello\.vscode\tasks.json```).


```json
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "cargo",
			"command": "build",
			"problemMatcher": [
				"$rustc"
			],
			"group": {
				"kind": "build",
				"isDefault": true
			},
			"label": "rust: cargo build",
			"presentation": {
				"reveal": "silent",
				"revealProblems": "onProblem",
				"close": true,
				"clear": true 
			}
		}
	]
}
```

Run with shortcut ```Ctrl + Shift + B```.

### Using launch (optional)

Create ```launch.json```. eg ```c:\Projects\hello\.vscode\launch.json```.

```json

{
    "version": "0.2.0",
    "configurations": [

        {
            "name": "Debug",
            "type": "lldb",
            "request": "launch",
            "program": "cargo",
            "args": ["run"],
            "stopAtEntry": false,
            "cwd": "${workspaceRoot}",
            "environment": [],
            "externalConsole": true,
            "env" : {
                //"RUST_BACKTRACE" : "1",
                //"RUST_LOG": "debug",
            }
        },
        
        {
            "name": "Release",
            "type": "lldb",
            "request": "launch",
            "program": "cargo",
            "args": [
                "run", "--release"
            ],
            "stopAtEntry": false,
            "cwd": "${workspaceRoot}",
            "environment": [],
            "externalConsole": true
        }
    ]
}
```
Run by pressing the ```F5``` key.

You can also choose between debug and release modes by clicking on the "Run and Debug" sidebar menu or using the shortcut ```Ctrl+Shift+D```.

## Global Config (optional)

Instead of storing launch in the project, you store it in the global settings file. eg ```data\user-data\User\settings.json```.

```json
{

    "launch": {
        "configurations": [

            {
                "name": "Debug",
                "type": "lldb",
                "request": "launch",
                "program": "cargo",
                "args": ["run"],
                "stopAtEntry": false,
                "cwd": "${workspaceRoot}",
                "environment": [],
                "externalConsole": true,
                "env" : {
                    //"RUST_BACKTRACE" : "1",
                    //"RUST_LOG": "debug",
                }
            },
            
            {
                "name": "Release",
                "type": "lldb",
                "request": "launch",
                "program": "cargo",
                "args": [
                    "run", "--release"
                ],
                "stopAtEntry": false,
                "cwd": "${workspaceRoot}",
                "environment": [],
                "externalConsole": true
            }
        ]
    },
    
    "security.workspace.trust.untrustedFiles": "open",
    "editor.accessibilitySupport": "off",
    "debug.allowBreakpointsEverywhere": true,
    "task.quickOpen.detail": false,
    "task.quickOpen.skip": true,
    "task.quickOpen.history": 1,
    "terminal.integrated.showExitAlert": false,
    "debug.terminal.clearBeforeReusing": true,
    "terminal.integrated.confirmOnKill": "never"
}
```

## Misc

### Breakpoints

I could only get breakpoints working by going to the ```main``` function in my project and clicking the "Debug" text button above it.
