# GenAIOps Tutorial - Day 2: Project Setup & Environment Configuration

Welcome to Day 2 of the **GenAIOps Tutorial** series by **LWS Labs**! This directory contains the initial environment setup, project structure, and package dependencies required to build and scale Generative AI applications using [`uv`](https://github.com/astral-sh/uv)—an extremely fast Python package and project manager written in Rust.

---

## 🛠️ Tech Stack & Dependencies

- **Package Manager:** `uv`
- **Core LLM SDKs:**
  - `openai`: Official OpenAI API client for GPT-3.5/GPT-4 models.
  - `groq`: Official Groq SDK for high-speed LLM inference.
- **Utilities:**
  - `python-dotenv`: Environment variable management (`.env`).
- **Development Tools:**
  - `ipykernel`: Jupyter Kernel support for running interactive notebooks.

---

## 📂 Directory Structure

The project follows a standard modular layout:

```text
Day2/
├── .venv/                  # Virtual environment created by uv
├── docs/                   # Documentation and project guides
├── notebooks/              # Jupyter notebooks for experimentation
│   └── ai_initial.ipynb    # Initial AI exploration notebook
├── src/                    # Source code directory
│   └── myApp/              # Main application package
│       ├── __init__.py     # Package initializer
│       └── main.py         # Entry point for the application
├── tests/                  # Unit and integration tests
├── .env                    # Environment variables (API keys) - create manually
├── .gitignore              # Git ignore file
├── pyproject.toml          # Project configuration and dependency list
└── uv.lock                 # Lockfile for precise dependency resolution
```

---

## 🚀 Setup & Installation Guide

Follow the step-by-step commands below to reproduce the environment:

### 1. Create and Navigate to Directory

```powershell
mkdir Day2
cd Day2
```

### 2. Initialize `uv` Project & Virtual Environment

```powershell
uv init
uv venv
```

### 3. Activate Virtual Environment

- **Windows (PowerShell):**
  ```powershell
  .\.venv\Scripts ctivate
  ```
- **Linux / macOS:**
  ```bash
  source .venv/bin/activate
  ```

### 4. Install Dependencies

Add core and development packages using `uv`:

```powershell
# Core dependencies
uv add openai groq python-dotenv

# Development dependencies
uv add --dev ipykernel

# Synchronize virtual environment
uv sync
```

### 5. Create Directory & File Structure

- **Bash / Git Bash / Zsh:**
  ```bash
  mkdir -p src/myApp docs notebooks tests
  touch notebooks/ai_initial.ipynb
  touch src/myApp/main.py src/myApp/__init__.py
  ```

- **PowerShell alternative:**
  ```powershell
  New-Item -ItemType Directory -Force -Path src/myApp, docs, notebooks, tests
  New-Item -ItemType File -Force -Path notebooks/ai_initial.ipynb, src/myApp/main.py, src/myApp/__init__.py
  ```

---

## 🔐 Environment Configuration

Create a `.env` file in the `Day2/` root directory to store your API keys securely:

```env
OPENAI_API_KEY=your_openai_api_key_here
GROQ_API_KEY=your_groq_api_key_here
```

> ⚠️ **Security Note:** Never commit your `.env` file to version control. Make sure `.env` is included in your `.gitignore`.

---

## Code

```python
import os
from dotenv import load_dotenv, find_dotenv

load_dotenv(find_dotenv(usecwd=True))
```

```python
from openai import OpenAI
client = OpenAI(
    api_key=os.environ.get("GROQ_API_KEY"),
    base_url="https://api.groq.com/openai/v1",
)

response = client.responses.create(
    input="What is the capital of France?",
    model="openai/gpt-oss-20b",
)
print(response.output_text)

```

## 🏃 Running the Application

To run the main entry point:

```bash
python src/myApp/main.py
```

To start a Jupyter notebook session using the project environment:

```bash
uv run jupyter notebook notebooks/ai_initial.ipynb
```

---

## 📚 Resources & References

- [uv Documentation](https://docs.astral.sh/uv/)
- [OpenAI Python API Reference](https://github.com/openai/openai-python)
- [Groq API Documentation](https://console.groq.com/docs/quickstart)
