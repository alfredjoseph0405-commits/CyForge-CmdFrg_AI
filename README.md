````markdown
# Nmap Command Generator and Descriptor Tool

## Overview
This tool allows you to generate Nmap commands based on natural language prompts and understand existing Nmap commands. It supports:

- Command generation for different scan types.
- Automatic alternate commands for non-administrative users.
- AI-based analysis of scan results.
- A GUI for ease of use (Tkinter).

---

## Requirements

### Python Modules
The following Python modules are required:

- `google-genai`
- `keyring`
- `tkinter` (usually comes pre-installed with Python)
- `shlex` (standard library)
- `subprocess` (standard library)
- `json` (standard library)
- `threading` (standard library)
- `messagebox` (from tkinter)

Install the external modules using pip:

```bash
pip install google-genai keyring
````

> On Linux, if `pip` is blocked, use `pip3` or `python3 -m pip`, or use a virtual environment.

---

### Nmap Installation

#### Linux

* **Debian/Ubuntu/Kali**:

```bash
sudo apt update
sudo apt install nmap -y
```

* **Fedora/CentOS**:

```bash
sudo dnf install nmap -y
```

#### macOS

> Install [Homebrew](https://brew.sh/) first if not installed, then:

```bash
brew install nmap
```

#### Windows

> Download the official installer from [Nmap Download Page](https://nmap.org/download.html) and follow the setup instructions.

---

## Usage

1. Clone or download this repository.
2. Install Python modules as described above.
3. Make sure Nmap is installed and available in your PATH.
4. Run the GUI:

```bash
python nm.py
```

5. Enter a prompt in the generator to create an Nmap command.
6. View the generated command and description.
7. For analysis, select an existing command to understand its purpose and AI analysis of results.

---

## Troubleshooting

* **Tkinter window not resizing**: Some platforms may not support `mn.state("zoomed")`. The tool falls back to normal state automatically.
* **Permission issues with Nmap**: Some scans require administrative privileges (SYN scan, OS detection). Use `sudo` on Linux/macOS or run as Administrator on Windows.
* **Missing modules**: Ensure you install the modules with pip as described.
* **Raw socket errors**: For non-admin users, only TCP Connect (`-sT`) scans on allowed ports will work.

---

## Notes

* The tool normalizes privileged flags and `sudo` commands automatically for non-admin users.
* Only TCP connect scans (`-sT`) without privileged flags can run without elevated permissions.
* AI analysis requires a valid API key from Google AI Studio set in keyring.

---


# AI Bandit Security Scanner

## Overview

AI Bandit Security Scanner is a Python-based tool that combines static code analysis with AI-powered security insights.
It uses **Bandit** to scan Python code for common security vulnerabilities and then uses AI to explain the vulnerability and suggest secure fixes.

This tool helps developers and security engineers identify and understand security risks in Python projects.

---

## Features

* Static code analysis using Bandit
* AI-powered vulnerability explanation
* AI-generated secure code fixes
* Scan local folders for Python vulnerabilities
* Scan GitHub repositories
* Automatic JSON security report generation

---

## Technologies Used

* Python
* Bandit (Python security linter)
* OpenAI API
* Subprocess module
* JSON reporting

---

## Installation

### 1. Clone the Repository

```
git clone <your-repo-url>
cd <your-project-folder>
```

### 2. Install Dependencies

```
pip install bandit openai
```

### 3. Configure API Key

Open the file `ai_bandit_scanner.py` and add your OpenAI API key:

```
OPENAI_API_KEY = "your_api_key_here"
```

---

## Usage

Run the scanner:

```
python ai_bandit_scanner.py
```

You will see the following options:

```
AI Powered Security Scanner

1. Scan local folder
2. Scan GitHub repository
```

### Scan Local Folder

Enter the folder path containing Python files.

Example:

```
Enter folder path: D:\Projects\sample_app
```

### Scan GitHub Repository

Provide the GitHub repository URL.

Example:

```
https://github.com/user/project
```

---

## Example Vulnerable Code

```
import subprocess

user_input = input()

subprocess.run("ls " + user_input, shell=True)
```

### Detected Issue

* Command Injection vulnerability due to `shell=True`.

---

## Output

After scanning, the tool generates a file:

```
security_report.json
```

Example report structure:

```
{
  "scan_time": "2026-03-07",
  "total_issues": 1,
  "issues": [
    {
      "issue_text": "subprocess call with shell=True",
      "issue_severity": "HIGH",
      "filename": "app.py",
      "line_number": 12,
      "ai_analysis": "Explanation and secure fix..."
    }
  ]
}
```

---

## Project Structure

```
ai_bandit_scanner.py
security_report.json
README.md
```

---

## How It Works

1. The tool scans Python code using Bandit.
2. Bandit detects security vulnerabilities.
3. The AI module analyzes each vulnerability.
4. AI provides explanation and secure code recommendations.
5. A structured security report is generated.

---

## Example Workflow

```
Python Source Code
        │
        ▼
Bandit Static Analysis
        │
        ▼
Detected Vulnerabilities
        │
        ▼
AI Security Analysis
        │
        ▼
Detailed Security Report
```

---

## Use Cases

* Secure code reviews
* DevSecOps pipelines
* Learning secure coding practices
* Cybersecurity projects
* Vulnerability analysis

---

## Future Improvements

* Web dashboard for security reports
* Automatic vulnerability patch generation
* CI/CD integration
* Machine learning vulnerability detection
* Multi-language support

---

## Disclaimer

This tool is intended for educational and security research purposes only. Always test security tools in controlled environments.

---

## License

MIT License

## License

This tool is provided as-is for educational and internal network testing purposes. Use responsibly and only on networks you own or have permission to scan.

