# Rust On Windows Guide

Quick guide to setting up rust development on Windows, since information I found was very confusing.

* **rust up** - x86_64-pc-windows-msvc from [Other Rust Installation Methods](https://forge.rust-lang.org/infra/other-installation-methods.html)

* **vs build tools** - *rust up* should download this for you, select and install **Desktop Development with C++**

* **vs code** - from [vscode website](https://code.visualstudio.com/Download). The **Zip** verson can be made portable by creating a folder called **data** inside its directory (instead of using the windows users "roaming" folder).

* **vs code extensions** - [better toml](https://marketplace.visualstudio.com/items?itemName=bungcip.better-toml), [CodeLLDB](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb) and [rust analyzer](https://marketplace.visualstudio.com/items?itemName=matklad.rust-analyzer) (the alternate [rust](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust) extension wasn't showing inferred types for me)

* **vs code settings**

In ```data\user-data\User\settings.json``` (optional)

```json
{
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

In vs code, goto file, save workspace as, and save to your project's directory. eg ```c:\Projects\hello\workspace.code-workspace```.
