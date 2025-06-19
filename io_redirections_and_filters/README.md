# Shell I/O Redirections and Filters

This project explores shell I/O redirections and filters, teaching fundamental concepts of how to manipulate input and output streams in Unix-like systems.

## Learning Objectives

By completing this project, you will understand:

- **Command Usage**: How to use essential commands like `head`, `tail`, `find`, `wc`, `sort`, `uniq`, `grep`, and `tr`
- **I/O Redirection**: How to redirect standard output to files and get input from files
- **Piping**: How to chain commands together using pipes to create powerful data processing workflows
- **Special Characters**: Understanding shell special characters and their proper usage
- **File Formats**: The structure and purpose of `/etc/passwd` and `/etc/shadow` files

## Key Concepts

### I/O Redirection
- `>` - Redirect output to a file (overwrite)
- `>>` - Redirect output to a file (append)
- `<` - Get input from a file
- `|` - Pipe output from one command to another

### Essential Commands
- `echo` - Display text
- `cat` - Display file contents
- `head` - Show first lines of a file
- `tail` - Show last lines of a file
- `wc` - Count words, lines, characters
- `sort` - Sort lines of text
- `uniq` - Remove duplicate lines
- `grep` - Search for patterns
- `tr` - Translate or delete characters
- `cut` - Extract columns from text
- `find` - Search for files and directories

## Project Requirements

- All scripts must be exactly **two lines long**
- First line must be `#!/bin/bash`
- Scripts must be executable
- Tested on Ubuntu 20.04 LTS
- No use of backticks, `&&`, `||`, `;`, `sed`, or `awk`

## Scripts Description

Each script in this project demonstrates specific I/O redirection and filtering techniques:

- `0-hello_world` - Prints "Hello, World" to standard output
- Additional scripts will be documented as they are created

## Usage

Make scripts executable and run them:
```bash
chmod +x script_name
./script_name
```

## Resources

- Shell I/O Redirection documentation
- Special Characters reference
- Man pages for all commands used (`man command_name`)
