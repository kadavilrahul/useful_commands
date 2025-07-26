# Linux Commands Reference

## 📋 Table of Contents
- [Custom Commands and Aliases](#custom-commands-and-aliases)
- [Command History Management](#command-history-management)
- [System Information](#system-information)
- [User Management](#user-management)
- [System Configuration](#system-configuration)
- [Package Management](#package-management)
- [Service Management](#service-management)
- [File Operations](#file-operations)
- [SSH Operations](#ssh-operations)
- [Monitoring](#monitoring)
- [Swap Management](#swap-management)
- [Other Commands](#other-commands)

## Custom Commands and Aliases

### Shell Aliases

#### Clear Command Alias
**Purpose**: Quick shortcut for clearing the terminal screen

**Implementation**:
```bash
# Add to ~/.bashrc
alias c='clear'
```

**Usage**:
```bash
c  # Clears the terminal screen
```

**Setup**:
1. Add the alias to your shell configuration file:
   ```bash
   echo "alias c='clear'" >> ~/.bashrc
   ```
2. Reload the configuration:
   ```bash
   source ~/.bashrc
   ```

### Smart Functions

#### Clone Command with Fuzzy Search
**Purpose**: Quickly clone GitHub repositories using keywords with tab completion

**Features**:
- Fuzzy search by repository name keywords
- Tab completion for common keywords
- Clones to current directory and automatically enters the folder
- Shows repository info after cloning
- Handles multiple matches with interactive selection

**Implementation**:
```bash
# Smart clone function is stored in /root/.clone_helper.sh
# Automatically loaded via ~/.bashrc
```

**Usage**:
```bash
clone email      # Finds email_automation_private, setup_email_system, etc.
clone html       # Finds generate_html_from_csv, etc.
clone wordpress  # Finds install_wordpress_on_lamp, etc.
clone useful     # Finds useful_commands repo
```

**Tab Completion Keywords**:
- `email`, `html`, `csv`, `wordpress`, `woocommerce`, `automation`
- `generate`, `import`, `install`, `migration`, `backup`, `clone`
- `useful`, `commands`, `agent`, `streamlit`, `python`, `nodejs`, `go`

**Setup**:
1. The function is automatically available after running the setup
2. Uses your existing GitHub configuration from `/root/projects/Repositories/clone_repos/config.json`
3. Works with both public and private repositories (if token is configured)

**Interactive Features**:
- If multiple matches found, shows numbered list for selection
- Press Enter to select the first option
- Shows README preview and recent commits after cloning
- Handles existing directories gracefully

## Command History Management

### Re-run Previous Commands
Using Command Number:
```bash
!<number>
```

Repeat Last Command:
```bash
!!
```

Search and Execute with String:
```bash
!<command_prefix>
```

Reverse Search:
- Press `Ctrl + R` to initiate reverse search
- Type part of the command, and the terminal will auto-complete with the most recent match
- Press Enter to execute or `Ctrl + R` again for older matches

Using fc Command:
```bash
fc -s <number>
```

View Command History:
```bash
history
```

Reload History:
```bash
history -r
```

## System Information

### Network and IP
Check IP:
```bash
ip a
```

Show Network Interfaces:
```bash
ifconfig
```

### System Details
List Hardware:
```bash
sudo apt-get install lshw
```
```bash
sudo lshw
```

CPU Information:
```bash
lscpu
```

Memory Usage:
```bash
free -h
```

Disk Usage:
```bash
df -h
```

Current User:
```bash
whoami
```

Kernel Information:
```bash
uname -a
```

OS Details:
```bash
cat /etc/os-release
```

Distribution Information:
```bash
lsb_release -a
```

Server Hostname:
```bash
hostname
```

### Disk Usage
Root Partition Usage:
```bash
df -h /
```

Directory Sizes:
```bash
du -sh /path/*
```

Interactive Disk Usage Analyzer:
```bash
sudo apt install ncdu
```
```bash
ncdu /
```

### System Performance
Interactive Process Viewer:
```bash
htop
```

Memory Usage in MB:
```bash
free -m
```

## User Management

### Password Management
Change Root Password:
```bash
passwd
```

Change User Password:
```bash
sudo passwd username
```

### User Switching
Switch to Another User:
```bash
su username
```

Switch to Root:
```bash
sudo -i
```
```bash
sudo bash
```
Delete user and its home directory
```bash
sudo userdel -r username
```

### User Information
Show Logged in Users:
```bash
who
```

List System Users:
```bash
awk -F: '$3<1000 {print $1}' /etc/passwd
```

## System Configuration

### Timezone
Show Time Settings:
```bash
timedatectl
```

Set Timezone:
```bash
sudo timedatectl set-timezone Asia/Kolkata
```

### Language and Locale
Check Current Language:
```bash
locale
```

List Available Languages:
```bash
locale -a
```

Change Language:
```bash
sudo nano /etc/default/locale
```
Add these lines:
```bash
LANG=en_US.UTF-8
LANGUAGE=en_US.UTF-8
LC_ALL=en_US.UTF-8
```
Then run:
```bash
source /etc/default/locale
```
```bash
sudo reboot
```

### Firewall
Enable Firewall:
```bash
sudo ufw enable -y
```

Check Firewall Status:
```bash
sudo ufw status
```

Allow SSH:
```bash
sudo ufw allow ssh
```

## Package Management

### System Updates
Update Package Lists:
```bash
sudo apt update
```

Upgrade Packages:
```bash
sudo apt upgrade -y
```

Full System Upgrade:
```bash
sudo apt update && sudo apt upgrade -y && sudo apt dist-upgrade -y && sudo apt autoremove -y && sudo update-grub && sudo snap refresh
```

### Package Installation/Removal
Install Package:
```bash
sudo apt install package_name
```

Remove Package:
```bash
sudo apt remove package_name
```

## Service Management

### Apache
Reload Apache:
```bash
sudo systemctl reload apache2
```

Enable Apache:
```bash
sudo systemctl enable apache2
```

Start Apache:
```bash
sudo systemctl start apache2
```

Restart Apache:
```bash
sudo systemctl restart apache2
```

### Redis
Restart Redis:
```bash
sudo systemctl restart redis
```

### MySQL
Check MySQL Status:
```bash
sudo systemctl status mysql
```

Restart MySQL:
```bash
sudo systemctl restart mysql
```

## File Operations

### Create and Edit
Create Empty File:
```bash
touch filename
```

Edit File:
```bash
nano filename
```

### Remove Files/Directories
Remove Directory:
```bash
rm -r directory
```
Remove all files and subdirectories inside a directory but keep the directory itself, use:

```bash
rm -rf /path/to/directory/*
```
Remove all files and subdirectories alongwith hidden files
```bash
rm -rf /var/www/main.silkroademart.com/{*,.*}
```
Force Remove Directory:
```bash
rm -rf directory
```

Empty File:
```bash
> filename
```

### Copy and Move
Copy Directory:
```bash
cp -r source destination
```
Examples:
Copying a directory:
```bash
cp -r myfolder backup/
```
Copy only the contents of a directory (not the directory itself) to a new directory, use:

```bash
cp -r source/* destination/
```
Explanation:
cp -r → Copies directories and files recursively.
source/* → Copies all files and subdirectories inside source (but not source itself).
destination/ → The target directory where the files and subdirectories will be copied

Copy Directory with Spaces:
```bash
cp -r "source directory" "destination directory"
```

Move/Rename:
```bash
mv source destination
```

### Find Files
Find by Extension:
```bash
find / -type f -name "*.extension"
```

Using locate:
```bash
sudo apt install plocate
```
```bash
locate filename
```

### Search in Files
Search Pattern in Files:
```bash
grep -r "pattern" /path/to/search
```

## SSH Operations

### SSH Connection
SSH with Password:
```bash
sshpass -p "password" ssh -o StrictHostKeyChecking=no user@host
```

### SSH Service
Restart SSH:
```bash
sudo systemctl restart ssh
```
```bash
sudo systemctl restart sshd
```

## Monitoring

### Watch Command
Monitor Command Output:
```bash
watch -n 5 command
```

Example - Monitor Disk Usage:
```bash
watch -n 5 df -h
```

### Log Viewing
View Log File:
```bash
tail -f /var/log/apache2/error.log
```

View System Logs:
```bash
tail -f /var/log/syslog
```

## Swap Management
Create Swap File:
```bash
sudo fallocate -l 1G /swapfile
```
```bash
sudo chmod 600 /swapfile
```
```bash
sudo mkswap /swapfile
```
```bash
sudo swapon /swapfile
```

Make Swap Permanent:
```bash
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

## Additional Examples

### Advanced File Operations
Remove Files with Spaces:
```bash
sudo rm -rf "/path/to/folder with spaces"
```

Move Large Files:
```bash
mv /source/large_file.tar.gz /destination/
```

Copy Folders with Spaces:
```bash
cp -r "/source folder" "/destination folder"
```

### Log Analysis
Search for Errors in Logs:
```bash
grep -r "error" /var/log
```

Monitor Multiple Log Files:
```bash
tail -f /var/log/apache2/error.log /var/log/syslog
```

### File Operations Examples
Remove Files with Spaces:
```bash
sudo rm -rf "/root/duplicate detection 03"
```

Move Files:
```bash
mv /source/file.tar.gz /destination/
```

Copy Folders with Spaces:
```bash
cp -r "/source folder" "/destination folder"
```

Search Example:
```bash
grep -r "error" /var/log
```

### Additional Examples
Search in Log Files:
```bash
grep -r "error" /var/log
```
