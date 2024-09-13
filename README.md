# inline-copy

A simple Node.js command-line tool for macOS that reads the contents of one or more files, formats them, outputs the result to the console, and automatically copies it to your clipboard.
This is useful when you want to copy the content of multiple files to a single location, like a LLM chat message.

## Table of Contents

- [inline-copy](#inline-copy)
  - [Table of Contents](#table-of-contents)
  - [Features](#features)
  - [Installation](#installation)
    - [Prerequisites](#prerequisites)
    - [Clone the Repository](#clone-the-repository)
    - [Make the Script Executable](#make-the-script-executable)
    - [Add the Script to Your PATH](#add-the-script-to-your-path)
      - [Option 1: Create a Symlink in `/usr/local/bin`](#option-1-create-a-symlink-in-usrlocalbin)
      - [Option 2: Add Your Scripts Directory to PATH](#option-2-add-your-scripts-directory-to-path)
  - [Usage](#usage)
    - [Syntax](#syntax)
    - [Output Format](#output-format)
  - [Examples](#examples)
    - [Example 1: Single File](#example-1-single-file)
    - [Example 2: Multiple Files](#example-2-multiple-files)
  - [Notes](#notes)
  - [License](#license)
- [Additional Information](#additional-information)

## Features

- **Read Multiple Files**: Include one or more files in a single command.
- **Formatted Output**: Outputs file contents with clear separators and file names.
- **Clipboard Integration**: Automatically copies the formatted output to your clipboard.
- **Console Output**: Displays the formatted content in your terminal.

## Installation

### Prerequisites

- **Node.js**: Ensure that Node.js is installed on your macOS system.

  ```bash
  node -v
  ```

  If Node.js is not installed, download it from the [official website](https://nodejs.org/) or install it via Homebrew:

  ```bash
  brew install node
  ```

### Clone the Repository

1. **Create a Directory for Your Scripts (Optional)**:

   ```bash
   mkdir -p ~/scripts
   ```

2. **Save the Script**:

   Clone this repository to your scripts directory:

   ```bash
   git clone https://github.com/sebastienfi/inline-copy.git ~/scripts/inline-copy
   ```

### Make the Script Executable

```bash
chmod +x ~/scripts/inline-copy/inline-copy
```

### Add the Script to Your PATH

#### Option 1: Create a Symlink in `/usr/local/bin`

This allows you to run `inline-copy` from anywhere without moving the script.

```bash
sudo ln -s ~/scripts/inline-copy/inline-copy /usr/local/bin/inline-copy
```

#### Option 2: Add Your Scripts Directory to PATH

1. **Edit Your Shell Profile**:

   - For **bash**:

     ```bash
     nano ~/.bash_profile
     ```

   - For **zsh** (default shell in newer macOS versions):

     ```bash
     nano ~/.zshrc
     ```

2. **Add the Following Line**:

   ```bash
   export PATH="$PATH:$HOME/scripts/inline-copy"
   ```

3. **Reload Your Shell Configuration**:

   - For **bash**:

     ```bash
     source ~/.bash_profile
     ```

   - For **zsh**:

     ```bash
     source ~/.zshrc
     ```
## Usage

### Syntax

```bash
inline-copy "<file-1>" "<file-2>" "<file-3>" ...
```

- Replace `<file-n>` with the relative or absolute paths to the files you want to include.
- Enclose file paths with spaces in quotes.

### Output Format

The script outputs formatted content to the console and copies it to your clipboard. The format is:

```
###

---
File: "file-n"

<file-contents>
---

###
```

- Each file's content is enclosed between `---` separators.
- The entire output is enclosed between `###` separators.

## Examples

### Example 1: Single File

```bash
inline-copy "example.txt"
```

**Output:**

```
###

---
File: "example.txt"

<contents of example.txt>
---

###
```

### Example 2: Multiple Files

```bash
inline-copy "script.js" "styles.css" "index.html"
```

**Output:**

```
###

---
File: "script.js"

<contents of script.js>
---

---
File: "styles.css"

<contents of styles.css>
---

---
File: "index.html"

<contents of index.html>
---

###
```

## Notes

- **Clipboard Copy**: The script uses the `pbcopy` command, which is available by default on macOS, to copy the output to the clipboard.
- **Error Handling**: If a file is not found or cannot be read, the script will display an error message and exit.
- **Relative Paths**: The script resolves file paths relative to the current working directory.
- **No External Dependencies**: The script uses only built-in Node.js modules.

## License

This project is licensed under the MIT License.

---

Feel free to customize the script or reach out if you have any questions!

# Additional Information

**Updating the Script:**

To update the script with the latest changes from the repository, navigate to the directory and pull the latest commits:

```bash
cd ~/scripts/inline-copy
git pull
```

