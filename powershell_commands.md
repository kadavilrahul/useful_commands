# PowerShell Commands Reference

## Basic Navigation

### Directory Operations
List Directory Contents (Shows files and folders in current directory):
```powershell
Get-ChildItem  # Full command
ls             # Alias
dir            # Alias

# Example - List all .txt files:
Get-ChildItem *.txt
# Example - List all items including hidden:
Get-ChildItem -Force
```

Change Directory (Navigate to different folder):
```powershell
Set-Location path  # Full command
cd path           # Alias

# Example - Change to Documents folder:
cd C:\Users\Username\Documents
# Example - Go up one level:
cd ..
```

Get Current Directory (Show where you are):
```powershell
Get-Location  # Full command
pwd           # Alias

# Example:
pwd  # Outputs something like: C:\Users\Username
```

Create Directory (Make new folder):
```powershell
New-Item -ItemType Directory -Path "DirectoryName"  # Full command
mkdir DirectoryName                                 # Alias

# Example - Create nested directories:
mkdir "C:\Projects\NewProject\src"
```

Remove Directory (Delete folder):
```powershell
Remove-Item -Path "DirectoryName" -Recurse  # Full command
rmdir DirectoryName                         # Alias

# Example - Remove directory with confirmation:
Remove-Item "OldProject" -Recurse -Confirm
```

## File Operations

### Basic File Commands
Create New File:
```powershell
New-Item -ItemType File -Path "filename.txt"

# Example - Create file with content:
New-Item -ItemType File -Path "log.txt" -Value "Initial log entry"
```

Copy File (Duplicate files or directories):
```powershell
Copy-Item "source" "destination"  # Full command
cp source destination            # Alias

# Example - Copy with overwrite:
Copy-Item "report.docx" "backup/report.docx" -Force
# Example - Copy multiple files:
Copy-Item "C:\logs\*.log" "D:\backup"
```

Move/Rename File:
```powershell
Move-Item "source" "destination"  # Full command
mv source destination            # Alias

# Example - Rename file:
Move-Item "old.txt" "new.txt"
# Example - Move to different directory:
Move-Item "document.pdf" "C:\Archive\"
```

Delete File:
```powershell
Remove-Item "filename"  # Full command
del filename           # Alias
rm filename           # Alias

# Example - Delete with confirmation:
Remove-Item "temp.txt" -Confirm
# Example - Delete multiple files:
Remove-Item *.tmp
```

Get File Content (Read file):
```powershell
Get-Content "filename"  # Full command
cat filename           # Alias
type filename         # Alias

# Example - Read first 5 lines:
Get-Content "log.txt" -Head 5
# Example - Read and wait for changes:
Get-Content "log.txt" -Wait
```

Write to File:
```powershell
# Overwrite existing content:
Set-Content -Path "file.txt" -Value "text"
# Append to existing content:
Add-Content -Path "file.txt" -Value "text"

# Example - Log with timestamp:
Add-Content "log.txt" "$(Get-Date) - Process started"
```

### File Search
Find Files (Search for files in directories):
```powershell
Get-ChildItem -Path "C:\" -Filter "*.txt" -Recurse

# Example - Find all PowerShell scripts modified in last 24 hours:
Get-ChildItem -Path C:\ -Filter *.ps1 -Recurse | 
    Where-Object { $_.LastWriteTime -gt (Get-Date).AddDays(-1) }
```

Search File Content (Find text in files):
```powershell
Select-String -Path "*.txt" -Pattern "searchterm"

# Example - Find 'error' in log files:
Select-String -Path "C:\Logs\*.log" -Pattern "error" -Context 2,2
```

## System Information

### System Details
Get OS Information:
```powershell
Get-ComputerInfo

# Example - Get specific OS info:
Get-ComputerInfo | Select-Object WindowsVersion, OsName, OsVersion
```

Get IP Configuration:
```powershell
Get-NetIPConfiguration  # Full command
ipconfig               # Alias

# Example - Get detailed IP info:
Get-NetIPConfiguration | Select-Object InterfaceDescription, IPv4Address
```

### Process Management
List Processes (Show running programs):
```powershell
Get-Process  # Full command
ps           # Alias

# Example - Find specific process:
Get-Process -Name "chrome"
# Example - Sort by memory usage:
Get-Process | Sort-Object -Property WS -Descending | Select-Object -First 10
```

Stop Process (End running program):
```powershell
Stop-Process -Name "processname"
Stop-Process -Id processId

# Example - Stop all Chrome instances:
Stop-Process -Name "chrome" -Force
```

## User Management

### User Information
Get Current User:
```powershell
$env:USERNAME
whoami

# Example - Get full user details:
whoami /all
```

Create New User:
```powershell
New-LocalUser -Name "username" -Password (ConvertTo-SecureString "password" -AsPlainText -Force)

# Example - Create user and add to group:
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
New-LocalUser "JohnDoe" -Password $password -FullName "John Doe" -Description "Staff"
Add-LocalGroupMember -Group "Users" -Member "JohnDoe"
```

## Network Operations

### Network Commands
Test Connection (Check if host is reachable):
```powershell
Test-Connection "hostname/IP"  # Full command
ping hostname/IP             # Alias

# Example - Test with count:
Test-Connection "google.com" -Count 2
```

Download File:
```powershell
Invoke-WebRequest -Uri "URL" -OutFile "filename"
wget URL -OutFile filename  # Alias

# Example - Download with progress:
Invoke-WebRequest "https://example.com/file.zip" -OutFile "download.zip" -Progress
```

## Script Execution

### Execution Policy
Get/Set Execution Policy:
```powershell
Get-ExecutionPolicy
Set-ExecutionPolicy RemoteSigned

# Example - Set for current user only:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

## Error Handling
Try-Catch Block (Handle errors gracefully):
```powershell
try {
    # Attempt something risky
    Remove-Item "nonexistent.txt"
} catch {
    # Handle the error
    Write-Error "Failed to remove file: $_"
}

# Example - Multiple error types:
try {
    $number = "abc" / 2
} catch [DivideByZeroException] {
    Write-Error "Cannot divide by zero!"
} catch [System.Management.Automation.RuntimeException] {
    Write-Error "Invalid operation!"
} catch {
    Write-Error "An unknown error occurred: $_"
}
```

## Common Aliases
```powershell
cls     # Clear-Host (clear screen)
copy    # Copy-Item
del     # Remove-Item
dir     # Get-ChildItem
echo    # Write-Output
move    # Move-Item
rd      # Remove-Item -Recurse
ren     # Rename-Item
type    # Get-Content
```

## Remote Management

### Remote Sessions
Create Remote Session:
```powershell
Enter-PSSession -ComputerName "hostname"

# Example - Connect to remote machine:
Enter-PSSession -ComputerName "RemotePC" -Credential (Get-Credential)
```

Copy Files to Remote:
```powershell
Copy-Item "source" -Destination "\\hostname\path" -Recurse

# Example - Copy files to remote machine:
Copy-Item "C:\Files\*" -Destination "\\RemotePC\C$\Files\" -Recurse
```

Execute Remote Command:
```powershell
Invoke-Command -ComputerName "hostname" -ScriptBlock { command }

# Example - Run command on remote machine:
Invoke-Command -ComputerName "RemotePC" -ScriptBlock { Get-Process }
```

## Package Management

### Package Commands
List Available Packages:
```powershell
Get-Package

# Example - List all installed packages:
Get-Package -ListAvailable
```

Find Package:
```powershell
Find-Package "packagename"

# Example - Search for package:
Find-Package -Name "Microsoft.PowerShell"
```

Install Package:
```powershell
Install-Package "packagename"

# Example - Install package:
Install-Package -Name "Microsoft.PowerShell"
```

Uninstall Package:
```powershell
Uninstall-Package "packagename"

# Example - Uninstall package:
Uninstall-Package -Name "Microsoft.PowerShell"
```

## Environment Variables

### Variable Operations
List All Environment Variables:
```powershell
Get-ChildItem Env:

# Example - List all environment variables:
Get-ChildItem Env: | Sort-Object Name
```

Get Specific Variable:
```powershell
$env:VARIABLE_NAME

# Example - Get PATH variable:
$env:PATH
```

Set Environment Variable:
```powershell
$env:VARIABLE_NAME = "value"

# Example - Set new variable:
$env:NEW_VAR = "New Value"
```

## Disk Management

### Disk Information
Get Disk Space:
```powershell
Get-PSDrive

# Example - Get disk space for C: drive:
Get-PSDrive -PSProvider FileSystem -Root "C:\"
```

Get Volume Information:
```powershell
Get-Volume

# Example - Get volume information for C: drive:
Get-Volume -DriveLetter C
```

Get Physical Disk Info:
```powershell
Get-PhysicalDisk

# Example - Get physical disk information:
Get-PhysicalDisk | Select-Object FriendlyName, Size, OperationalStatus
```

1. Setting Up Your Profile for Enhanced History
Open your profile on powershell

notepad $PROFILE

Add following line

function connect-silkroad {
    ssh user@IP
}

Run this command or it will be run at powershell startup
. $PROFILE
Call function to run the command like
connect-silkroad


2. Move to root
cd \

3. Move to home
cd ~

4. Delete folder with all content
Remove-Item -Path "C:\Path\To\Folder" -Recurse -Force
