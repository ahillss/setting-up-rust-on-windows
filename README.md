# Rust On Windows Guide

Quick guide to setting up rust development on Windows, since information I found was very confusing.

* **rust up** - Download x86_64-pc-windows-msvc from [Other Rust Installation Methods](https://forge.rust-lang.org/infra/other-installation-methods.html)

* **vs build tools** - *rust up* should download this for you, select and install **Desktop Development with C++**

* **visual studio code** - Download from [here](https://code.visualstudio.com/Download). The **Zip** verson can be made portable by creating a folder called **data** inside its directory (instead of using the windows users "roaming" folder).

* **visual code extensions** - Install [better toml](https://marketplace.visualstudio.com/items?itemName=bungcip.better-toml), [rust analyzer](https://marketplace.visualstudio.com/items?itemName=matklad.rust-analyzer) (the alternate [rust extension](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust) wasn't showing inferred types for me), [CodeLLDB](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb)
