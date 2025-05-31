---
id: pwsh Commands
aliases: []
tags: []
---

see to
[[wezterm config]]
[[Neovim Commands]]

## **PowerShell Essentials Cheat Sheet**

### **File Management**

```powershell
# List directory contents (ls)
Get-ChildItem
ls -Recurse  # List recursively
ls -Hidden    # Show hidden files

# Create directory
New-Item -Name "FolderName" -ItemType Directory

# Copy files
Copy-Item "source.txt" "destination.txt" -Force

# Delete files/folders
Remove-Item "file.txt" -Force
rm -Recurse -Force ./folder  # Force delete folder

# Find files
Get-ChildItem -Recurse -Filter "*.log"
```

### **Process Management**

```powershell
# List running processes
Get-Process
ps | Where-Object { $_.CPU -gt 100 }  # CPU-heavy processes

# Kill process
Stop-Process -Name "processname" -Force
kill -Id 1234  # By PID
```

### **System Information**

```powershell
# Get system info
Get-ComputerInfo
Get-Disk
Get-NetIPAddress  # Network info
Get-Service | Where Status -eq "Running"  # Running services

# Hardware info
Get-WmiObject Win32_Processor
Get-WmiObject Win32_PhysicalMemory
```

### **Network Tools**

```powershell
# Ping test
Test-NetConnection google.com
tnc 8.8.8.8 -Port 443  # Port check

# DNS lookup
Resolve-DnsName google.com
nslookup google.com

# Show network adapters
Get-NetAdapter
```

### **Package Management**

```powershell
# Windows Package Manager (winget)
winget search python
winget install Mozilla.Firefox
winget upgrade --all

# PowerShell Gallery
Find-Module "ModuleName"
Install-Module -Name "PSWindowsUpdate"
```

### **User & Permissions**

```powershell
# User management
Get-LocalUser
New-LocalUser -Name "John"
Add-LocalGroupMember -Group "Administrators" -Member "John"

# Run as admin
Start-Process pwsh -Verb RunAs
```

### **Scripting & Automation**

```powershell
# Get command help
Get-Help Get-Process -Examples
Update-Help  # Refresh help docs

# List available commands
Get-Command *network*

# Create alias
New-Alias open Invoke-Item

# Execution policies
Set-ExecutionPolicy RemoteSigned
```

### **Useful Aliases (Unix-like)**

```powershell
cat       # Get-Content
curl     # Invoke-WebRequest
diff     # Compare-Object
man      # Get-Help
history  # Get-History
clear    # Clear-Host
```

### **Powerful Pipeline Examples**

```powershell
# Find large files (>100MB)
Get-ChildItem -Recurse | Where-Object { $_.Length -gt 100MB }

# Last 10 modified files
ls | Sort LastWriteTime -Descending | Select -First 10

# Export to CSV
Get-Process | Export-Csv processes.csv
```

### **Environment Variables**

```powershell
$env:Path += ";C:\MyTools"  # Add to PATH
Get-ChildItem Env:  # List all variables
```

### **Profile Customization**

```powershell
notepad $PROFILE  # Edit profile
. $PROFILE        # Reload profile
```

---

**Pro Tip:** Use `Get-Command` to discover commands and `Get-Help <command> -Full` for detailed documentation. For Linux-like experience, install `PSReadLine` module for better tab completion and history.
