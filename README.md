# 🤖 Google Agents CLI — Full Setup Guide

Build AI agents from a single prompt. Works with Gemini CLI, Claude Code, Cursor, Codex.

[![YouTube](https://img.shields.io/badge/YouTube-Watch_Demo-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtube.com/@your-channel)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Node](https://img.shields.io/badge/Node-LTS-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org)
[![Google Cloud](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)](https://cloud.google.com)
[![Gemini](https://img.shields.io/badge/Gemini_API-Free_Tier-8E44AD?style=for-the-badge)](https://aistudio.google.com)

---

## 🎥 Watch the Full Walkthrough

[![Watch on YouTube](https://img.shields.io/badge/▶_Watch_on_YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=Qx_HIHy5-IQ)

---

## 📋 What This Covers

- ✅ Full Windows / Mac / Linux setup
- ✅ Google Cloud project + Gemini API key
- ✅ Agents CLI install + 7 skills
- ✅ Building an AI News Briefing Agent
- ✅ Common gotchas + fixes

---

## 🛠️ Prerequisites

| Tool | Why |
|---|---|
| **Node.js LTS** | For Gemini CLI |
| **Python 3.11+** | For Agents CLI runtime |
| **uv** | Fast Python package manager |
| **gcloud CLI** | Google Cloud auth |

---

## 🪟 Windows Setup

```powershell
# 1. Install Node.js LTS → https://nodejs.org

# 2. Install Python (check "Add Python to PATH")
pip install uv

# 3. Install gcloud CLI
winget install Google.CloudSDK
# Restart terminal

# 4. Set up Google Cloud project
gcloud init
gcloud projects create agents-cli-demo
gcloud config set project agents-cli-demo

# 5. Set Gemini API key (get from https://aistudio.google.com/apikey)
[System.Environment]::SetEnvironmentVariable("GEMINI_API_KEY", "your-key", "User")

# 6. Install Gemini CLI
npm install -g @google/gemini-cli

# 7. Install Agents CLI (the main install)
uvx google-agents-cli setup

# 8. Verify
mkdir agents-cli-demo
cd agents-cli-demo
gemini
# Should show "7 skills" loaded on right
```

---

## 🍎 macOS Setup

```bash
# 1. Node.js
brew install node

# 2. Python + uv
brew install python uv

# 3. gcloud CLI
brew install --cask google-cloud-sdk

# 4. Google Cloud project
gcloud init
gcloud projects create agents-cli-demo
gcloud config set project agents-cli-demo

# 5. Gemini API key
echo 'export GEMINI_API_KEY="your-key"' >> ~/.zshrc
source ~/.zshrc

# 6. Gemini CLI
npm install -g @google/gemini-cli

# 7. Agents CLI
uvx google-agents-cli setup

# 8. Verify
mkdir agents-cli-demo && cd agents-cli-demo && gemini
```

---

## 🐧 Linux Setup (Ubuntu/Debian)

```bash
# 1. Node.js
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs

# 2. Python + uv
sudo apt install -y python3 python3-pip
pip install uv

# 3. gcloud CLI
curl https://sdk.cloud.google.com | bash
exec -l $SHELL

# 4. Google Cloud project
gcloud init
gcloud projects create agents-cli-demo
gcloud config set project agents-cli-demo

# 5. Gemini API key
echo 'export GEMINI_API_KEY="your-key"' >> ~/.bashrc
source ~/.bashrc

# 6. Gemini CLI
npm install -g @google/gemini-cli

# 7. Agents CLI
uvx google-agents-cli setup

# 8. Verify
mkdir agents-cli-demo && cd agents-cli-demo && gemini
```

---

## 🚀 Build Your First Agent

Inside Gemini CLI, paste:

```
Use agents CLI to scaffold a daily AI news briefing agent.
The agent takes a topic as input, searches for the latest news 
from technology and capital sources, then generates a structured 
morning briefing with: 5 key headlines, a TLDR summary under 50 
words, top funding moves, and a "why this matters" insight.
Build and test locally only.
```

The wizard will ask:
- **Project Name** → `ai-news-briefing`
- **Search Tool** → `Mock Search` (no extra setup)
- **Sources** → `TechCrunch, The Verge, Bloomberg, Reuters, VentureBeat`

---

## ⚠️ Common Gotchas

### 1. `gcloud not recognized` after install
**Fix:** Close + reopen terminal, OR refresh PATH:
```powershell
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
```

### 2. `DefaultCredentialsError`
**Fix:**
```bash
gcloud auth application-default login
```

### 3. Vertex AI billing error
**Fix:** Open `agent.py`, change:
```python
os.environ["GOOGLE_GENAI_USE_VERTEXAI"] = "False"
```

### 4. `RESOURCE_EXHAUSTED` (quota hit)
**Fix:** Switch model in `agent.py`:
```python
model="gemini-2.5-flash"  # higher free quota
```

---

## 🧠 The 7 Skills

| Skill | Purpose |
|---|---|
| **workflow** | Asks clarifying questions before building |
| **scaffold** | Creates project structure |
| **adk-code** | Writes Agent Development Kit syntax |
| **eval** | Tests agent against sample data |
| **deploy** | Pushes to Cloud Run / Agent Runtime |
| **observability** | Captures prompts, tools, tokens |
| **publish** | Registers in Gemini Enterprise |

---

## 📚 Resources

- 📦 [Official GitHub Repo](https://github.com/google/agents-cli)
- 📝 [Google Developers Blog](https://developers.googleblog.com/agents-cli-in-agent-platform-create-to-production-in-one-cli/)
- 🔑 [Get Gemini API Key](https://aistudio.google.com/apikey)
- ☁️ [Google Cloud Console](https://console.cloud.google.com)

---

## 📺 Watch the Tutorial

[![YouTube](https://img.shields.io/badge/▶_Full_Walkthrough_on_YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=Qx_HIHy5-IQ)

---

## 📄 License

MIT — free to use, share, modify.

---

⭐ **If this helped you, star the repo and subscribe on YouTube!**
