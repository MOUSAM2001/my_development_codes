# 🏁 CLI Basics - Your First Commands

## 🎯 Learning Objectives
By the end of this lesson, you'll know:
- How to navigate directories
- Basic file operations
- Essential terminal shortcuts
- How to get help when stuck

## 📍 Where Am I? Navigation Commands

### `pwd` - Print Working Directory
```bash
pwd
# Shows your current location
# Example output: /workspaces/my_development_codes/CLI tutorial
```

### `ls` - List Contents
```bash
ls                    # List files and folders
ls -l                 # Detailed list (permissions, size, date)
ls -la                # Include hidden files (starting with .)
ls -lh                # Human-readable file sizes
ls *.md               # List only .md files
```

### `cd` - Change Directory
```bash
cd /                  # Go to root directory
cd ~                  # Go to home directory
cd ..                 # Go up one level
cd ../..              # Go up two levels
cd -                  # Go to previous directory
cd "CLI tutorial"     # Go to folder with spaces (use quotes)
```

## 📂 Understanding Paths

### Absolute vs Relative Paths
```bash
# Absolute path (starts from root)
cd /workspaces/my_development_codes/CLI tutorial

# Relative path (from current location)
cd ../CLI tutorial
cd ./exercises        # ./ means current directory
```

### Special Directory Symbols
- `.` = Current directory
- `..` = Parent directory
- `~` = Home directory
- `/` = Root directory
- `-` = Previous directory

## 🔍 Getting Help

### `man` - Manual Pages
```bash
man ls                # Read the manual for ls command
man pwd               # Read about pwd
man man               # Read about the man command itself!
```

### `--help` Flag
```bash
ls --help             # Quick help for ls
cd --help             # Help for cd
```

### `which` and `type`
```bash
which python          # Find where python is installed
type ls               # Show what type of command ls is
```

## ⌨️ Essential Shortcuts

### Navigation Shortcuts
- `Ctrl + C` - Stop/cancel current command
- `Ctrl + L` - Clear screen (same as `clear`)
- `Ctrl + A` - Go to beginning of line
- `Ctrl + E` - Go to end of line
- `Tab` - Auto-complete commands/files
- `↑` / `↓` - Navigate command history

### Command History
```bash
history               # Show command history
!123                  # Run command number 123 from history
!!                    # Run last command again
!ls                   # Run last command starting with 'ls'
```

## 🎮 Hands-On Exercises

### Exercise 1: Basic Navigation
```bash
# Try these commands in order:
pwd                   # Where are you?
ls                    # What's here?
cd ~                  # Go home
pwd                   # Confirm you're home
cd -                  # Go back
ls -la                # Detailed listing with hidden files
```

### Exercise 2: Explore Your System
```bash
# Navigate around your system:
cd /                  # Go to root
ls                    # See system directories
cd usr                # Explore usr directory
cd bin                # See system binaries
ls | head -10         # List first 10 items
cd ~                  # Go back home
```

### Exercise 3: Practice Tab Completion
```bash
# Type these partially and press Tab:
cd CLI<Tab>           # Should complete to "CLI tutorial"
ls ex<Tab>            # Should show exercises folder
```

## 🏆 Quick Quiz
Test yourself:
1. How do you go to your home directory?
2. What command shows your current location?
3. How do you list files with detailed information?
4. What does `cd ..` do?
5. How do you get help for a command?

### Answers:
1. `cd ~` or just `cd`
2. `pwd`
3. `ls -l`
4. Goes up one directory level
5. `man command` or `command --help`

## 🎯 Next Steps
Once you're comfortable with navigation:
- Move to [02_File_Operations.md](./02_File_Operations.md)
- Practice these commands daily
- Try exploring different directories

## 💡 Pro Tips
- Use `Tab` completion - it saves time and prevents typos
- `Ctrl + C` is your friend when things go wrong
- Don't be afraid to explore - you can always `cd` back
- Keep a terminal open and practice during breaks

Ready for file operations? Let's go! 🚀
