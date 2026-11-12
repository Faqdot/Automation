# 🚀 Bash Scripting – Complete Hands-On Practical Course

A comprehensive, step-by-step Bash scripting course designed to take you from beginner to advanced Linux automation.

This repository contains practical labs, real-world scenarios, hands-on exercises, and projects inspired by everyday Linux Administration and DevOps engineering tasks.

**Learn by doing, practice every day, and build real-world automation skills.**

---

## 🎯 Learning Objectives

By completing this repository, you will learn how to:

- Understand Bash shell fundamentals.
- Write and execute Bash scripts.
- Work with variables, arrays, and functions.
- Implement conditions, loops, and case statements.
- Automate Linux administration tasks.
- Manage files, directories, and permissions.
- Monitor processes, memory, and disk usage.
- Analyze application logs.
- Automate backups and deployments.
- Schedule tasks using Cron.
- Debug and troubleshoot Bash scripts.
- Build reusable automation tools.

---

## 🛠️ Prerequisites

- Basic Linux command-line knowledge.
- Ubuntu Linux / RHEL / CentOS / WSL2.
- Bash shell.
- Text editor (Nano or Vim).
- Basic understanding of file permissions.

### Verify Your Environment

```bash
whoami
pwd
uname -a
bash --version
```

---

## 📚 Course Roadmap

| Level | Topics | Labs |
|---|---|---|
| Level 1 | Bash Fundamentals | 1–5 |
| Level 2 | Programming Logic | 6–10 |
| Level 3 | Functions and Error Handling | 11–15 |
| Level 4 | Linux Administration | 16–20 |
| Level 5 | Real-World DevOps Automation | 21–25 |
| Level 6 | Advanced Bash Engineering | 26–30 |

---

# 🟢 LEVEL 1 – Bash Fundamentals

| Lab | Topic | Practical Exercise |
|---|---|---|
| 01 | First Bash Script | Create and execute hello.sh |
| 02 | Variables | Store and display information |
| 03 | Command-Line Arguments | Pass values to scripts |
| 04 | Arithmetic Operations | Build a calculator |
| 05 | File Operations | Read and write files |

# 🟡 LEVEL 2 – Programming Logic

| Lab | Topic | Practical Exercise |
|---|---|---|
| 06 | If / Else / Elif | Server reachability check |
| 07 | Comparison Operators | Compare values |
| 08 | For Loops | Process multiple services |
| 09 | While Loops | Implement retry logic |
| 10 | Case Statements | Create an administration menu |

# 🔵 LEVEL 3 – Professional Bash Scripting

| Lab | Topic | Practical Exercise |
|---|---|---|
| 11 | Functions | Build reusable functions |
| 12 | Arrays | Manage multiple servers |
| 13 | Exit Codes | Handle command success and failure |
| 14 | Error Handling | Use strict-mode scripting |
| 15 | Logging | Create application log files |

# 🟣 LEVEL 4 – Linux Administration Automation

| Lab | Topic | Practical Exercise |
|---|---|---|
| 16 | File Automation | Organize files and directories |
| 17 | Permissions | Automate permission management |
| 18 | Process Monitoring | Check running processes |
| 19 | Disk Monitoring | Detect high disk utilization |
| 20 | Service Monitoring | Check systemd services |

# 🔴 LEVEL 5 – Real-World DevOps Automation

| Lab | Topic | Practical Exercise |
|---|---|---|
| 21 | Log Analysis | Find ERROR and WARNING messages |
| 22 | Backup Automation | Create timestamped backups |
| 23 | System Health Report | Generate server health reports |
| 24 | Cron Jobs | Schedule automatic scripts |
| 25 | Deployment Automation | Simulate application deployment |

# ⚫ LEVEL 6 – Advanced Bash Engineering

| Lab | Topic | Practical Exercise |
|---|---|---|
| 26 | Getopts | Build command-line utilities |
| 27 | String Manipulation | Process and transform strings |
| 28 | AWK, SED and GREP | Analyze log files |
| 29 | Debugging | Troubleshoot Bash scripts |
| 30 | Trap and Cleanup | Handle temporary resources |

---

## 📁 Repository Structure

```text
bash-scripting/
│
├── README.md
│
├── 01-bash-fundamentals/
│   ├── 01-hello.sh
│   ├── 02-variables.sh
│   ├── 03-arguments.sh
│   ├── 04-calculator.sh
│   └── 05-file-operations.sh
│
├── 02-programming-logic/
│   ├── 06-if-else.sh
│   ├── 07-comparison.sh
│   ├── 08-for-loop.sh
│   ├── 09-while-loop.sh
│   └── 10-case-statement.sh
│
├── 03-professional-scripting/
│   ├── 11-functions.sh
│   ├── 12-arrays.sh
│   ├── 13-exit-codes.sh
│   ├── 14-error-handling.sh
│   └── 15-logging.sh
│
├── 04-linux-administration/
│   ├── 16-file-manager.sh
│   ├── 17-permissions.sh
│   ├── 18-process-monitor.sh
│   ├── 19-disk-monitor.sh
│   └── 20-service-monitor.sh
│
├── 05-devops-automation/
│   ├── 21-log-analyzer.sh
│   ├── 22-backup.sh
│   ├── 23-health-report.sh
│   ├── 24-cron-automation.sh
│   └── 25-deployment.sh
│
├── 06-advanced-bash/
│   ├── 26-getopts.sh
│   ├── 27-string-manipulation.sh
│   ├── 28-log-processing.sh
│   ├── 29-debugging.sh
│   └── 30-cleanup.sh
│
└── projects/
    ├── server-health-monitor/
    ├── backup-automation/
    ├── log-monitoring/
    ├── user-audit/
    └── deployment-simulator/
```

---

## 💻 How to Run Bash Scripts

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/bash-scripting.git
```

Navigate into the repository:

```bash
cd bash-scripting
```

Give execution permission:

```bash
chmod +x script.sh
```

Execute the script:

```bash
./script.sh
```

Alternatively:

```bash
bash script.sh
```

---

## 🚀 Real-World Projects

### 1. Server Health Monitoring

**Objective:** Monitor Linux server health.

Features:
- Hostname and uptime information.
- CPU and memory information.
- Disk utilization monitoring.
- Threshold-based warnings.
- Automated health reports.

### 2. Automated Backup Management

**Objective:** Automate application and directory backups.

Features:
- Timestamped backup archives.
- Backup integrity validation.
- Logging.
- Backup retention management.
- Restore testing.

### 3. Log Monitoring and Analysis

**Objective:** Identify application errors.

Features:
- ERROR detection.
- WARNING detection.
- HTTP status code analysis.
- Error counting.
- Log summary reports.

### 4. Linux User Account Audit

**Objective:** Audit Linux user accounts.

Features:
- Extract usernames.
- Identify login shells.
- Count accounts.
- Generate account audit reports.

### 5. Application Deployment Automation

**Objective:** Simulate a deployment workflow.

Features:
- Version-based release directories.
- Deployment logs.
- Release validation.
- Previous release management.
- Rollback simulation.

---

## 🔍 Important Bash Commands

| Command | Description |
|---|---|
| `echo` | Print output |
| `read` | Accept user input |
| `grep` | Search text |
| `awk` | Process structured text |
| `sed` | Transform text |
| `find` | Search files |
| `cut` | Extract fields |
| `sort` | Sort data |
| `uniq` | Find unique lines |
| `wc` | Count lines and words |
| `chmod` | Change permissions |
| `tar` | Create archives |
| `cron` | Schedule jobs |
| `ps` | Display processes |
| `df` | Display filesystem usage |
| `free` | Display memory usage |
| `systemctl` | Manage systemd services |

---

## 🧪 Debugging and Code Quality

Syntax validation:

```bash
bash -n script.sh
```

Debug execution:

```bash
bash -x script.sh
```

Static analysis:

```bash
shellcheck script.sh
```

Install ShellCheck on Ubuntu:

```bash
sudo apt update
sudo apt install shellcheck
```

---

## 📅 14-Day Learning Plan

| Day | Learning Activity |
|---|---|
| 01 | Bash fundamentals |
| 02 | Conditions |
| 03 | Loops and case statements |
| 04 | Functions and arrays |
| 05 | Exit codes and logging |
| 06 | Files and permissions |
| 07 | Process and disk monitoring |
| 08 | Log analysis |
| 09 | Backup automation |
| 10 | System health reports |
| 11 | Cron automation |
| 12 | Deployment automation |
| 13 | Advanced scripting |
| 14 | Real-world projects |

---

## ✅ Learning Progress Tracker

- [ ] Complete Level 1 – Fundamentals
- [ ] Complete Level 2 – Programming Logic
- [ ] Complete Level 3 – Professional Scripting
- [ ] Complete Level 4 – Linux Administration
- [ ] Complete Level 5 – DevOps Automation
- [ ] Complete Level 6 – Advanced Bash
- [ ] Build Server Health Monitoring
- [ ] Build Backup Automation
- [ ] Build Log Monitoring
- [ ] Build User Account Audit
- [ ] Build Deployment Simulator

---

## 🎯 Final Learning Outcome

After completing this repository, you should be able to:

- Write Bash scripts independently.
- Automate repetitive Linux administration tasks.
- Monitor Linux server resources.
- Create reliable backup scripts.
- Analyze application logs.
- Automate routine operational workflows.
- Understand Bash scripting in DevOps environments.

---

## 📖 Recommended Tools

- Linux
- Bash
- Git and GitHub
- ShellCheck
- Visual Studio Code
- Docker
- Jenkins
- Ansible

---

## 🤝 Contributions

Suggestions, improvements, and practical lab contributions are welcome.

If you find this repository useful, consider giving it a ⭐.

---

## ⚠️ Disclaimer

This repository is intended for educational and practical learning purposes.

Always test scripts in a safe lab environment before using them on production servers. Review commands, permissions, and destructive operations carefully.

---

**Happy Learning! 🐧**

*Learn Bash. Automate Linux. Build DevOps Skills.*
