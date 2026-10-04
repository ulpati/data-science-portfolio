# 🗂️ File Organizer

Python-based automated file management system that organizes files by type into categorized subfolders with CSV tracking.

[![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](../LICENSE)
[![Feedback](https://img.shields.io/badge/Feedback-500%2F500-brightgreen.svg)]()
[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)]()

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Installation](#-installation)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Implementation Details](#-implementation-details)
- [Acknowledgements](#-acknowledgements)

## 🎯 Overview

This project was developed for the Python & NumPy module of the start2impact Data Science Master program. It implements an intelligent file organization system that automatically categorizes and moves files based on their extensions. The system maintains a CSV log of all operations, creates folders dynamically, and provides a command-line interface for selective file processing.

The project demonstrates fundamental Python concepts including file I/O operations, CSV handling, command-line argument parsing, and automated directory management. It's designed to handle incremental additions without overwriting existing data.

**Score: 500/500**

## ✨ Features

- **Automatic Categorization** - Organizes files by type: images (jpg, jpeg, png), documents (txt, odt), audio (mp3)
- **Dynamic Folder Creation** - Automatically creates target subfolders if they don't exist
- **CSV Logging** - Tracks all file operations with name, type, and size information
- **Incremental Updates** - Appends to existing logs without overwriting previous entries
- **CLI Interface** - Command-line tool for selective file processing with argument validation
- **Extensible Design** - Easy to add new file types and categories

## 🚀 Installation

### Prerequisites

```bash
# Python 3.7 or higher required
python --version
```

### Setup

```bash
# Clone repository
git clone https://github.com/ulpati/data-science-portfolio.git
cd data-science-portfolio/file_organizer

# No additional dependencies required (uses Python standard library)
```

## 💻 Usage

### Quick Start - Jupyter Notebook Version

Run all files at once using the notebook implementation:

```bash
jupyter notebook fileorganizer.ipynb
```

Execute cells sequentially to process all files in the `files/` directory.

### CLI Tool - Selective Processing

Process individual files using the command-line script:

```bash
# Process a specific file
python addfile.py song1.mp3

# View available files and help
python addfile.py --help
```

### Expected Behavior

**Before execution:**
```
files/
├── bw.png
├── ciao.txt
├── daffodil.jpg
├── eclipse.png
├── pippo.odt
├── song1.mp3
├── song2.mp3
└── trump.jpeg
```

**After execution:**
```
files/
├── audio/
│   ├── song1.mp3
│   └── song2.mp3
├── docs/
│   ├── ciao.txt
│   └── pippo.odt
├── images/
│   ├── bw.png
│   ├── daffodil.jpg
│   ├── eclipse.png
│   └── trump.jpeg
└── recap.csv         # Log file with file metadata
```

### Output Format

Console output displays file information:
```
bw type:images size:12345B
ciao type:docs size:456B
song1 type:audio size:3456789B
```

CSV log format:
```csv
name,type,size(B)
bw,images,12345
ciao,docs,456
song1,audio,3456789
```

## 📁 Project Structure

```
file_organizer/
├── README.md              # This file
├── fileorganizer.ipynb   # Jupyter notebook implementation (batch processing)
├── addfile.py            # CLI script (single file processing)
└── files/                # Target directory for file organization
    ├── [original files]  # Files to be organized
    ├── audio/            # Created automatically
    ├── docs/             # Created automatically
    ├── images/           # Created automatically
    └── recap.csv         # Operation log
```

## 🔧 Implementation Details

### Supported File Types

| Extension | Category | Description |
|-----------|----------|-------------|
| .mp3      | audio    | Audio files |
| .txt      | docs     | Text documents |
| .odt      | docs     | OpenDocument text |
| .jpg, .jpeg | images | JPEG images |
| .png      | images   | PNG images |

### Key Functions

**`manage_file(file, directory, extensions, file_csv)`**
- Checks file extension against supported types
- Retrieves file size in bytes
- Creates target subfolder if needed
- Moves file to appropriate category
- Logs operation to recap.csv
- Prints file information to console

### Libraries Used

- **os** - File system operations, path manipulation
- **shutil** - High-level file operations (move)
- **csv** - CSV file reading and writing
- **argparse** - Command-line argument parsing (CLI version)

### Design Decisions

1. **Incremental Processing** - Appends to recap.csv instead of overwriting
2. **Error Handling** - Validates extensions before processing
3. **Alphabetical Processing** - Files sorted alphabetically for consistent ordering
4. **Raw Strings** - Uses raw strings (r'files') for cross-platform path compatibility
5. **Dynamic Folder Creation** - Checks for subfolder existence before creating

## 🤝 Acknowledgements

This project was developed for the **start2impact Data Science Master Program**.

**Course:** Python & NumPy  
**Institution:** start2impact University  
**Project Type:** Automated File Management System