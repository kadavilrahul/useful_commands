# WSL (Windows Subsystem for Linux) Guide

## Installation

Install Ubuntu from Microsoft Store.

## Steps to Enable WSL on Windows

The error `0x8007019e` occurs because the Windows Subsystem for Linux (WSL) is not enabled on your machine.

### 1. Open PowerShell as Administrator
- Press `Windows Key + X` and select **Windows PowerShell (Admin)** or **Command Prompt (Admin)**

### 2. Enable WSL
Run the following command to enable WSL:
```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

### 3. Enable the Virtual Machine Platform
In the same PowerShell window, run this command:
```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

### 4. Restart your PC
Restart your PC to apply the changes.

### 5. Install WSL
After the restart, run the following command to install the latest WSL version:
```powershell
wsl --install
```

After performing these steps, you should no longer encounter the `0x8007019e` error when attempting to install or use WSL.

## Upgrading WSL 1 to WSL 2

If you encounter the error "WSL 1 is not supported. Please upgrade to WSL 2 or above" when installing packages like `@anthropic-ai/claude-code`, follow these steps:

### 1. Check Current WSL Version
```powershell
wsl -l -v
```

### 2. Enable Virtual Machine Platform
Run in PowerShell as Administrator:
```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
Restart your system after this.

### 3. Install WSL 2 Kernel Update
Download and install from Microsoft's official page: [WSL 2 Linux Kernel Update Package](https://aka.ms/wsl2kernel)

### 4. Set WSL 2 as Default (Optional)
```powershell
wsl --set-default-version 2
```

### 5. Convert Existing Distribution to WSL 2
```powershell
wsl --set-version Ubuntu-24.04 2
```
Replace `Ubuntu-24.04` with your actual distribution name from step 1.

### 6. Confirm Upgrade
```powershell
wsl -l -v
```
Should show VERSION 2 for your distribution.

## Uninstall WSL on Windows

```powershell
wsl --list --verbose
wsl --unregister <DistroName>
```

## Troubleshooting

For HyperV issues, check this [Microsoft documentation](https://learn.microsoft.com/en-us/windows/wsl/troubleshooting#error-0x80370102-the-virtual-machine-could-not-be-started-because-a-required-feature-is-not-installed).

## Initial Setup

```bash
sudo apt update && sudo apt upgrade -y
```

## File Transfer Between Windows and WSL

### Copy and Paste Guidelines
- Copy files from Windows folder and paste in `Home/rahul` only (i.e., `\\wsl.localhost\Ubuntu\home\rahul`)
- Other locations will have permission issues

### Command to Copy Files

#### Windows to Ubuntu
To copy a folder from Windows to Ubuntu WSL:

```bash
sudo cp -r /mnt/c/Users/Admin/Dropbox/Synchronization/Business/Ecommerce/Codes/Chatgpt_chats ~/Chatgpt_chats/
```

#### Ubuntu to Windows
```bash
sudo bash
cp /root/.npm/_logs/2024-10-18T09_48_09_445Z-debug.log /mnt/c/Users/Admin/Downloads/
```

### Command Explanation
- `sudo`: Elevates the command to run with administrative privileges
- `cp`: The copy command in Linux
- `-r`: Allows copying directories recursively (including all files and subdirectories)
- `/mnt/c/...`: Linux path that points to your Windows C:\ drive
- `~/`: Refers to your home directory in WSL

### Steps to Copy Files
1. Open your Ubuntu WSL terminal
2. Run the copy command
3. Find the copied files in your WSL home directory (`/home/<your_username>/`)

## Network Configuration

### Find IP Address
```bash
sudo apt install net-tools
ifconfig
```

### Access WSL from Windows
- WSL IP: `localhost` or `127.0.0.1`
- Access WSL services from Windows using `localhost:<port>`

### Port Forwarding
```powershell
# Forward port from WSL to Windows
netsh interface portproxy add v4tov4 listenport=<windows_port> listenaddress=0.0.0.0 connectport=<wsl_port> connectaddress=<wsl_ip>

# List port forwarding rules
netsh interface portproxy show all

# Delete port forwarding rule
netsh interface portproxy delete v4tov4 listenport=<port>
```
## Access root folders
## Connect to root
```bash
sudo apt update
```
Install and start OpenSSH server inside WSL:
```bash
sudo apt install openssh-server -y
```
```bash
sudo service ssh start
```
Check it’s running:
```bash
ps aux | grep sshd
```
Set a password for root
```
sudo passwd root
```
Open the SSH server config inside WSL:
```bash
sudo nano /etc/ssh/sshd_config
```
Find these lines (they may be commented out with #):
```
PermitRootLogin prohibit-password
```
or
```
PermitRootLogin no
```

Change it to:
```
PermitRootLogin yes
```
Try to connect to root
```bash
ssh root@localhost
```

## WSL Management Commands

### Version and Distribution Management
```bash
# Check WSL version
wsl --version

# List installed distributions
wsl --list --verbose
wsl -l -v

# Set default distribution
wsl --set-default <DistroName>

# Set WSL version for a distribution
wsl --set-version <DistroName> <Version>

# Update WSL
wsl --update

# Check WSL status
wsl --status
```

### Starting and Stopping WSL
```bash
# Start specific distribution
wsl -d <DistroName>

# Shutdown all WSL instances
wsl --shutdown

# Terminate specific distribution
wsl --terminate <DistroName>

# Run command in WSL from Windows
wsl <command>
wsl -d <DistroName> <command>
```

### Import and Export Distributions
```bash
# Export distribution
wsl --export <DistroName> <FileName.tar>

# Import distribution
wsl --import <DistroName> <InstallLocation> <FileName.tar>

# Import with version
wsl --import <DistroName> <InstallLocation> <FileName.tar> --version <Version>
```

## File System Operations

### Mount Windows Drives
```bash
# Windows drives are automatically mounted under /mnt/
ls /mnt/c/  # Access C: drive
ls /mnt/d/  # Access D: drive

# Manual mount
sudo mkdir /mnt/usb
sudo mount -t drvfs D: /mnt/usb
```

### File Permissions
```bash
# Fix file permissions for copied files
chmod +x filename
chmod 755 directory/
chown $USER:$USER filename

# Change ownership recursively
sudo chown -R $USER:$USER /path/to/directory
```

### Symbolic Links
```bash
# Create symbolic link to Windows directory
ln -s /mnt/c/Users/$USER/Documents ~/Documents

# Create symbolic link to WSL directory from Windows
# Run in Windows Command Prompt as Administrator
mklink /D C:\WSL-Home \\wsl$\Ubuntu\home\username
```

## Performance Optimization

### WSL Configuration (.wslconfig)
Create `C:\Users\<username>\.wslconfig`:
```ini
[wsl2]
memory=4GB
processors=2
swap=2GB
swapFile=C:\\temp\\wsl-swap.vhdx
localhostForwarding=true
```

### Distribution-specific Configuration (wsl.conf)
Create `/etc/wsl.conf` in WSL:
```ini
[automount]
enabled = true
root = /mnt/
options = "metadata,umask=22,fmask=11"

[network]
generateHosts = true
generateResolvConf = true

[boot]
systemd = true
```

## Development Environment Setup

### Install Essential Tools
```bash
# Install development environment
sudo apt update && sudo apt upgrade -y && sudo apt install build-essential curl wget git vim nano -y

# Install Node.js via NodeSource
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install nodejs -y

# Install Python and pip
sudo apt install python3 python3-pip -y

# Install Docker (see cli_tools_curated.md for complete setup)
curl -fsSL https://get.docker.com -o get-docker.sh && sudo sh get-docker.sh && sudo usermod -aG docker $USER
```

### SSH Setup
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# Start SSH agent
eval "$(ssh-agent -s)"

# Add SSH key
ssh-add ~/.ssh/id_ed25519

# Copy public key
cat ~/.ssh/id_ed25519.pub
```

## Common Troubleshooting

### WSL Won't Start
```powershell
# Check if WSL is enabled
dism.exe /online /get-featureinfo /featurename:Microsoft-Windows-Subsystem-Linux

# Reset WSL
wsl --shutdown
wsl --unregister <DistroName>
# Reinstall from Microsoft Store
```

### Performance Issues
```bash
# Check disk usage
df -h
du -sh ~/*

# Clean package cache
sudo apt autoremove
sudo apt autoclean

# Compact WSL disk (run in PowerShell as Admin)
wsl --shutdown
diskpart
# select vdisk file="C:\Users\<username>\AppData\Local\Packages\<PackageName>\LocalState\ext4.vhdx"
# compact vdisk
```

### Network Issues
```bash
# Reset network configuration
sudo rm /etc/resolv.conf
sudo bash -c 'echo "nameserver 8.8.8.8" > /etc/resolv.conf'

# Restart WSL networking
wsl --shutdown
# Restart WSL
```

### File Permission Issues
```bash
# Fix Windows file permissions in WSL
sudo umount /mnt/c
sudo mount -t drvfs C: /mnt/c -o metadata,uid=1000,gid=1000,umask=022,fmask=111
```

### Memory Issues
```bash
# Check memory usage
free -h
ps aux --sort=-%mem | head

# Clear cache
sudo sync
sudo echo 3 > /proc/sys/vm/drop_caches
```

## Backup and Recovery

### Backup WSL Distribution
```powershell
# Create backup
wsl --export Ubuntu C:\Backup\ubuntu-backup.tar

# Restore from backup
wsl --import Ubuntu-Restored C:\WSL\Ubuntu-Restored C:\Backup\ubuntu-backup.tar
```

### Reset WSL Installation
```powershell
# Complete reset
wsl --unregister <DistroName>
# Reinstall from Microsoft Store

# Reset to default settings
wsl --install --distribution <DistroName>
```

## Useful Aliases and Functions

Add to `~/.bashrc` or `~/.zshrc`:
```bash
# Quick navigation
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'

# WSL specific
alias windir='cd /mnt/c/Users/$USER'
alias reload='source ~/.bashrc'

# Git shortcuts (see git.md for complete reference)
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'

# System info
alias sysinfo='uname -a && lsb_release -a'
```
