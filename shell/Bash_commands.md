---
id: Bash commands
aliases: []
tags: []
---

## **Bash Essentials Cheat Sheet**

### **File Management**

```bash
# List directory contents
ls
ls -l      # Detailed list
ls -a      # Show hidden files
ls -lh     # Human-readable sizes

# Create directory
mkdir dirname
mkdir -p parent/child  # Create nested directories

# Copy files
cp file.txt destination/
cp -r dir/ destination/  # Copy directories recursively

# Move/rename files
mv old.txt new.txt

# Delete files/folders
rm file.txt
rm -r dirname  # Delete directory recursively
rm -rf dirname # Force delete (caution!)

# Find files
find . -name "*.log"  # Search by name
grep -r "pattern" /path  # Search content in files

# Create file
touch newfile.txt
```

### **Process Management**

```bash
# List running processes
ps aux
ps aux | grep "processname"

# Monitor processes
top
htop  # Interactive viewer (install separately)

# Kill process
kill 1234         # By PID
killall processname
pkill -f "pattern"
```

### **System Information**

```bash
# System info
uname -a          # Kernel info
df -h             # Disk space
free -h           # Memory usage
lscpu             # CPU information

# Hardware info
lshw              # Detailed hardware (requires install)
dmidecode         # BIOS/hardware info
```

### **Network Tools**

```bash
# Ping test
ping google.com
ping -c 4 8.8.8.8  # Limited packets

# Network configuration
ifconfig          # Deprecated, use 'ip a'
ip a              # Show IP addresses
netstat -tulpn    # Listening ports

# DNS lookup
nslookup google.com
dig google.com

# Download files
wget https://example.com/file
curl -O https://example.com/file
```

### **Package Management**

```bash
# Debian/Ubuntu (apt)
sudo apt update
sudo apt install package
sudo apt remove package

# RedHat/CentOS (yum/dnf)
sudo yum install package
sudo dnf upgrade

# Search packages
apt search pattern
yum search pattern
```

### **User & Permissions**

```bash
# Run as superuser
sudo command

# File permissions
chmod 755 file.sh     # Numeric mode
chmod +x script.sh    # Make executable
chown user:group file # Change ownership

# User management
sudo adduser username
sudo passwd username
```

### **Scripting & Automation**

```bash
# Create executable script
#!/bin/bash           # Shebang line
echo "Hello World!"

# Variables
name="John"
echo "Hello $name"

# Conditional
if [ $age -gt 18 ]; then
    echo "Adult"
fi

# Loops
for i in {1..5}; do
    echo $i
done
```

### **Useful Aliases**

```bash
# Add to ~/.bashrc
alias ll='ls -alF'
alias cls='clear'
alias ..='cd ..'
alias grep='grep --color=auto'
```

### **Powerful Pipeline Examples**

```bash
# Find large files (>100MB)
find . -type f -size +100M

# Count lines in files
wc -l file.txt

# Process text
cat file.txt | sort | uniq -c | sort -nr

# Monitor log files
tail -f /var/log/syslog | grep "error"
```

### **Environment Variables**

```bash
export PATH="$PATH:/my/custom/path"
printenv              # List all variables
echo $HOME            # Show specific variable
```

### **Profile Customization**

```bash
nano ~/.bashrc        # Edit configuration
source ~/.bashrc      # Reload settings
```
