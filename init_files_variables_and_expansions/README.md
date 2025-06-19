# Shell Init Files, Variables and Expansions

This project explores shell initialization files, variables, expansions, and advanced shell scripting concepts including aliases, arithmetic operations, and text transformations.

## Learning Objectives

By completing this project, you will understand:

- **Shell Initialization**: How `/etc/profile`, `/etc/profile.d/`, and `~/.bashrc` work
- **Variables**: Local vs global variables, reserved variables, and special parameters
- **Expansions**: Command substitution, arithmetic expansion, and parameter expansion
- **Aliases**: Creating, listing, and managing command shortcuts
- **Shell Arithmetic**: Performing mathematical operations in the shell
- **Text Processing**: Character transformations and format conversions

## Key Concepts

### Variables and Environment
- **Local Variables**: Available only in current shell session
- **Global Variables**: Exported to child processes via `export`
- **Reserved Variables**: `HOME`, `PATH`, `PS1`, `USER`, `PWD`, `OLDPWD`
- **Special Parameters**: `$?` (exit status), `$0` (script name), `$#` (argument count)

### Shell Arithmetic
- **Basic Operations**: `$((expression))` for addition, subtraction, multiplication, division
- **Exponentiation**: `$((base ** exponent))`
- **Base Conversion**: `$((base#number))` for different number bases

### Text Processing
- **Character Translation**: `tr` command for character substitution
- **Format Output**: `printf` for formatted text output
- **Line Processing**: `paste`, `cut` for manipulating text streams

## Scripts Description

### Basic Operations
- `0-alias` - Creates an alias that maps `ls` to `rm *`
- `1-hello_you` - Greets the current user using the `$USER` variable
- `2-path` - Adds `/action` directory to the PATH environment variable
- `3-paths` - Counts the number of directories in the PATH

### Variable Management
- `4-global_variables` - Lists all environment variables using `printenv`
- `5-local_variables` - Lists all variables and functions using `set`
- `6-create_local_variable` - Creates a local variable `BEST=School`
- `7-create_global_variable` - Creates and exports a global variable `BEST=School`

### Arithmetic Operations
- `8-true_knowledge` - Adds 128 to the `TRUEKNOWLEDGE` environment variable
- `9-divide_and_rule` - Divides `POWER` by `DIVIDE` environment variables
- `10-love_exponent_breath` - Calculates `BREATH` to the power of `LOVE`
- `11-binary_to_decimal` - Converts binary number to decimal using base conversion

### Advanced Text Processing
- `12-combinations` - Generates all two-letter combinations except "oo"
- `13-print_float` - Formats numbers with exactly two decimal places
- `14-decimal_to_hexadecimal` - Converts decimal numbers to hexadecimal
- `15-rot13` - Applies ROT13 cipher for text encryption/decryption
- `16-odd` - Prints every other line from input, starting with the first
- `17-water_and_stir` - Performs addition using custom base systems

## Usage Examples

### Running Scripts
```bash
# Make scripts executable
chmod +x script_name

# Source scripts that modify environment
source ./0-alias
source ./2-path

# Execute scripts directly
./1-hello_you
./8-true_knowledge
```

### Testing with Variables
```bash
# Set environment variables for testing
export TRUEKNOWLEDGE=1209
export POWER=42784
export DIVIDE=32
export BINARY=10100111001

# Run arithmetic scripts
./8-true_knowledge    # Output: 1337
./9-divide_and_rule   # Output: 1337
./11-binary_to_decimal # Output: 1337
```

### Text Processing Examples
```bash
# ROT13 encryption
echo "Hello World" | ./15-rot13

# Print combinations
./12-combinations | head -10

# Format floating point
export NUM=3.14159
./13-print_float      # Output: 3.14
```

## Technical Requirements

- All scripts are exactly **two lines long** (shebang + command)
- First line must be `#!/bin/bash`
- No use of forbidden operators: `&&`, `||`, `;`
- No use of forbidden commands: `bc`, `sed`, `awk`
- All files must be executable
- Tested on Ubuntu 20.04 LTS

## Key Shell Features Demonstrated

### Arithmetic Expansion
```bash
echo $((128 + TRUEKNOWLEDGE))    # Addition
echo $((POWER / DIVIDE))         # Division
echo $((BREATH ** LOVE))         # Exponentiation
echo $((2#$BINARY))              # Base conversion
```

### Variable Operations
```bash
export VARIABLE="value"          # Global variable
VARIABLE="value"                 # Local variable
echo $USER                       # Built-in variable
```

### Text Transformations
```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m'      # ROT13 cipher
printf "%.2f\n" $NUM             # Format floating point
printf "%x\n" $DECIMAL           # Hexadecimal conversion
```

## Important Notes

- **Alias Safety**: Script 0-alias creates a dangerous alias that replaces `ls` with `rm *`
- **Sourcing vs Execution**: Some scripts need to be sourced (`. script`) to affect the current shell
- **Base Conversions**: The shell supports various number bases using the format `base#number`
- **ROT13**: A simple letter substitution cipher that shifts letters by 13 positions

## Resources

- Shell Expansions and Parameter Substitution
- Shell Arithmetic and Mathematical Operations
- Environment Variables and Shell Initialization
- Text Processing with Standard Unix Tools
