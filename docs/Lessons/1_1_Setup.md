# 1.1 Setup (Windows)

This page contains short, focused instructions and official links to install the tools you'll need for the course on Windows: Python, Git, and Visual Studio Code (VS Code), plus recommended VS Code extensions.

## Install Python

1. Visit the official Python downloads page for Windows: https://www.python.org/downloads/windows/
2. Download the latest stable Python 3.x installer (choose the "Windows installer (64-bit)" for most modern machines).
3. Run the installer and IMPORTANT: check "Add Python 3.x to PATH" at the bottom of the installer window before clicking "Install Now".
4. Verify installation by opening a new Command Prompt (Win+R, type cmd) and running:

	 python --version

Troubleshooting: If `python` is not recognized, reopen your terminal, or restart your PC to ensure PATH changes take effect. You can also run the installer again and choose "Repair".

## Install Git

1. Download Git for Windows: https://git-scm.com/download/win
2. Run the installer and accept the defaults (these are reasonable for beginners). Key options you'll see:
	 - Use Git from the Windows Command Prompt (recommended so `git` works in cmd and PowerShell).
	 - Choose your preferred line ending conversions (the default is fine).
3. After installation, verify with:

	 git --version

Tip: If you plan to use Git from VS Code's terminal, default settings work well.

## Install Visual Studio Code (VS Code)

1. Download VS Code for Windows: https://code.visualstudio.com/
2. Run the installer and follow the prompts. Useful options on the installer screen:
	 - "Add to PATH" (allows launching `code` from terminal)
	 - "Open with Code" context menu entries (useful for opening folders/files)
3. Launch VS Code and open a terminal (View → Terminal) to ensure `code` and the shell integration work.

## Recommended VS Code Extensions for Python development

Install the following extensions from the VS Code Marketplace (use the Extensions view or the links below):

- Python (Microsoft) — https://marketplace.visualstudio.com/items?itemName=ms-python.python
	- Provides linting, debugging, IntelliSense, code navigation, and environment management.
- Pylance (Microsoft) — https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance
	- High-performance language support and type checking (recommended alongside the Python extension).
- GitLens — https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens
	- Enhances Git support inside VS Code with blame annotations, history, and navigation.
- Code Spell Checker — https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker
	- Lightweight spell checking for comments and documentation.

Optional (useful later):

- Jupyter — https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter
	- If you plan to run Jupyter notebooks inside VS Code.
- Bracket Pair Colorizer / similar — improves bracket matching visuals.

## Quick setup checklist

1. Install Python and confirm `python --version` works.
2. Install Git and confirm `git --version` works.
3. Install VS Code and open a project folder.
4. Install the Python and Pylance extensions in VS Code.

## Next steps and tips

- Create a folder for your course projects (for example, `C:\Users\YourName\Projects\python-tutorial`) and open it in VS Code.
- Create a virtual environment for each project with:

	python -m venv .venv

	Then activate it in PowerShell:

	.\.venv\Scripts\Activate.ps1

	(In Command Prompt use `.venv\Scripts\activate.bat`.)
- In VS Code, select the Python interpreter from the status bar and choose the interpreter inside `.venv`.

## What is a virtual environment (and why use one?)

A virtual environment (venv) is an isolated Python runtime that keeps a project's dependencies (libraries and packages) separate from other projects and from the system-wide Python installation. For beginners, think of it like a small, private workspace for each project so you can safely install packages without affecting other projects.

Why use virtual environments:

- Avoid dependency conflicts: Different projects can require different versions of the same package (for example, `requests` or `pandas`). venv keeps those versions separate.
- Reproducibility: You can capture the exact packages a project needs (via `pip freeze > requirements.txt`) and reproduce the environment elsewhere.
- Safety: Installing packages globally can accidentally change tools used by other projects or the OS; venv prevents that.

## Using virtual environments inside VS Code (recommended)

It's a good idea to create and activate virtual environments using the integrated terminal in VS Code — that keeps the workflow in one place and ensures the editor picks the correct interpreter.

Steps (PowerShell — default on many Windows systems):

1. Open your project folder in VS Code (File → Open Folder...).
2. Open the integrated terminal (View → Terminal). By default this may open PowerShell or the terminal you configured.
3. Create a virtual environment:

	python -m venv .venv

4. Activate the virtual environment in PowerShell:

	.\.venv\Scripts\Activate.ps1

	If PowerShell blocks the script due to execution policy, run (in an Administrator PowerShell only):

	Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

	Then try activating again.

Steps (Command Prompt):

1. Open the integrated terminal and switch to Command Prompt (click the terminal dropdown → Select Default Shell → Command Prompt) if preferred.
2. Create the venv as above:

	python -m venv .venv

3. Activate in Command Prompt:

	.venv\Scripts\activate.bat

After activation you'll see your prompt prefixed with `(.venv)` or similar. In VS Code you should also see the selected interpreter change in the lower-left status bar — if not, press Ctrl+Shift+P → "Python: Select Interpreter" and pick the `.venv` interpreter.

Installing packages inside the active venv

With the venv activated in the integrated terminal, install packages with pip as usual:

PowerShell (copy/paste into VS Code terminal):

```powershell
pip install requests pandas
```

Command Prompt (copy/paste into VS Code terminal):

```bat
pip install requests pandas
```

To record your dependencies for sharing:

pip freeze > requirements.txt

To re-create the environment on another machine:

python -m venv .venv
Activate the venv, then:
pip install -r requirements.txt

Note: VS Code's Python extension will detect virtual environments in the workspace folder automatically and offer to select them. Using the integrated terminal keeps activation and package installs consistent with what the editor uses for IntelliSense and linting.

Screenshots (optional)

Add screenshots to illustrate these steps (recommended for beginners). Suggested images:

- `lessons_assets/vscode_interpreter.png` — VS Code status bar interpreter selector.
- `lessons_assets/terminal_activation.png` — Terminal showing `(.venv)` activated prompt.

To include images in this lesson, add Markdown like:

```markdown
![VS Code interpreter selector](Lessons/assets/vscode_interpreter.png)
![Terminal activation](Lessons/assets/terminal_activation.png)
```

---

Last updated: 2025-10-07
