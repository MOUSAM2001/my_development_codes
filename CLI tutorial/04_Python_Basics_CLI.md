# 🐍 Python CLI Basics - Python from the Command Line

## 🎯 Learning Objectives
By the end of this lesson, you'll master:
- Running Python from the command line
- Python one-liners for quick tasks
- Managing Python packages with pip
- Understanding Python paths and modules

## 🚀 Running Python from Command Line

### Interactive Python Shell
```bash
python                          # Start Python interactive shell
python3                         # Use Python 3 specifically (on systems with both)
exit()                          # Exit Python shell (or Ctrl+D)

# Quick calculations
python -c "print(2**10)"        # Calculate 2^10
python -c "import math; print(math.pi)"  # Print pi value
```

### Running Python Files
```bash
python script.py                # Run Python script
python script.py arg1 arg2      # Run with command line arguments
python -u script.py             # Unbuffered output (see output immediately)
python -O script.py             # Optimized mode (remove assert statements)
```

### Python One-Liners
```bash
# Mathematical calculations
python -c "print(sum(range(1, 101)))"  # Sum of 1 to 100

# Date and time
python -c "import datetime; print(datetime.datetime.now())"

# JSON formatting
echo '{"name":"John","age":30}' | python -m json.tool

# URL encoding/decoding
python -c "import urllib.parse; print(urllib.parse.quote('hello world'))"

# Generate random password
python -c "import string, random; print(''.join(random.choices(string.ascii_letters + string.digits, k=12)))"
```

## 📦 Package Management with pip

### Installing Packages
```bash
pip install package_name        # Install latest version
pip install package_name==1.2.3 # Install specific version
pip install package_name>=1.0   # Install minimum version
pip install -r requirements.txt # Install from requirements file
pip install --upgrade package_name # Upgrade to latest version
```

### Managing Packages
```bash
pip list                        # List installed packages
pip list --outdated             # Show outdated packages
pip show package_name           # Show package information
pip uninstall package_name      # Uninstall package
pip freeze                      # List packages with versions
pip freeze > requirements.txt   # Save current environment
```

### Package Information
```bash
pip search search_term          # Search for packages (if available)
pip show -f package_name        # Show files installed by package
pip check                       # Check for dependency conflicts
```

## 🛠️ Python Module Execution

### Running Modules as Scripts
```bash
python -m module_name           # Run module as script
python -m pip install requests # Use pip as module
python -m json.tool file.json   # Pretty print JSON file
python -m http.server           # Start simple HTTP server
python -m http.server 8080      # Start server on port 8080
```

### Useful Built-in Modules
```bash
python -m calendar 2024         # Show calendar for 2024
python -m calendar 2024 12      # Show December 2024
python -m pdb script.py         # Run script with debugger
python -m profile script.py     # Profile script performance
python -m timeit "code_to_time"  # Time code execution
```

## 📂 Python Paths and Environment

### Finding Python Information
```bash
which python                    # Find Python executable location
python --version                # Show Python version
python -c "import sys; print(sys.path)"  # Show Python path
python -c "import sys; print(sys.executable)"  # Show Python executable
```

### Environment Variables
```bash
export PYTHONPATH=/path/to/modules:$PYTHONPATH  # Add to Python path
python -c "import os; print(os.environ.get('PYTHONPATH'))"  # Check PYTHONPATH
export PYTHONDONTWRITEBYTECODE=1  # Don't create .pyc files
export PYTHONUNBUFFERED=1        # Unbuffered output
```

## 🔧 Command Line Arguments

### sys.argv - Basic Arguments
```python
# script.py
import sys
print(f"Script name: {sys.argv[0]}")
print(f"Arguments: {sys.argv[1:]}")
```

```bash
python script.py hello world    # Output: Arguments: ['hello', 'world']
```

### argparse - Professional Argument Parsing
```python
# advanced_script.py
import argparse

parser = argparse.ArgumentParser(description='Process some data')
parser.add_argument('filename', help='Input filename')
parser.add_argument('-o', '--output', help='Output filename')
parser.add_argument('-v', '--verbose', action='store_true', help='Verbose output')
parser.add_argument('--count', type=int, default=1, help='Number of iterations')

args = parser.parse_args()
print(f"Processing {args.filename}")
if args.verbose:
    print("Verbose mode enabled")
```

```bash
python advanced_script.py input.txt -o output.txt --verbose --count 5
python advanced_script.py --help    # Show help message
```

## 🎮 Hands-On Exercises

### Exercise 1: Python Calculator
```bash
# Create a simple calculator using Python one-liners

# Basic operations
python -c "print(f'5 + 3 = {5 + 3}')"
python -c "print(f'10 / 3 = {10 / 3:.2f}')"
python -c "print(f'2^8 = {2**8}')"

# More complex calculations
python -c "import math; print(f'sin(π/2) = {math.sin(math.pi/2)}')"
python -c "import statistics; data=[1,2,3,4,5]; print(f'Mean: {statistics.mean(data)}')"
```

### Exercise 2: File Processing
```bash
# Create a test file
echo -e "apple\nbanana\ncherry\napple\ndate" > fruits.txt

# Count lines
python -c "with open('fruits.txt') as f: print(f'Lines: {len(f.readlines())}')"

# Count unique items
python -c "with open('fruits.txt') as f: print(f'Unique: {len(set(f.read().strip().split()))}')"

# Find duplicates
python -c "
import collections
with open('fruits.txt') as f:
    items = f.read().strip().split('\n')
    counts = collections.Counter(items)
    duplicates = [item for item, count in counts.items() if count > 1]
    print(f'Duplicates: {duplicates}')
"
```

### Exercise 3: Quick Data Analysis
```bash
# Create sample data
python -c "
import csv
import random
data = [['Name', 'Age', 'Score']]
names = ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve']
for name in names:
    data.append([name, random.randint(20, 50), random.randint(60, 100)])

with open('sample_data.csv', 'w', newline='') as f:
    writer = csv.writer(f)
    writer.writerows(data)
print('Sample data created!')
"

# Analyze the data
python -c "
import csv
with open('sample_data.csv') as f:
    reader = csv.DictReader(f)
    data = list(reader)
    
    ages = [int(row['Age']) for row in data]
    scores = [int(row['Score']) for row in data]
    
    print(f'Average age: {sum(ages)/len(ages):.1f}')
    print(f'Average score: {sum(scores)/len(scores):.1f}')
    print(f'Highest score: {max(scores)}')
"
```

## 🌐 Network and Web Tasks

### HTTP Requests
```bash
# Simple HTTP requests (requires requests package)
pip install requests

python -c "
import requests
response = requests.get('https://api.github.com/users/octocat')
print(f'Status: {response.status_code}')
print(f'Name: {response.json()[\"name\"]}')
"

# Download file
python -c "
import requests
url = 'https://httpbin.org/json'
response = requests.get(url)
with open('downloaded.json', 'w') as f:
    f.write(response.text)
print('File downloaded!')
"
```

### Simple HTTP Server
```bash
# Start a simple web server
python -m http.server 8000      # Serves current directory on port 8000
# Open browser to http://localhost:8000

# Custom server with specific directory
cd /path/to/serve
python -m http.server 8080
```

## 📊 Data Processing One-Liners

### CSV Processing
```bash
# Read CSV and print specific column
python -c "
import csv
with open('data.csv') as f:
    reader = csv.reader(f)
    for row in reader:
        print(row[0])  # First column
"

# Convert CSV to JSON
python -c "
import csv, json
with open('data.csv') as f:
    reader = csv.DictReader(f)
    data = list(reader)
    print(json.dumps(data, indent=2))
"
```

### JSON Processing
```bash
# Pretty print JSON
cat data.json | python -m json.tool

# Extract specific field from JSON
python -c "
import json
with open('data.json') as f:
    data = json.load(f)
    print(data['field_name'])
"

# Convert JSON to CSV
python -c "
import json, csv
with open('data.json') as f:
    data = json.load(f)

with open('output.csv', 'w', newline='') as f:
    if data:
        writer = csv.DictWriter(f, fieldnames=data[0].keys())
        writer.writeheader()
        writer.writerows(data)
"
```

## 🧪 Testing and Debugging

### Quick Testing
```bash
# Run doctests
python -m doctest module.py -v

# Run unit tests
python -m unittest test_module.py
python -m unittest discover -s tests/

# Python debugger
python -m pdb script.py         # Start with debugger
python -c "import pdb; pdb.set_trace(); print('Debug here')"
```

### Performance Testing
```bash
# Time execution
python -m timeit "sum(range(100))"
python -m timeit -n 1000 "sorted([3,1,4,1,5,9,2,6])"

# Profile script
python -m cProfile script.py
python -m cProfile -s cumulative script.py  # Sort by cumulative time
```

## 🛠️ Real-World Python CLI Scripts

### 1. System Information Script
```python
#!/usr/bin/env python3
# sysinfo.py
import platform
import psutil
import datetime

def main():
    print("=== System Information ===")
    print(f"OS: {platform.system()} {platform.release()}")
    print(f"Python: {platform.python_version()}")
    print(f"CPU Usage: {psutil.cpu_percent()}%")
    print(f"Memory Usage: {psutil.virtual_memory().percent}%")
    print(f"Disk Usage: {psutil.disk_usage('/').percent}%")
    print(f"Current Time: {datetime.datetime.now()}")

if __name__ == "__main__":
    main()
```

### 2. File Organizer Script
```python
#!/usr/bin/env python3
# organize_files.py
import os
import shutil
import argparse
from pathlib import Path

def organize_files(directory):
    """Organize files by extension into subdirectories."""
    path = Path(directory)
    
    for file_path in path.iterdir():
        if file_path.is_file():
            extension = file_path.suffix.lower()
            if extension:
                # Create directory for extension
                ext_dir = path / extension[1:]  # Remove the dot
                ext_dir.mkdir(exist_ok=True)
                
                # Move file
                new_path = ext_dir / file_path.name
                shutil.move(str(file_path), str(new_path))
                print(f"Moved {file_path.name} to {ext_dir.name}/")

def main():
    parser = argparse.ArgumentParser(description="Organize files by extension")
    parser.add_argument("directory", help="Directory to organize")
    args = parser.parse_args()
    
    organize_files(args.directory)

if __name__ == "__main__":
    main()
```

### 3. Log Monitor Script
```python
#!/usr/bin/env python3
# logmonitor.py
import time
import argparse
from pathlib import Path

def monitor_log(filename, keyword=None):
    """Monitor a log file for new lines, optionally filtering by keyword."""
    path = Path(filename)
    
    # Start at end of file
    with open(path, 'r') as f:
        f.seek(0, 2)  # Go to end
        
        while True:
            line = f.readline()
            if not line:
                time.sleep(0.1)
                continue
                
            line = line.strip()
            if keyword is None or keyword.lower() in line.lower():
                print(f"{time.strftime('%H:%M:%S')} - {line}")

def main():
    parser = argparse.ArgumentParser(description="Monitor log file")
    parser.add_argument("logfile", help="Log file to monitor")
    parser.add_argument("-k", "--keyword", help="Filter by keyword")
    args = parser.parse_args()
    
    try:
        monitor_log(args.logfile, args.keyword)
    except KeyboardInterrupt:
        print("\nMonitoring stopped.")

if __name__ == "__main__":
    main()
```

## 🎯 Advanced Python CLI Techniques

### Environment Management
```bash
# Check Python environment
python -c "
import sys
import site
print(f'Python executable: {sys.executable}')
print(f'Python version: {sys.version}')
print(f'Site packages: {site.getsitepackages()}')
print(f'User site: {site.getusersitepackages()}')
"

# List all installed packages with sizes
python -c "
import pkg_resources
import os
for dist in pkg_resources.working_set:
    try:
        path = dist.location
        size = sum(os.path.getsize(os.path.join(dirpath, filename))
                  for dirpath, dirnames, filenames in os.walk(path)
                  for filename in filenames) / (1024*1024)
        print(f'{dist.project_name}: {size:.1f} MB')
    except:
        print(f'{dist.project_name}: Unknown size')
"
```

### Interactive Python Tools
```bash
# Interactive Python with better REPL
pip install ipython
ipython                         # Enhanced interactive shell

# Jupyter console
pip install jupyter
jupyter console                 # Jupyter-powered console

# Python REPL with readline support
python -c "import readline, rlcompleter; readline.parse_and_bind('tab: complete')"
```

## 🏆 Challenge Exercises

### Challenge 1: System Monitor
Create a Python one-liner that shows:
- Current CPU usage
- Available memory
- Network connections
- Running processes

### Challenge 2: Data Converter
Build a command-line tool that converts between:
- CSV ↔ JSON
- XML ↔ JSON
- YAML ↔ JSON

### Challenge 3: File Utilities
Create Python one-liners for:
- Finding duplicate files
- Calculating directory sizes
- Renaming files in bulk
- Finding large files

## 🎯 Quick Quiz
1. How do you run a Python module as a script?
2. What's the difference between `pip install` and `pip install --user`?
3. How do you see Python's import path?
4. What does `python -u` do?
5. How do you create a requirements.txt file?

### Answers:
1. `python -m module_name`
2. `--user` installs in user directory, not system-wide
3. `python -c "import sys; print(sys.path)"`
4. Makes output unbuffered (shows immediately)
5. `pip freeze > requirements.txt`

## 🎯 Next Steps
Ready for Python scripts? Move to [05_Python_Scripts.md](./05_Python_Scripts.md)

## 💡 Pro Tips
- Use `python -i script.py` to run script then stay in interactive mode
- `python -m pip` is more reliable than just `pip`
- Use `python -c` for quick calculations and file processing
- `python -m http.server` is great for quick file sharing
- Always check Python version with `python --version`

Master these Python CLI basics and you'll be ready to create powerful scripts! 🚀
