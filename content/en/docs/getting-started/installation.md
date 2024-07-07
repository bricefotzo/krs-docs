---
title: "Installing (KRS)"
weight: 20
---

Follow these steps to install KRS on your system:

## 1. Clone the Repository

First, clone the KRS repository from GitHub:

```bash
git clone https://github.com/kubetoolsca/krs.git
````
2. Navigate to the KRS Directory
Change your current directory to the cloned KRS repository:
```bash
cd krs
```
3. Install KRS
Use pip to install KRS locally on your system:
```bash
pip install .
```
This command will install KRS and all its dependencies.
4. Verify Installation
To verify that KRS has been installed correctly, run:
```bash
krs --help
```
This should display the KRS help message, showing all available commands.
**Next Steps**
Now that you have KRS installed, you're ready to start using it. Begin by initializing KRS:
```bash
krs init
```
For more information on how to use KRS, check out the Usage section of the documentation.