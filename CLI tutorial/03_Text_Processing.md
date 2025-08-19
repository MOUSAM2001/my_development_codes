# 🔤 Text Processing - Mastering Text with CLI

## 🎯 Learning Objectives
By the end of this lesson, you'll master:
- Advanced text searching with grep
- Text manipulation with sed and awk
- Sorting and filtering data
- Regular expressions for pattern matching

## 🔍 Advanced Searching with grep

### Basic grep Patterns
```bash
grep "pattern" file.txt         # Basic search
grep -i "pattern" file.txt      # Case insensitive (-i)
grep -v "pattern" file.txt      # Invert match (show lines NOT matching)
grep -n "pattern" file.txt      # Show line numbers (-n)
grep -c "pattern" file.txt      # Count matching lines (-c)
```

### Advanced grep Options
```bash
grep -r "pattern" directory/    # Recursive search in directory
grep -l "pattern" *.txt         # Show only filenames with matches
grep -w "word" file.txt         # Match whole words only
grep -A 3 "pattern" file.txt    # Show 3 lines After match
grep -B 3 "pattern" file.txt    # Show 3 lines Before match
grep -C 3 "pattern" file.txt    # Show 3 lines of Context
```

### Regular Expressions with grep
```bash
grep "^start" file.txt          # Lines starting with "start"
grep "end$" file.txt            # Lines ending with "end"
grep "^$" file.txt              # Empty lines
grep "[0-9]" file.txt           # Lines containing numbers
grep "[a-zA-Z]" file.txt        # Lines containing letters
grep "colou?r" file.txt         # Match "color" or "colour" (? = optional)
grep "test.*ing" file.txt       # Match "test" followed by anything then "ing"
```

## ✂️ Text Manipulation with sed

### Basic sed Operations
```bash
sed 's/old/new/' file.txt       # Replace first occurrence per line
sed 's/old/new/g' file.txt      # Replace all occurrences (g = global)
sed 's/old/new/gi' file.txt     # Global + case insensitive
sed '1,5s/old/new/' file.txt    # Replace in lines 1-5 only
```

### Advanced sed Commands
```bash
sed '/pattern/d' file.txt       # Delete lines matching pattern
sed '/^$/d' file.txt            # Delete empty lines
sed '/^#/d' file.txt            # Delete comment lines (starting with #)
sed 'n;d' file.txt              # Delete every second line (n=next, d=delete)
sed '1d' file.txt               # Delete first line
sed '$d' file.txt               # Delete last line
```

### sed with Regular Expressions
```bash
sed 's/[0-9]/X/g' file.txt      # Replace all digits with X
sed 's/^[ \t]*//' file.txt      # Remove leading spaces and tabs
sed 's/[ \t]*$//' file.txt      # Remove trailing spaces and tabs
sed 's/\([a-z]*\)/\U\1/g' file.txt  # Convert to uppercase
```

## 🧮 Powerful Processing with awk

### Basic awk Syntax
```bash
awk '{print}' file.txt          # Print all lines (same as cat)
awk '{print $1}' file.txt       # Print first column/field
awk '{print $1, $3}' file.txt   # Print first and third columns
awk '{print NF, $0}' file.txt   # Print number of fields and the line
```

### awk Field Separators
```bash
awk -F',' '{print $2}' file.csv    # Use comma as field separator
awk -F':' '{print $1}' /etc/passwd # Use colon as separator
awk -F'\t' '{print $1}' file.tsv   # Use tab as separator
```

### awk Patterns and Conditions
```bash
awk '/pattern/ {print}' file.txt    # Print lines matching pattern
awk '$1 > 100' numbers.txt          # Print lines where first field > 100
awk 'length($0) > 80' file.txt      # Print lines longer than 80 characters
awk 'NF > 3' file.txt               # Print lines with more than 3 fields
awk 'NR > 1' file.txt               # Skip header (print from line 2)
```

### awk Built-in Variables
```bash
awk '{print NR, $0}' file.txt       # NR = line number
awk '{print NF, $0}' file.txt       # NF = number of fields
awk 'END {print NR}' file.txt       # Count total lines
awk '{sum += $1} END {print sum}' numbers.txt  # Sum first column
```

## 🔢 Sorting and Filtering

### `sort` - Sort Lines
```bash
sort file.txt                   # Sort alphabetically
sort -n numbers.txt             # Sort numerically (-n)
sort -r file.txt                # Reverse sort (-r)
sort -k2 file.txt               # Sort by second column (-k2)
sort -t',' -k2n data.csv        # Sort CSV by 2nd column numerically
sort -u file.txt                # Sort and remove duplicates (-u)
```

### `uniq` - Handle Duplicates
```bash
uniq file.txt                   # Remove consecutive duplicates
sort file.txt | uniq            # Remove all duplicates
sort file.txt | uniq -c         # Count occurrences
sort file.txt | uniq -d         # Show only duplicate lines
sort file.txt | uniq -u         # Show only unique lines
```

### `cut` - Extract Columns
```bash
cut -c1-10 file.txt             # Extract characters 1-10
cut -f1,3 file.txt              # Extract fields 1 and 3 (tab-separated)
cut -d',' -f2 file.csv          # Extract 2nd field from CSV
cut -d':' -f1 /etc/passwd       # Extract usernames from passwd file
```

## 🔄 Pipes and Redirection

### Combining Commands with Pipes
```bash
cat file.txt | grep "error" | wc -l     # Count error lines
ls -la | sort -k5 -n | tail -5          # Show 5 largest files
ps aux | grep python | awk '{print $2}'  # Get Python process IDs
```

### Input/Output Redirection
```bash
command > file.txt              # Write output to file (overwrite)
command >> file.txt             # Append output to file
command < file.txt              # Use file as input
command 2> error.log            # Redirect errors to file
command > output.txt 2>&1       # Redirect both output and errors
```

## 📊 Text Analysis Tools

### `wc` - Word Count
```bash
wc file.txt                     # Lines, words, characters
wc -l file.txt                  # Count lines only
wc -w file.txt                  # Count words only
wc -c file.txt                  # Count characters only
```

### `tr` - Translate Characters
```bash
tr 'a-z' 'A-Z' < file.txt       # Convert to uppercase
tr -d ' ' < file.txt            # Delete spaces
tr -s ' ' < file.txt            # Squeeze multiple spaces to one
echo "hello world" | tr ' ' '_' # Replace spaces with underscores
```

### `column` - Format Columns
```bash
column -t file.txt              # Align columns nicely
column -s',' -t file.csv        # Format CSV with comma separator
```

## 🎮 Hands-On Exercises

### Exercise 1: Log Analysis
```bash
# Create a sample log file
cat > sample.log << EOF
2024-01-01 10:00:01 INFO User login successful
2024-01-01 10:05:23 ERROR Database connection failed
2024-01-01 10:10:45 INFO User logout
2024-01-01 10:15:12 WARNING Low disk space
2024-01-01 10:20:33 ERROR Authentication failed
2024-01-01 10:25:44 INFO User login successful
EOF

# Practice text processing
grep "ERROR" sample.log                    # Find errors
grep -c "INFO" sample.log                  # Count info messages
awk '{print $1, $2, $3}' sample.log       # Extract timestamp and level
sed 's/ERROR/CRITICAL/' sample.log         # Replace ERROR with CRITICAL
```

### Exercise 2: CSV Processing
```bash
# Create sample CSV
cat > data.csv << EOF
Name,Age,City,Salary
John,25,NYC,50000
Jane,30,LA,60000
Bob,35,Chicago,55000
Alice,28,NYC,52000
EOF

# Practice CSV operations
cut -d',' -f1,3 data.csv                   # Extract names and cities
awk -F',' '$2 > 27 {print $1, $4}' data.csv  # Names and salaries for age > 27
sort -t',' -k4 -n data.csv                 # Sort by salary
grep "NYC" data.csv | cut -d',' -f1        # Names of NYC residents
```

### Exercise 3: System Information
```bash
# Analyze system processes
ps aux | head -1; ps aux | sort -k3 -nr | head -5  # Top 5 CPU processes
ps aux | awk '{sum += $4} END {print "Total Memory:", sum "%"}'  # Total memory usage

# Analyze disk usage
df -h | grep -v "tmpfs" | sort -k5 -nr     # Sort filesystems by usage
```

## 🛠️ Real-World Text Processing Scripts

### 1. Clean and Process Data File
```bash
#!/bin/bash
# clean_data.sh - Clean CSV data file

input_file="$1"
output_file="${input_file%.csv}_cleaned.csv"

# Remove empty lines, fix encoding, standardize separators
sed '/^$/d' "$input_file" |              # Remove empty lines
tr -d '\r' |                             # Remove carriage returns
sed 's/;/,/g' |                          # Replace semicolons with commas
sed 's/,,/,/g' > "$output_file"          # Remove double commas

echo "Cleaned data saved to: $output_file"
```

### 2. Log Analysis Script
```bash
#!/bin/bash
# analyze_logs.sh - Analyze web server logs

log_file="$1"

echo "=== Log Analysis Report ==="
echo "Total lines: $(wc -l < "$log_file")"
echo "Unique IPs: $(awk '{print $1}' "$log_file" | sort -u | wc -l)"
echo "Top 10 IPs:"
awk '{print $1}' "$log_file" | sort | uniq -c | sort -nr | head -10

echo -e "\nTop 10 requested pages:"
awk '{print $7}' "$log_file" | sort | uniq -c | sort -nr | head -10

echo -e "\nError codes summary:"
awk '{print $9}' "$log_file" | grep "^[45]" | sort | uniq -c | sort -nr
```

### 3. Text Statistics Script
```bash
#!/bin/bash
# text_stats.sh - Comprehensive text analysis

file="$1"

echo "=== Text Statistics for $file ==="
echo "Lines: $(wc -l < "$file")"
echo "Words: $(wc -w < "$file")"
echo "Characters: $(wc -c < "$file")"
echo "Average words per line: $(awk '{total += NF; count++} END {print total/count}' "$file")"
echo -e "\nMost common words:"
tr -s ' ' '\n' < "$file" | tr '[:upper:]' '[:lower:]' | sort | uniq -c | sort -nr | head -10
```

## 🎯 Advanced Patterns and Regular Expressions

### Common Regex Patterns
```bash
# Email addresses
grep -E '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}' file.txt

# IP addresses
grep -E '([0-9]{1,3}\.){3}[0-9]{1,3}' file.txt

# Phone numbers (various formats)
grep -E '(\+?1?[-.\s]?)?(\([0-9]{3}\)|[0-9]{3})[-.\s]?[0-9]{3}[-.\s]?[0-9]{4}' file.txt

# URLs
grep -E 'https?://[^\s]+' file.txt

# Date formats (MM/DD/YYYY)
grep -E '[0-9]{1,2}/[0-9]{1,2}/[0-9]{4}' file.txt
```

### Advanced sed Patterns
```bash
# Extract email domains
sed -n 's/.*@\([^.]*\.[^.]*\).*/\1/p' emails.txt

# Convert file paths
sed 's|/|\\|g' unix_paths.txt              # Convert Unix to Windows paths

# Add line numbers
sed = file.txt | sed 'N;s/\n/\t/'          # Add tab-separated line numbers

# Comment out lines matching pattern
sed '/pattern/s/^/# /' file.txt             # Add # at beginning of matching lines
```

## 🏆 Challenge Exercises

### Challenge 1: Web Log Analysis
Given a web server log, extract:
1. Top 10 most visited pages
2. Unique visitors per hour
3. Most common user agents
4. Error rate by hour

### Challenge 2: CSV Data Cleaning
Clean a messy CSV file by:
1. Removing duplicate rows
2. Standardizing date formats
3. Fixing encoding issues
4. Removing invalid entries

### Challenge 3: Configuration File Processing
Process configuration files to:
1. Extract all variable definitions
2. Find unused variables
3. Generate documentation
4. Validate syntax

## 🎯 Quick Quiz
1. How do you find lines that don't contain a specific pattern?
2. What's the difference between `sed 's/old/new/'` and `sed 's/old/new/g'`?
3. How do you count unique lines in a file?
4. What does `awk '{print NF}'` do?
5. How do you replace all digits with 'X' in a file?

### Answers:
1. `grep -v "pattern" file.txt`
2. First replaces only first occurrence per line, second replaces all occurrences
3. `sort file.txt | uniq | wc -l`
4. Prints the number of fields in each line
5. `sed 's/[0-9]/X/g' file.txt`

## 🎯 Next Steps
Ready for Python CLI? Move to [04_Python_Basics_CLI.md](./04_Python_Basics_CLI.md)

## 💡 Pro Tips
- Test regex patterns with small files first
- Use `grep --color=always` to highlight matches
- Combine multiple tools with pipes for powerful processing
- Save complex commands as scripts for reuse
- Use `tee` to save intermediate results: `command | tee intermediate.txt | next_command`

Master these text processing tools and you'll handle any data manipulation task! 🚀
