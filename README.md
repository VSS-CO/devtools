# 🛠️ Toolbox CLI

![Toolbox CLI Banner](https://user-images.githubusercontent.com/yourusername/toolbox-banner.png)

[![PyPI Version](https://img.shields.io/pypi/v/toolbox-cli?color=blue&label=PyPI)](https://pypi.org/project/toolbox-cli/) 
[![Python Version](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/) 
[![License](https://img.shields.io/github/license/yourusername/toolbox)](LICENSE) 
[![Build Status](https://img.shields.io/github/actions/workflow/status/yourusername/toolbox/ci.yml?branch=main)](https://github.com/yourusername/toolbox/actions) 

> [!NOTE]
> Toolbox CLI is a unified developer toolset for automation tasks including token generation, env file creation, repo health checks, config validation, and API smoke testing.

---

## ⚡ Quick Features

- 🔑 **Token Generator** – Alphanumeric & URL-safe tokens  
- 📄 **Env Generator** – `.env` file creation with auto-generated secrets  
- 📦 **Repo Health Checker** – Detect missing files, large files, TODO/FIXME  
- ⚙️ **Config Validator** – JSON/YAML required keys validation  
- 🌐 **API Smoke Tester** – Endpoint status checks, retries, token auth  
- 🖥️ **Interactive CLI Mode** – Run commands without typing `python main.py` every time

> [!TIP]
> You can use `python main.py` to run commands locally, or install globally via `pip install -e .` to use `toolbox` from anywhere.

---

## ⚡ Getting Started

### Run Commands Directly
```bash
python main.py token generate --length 32
python main.py env create DB_HOST=localhost DEBUG=true
python main.py repo health --path ./my-repo --max-size 10
````

### Interactive Mode

```bash
python main.py
```

* `help` → show available commands
* `exit` / `quit` → quit shell

Example session:

```
toolbox> token generate --length 32
toolbox> env create API_KEY= --out .env.local
toolbox> exit
```

> [!IMPORTANT]
> Interactive mode allows quick experimentation without repeatedly typing `python main.py`. All flags and arguments work the same.

---

## 🔑 Token Generator

```bash
python main.py token generate
python main.py token generate --length 64
python main.py token generate --url-safe
```

> [!TIP]
> Use URL-safe tokens for API keys embedded in URLs or QR codes.

---

## 📄 Env Generator

```bash
python main.py env create DB_HOST=localhost DEBUG=true
python main.py env create API_KEY= DB_PASS= --out .env.local
```

> [!WARNING]
> Existing `.env` files will be overwritten if the same filename is specified.

---

## 📦 Repo Health Checker

```bash
python main.py repo health
python main.py repo health --path ./my-repo --max-size 5
```

> [!NOTE]
> Ideal for keeping projects clean and detecting large/untracked files early.

---

## ⚙️ Config Validator

```bash
python main.py config validate config.yaml --require app.name app.port
python main.py config validate config.json --require database.url database.user
```

> [!CAUTION]
> Required keys must match exactly; otherwise, validation fails.

---

## 🌐 API Smoke Tester

```bash
python main.py api smoke https://api.example.com /health /status
python main.py api smoke https://api.example.com /health=200 /login=401
python main.py api smoke https://api.example.com /health=200 --retries 3 --timeout 5 --token MY_API_TOKEN
```

> [!TIP]
> Integrate API smoke tests into CI pipelines to monitor endpoint reliability automatically.

---

## 📌 Command Structure Overview

```
toolbox
├─ token
│  └─ generate [--length N] [--url-safe]
├─ env
│  └─ create <KEY=VALUE ...> [--out FILE]
├─ repo
│  └─ health [--path PATH] [--max-size N]
├─ config
│  └─ validate <file> [--require key1 key2 ...]
├─ api
│  └─ smoke <base_url> <endpoint ...> [--token TOKEN] [--retries N] [--timeout N]
└─ interactive mode (run 'python main.py' without args)
```

> [!NOTE]
> All CLI commands can be run in interactive mode or directly with `python main.py`.

---

## 📦 Installation (Optional)

Clone the repo and install locally:

```bash
git clone https://github.com/yourusername/toolbox.git
cd toolbox
pip install -e .
```

Now you can run commands directly:

```bash
toolbox token generate --length 32
toolbox env create API_KEY= --out .env.local
```

> [!TIP]
> Installing with `pip -e` allows updates from the repo to reflect immediately in your CLI without reinstalling.

---

## 💡 Tips for Productivity

* Combine multiple tools in scripts for CI/CD automation.
* Use interactive mode for rapid exploration and testing.
* Auto-generate `.env` secrets for secure local setups.
* Integrate API smoke tests in CI pipelines for reliable endpoints.
* Keep repo health in check to avoid large, untracked files.

---

> [!IMPORTANT]
> Toolbox CLI is designed for **developer efficiency and automation**, not as a production deployment platform.

```

