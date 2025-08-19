# 🐍 Python CLI Cheat Sheet

## 🚀 Python Execution
```bash
# Basic Execution
python script.py               # Run Python script
python3 script.py              # Use Python 3 specifically
python -u script.py            # Unbuffered output
python -O script.py            # Optimized mode
python -i script.py            # Interactive after execution

# One-liners
python -c "print('Hello')"     # Execute single command
python -c "import math; print(math.pi)"  # Import and execute
```

## 📦 Package Management
```bash
# pip Basics
pip install package            # Install package
pip install package==1.2.3     # Install specific version
pip install --upgrade package  # Upgrade package
pip uninstall package         # Remove package
pip list                      # List installed packages
pip list --outdated           # Show outdated packages
pip show package              # Package information
pip freeze                    # List with versions
pip freeze > requirements.txt # Save requirements
pip install -r requirements.txt # Install from file

# Advanced pip
pip install --user package    # Install for user only
pip install -e .              # Install in development mode
pip install git+https://...   # Install from git repo
```

## 🛠️ Module Execution
```bash
# Run modules as scripts
python -m pip install package # Use pip as module
python -m json.tool file.json  # Pretty print JSON
python -m http.server 8000     # Start web server
python -m calendar 2024        # Show calendar
python -m timeit "code"        # Time code execution
python -m pdb script.py        # Run with debugger
python -m profile script.py    # Profile script
```

## 🔍 Environment Info
```bash
# Python Information
python --version              # Python version
which python                 # Python location
python -c "import sys; print(sys.executable)"  # Python path
python -c "import sys; print(sys.path)"        # Module search paths

# Environment Variables
export PYTHONPATH=/path:$PYTHONPATH   # Add to Python path
export PYTHONDONTWRITEBYTECODE=1      # No .pyc files
export PYTHONUNBUFFERED=1            # Unbuffered output
```

## 📊 Quick Data Processing
```bash
# File Operations
python -c "with open('file.txt') as f: print(len(f.readlines()))"  # Count lines
python -c "import os; print(os.path.getsize('file.txt'))"         # File size

# JSON Processing
cat data.json | python -m json.tool                    # Pretty print
python -c "import json; print(json.load(open('data.json'))['key'])"  # Extract value

# CSV Processing
python -c "
import csv
with open('data.csv') as f:
    reader = csv.reader(f)
    for row in reader: print(row[0])
"

# Statistics
python -c "
import statistics
data = [1,2,3,4,5]
print(f'Mean: {statistics.mean(data)}')
print(f'Median: {statistics.median(data)}')
"
```

## 🌐 Network & Web
```bash
# HTTP Requests (requires requests)
python -c "
import requests
r = requests.get('https://api.github.com/users/octocat')
print(r.json()['name'])
"

# Download file
python -c "
import urllib.request
urllib.request.urlretrieve('https://example.com/file.txt', 'local.txt')
"

# Simple server
python -m http.server 8000     # Serve current directory
python -m http.server 8080 --bind 127.0.0.1  # Bind to localhost only
```

## 🧮 Math & Calculations
```bash
# Basic math
python -c "print(2**10)"       # Power
python -c "print(sum(range(1, 101)))"  # Sum 1 to 100
python -c "import math; print(math.factorial(5))"  # Factorial

# Advanced math
python -c "
import math
import statistics
data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(f'Mean: {statistics.mean(data)}')
print(f'StdDev: {statistics.stdev(data)}')
print(f'Sqrt(50): {math.sqrt(50)}')
"
```

## 📅 Date & Time
```bash
# Current date/time
python -c "import datetime; print(datetime.datetime.now())"
python -c "import time; print(time.time())"  # Unix timestamp

# Date formatting
python -c "
import datetime
now = datetime.datetime.now()
print(now.strftime('%Y-%m-%d %H:%M:%S'))
"

# Date calculations
python -c "
import datetime
today = datetime.date.today()
week_ago = today - datetime.timedelta(days=7)
print(f'Week ago: {week_ago}')
"
```

## 🔐 Encoding & Hashing
```bash
# Base64 encoding
python -c "
import base64
text = 'Hello World'
encoded = base64.b64encode(text.encode()).decode()
print(f'Encoded: {encoded}')
decoded = base64.b64decode(encoded).decode()
print(f'Decoded: {decoded}')
"

# URL encoding
python -c "
import urllib.parse
url = 'hello world'
encoded = urllib.parse.quote(url)
print(f'Encoded: {encoded}')
"

# Hashing
python -c "
import hashlib
text = 'Hello World'
md5 = hashlib.md5(text.encode()).hexdigest()
sha256 = hashlib.sha256(text.encode()).hexdigest()
print(f'MD5: {md5}')
print(f'SHA256: {sha256}')
"
```

## 📝 Text Processing
```bash
# String operations
python -c "print('hello world'.title())"    # Title case
python -c "print('HELLO WORLD'.lower())"    # Lower case
python -c "print('  hello  '.strip())"      # Remove whitespace

# Regular expressions
python -c "
import re
text = 'Phone: 123-456-7890'
phone = re.search(r'\d{3}-\d{3}-\d{4}', text)
print(phone.group() if phone else 'Not found')
"

# Text statistics
python -c "
text = 'This is a sample text for analysis'
words = text.split()
print(f'Words: {len(words)}')
print(f'Characters: {len(text)}')
print(f'Unique words: {len(set(words))}')
"
```

## 🧪 Testing & Debugging
```bash
# Run tests
python -m unittest test_module.py         # Run specific test
python -m unittest discover               # Discover and run tests
python -m doctest module.py               # Run doctests

# Profiling
python -m cProfile script.py              # Profile script
python -m timeit "sum(range(100))"        # Time single statement

# Debugging
python -m pdb script.py                   # Start with debugger
python -c "import pdb; pdb.set_trace(); print('debug')"  # Add breakpoint
```

## 🗃️ File System Operations
```bash
# Directory operations
python -c "import os; print(os.getcwd())"                    # Current directory
python -c "import os; os.makedirs('path/to/dir', exist_ok=True)"  # Create dirs
python -c "import shutil; shutil.rmtree('directory')"        # Remove directory

# File operations
python -c "import os; print(os.path.exists('file.txt'))"     # Check if exists
python -c "import os; print(os.path.getsize('file.txt'))"    # File size
python -c "import glob; print(glob.glob('*.py'))"            # Find files by pattern

# Path operations
python -c "
import os
path = '/home/user/document.txt'
print(f'Directory: {os.path.dirname(path)}')
print(f'Filename: {os.path.basename(path)}')
print(f'Extension: {os.path.splitext(path)[1]}')
"
```

## 🎲 Random & Generation
```bash
# Random numbers
python -c "import random; print(random.randint(1, 100))"     # Random integer
python -c "import random; print(random.choice(['a', 'b', 'c']))"  # Random choice

# Generate data
python -c "
import random
import string
# Generate random password
password = ''.join(random.choices(string.ascii_letters + string.digits, k=12))
print(f'Password: {password}')
"

# UUID generation
python -c "import uuid; print(uuid.uuid4())"                 # Random UUID
```

## 🔧 System Operations
```bash
# System information
python -c "import platform; print(platform.system())"       # OS name
python -c "import platform; print(platform.python_version())"  # Python version

# Process operations
python -c "import os; print(os.getpid())"                   # Current process ID
python -c "import subprocess; subprocess.run(['ls', '-la'])" # Run system command

# Environment variables
python -c "import os; print(os.environ.get('HOME'))"        # Get env variable
python -c "import os; print(dict(os.environ))"              # All env variables
```

## 🎯 Common One-Liner Patterns
```bash
# Count files by extension
python -c "
import os
from collections import Counter
files = [f for f in os.listdir('.') if os.path.isfile(f)]
extensions = [os.path.splitext(f)[1] for f in files]
counter = Counter(extensions)
for ext, count in counter.most_common():
    print(f'{ext or \"no extension\"}: {count}')
"

# Find duplicate files
python -c "
import os
import hashlib
from collections import defaultdict

def get_hash(filename):
    with open(filename, 'rb') as f:
        return hashlib.md5(f.read()).hexdigest()

files = [f for f in os.listdir('.') if os.path.isfile(f)]
hashes = defaultdict(list)
for f in files:
    try:
        hashes[get_hash(f)].append(f)
    except:
        pass

for hash_val, file_list in hashes.items():
    if len(file_list) > 1:
        print(f'Duplicates: {file_list}')
"

# Generate CSV from JSON
python -c "
import json
import csv
import sys

with open('data.json') as f:
    data = json.load(f)

if data:
    with open('output.csv', 'w', newline='') as f:
        writer = csv.DictWriter(f, fieldnames=data[0].keys())
        writer.writeheader()
        writer.writerows(data)
    print('CSV created successfully')
"
```

## 💡 Pro Tips
- Use `python -i` to stay in interactive mode after script execution
- `python -m pip` is more reliable than just `pip`
- Use `sys.argv` for command-line arguments in scripts
- `python -u` for real-time output (unbuffered)
- Use `pathlib` instead of `os.path` for modern path handling
- `python -c` is great for quick calculations and transformations
- Always handle exceptions in one-liners with try/except
- Use `argparse` for professional command-line interfaces

## 🚨 Common Gotchas
- Different behavior between Python 2 and 3
- Integer division: use `//` for floor division
- String encoding issues with special characters
- Module import paths and PYTHONPATH
- Package installation conflicts
- Virtual environment activation

Remember: Python's standard library is vast - explore it! 🐍🚀
