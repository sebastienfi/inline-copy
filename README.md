# inline-copy

A simple Node.js command-line tool for macOS that reads the contents of one or more files (supports glob patterns), formats them, outputs the result to the console, and automatically copies it to your clipboard. This is useful when you want to copy the content of multiple files to a single location, like an LLM chat message.

## Table of Contents

- [inline-copy](#inline-copy)
  - [Table of Contents](#table-of-contents)
  - [Features](#features)
  - [Installation](#installation)
    - [Prerequisites](#prerequisites)
    - [Clone the Repository](#clone-the-repository)
    - [Install Dependencies](#install-dependencies)
    - [Make the Script Executable](#make-the-script-executable)
    - [Add the Script to Your PATH](#add-the-script-to-your-path)
      - [Option 1: Create a Symlink in `/usr/local/bin`](#option-1-create-a-symlink-in-usrlocalbin)
      - [Option 2: Add Your Scripts Directory to PATH](#option-2-add-your-scripts-directory-to-path)
  - [Usage](#usage)
    - [Syntax](#syntax)
    - [Output Format](#output-format)
  - [Examples](#examples)
    - [Example 1: Single File](#example-1-single-file)
    - [Example 2: Multiple Files with Glob Patterns](#example-2-multiple-files-with-glob-patterns)
  - [Notes](#notes)
  - [License](#license)
  - [Additional Information](#additional-information)
  - [Example Usage](#example-usage)
  - [Need Help?](#need-help)

## Features

- **Read Multiple Files**: Include one or more files or glob patterns in a single command.
- **Glob Pattern Support**: Use glob patterns to specify files.
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

Clone this repository to your scripts directory:

```bash
git clone https://github.com/sebastienfi/inline-copy.git ~/scripts/inline-copy
```

### Install Dependencies

Navigate to the project directory and install the required modules:

```bash
cd ~/scripts/inline-copy
npm install
```

### Make the Script Executable

```bash
chmod +x inline-copy
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
inline-copy "<file-pattern-1>" "<file-pattern-2>" "<file-pattern-3>" ...
```

- Replace `<file-pattern-n>` with the relative or absolute file paths or glob patterns.
- Enclose patterns with spaces in quotes.

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
- File contents are wrapped in code blocks using triple backticks for better readability.

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

### Example 2: Multiple Files with Glob Patterns

```bash
inline-copy "*.js" "src/**/*.css" "README.md"
```

**Explanation:**

- `*.js`: All `.js` files in the current directory.
- `src/**/*.css`: All `.css` files in any subdirectory of `src`.
- `README.md`: Includes the `README.md` file.

**Output:**

```
###

---
File: "app.js"

<contents of app.js>
---

---
File: "utils/helper.js"

<contents of utils/helper.js>
---

---
File: "src/styles/main.css"

<contents of src/styles/main.css>
---

---
File: "README.md"

<contents of README.md>
---

###
```

## Notes

- **Glob Patterns**: The script supports glob patterns for flexible file selection.
- **Clipboard Copy**: The script uses the `pbcopy` command, which is available by default on macOS, to copy the output to the clipboard.
- **Error Handling**: If a pattern matches no files, the script will display an error message but continue processing other patterns.
- **Relative Paths**: The script resolves file paths relative to the current working directory.
- **Dependencies**: The script uses the `glob` module for pattern matching.

## License

This project is licensed under the MIT License.

---

Feel free to customize the script or reach out if you have any questions!

## Additional Information

**Updating the Script:**

To update the script with the latest changes from the repository, navigate to the directory and pull the latest commits:

```bash
cd ~/scripts/inline-copy
git pull
```

---

## Example Usage

- **Include all JavaScript files in the current directory:**

  ```bash
  inline-copy "*.js"
  ```

- **Include all Markdown files in `docs` directory:**

  ```bash
  inline-copy "docs/**/*.md"
  ```

- **Include specific files:**

  ```bash
  inline-copy "inline-copy" "README.md"
  ```

---

## Need Help?

Feel free to open an issue on the repository or reach out if you have any questions!
