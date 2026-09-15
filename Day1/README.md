# GenAIOps Lab — Day 1 Setup Guide

This guide covers the basic setup required for the **GenAIOps Lab – Day 1** environment on Windows.

> **Security note:** Never commit API keys, passwords, or other secrets to GitHub. The Groq API key that was included in the original setup notes should be treated as exposed. **Revoke/rotate it in Groq and use the new key through an environment variable or `.env` file instead.**

---

## 1. Groq Account

Open the Groq Console:

https://console.groq.com/

Sign in or create an account if you do not already have one.

### API Key

Create a Groq API key from the Groq Console.

**Do not paste the API key directly into this README or source code.**

For example, store it in a `.env` file:

```env
GROQ_API_KEY=your_new_groq_api_key
```

Add `.env` to `.gitignore` so the key is not uploaded to GitHub.

---

## 2. AWS Account

Open the AWS Console:

https://aws.amazon.com/console/

If you do not have an AWS account, create one and complete the required account setup.

> **AWS billing reminder:** Some AWS services can incur charges. Check pricing and billing information before creating paid resources.

---

## 3. Install Visual Studio Code

Download and install VS Code:

https://code.visualstudio.com/download

After installation, open VS Code and make sure the integrated PowerShell terminal is available.

---

## 4. Create the GenAIOps Project Folder

Open PowerShell and create your project folder.

Example:

```powershell
PS D:\> mkdir GenAIOps
PS D:\> cd GenAIOps
```

Create the Day 1 folder:

```powershell
PS D:\GenAIOps> mkdir Day1
PS D:\GenAIOps> cd Day1
```

Your project path should now look similar to:

```text
D:\GenAIOps\Day1
```

---

## 5. Install `uv`

`uv` is a fast Python package and project manager.

Installation instructions:

https://docs.astral.sh/uv/getting-started/installation/

### Windows PowerShell

Run:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Verify the installation:

```powershell
uv --version
```

You should see the installed `uv` version.

---

## 6. Restart VS Code and PowerShell

After installing `uv`:

1. Close VS Code.
2. Close PowerShell.
3. Reopen VS Code.
4. Open a new PowerShell terminal.
5. Navigate back to the Day 1 project.

Example:

```powershell
PS D:\GenAIOps> cd Day1
PS D:\GenAIOps\Day1>
```

---

## 7. Initialize the Python Project

From the `Day1` directory, run:

```powershell
uv init
```

This creates the basic Python project files.

Then install `ipykernel` as a development dependency:

```powershell
uv add --dev ipykernel
```

---

## 8. Activate the Virtual Environment

Activate the `.venv` environment:

```powershell
PS D:\GenAIOps\Day1> .\.venv\Scripts\activate
```

After activation, your terminal should look similar to:

```powershell
(day1) PS D:\GenAIOps\Day1>
```

### Verify Python

Run:

```powershell
python --version
```

You can also verify that Python is using the project environment:

```powershell
where.exe python
```

The path should point to the `.venv` inside your Day1 project.

---

## 9. GitHub Account

Create a GitHub account if you do not already have one:

https://github.com/

If you already have an account, sign in.

GitHub will be used to store and manage the GenAIOps Lab code.

### Important

Before pushing the project to GitHub, make sure sensitive files are excluded.

Recommended `.gitignore` entries:

```gitignore
.venv/
.env
__pycache__/
*.py[cod]
.ipynb_checkpoints/
.vscode/
```

---

## 10. VS Code Extensions

Open VS Code and install the following extensions.

### A. Ruff

**Ruff** provides Python linting and formatting support.

Search the VS Code Extensions marketplace for:

```text
Ruff
```

Install the official Ruff extension.

---

### B. Coding Assistant

You can use either:

- **Codex – OpenAI's coding agent**
- **GitHub Copilot Chat**

If one service reaches its usage limit, you can use the other available option.

Search the VS Code Extensions marketplace and install the appropriate extension.

---

### C. Postman

Install the **Postman** extension if you want to work with API requests directly from VS Code.

Search for:

```text
Postman
```

You can also use the Postman desktop application if preferred.

---

# 11. Recommended Day 1 Project Structure

After setup, your project can look like:

```text
GenAIOps/
└── Day1/
    ├── .venv/
    ├── .gitignore
    ├── .env
    ├── README.md
    ├── pyproject.toml
    └── ...
```

> Do not commit `.venv/` or `.env` to GitHub.

---

# 12. Quick Setup Checklist

Use this checklist to confirm that the environment is ready.

- [ ] Groq account created
- [ ] Groq API key created and stored securely
- [ ] Exposed/old Groq API key revoked or rotated
- [ ] AWS account created or existing account available
- [ ] VS Code installed
- [ ] `GenAIOps` project folder created
- [ ] `Day1` folder created
- [ ] `uv` installed
- [ ] `uv --version` works
- [ ] `uv init` completed
- [ ] `ipykernel` installed
- [ ] `.venv` created
- [ ] Virtual environment activated
- [ ] Python verified
- [ ] GitHub account available
- [ ] Ruff installed
- [ ] Codex or GitHub Copilot Chat installed
- [ ] Postman installed

---

# 13. Useful Links

| Tool | Link |
|---|---|
| Groq Console | https://console.groq.com/ |
| AWS Console | https://aws.amazon.com/console/ |
| VS Code | https://code.visualstudio.com/download |
| uv Installation | https://docs.astral.sh/uv/getting-started/installation/ |
| GitHub | https://github.com/ |

---

# 14. First Commands Summary

For a new Windows machine, the main PowerShell commands are:

```powershell
# Install uv
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

# Create project
mkdir D:\GenAIOps
cd D:\GenAIOps
mkdir Day1
cd Day1

# Initialize project
uv init

# Install development dependency
uv add --dev ipykernel

# Activate virtual environment
.\.venv\Scripts\activate

# Verify
uv --version
python --version
where.exe python
```

---

## Security Reminder

**Never publish API keys in:**

- `README.md`
- GitHub repositories
- screenshots
- notebooks
- source code
- chat messages
- public documentation

Use environment variables or a local `.env` file instead, and add `.env` to `.gitignore`.
