# Windows Commands Reference

## 🚀 Essential Keyboard Shortcuts

### System & Window Management

Show desktop (toggle):
```
Win + D
```

Open File Explorer:
```
Win + E
```

Lock your computer:
```
Win + L
```

Open Task View (virtual desktops):
```
Win + Tab
```

Switch between open apps:
```
Alt + Tab
```

Close current window/app:
```
Alt + F4
```

Open Task Manager directly:
```
Ctrl + Shift + Esc
```

Snap windows (left/right/top/bottom):
```
Win + Arrow keys
```

Create a new virtual desktop:
```
Win + Ctrl + D
```

Switch virtual desktops:
```
Win + Ctrl + ← / →
```

### File & Folder Management

Copy:
```
Ctrl + C
```

Cut:
```
Ctrl + X
```

Paste:
```
Ctrl + V
```

Undo:
```
Ctrl + Z
```

Redo:
```
Ctrl + Y
```

Permanently delete a file:
```
Shift + Delete
```

Open properties of selected file:
```
Alt + Enter
```

Create new folder:
```
Ctrl + Shift + N
```

Rename selected item:
```
F2
```

Select all items:
```
Ctrl + A
```

### Navigation & Search

Open Search:
```
Win + S
```

Open Search (alternative):
```
Win
```

Find in most apps:
```
Ctrl + F
```

Open Run dialog:
```
Win + R
```

Open Settings:
```
Win + I
```

Navigate back in Explorer:
```
Alt + ←
```

Navigate forward in Explorer:
```
Alt + →
```

### Browser (Edge, Chrome, Firefox)

Open new tab:
```
Ctrl + T
```

Reopen last closed tab:
```
Ctrl + Shift + T
```

Close current tab:
```
Ctrl + W
```

Switch between tabs (forward):
```
Ctrl + Tab
```

Switch between tabs (backward):
```
Ctrl + Shift + Tab
```

Focus address bar:
```
Ctrl + L
```

Focus address bar (alternative):
```
Alt + D
```

Downloads:
```
Ctrl + J
```

History:
```
Ctrl + H
```

Open incognito window:
```
Ctrl + Shift + N
```

### Typing & Text Editing

Move cursor word by word (left):
```
Ctrl + ←
```

Move cursor word by word (right):
```
Ctrl + →
```

Select word by word (left):
```
Ctrl + Shift + ←
```

Select word by word (right):
```
Ctrl + Shift + →
```

Delete whole word to the left:
```
Ctrl + Backspace
```

Delete word to the right:
```
Ctrl + Delete
```

Save:
```
Ctrl + S
```

Print:
```
Ctrl + P
```

### Developer/Power User

Power user menu:
```
Win + X
```

Run app as administrator:
```
Ctrl + Shift + Enter
```

Cancel command in terminal:
```
Ctrl + C
```

Auto-complete file/folder name in CMD/PowerShell:
```
Tab
```

## Most Common Commands

### Basic Navigation & File Operations

List directory contents:
```cmd
dir
```

Change directory:
```cmd
cd [path]
```

Go up one directory:
```cmd
cd ..
```

Create directory:
```cmd
mkdir [dirname]
```

Copy files:
```cmd
copy [source] [destination]
```

Move/rename files:
```cmd
move [source] [destination]
```

Delete files:
```cmd
del [filename]
```

Display file contents:
```cmd
type [filename]
```

### Essential System Commands

Display current username:
```cmd
whoami
```

Display IP configuration:
```cmd
ipconfig
```

Test network connectivity:
```cmd
ping [hostname/ip]
```

List running processes:
```cmd
tasklist
```

Kill process by name:
```cmd
taskkill /im [processname]
```

Clear DNS cache:
```cmd
ipconfig /flushdns
```

System file checker:
```cmd
sfc /scannow
```

### Quick System Info

Display Windows version:
```cmd
ver
```

Display computer name:
```cmd
hostname
```

Display system configuration:
```cmd
systeminfo
```

## File and Directory Operations

### Advanced Navigation

Go to root directory:
```cmd
cd \
```

List all files including hidden:
```cmd
dir /a
```

Display directory structure:
```cmd
tree
```

### Advanced File Operations

Copy directories recursively:
```cmd
xcopy [source] [dest] /s
```

Remove empty directory:
```cmd
rmdir [dirname]
```

Remove directory and contents:
```cmd
rmdir /s [dirname]
```

Display file contents page by page:
```cmd
more [filename]
```

## Network Commands

### Advanced Network Configuration

Display detailed IP configuration:
```cmd
ipconfig /all
```

Release IP address:
```cmd
ipconfig /release
```

Renew IP address:
```cmd
ipconfig /renew
```

### Network Troubleshooting

Trace route to destination:
```cmd
tracert [hostname/ip]
```

DNS lookup:
```cmd
nslookup [hostname]
```

Display network connections:
```cmd
netstat -an
```

Test port connectivity:
```cmd
telnet [host] [port]
```

## Process Management

### Advanced Process Operations

List processes with services:
```cmd
tasklist /svc
```

Kill process by PID:
```cmd
taskkill /pid [processid]
```

Force kill process:
```cmd
taskkill /f /im [process]
```

### Network Shares

View network computers:
```cmd
net view
```

Display mapped drives:
```cmd
net use
```

Map network drive:
```cmd
net use [drive:] [\\server\share]
```

Disconnect mapped drive:
```cmd
net use [drive:] /delete
```

## System Tools & Utilities

### Common System Tools

System configuration utility:
```cmd
msconfig
```

Event viewer:
```cmd
eventvwr
```

Device manager:
```cmd
devmgmt.msc
```

Services console:
```cmd
services.msc
```

### Service Management

List all services:
```cmd
sc query
```

Start service:
```cmd
net start [servicename]
```

Stop service:
```cmd
net stop [servicename]
```

Query specific service:
```cmd
sc query [servicename]
```

Set service to auto start:
```cmd
sc config [service] start=auto
```

### Disk Operations

Check disk for errors:
```cmd
chkdsk [drive:]
```

Fix disk errors:
```cmd
chkdsk [drive:] /f
```

Show free disk space:
```cmd
fsutil volume diskfree [drive:]
```

Disk cleanup utility:
```cmd
cleanmgr
```

## System Information & Hardware

### Alternative System Info Commands

Display current username (alternative):
```cmd
echo %username%
```

Display computer name (alternative):
```cmd
echo %computername%
```

### Hardware Information

Get CPU information:
```cmd
wmic cpu get name
```

Get RAM information:
```cmd
wmic memorychip get capacity
```

Get disk information:
```cmd
wmic diskdrive get size,model
```

DirectX diagnostics tool:
```cmd
dxdiag
```

## File Attributes & Permissions

### File Attributes

Show file attributes:
```cmd
attrib [filename]
```

Hide file:
```cmd
attrib +h [filename]
```

Unhide file:
```cmd
attrib -h [filename]
```

Make file read-only:
```cmd
attrib +r [filename]
```

Remove read-only attribute:
```cmd
attrib -r [filename]
```

### Permissions

Display permissions:
```cmd
icacls [file/folder]
```

Grant full control:
```cmd
icacls [file] /grant [user]:F
```

Remove user permissions:
```cmd
icacls [file] /remove [user]
```

Take ownership of file:
```cmd
takeown /f [file]
```

## User Management

List user accounts:
```cmd
net user
```

Display user details:
```cmd
net user [username]
```

Change user password:
```cmd
net user [user] [password]
```

List local groups:
```cmd
net localgroup
```

List admin group members:
```cmd
net localgroup administrators
```

## Environment Variables

Display all environment variables:
```cmd
set
```

Display specific variable:
```cmd
set [variable]
```

Set environment variable:
```cmd
set [variable]=[value]
```

Set permanent environment variable:
```cmd
setx [variable] [value]
```

Display PATH variable:
```cmd
echo %PATH%
```

Display current PATH:
```cmd
path
```

Add to PATH temporarily:
```cmd
path [newpath];%path%
```

## PowerShell Commands

### Basic PowerShell

List running processes:
```powershell
Get-Process
```

List services:
```powershell
Get-Service
```

List directory contents (ls equivalent):
```powershell
Get-ChildItem
```

Copy files:
```powershell
Copy-Item [source] [dest]
```

Move files:
```powershell
Move-Item [source] [dest]
```

Delete files/folders:
```powershell
Remove-Item [path]
```

Create directory:
```powershell
New-Item -ItemType Directory [name]
```

### Advanced PowerShell

Get recent system events:
```powershell
Get-EventLog System -Newest 10
```

Get system info:
```powershell
Get-WmiObject Win32_ComputerSystem
```

Ping equivalent:
```powershell
Test-Connection [hostname]
```

## Advanced & Specialized Commands

### Registry Operations

Open registry editor:
```cmd
regedit
```

Query registry key:
```cmd
reg query [keypath]
```

Add registry value:
```cmd
reg add [keypath] /v [name] /d [data]
```

Delete registry value:
```cmd
reg delete [keypath] /v [name]
```

### Windows Features

List Windows features:
```cmd
dism /online /get-features
```

Enable feature:
```cmd
dism /online /enable-feature /featurename:[name]
```

Disable feature:
```cmd
dism /online /disable-feature /featurename:[name]
```

### Advanced System Tools

System information:
```cmd
msinfo32
```

Group policy editor:
```cmd
gpedit.msc
```

Disk partitioning utility:
```cmd
diskpart
```

Boot configuration:
```cmd
bcdedit
```

### System Maintenance

Repair system image:
```cmd
dism /online /cleanup-image /restorehealth
```

Defragment disk:
```cmd
defrag [drive:]
```

Show directory sizes:
```cmd
dir [drive:] /-c
```

Compress folder:
```cmd
compact /c [folder]
```

Uncompress folder:
```cmd
compact /u [folder]
```

### Security Commands

Update group policy:
```cmd
gpupdate /force
```

Show user privileges:
```cmd
whoami /priv
```

Run as different user:
```cmd
runas /user:[user] [command]
```

Securely delete free space:
```cmd
cipher /w:[folder]
```

### Shutdown & Boot

Shutdown immediately:
```cmd
shutdown /s /t 0
```

Restart immediately:
```cmd
shutdown /r /t 0
```

Abort shutdown:
```cmd
shutdown /a
```

## Batch File Operations

### Batch Commands

Disable command echoing:
```cmd
@echo off
```

Wait for user input:
```cmd
pause
```

Wait for specified seconds:
```cmd
timeout /t [seconds]
```

Jump to label:
```cmd
goto [label]
```

Conditional execution:
```cmd
if exist [file] [command]
```

Loop through files:
```cmd
for %%i in (*.*) do [command]
```

### Variables in Batch

Get user input:
```cmd
set /p variable=Enter value:
```

Arithmetic operations:
```cmd
set /a result=5+3
```

Display variable value:
```cmd
echo %variable%
```

## Tips and Tricks

- Use `Tab` key for auto-completion
- Use `F7` to see command history
- Use `Ctrl+C` to cancel running command
- Use `>` to redirect output to file: `dir > filelist.txt`
- Use `>>` to append output to file: `dir >> filelist.txt`
- Use `|` to pipe output to another command: `dir | find "txt"`
- Use `&` to run multiple commands: `dir & echo done`
- Use `&&` to run second command only if first succeeds
- Use `||` to run second command only if first fails