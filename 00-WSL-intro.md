# What is WSL?

> "The Windows Subsystem for Linux lets developers run a GNU/Linux environment -- including most command-line tools, utilities, and applications -- directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup."
>
> <small><https://learn.microsoft.com/en-us/windows/wsl/about></small>

---

## Some Features

- **A merge of Linux and Windows** &#x1F60D;
- Linux bash (and its commands) on Windows
- Development environment with linux
- Use linux commands in powershell
- No need for a virtual machine setup

---

## Setup - Enable Windows Subsystem for Linux <small>Part 1/3</small>

1. Open PowerShell as an admin.
   - On the Start menu, type PowerShell to pull up the desktop app.
   - Right-click Windows PowerShell and select Run as administrator.

2. Copy and paste this script to enable the WSL feature:

   ```powershell
   Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
   ```

3. Restart your computer when prompted.
4. And reopen your powershell admin console.

---

## Setup - Install a Linux Distribution <small>Part 2/3</small>

> :link: [List of WSL Basic Commands](https://learn.microsoft.com/en-us/windows/wsl/basic-commands)

1. (Re)open PowerShell as an admin.
2. Check WSL status:
   
   ```bash
   wsl --status
   ```

   - Is WSL Version 2 active? If not

    ```bash
    wsl --set-default-version 2
    ```

3. List available linux distributions:

   ```bash
   wsl --list --online
   ```
   
---
   
## Setup - Install a Linux Distribution <small>Part 3/3</small>
   
4. Install for example ("latest") Ubuntu:

   ```bash
   wsl --install --distribution ubuntu --web-download
   ```

5. After Ubuntu starts - set up your Linux username and password
   - this will be your default account
   - this account has `sudo` (Super User DO) admin rights
   - don't forget your password - you need it for `sudo`-ing!
6. Update your system (within WSL Distro):

   ```bash
   sudo apt update
   sudo apt upgrade
   ```


---

## Some Useful WSL Commands

| Command | Info |
| -------- | -------- |
| `wsl --list --verbose` | list details on local installed distributions |
| `wsl -d <Distro> --user <User>` | run/start specific linux distro  as user|
| `<Distro> config --default-user <User>` | Change Default user of a distro |
| `wsl --terminate <Distro>` | Terminate (end) a specific distro |
| `wsl --mount <DiskPath> ` | Mount a disk or device - see [WSL Mount](https://learn.microsoft.com/en-us/windows/wsl/basic-commands#mount-a-disk-or-device) |

*Hint: to leave an running WSL and return to powershell type* `exit`.

---

## Setup/Tryout WSL Development Environment

> :link: [DevEnv Setup](https://learn.microsoft.com/en-us/windows/wsl/setup/environment)

- [Terminal Setup](https://learn.microsoft.com/en-us/windows/wsl/setup/environment#set-up-windows-terminal)
- [Tryout Integration between Linux and Unix](https://learn.microsoft.com/en-us/training/modules/get-started-with-windows-subsystem-for-linux/3-integration-between-linux-and-windows)
- [VSCode Setup](https://learn.microsoft.com/en-us/windows/wsl/setup/environment#use-visual-studio-code)
- [VSCode Setup Training](https://learn.microsoft.com/en-us/training/modules/get-started-with-windows-subsystem-for-linux/5-vscode-integration)


---

### You Forgot Your User Password?

1. In PowerShell: `wsl -d <Distro> -u root`
2. Within WSL: `passwd <username>`
   - where `<username>` is the username of the account whose password you've forgotten.
3. You will be prompted to enter a new UNIX password and then confirm that password.
4. Once you're told that the password has updated successfully, close WSL inside of PowerShell using the command: exit.
