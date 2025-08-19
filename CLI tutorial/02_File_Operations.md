# 📁 File Operations - Mastering Files and Directories

## 🎯 Learning Objectives
By the end of this lesson, you'll master:
- Creating, copying, moving, and deleting files/folders
- Understanding file permissions
- File content viewing and editing
- Finding files efficiently

## 📝 Creating Files and Directories

### `touch` - Create Empty Files
```bash
touch newfile.txt              # Create empty file
touch file1.txt file2.txt      # Create multiple files
touch "my file.txt"            # File with spaces (use quotes)
touch .hidden_file             # Hidden file (starts with .)
```

### `mkdir` - Create Directories
```bash
mkdir new_folder               # Create single directory
mkdir -p path/to/new/folder    # Create nested directories (-p = parents)
mkdir folder1 folder2          # Create multiple directories
mkdir "My Documents"           # Directory with spaces
```

## 📋 Copying and Moving

### `cp` - Copy Files and Directories
```bash
cp file1.txt file2.txt         # Copy file1 to file2
cp file1.txt /path/to/dest/    # Copy to different directory
cp *.txt backup/               # Copy all .txt files to backup folder
cp -r folder1 folder2          # Copy directory recursively (-r)
cp -v source dest              # Verbose output (-v shows what's happening)
```

### `mv` - Move/Rename Files and Directories
```bash
mv oldname.txt newname.txt     # Rename file
mv file.txt /path/to/dest/     # Move file to different directory
mv folder1 folder2             # Rename directory
mv *.log logs/                 # Move all .log files to logs directory
```

## 🗑️ Deleting Files and Directories

### `rm` - Remove Files
```bash
rm file.txt                    # Delete single file
rm file1.txt file2.txt         # Delete multiple files
rm *.tmp                       # Delete all .tmp files
rm -i file.txt                 # Interactive deletion (asks confirmation)
rm -v file.txt                 # Verbose deletion (shows what's deleted)
```

### `rmdir` and `rm -r` - Remove Directories
```bash
rmdir empty_folder             # Remove empty directory only
rm -r folder_name              # Remove directory and all contents
rm -rf folder_name             # Force remove (be careful! -f = force)
```

⚠️ **WARNING**: `rm -rf` permanently deletes everything! Use with caution.

## 👀 Viewing File Contents

### `cat` - Display Entire File
```bash
cat file.txt                   # Show entire file content
cat file1.txt file2.txt        # Show multiple files
cat -n file.txt                # Show with line numbers
```

### `less` and `more` - Page Through Large Files
```bash
less largefile.txt             # Navigate with arrow keys, q to quit
more largefile.txt             # Similar to less, space for next page
```

### `head` and `tail` - Show Beginning or End
```bash
head file.txt                  # Show first 10 lines
head -20 file.txt              # Show first 20 lines
tail file.txt                  # Show last 10 lines
tail -f logfile.txt            # Follow file (great for logs)
```

### `grep` - Search in Files
```bash
grep "search_term" file.txt    # Find lines containing search_term
grep -i "term" file.txt        # Case-insensitive search (-i)
grep -n "term" file.txt        # Show line numbers (-n)
grep -r "term" directory/      # Search recursively in directory
```

## 🔍 Finding Files

### `find` - Powerful File Search
```bash
find . -name "*.txt"           # Find all .txt files in current directory
find /home -name "config*"     # Find files starting with "config"
find . -type d -name "test*"   # Find directories starting with "test"
find . -size +1M               # Find files larger than 1MB
find . -mtime -7               # Find files modified in last 7 days
```

### `locate` - Fast File Search
```bash
locate filename.txt            # Quick search using database
updatedb                       # Update locate database (may need sudo)
```

### `which` - Find Command Location
```bash
which python                   # Find where python command is located
which -a python                # Show all python locations
```

## 🔐 File Permissions

### Understanding Permissions
```bash
ls -l file.txt                 # Shows: -rwxr-xr-- owner group other
```

Permission format: `[type][owner][group][other]`
- `r` = read (4)
- `w` = write (2)  
- `x` = execute (1)

### `chmod` - Change Permissions
```bash
chmod 755 script.sh            # rwxr-xr-x (owner: all, others: read+execute)
chmod +x script.sh             # Add execute permission for all
chmod u+w file.txt             # Add write permission for user (owner)
chmod g-r file.txt             # Remove read permission for group
chmod o=r file.txt             # Set other permissions to read-only
```

### `chown` - Change Ownership
```bash
chown user:group file.txt      # Change owner and group
chown user file.txt            # Change owner only
chown :group file.txt          # Change group only
```

## 🔗 Links and Shortcuts

### `ln` - Create Links
```bash
ln -s /path/to/file linkname   # Create symbolic link (-s)
ln file.txt hardlink.txt       # Create hard link
```

## 📊 File Information

### `stat` - Detailed File Information
```bash
stat file.txt                  # Shows size, permissions, timestamps
```

### `file` - Determine File Type
```bash
file document.pdf              # Shows file type and format
file *                         # Check all files in directory
```

### `du` and `df` - Disk Usage
```bash
du -h folder/                  # Show directory size human-readable
du -sh *                       # Show size of all items in current directory
df -h                          # Show disk space usage
```

## 🎮 Hands-On Exercises

### Exercise 1: Basic File Operations
```bash
# Create a practice workspace
mkdir cli_practice
cd cli_practice

# Create some files
touch file1.txt file2.txt
echo "Hello World" > greeting.txt
echo "Line 1" > multiline.txt
echo "Line 2" >> multiline.txt

# Try different viewing commands
cat greeting.txt
head multiline.txt
tail multiline.txt
```

### Exercise 2: Copy and Move Practice
```bash
# Create directories
mkdir backup temp

# Copy files
cp *.txt backup/
ls backup/

# Move and rename
mv file1.txt renamed_file.txt
mv temp/ archive_folder/
```

### Exercise 3: Search and Find
```bash
# Create test structure
mkdir -p project/src project/docs
touch project/src/main.py project/docs/readme.txt

# Practice finding
find . -name "*.txt"
find . -type d
grep -r "Hello" .
```

### Exercise 4: Permissions Practice
```bash
# Create a script
echo '#!/bin/bash
echo "Hello from script!"' > myscript.sh

# Make it executable
chmod +x myscript.sh
./myscript.sh

# Check permissions
ls -l myscript.sh
```

## 🏆 Real-World Examples

### Backup Important Files
```bash
# Create dated backup
cp important_file.txt "important_file_$(date +%Y%m%d).txt"

# Backup entire directory
cp -r project/ "project_backup_$(date +%Y%m%d)/"
```

### Clean Up Temporary Files
```bash
# Find and remove old temporary files
find /tmp -name "*.tmp" -mtime +7 -delete

# Remove empty directories
find . -type d -empty -delete
```

### Organize Downloads
```bash
# Move files by extension
mkdir -p ~/Downloads/{images,documents,videos}
mv ~/Downloads/*.{jpg,png,gif} ~/Downloads/images/
mv ~/Downloads/*.{pdf,doc,txt} ~/Downloads/documents/
mv ~/Downloads/*.{mp4,avi,mov} ~/Downloads/videos/
```

## 🔧 Advanced Tips

### Wildcards and Patterns
```bash
*                              # Matches any characters
?                              # Matches single character
[abc]                          # Matches a, b, or c
[a-z]                          # Matches any lowercase letter
{txt,pdf}                      # Matches txt OR pdf

# Examples:
ls *.{txt,md}                  # List .txt and .md files
rm temp_??.log                 # Remove temp_01.log, temp_02.log, etc.
```

### Bulk Operations
```bash
# Rename multiple files
for file in *.txt; do
    mv "$file" "${file%.txt}.bak"
done

# Create numbered files
for i in {1..10}; do
    touch "file_$i.txt"
done
```

## 🎯 Quick Quiz
1. How do you create a directory and its parent directories in one command?
2. What's the difference between `cp` and `mv`?
3. How do you make a file executable?
4. What command shows the last 20 lines of a file?
5. How do you search for files larger than 100MB?

### Answers:
1. `mkdir -p path/to/new/folder`
2. `cp` copies (original remains), `mv` moves/renames (original is moved)
3. `chmod +x filename`
4. `tail -20 filename`
5. `find . -size +100M`

## 🎯 Next Steps
Ready for text processing? Move to [03_Text_Processing.md](./03_Text_Processing.md)

## 💡 Pro Tips
- Always use `ls -la` to see permissions and hidden files
- Use `cp -v` and `mv -v` to see what's happening
- Test commands on copies first, especially with `rm`
- Use tab completion for file names to avoid typos
- `Ctrl+C` stops any running command

Master these file operations and you'll be ready for advanced text processing! 🚀
