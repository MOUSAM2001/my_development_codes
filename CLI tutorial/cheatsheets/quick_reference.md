# 🚀 CLI Quick Reference Cheat Sheet

## 📁 Navigation & File Operations
```bash
# Navigation
pwd                     # Print working directory
ls -la                  # List all files with details
cd /path/to/dir         # Change directory
cd ~                    # Go home
cd -                    # Go to previous directory

# File Operations
touch file.txt          # Create empty file
mkdir -p path/to/dir    # Create directory tree
cp -r source dest       # Copy recursively
mv old new              # Move/rename
rm -rf directory        # Remove directory (CAREFUL!)
ln -s target link       # Create symbolic link

# File Viewing
cat file.txt            # Show entire file
less file.txt           # Page through file
head -n 20 file.txt     # First 20 lines
tail -f log.txt         # Follow file (great for logs)
```

## 🔍 Search & Text Processing
```bash
# Finding Files
find . -name "*.py"     # Find Python files
find . -type f -size +1M # Files larger than 1MB
locate filename         # Fast search (uses database)
which command           # Find command location

# Text Search
grep -r "pattern" .     # Search recursively
grep -i "text" file     # Case insensitive
grep -v "exclude" file  # Invert match
grep -n "text" file     # Show line numbers

# Text Processing
sed 's/old/new/g' file  # Replace all occurrences
awk '{print $1}' file   # Print first column
sort file.txt           # Sort lines
uniq -c file.txt        # Count unique lines
cut -d',' -f2 file.csv  # Extract 2nd column from CSV
```

## 🐍 Python CLI Quick Commands
```bash
# Python Execution
python script.py        # Run script
python -c "print(2**10)" # One-liner
python -m module        # Run module as script
python -i script.py     # Interactive after script

# Package Management
pip install package     # Install package
pip list                # List installed packages
pip freeze > req.txt    # Save requirements
pip install -r req.txt  # Install from requirements

# Useful Modules
python -m json.tool file.json    # Pretty print JSON
python -m http.server 8000       # Start web server
python -m calendar 2024          # Show calendar
```

## 🔄 Pipes & Redirection
```bash
# Pipes
command1 | command2     # Pipe output to next command
ps aux | grep python    # Find Python processes
ls -la | sort -k5 -n    # Sort files by size

# Redirection
command > file.txt      # Write to file (overwrite)
command >> file.txt     # Append to file
command < input.txt     # Read from file
command 2> errors.log   # Redirect errors
command &> all.log      # Redirect everything
```

## 📊 System Information
```bash
# Process Management
ps aux                  # List all processes
top                     # Real-time process viewer
htop                    # Better top (if installed)
kill PID               # Kill process by ID
killall process_name   # Kill by name

# System Info
df -h                  # Disk usage human-readable
du -sh *               # Directory sizes
free -h                # Memory usage
uptime                 # System uptime
whoami                 # Current user
uname -a               # System information
```

## 🔐 Permissions & Ownership
```bash
# Permissions
chmod 755 file.sh      # rwxr-xr-x
chmod +x script.sh     # Add execute permission
chmod u+w file.txt     # Add write for user
chmod g-r file.txt     # Remove read for group

# Ownership
chown user:group file  # Change owner and group
chown user file        # Change owner only
sudo chown root file   # Change to root (needs sudo)
```

## 🌐 Network & Connectivity
```bash
# Network Info
ping google.com        # Test connectivity
wget URL               # Download file
curl -O URL            # Download with curl
ssh user@server        # Connect to remote server
scp file user@server:  # Copy file to server

# Port & Services
netstat -tulpn         # Show listening ports
ss -tulpn              # Modern netstat
lsof -i :8080          # What's using port 8080
```

## 🗄️ Archives & Compression
```bash
# Tar Archives
tar -czf archive.tar.gz directory/  # Create compressed archive
tar -xzf archive.tar.gz             # Extract compressed archive
tar -tzf archive.tar.gz             # List archive contents

# Zip Files
zip -r archive.zip directory/       # Create zip archive
unzip archive.zip                   # Extract zip
unzip -l archive.zip                # List zip contents
```

## ⚡ Keyboard Shortcuts
```bash
# Command Line Editing
Ctrl+A                 # Go to beginning of line
Ctrl+E                 # Go to end of line
Ctrl+U                 # Delete from cursor to beginning
Ctrl+K                 # Delete from cursor to end
Ctrl+W                 # Delete word before cursor
Ctrl+L                 # Clear screen
Ctrl+C                 # Cancel current command
Ctrl+Z                 # Suspend current command
Ctrl+R                 # Search command history

# Navigation
Tab                    # Auto-complete
↑/↓                   # Command history
Ctrl+R                 # Reverse search history
!!                     # Repeat last command
!string                # Repeat last command starting with string
```

## 🎯 Common Patterns
```bash
# Count files by extension
find . -name "*.py" | wc -l

# Find largest files
find . -type f -exec ls -la {} \; | sort -k5 -nr | head -10

# Backup with timestamp
cp important.txt "important_$(date +%Y%m%d_%H%M%S).txt"

# Remove files older than 30 days
find /tmp -type f -mtime +30 -delete

# Check disk usage by directory
du -h --max-depth=1 | sort -hr

# Monitor log files in real-time
tail -f /var/log/syslog | grep ERROR

# Count unique IPs in access log
awk '{print $1}' access.log | sort | uniq -c | sort -nr

# Convert spaces to underscores in filenames
for file in *; do mv "$file" "${file// /_}"; done
```

## 🔧 Environment Variables
```bash
# View and Set
echo $PATH             # Show PATH variable
export VAR=value       # Set variable
env                    # Show all variables
which $SHELL           # Show current shell

# Common Variables
$HOME                  # Home directory
$USER                  # Current username
$PWD                   # Current directory
$PATH                  # Executable search path
```

## 🎮 Pro Tips
- Use `man command` for detailed help
- `command --help` for quick help
- Tab completion saves time and prevents typos
- `history` shows command history
- Use `screen` or `tmux` for persistent sessions
- `alias ll='ls -la'` for custom shortcuts
- `Ctrl+C` stops most anything
- `which command` shows command location
- `type command` shows command type

## 🚨 Safety Tips
- Always double-check `rm -rf` commands
- Use `cp -i` and `mv -i` for interactive mode
- Test commands on copies first
- Use `ls` before `rm` to see what you're deleting
- Keep backups of important files
- Use quotes around filenames with spaces
- Be careful with sudo/root permissions

Remember: Practice makes perfect! 🚀
