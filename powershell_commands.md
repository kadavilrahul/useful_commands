# PowerShell Commands Reference

## Basic Navigation

### Directory Operations
List Directory Contents (Shows files and folders in current directory):

Full command:
```powershell
Get-ChildItem
```

Aliases:
```powershell
ls
```
```powershell
dir
```

List .txt files:
```powershell
Get-ChildItem *.txt
```

List all items including hidden:
```powershell
Get-ChildItem -Force
```

Change Directory (Navigate to different folder):

Full command:
```powershell
Set-Location path
```

Alias:
```powershell
cd path
```

Example - Change to Documents:
```powershell
cd C:\Users\Username\Documents
```

Go up one level:
```powershell
cd ..
```

Get Current Directory:

Full command:
```powershell
Get-Location
```

Alias:
```powershell
pwd
```

Create Directory:

Full command:
```powershell
New-Item -ItemType Directory -Path "DirectoryName"
```

Alias:
```powershell
mkdir DirectoryName
```

Create nested directories:
```powershell
mkdir "C:\Projects\NewProject\src"
```

Remove Directory:

Full command:
```powershell
Remove-Item -Path "DirectoryName" -Recurse
```

Alias:
```powershell
rmdir DirectoryName
```

Remove with confirmation:
```powershell
Remove-Item "OldProject" -Recurse -Confirm
```

## File Operations

### Basic File Commands
Create New File:
```powershell
New-Item -ItemType File -Path "filename.txt"
```

Create file with content:
```powershell
New-Item -ItemType File -Path "log.txt" -Value "Initial log entry"
```

Copy File:

Full command:
```powershell
Copy-Item "source" "destination"
```

Alias:
```powershell
cp source destination
```

Copy with overwrite:
```powershell
Copy-Item "report.docx" "backup/report.docx" -Force
```

Copy multiple files:
```powershell
Copy-Item "C:\logs\*.log" "D:\backup"
```

Move/Rename File:

Full command:
```powershell
Move-Item "source" "destination"
```

Alias:
```powershell
mv source destination
```

Rename file:
```powershell
Move-Item "old.txt" "new.txt"
```

Move to different directory:
```powershell
Move-Item "document.pdf" "C:\Archive\"
```

Delete File:

Full command:
```powershell
Remove-Item "filename"
```

Aliases:
```powershell
del filename
```
```powershell
rm filename
```

Delete with confirmation:
```powershell
Remove-Item "temp.txt" -Confirm
```

Delete multiple files:
```powershell
Remove-Item *.tmp
```

Get File Content:

Full command:
```powershell
Get-Content "filename"
```

Aliases:
```powershell
cat filename
```
```powershell
type filename
```

Read first 5 lines:
```powershell
Get-Content "log.txt" -Head 5
```

Read and wait for changes:
```powershell
Get-Content "log.txt" -Wait
```

Write to File:

Overwrite existing content:
```powershell
Set-Content -Path "file.txt" -Value "text"
```

Append to existing content:
```powershell
Add-Content -Path "file.txt" -Value "text"
```

Log with timestamp:
```powershell
Add-Content "log.txt" "$(Get-Date) - Process started"
```

### File Search
Find Files:
```powershell
Get-ChildItem -Path "C:\" -Filter "*.txt" -Recurse
```

Find recent PowerShell scripts:
```powershell
Get-ChildItem -Path C:\ -Filter *.ps1 -Recurse | Where-Object { $_.LastWriteTime -gt (Get-Date).AddDays(-1) }
```

Search File Content:
```powershell
Select-String -Path "*.txt" -Pattern "searchterm"
```

Search for errors in logs:
```powershell
Select-String -Path "C:\Logs\*.log" -Pattern "error" -Context 2,2
```

## System Information

### System Details
Get OS Information:
```powershell
Get-ComputerInfo
```

Get specific OS info:
```powershell
Get-ComputerInfo | Select-Object WindowsVersion, OsName, OsVersion
```

Get IP Configuration:

Full command:
```powershell
Get-NetIPConfiguration
```

Alias:
```powershell
ipconfig
```

Get detailed IP info:
```powershell
Get-NetIPConfiguration | Select-Object InterfaceDescription, IPv4Address
```

### Process Management
List Processes:

Full command:
```powershell
Get-Process
```

Alias:
```powershell
ps
```

Find specific process:
```powershell
Get-Process -Name "chrome"
```

Sort by memory usage:
```powershell
Get-Process | Sort-Object -Property WS -Descending | Select-Object -First 10
```

Stop Process:
```powershell
Stop-Process -Name "processname"
```
```powershell
Stop-Process -Id processId
```

Stop all Chrome instances:
```powershell
Stop-Process -Name "chrome" -Force
```

## User Management

### User Information
Get Current User:
```powershell
$env:USERNAME
```
```powershell
whoami
```

Get full user details:
```powershell
whoami /all
```

Create New User:
```powershell
New-LocalUser -Name "username" -Password (ConvertTo-SecureString "password" -AsPlainText -Force)
```

Create user with details:
```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
New-LocalUser "JohnDoe" -Password $password -FullName "John Doe" -Description "Staff"
Add-LocalGroupMember -Group "Users" -Member "JohnDoe"
```

## Network Operations

### Network Commands
Test Connection:

Full command:
```powershell
Test-Connection "hostname/IP"
```

Alias:
```powershell
ping hostname/IP
```

Test with count:
```powershell
Test-Connection "google.com" -Count 2
```

Download File:

Full command:
```powershell
Invoke-WebRequest -Uri "URL" -OutFile "filename"
```

Alias:
```powershell
wget URL -OutFile filename
```

Download with progress:
```powershell
Invoke-WebRequest "https://example.com/file.zip" -OutFile "download.zip" -Progress
```

## Script Execution

### Execution Policy
Get/Set Execution Policy:
```powershell
Get-ExecutionPolicy
```
```powershell
Set-ExecutionPolicy RemoteSigned
```

Set for current user:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

## Error Handling
Try-Catch Block:
```powershell
try {
    Remove-Item "nonexistent.txt"
} catch {
    Write-Error "Failed to remove file: $_"
}
```

Multiple error types:
```powershell
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
Clear Screen:
```powershell
cls
```

Copy:
```powershell
copy
```

Delete:
```powershell
del
```

List Directory:
```powershell
dir
```

Output:
```powershell
echo
```

Move:
```powershell
move
```

Remove Directory:
```powershell
rd
```

Rename:
```powershell
ren
```

Type File:
```powershell
type
```

## Remote Management

### Remote Sessions
Create Remote Session:
```powershell
Enter-PSSession -ComputerName "hostname"
```

Connect with credentials:
```powershell
Enter-PSSession -ComputerName "RemotePC" -Credential (Get-Credential)
```

Copy Files to Remote:
```powershell
Copy-Item "source" -Destination "\\hostname\path" -Recurse
```

Copy files example:
```powershell
Copy-Item "C:\Files\*" -Destination "\\RemotePC\C$\Files\" -Recurse
```

Execute Remote Command:
```powershell
Invoke-Command -ComputerName "hostname" -ScriptBlock { command }
```

Run process list remotely:
```powershell
Invoke-Command -ComputerName "RemotePC" -ScriptBlock { Get-Process }
```

## Package Management

### Package Commands
List Available Packages:
```powershell
Get-Package
```

List all installed:
```powershell
Get-Package -ListAvailable
```

Find Package:
```powershell
Find-Package "packagename"
```

Search specific package:
```powershell
Find-Package -Name "Microsoft.PowerShell"
```

Install Package:
```powershell
Install-Package "packagename"
```

Install specific package:
```powershell
Install-Package -Name "Microsoft.PowerShell"
```

Uninstall Package:
```powershell
Uninstall-Package "packagename"
```

Uninstall specific:
```powershell
Uninstall-Package -Name "Microsoft.PowerShell"
```

## Environment Variables

### Variable Operations
List All Environment Variables:
```powershell
Get-ChildItem Env:
```

List sorted:
```powershell
Get-ChildItem Env: | Sort-Object Name
```

Get Specific Variable:
```powershell
$env:VARIABLE_NAME
```

Get PATH:
```powershell
$env:PATH
```

Set Environment Variable:
```powershell
$env:VARIABLE_NAME = "value"
```

Set new variable:
```powershell
$env:NEW_VAR = "New Value"
```

## Disk Management

### Disk Information
Get Disk Space:
```powershell
Get-PSDrive
```

Get disk space for C: drive:
```powershell
Get-PSDrive -PSProvider FileSystem -Root "C:\"
```

Get Volume Information:
```powershell
Get-Volume
```

Get volume information for C: drive:
```powershell
Get-Volume -DriveLetter C
```

Get Physical Disk Info:
```powershell
Get-PhysicalDisk
```

Get physical disk information:
```powershell
Get-PhysicalDisk | Select-Object FriendlyName, Size, OperationalStatus
```

Move to root
```powershell
cd \
```

Move to home
```powershell
cd ~
```

Delete folder with all content
```powershell
Remove-Item -Path "C:\Path\To\Folder" -Recurse -Force
```

---------------------------------------------------------------
Setting Up Your Profile for Enhanced History:
 - Open your profile on powershell
```powershell
notepad $PROFILE
```

 - Add following line. Modify as required.

function server_name {
    ssh user@IP
}

 - Call function to run the command like
function-name

 - Run this command to run the script and loads any functions, aliases, or variables defined in the profile into the current PowerShell session
 ```powershell
. $PROFILE
```
---------------------------------------------------------------
