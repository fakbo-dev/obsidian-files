# Pwsh_commands

**Domain**:: #CLI #Windows #automation
**Expertise**:: `⚡️ Intermediate`
**Last Used**:: 2025-05-31
**Related**:: [[Wezterm_Config|wezterm_Config]]
**Tags**:: #cheatsheet #reference #powershell #Windows

## Core Syntax & Operations

```bash
# File Management
Get-ChildItem                   # List directory contents
New-Item -Name "Folder" -ItemType Directory  # Create directory
Copy-Item "source" "dest" -Force  # Copy files
Remove-Item "file" -Force       # Delete files/folders
Move-Item -Path 'source' -Destination 'source'

# Rename Files/folders
Rename-Item -Path "OldFolderName" -NewName "NewFolderName"
# Process Management
Get-Process                     # List running processes
Stop-Process -Name "process" -Force  # Kill process

# System Information
Get-ComputerInfo                # Comprehensive system info
Get-NetIPAddress                # Network information
```

## Productivity Shortcuts

```bash
# Unix-like aliases
Set-Alias cat Get-Content
Set-Alias curl Invoke-WebRequest
Set-Alias diff Compare-Object
Set-Alias man Get-Help
Set-Alias history Get-History
Set-Alias clear Clear-Host

# Custom shortcuts
function which($command) { Get-Command $command }
function touch($file) { New-Item $file -ItemType File }
```

## Common Patterns

### Basic Usage

```bash
# Find files recursively
Get-ChildItem -Recurse -Filter "*.log"

# Filter running services
Get-Service | Where Status -eq "Running"
```

### Composite Workflow

```bash
# Analyze large files
Get-ChildItem -Recurse |
Where-Object { $_.Length -gt 100MB } |
Sort-Object Length -Descending |
Select-Object FullName, Length |
Export-Csv large_files.csv
```

## Debugging Guide

```bash
# Get detailed error information
$Error[0] | Format-List * -Force

# Common error:
ERROR: "File cannot be loaded because running scripts is disabled"
FIX: "Set-ExecutionPolicy RemoteSigned -Scope CurrentUser"
```

## Real-World Examples

### System Maintenance

```bash
# Update all winget packages
winget upgrade --all --accept-package-agreements

# Clean temp files
Get-ChildItem $env:TEMP -Recurse |
Where LastWriteTime -lt (Get-Date).AddDays(-30) |
Remove-Item -Force -Recurse
```

### Development Workflow

```bash
# Run build script with error handling
try {
    & .\build.ps1
} catch {
    Write-Error "Build failed: $_"
    exit 1
}
```

## Advanced Techniques

```bash
# Parallel processing
1..10 | ForEach-Object -Parallel {
    "Processing $_"
    Start-Sleep 1
} -ThrottleLimit 5

# Custom objects
$user = [PSCustomObject]@{
    Name = "John"
    ID = 123
    Roles = @("Admin", "Developer")
}
```

## Configuration Snippets

### Minimal Profile

```bash
# Microsoft.bash_profile.ps1
Set-PSReadLineOption -EditMode Emacs
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -Colors @{ Command = 'Green' }
```

### Optimized Setup

```bash
# Enhanced prompt with git status
function prompt {
    $path = $($executionContext.SessionState.Path.CurrentLocation)
    $branch = (git branch --show-current 2>$null)
    $prompt = "$path"
    if ($branch) { $prompt += " [$branch]" }
    "$prompt> "
}
```

## Cross-Tool Integration

```bash
# With Neovim
function nvim {
    param([Parameter(ValueFromRemainingArguments)]$files)
    nvim-qt $files
}

# With SSH
function ssh ($hostname) {
    wezterm ssh $hostname
}
```

## Version-Specific Notes

| Version | Changes                     | Compatibility  |
| ------- | --------------------------- | -------------- |
| 5.1+    | Parallel processing support | Windows 10+    |
| 7.0+    | Ternary operators           | Cross-platform |

## Pro Tips

```bash
# Fuzzy find history with PSReadLine
Set-PSReadLineKeyHandler -Chord Ctrl+r -Function ReverseSearchHistory

# Rapid function testing
function Test-MyFunction { ... }
. Test-MyFunction  # Edit and reload with F5 in VSCode

# Object inspection
Get-Process | Get-Member     # Show properties/methods
Get-Process | Select -First 1 | Format-List *  # Show all properties
```

> **Remember**: Use `Get-Command` to discover commands and `Get-Help <command> -Full` for detailed documentation

## Reference Links

1. [bash Documentation](https://docs.microsoft.com/en-us/bash/)
2. [bash Gallery](https://www.bashgallery.com/)
3. [Awesome bash](https://github.com/janikvonrotz/awesome-bash)

---

### Package Management

```bash
# Windows Package Manager
winget search python
winget install Mozilla.Firefox
winget upgrade --all

# bash Modules
Install-Module -Name PSWindowsUpdate
Find-Module *AWS* | Install-Module
```

### Network Diagnostics

```bash
# Port testing
Test-NetConnection google.com -Port 443

# DNS troubleshooting
Resolve-DnsName google.com -Type A
Resolve-DnsName google.com -Type MX

# Network adapter details
Get-NetAdapter | Where Status -eq 'Up'
```

### User Management

```bash
# Create admin user
New-LocalUser -Name "AdminUser" -Password (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force)
Add-LocalGroupMember -Group "Administrators" -Member "AdminUser"

# Run as admin
Start-Process pwsh -Verb RunAs -ArgumentList "-NoExit", "-Command", "cd '$pwd'"
```

### Scripting Essentials

```bash
# Error handling
try {
    Get-Content "missing.txt" -ErrorAction Stop
} catch {
    Write-Warning "File not found: $_"
}

# Parameter validation
function Get-User {
    param(
        [Parameter(Mandatory)]
        [string]$Username
    )
    # Function logic
}

# Comment-based help
<#
.SYNOPSIS
Brief description
.DESCRIPTION
Detailed description
.PARAMETER Name
Parameter description
.EXAMPLE
Example command
#>
```

### Data Processing

```bash
# CSV manipulation
Import-Csv data.csv | Where { $_.Age -gt 30 } | Export-Csv filtered.csv

# JSON handling
$json = Get-Content config.json | ConvertFrom-Json
$json.Settings | ConvertTo-Json | Set-Content updated.json

# String manipulation
"HELLO".ToLower() -replace "l", "x"  # -> "hexxo"
```
