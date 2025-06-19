# Shell Loops, Conditions and Parsing

This project focuses on mastering shell scripting concepts including loops, conditional statements, and text parsing techniques. You'll learn to create robust scripts that handle repetitive tasks, make decisions, and process data files.

## Learning Objectives

By completing this project, you will understand:

- **Loop Constructs**: `for`, `while`, and `until` loops and when to use each
- **Conditional Logic**: `if/elif/else` statements and `case` statements
- **File Operations**: Testing file properties and processing file contents
- **Text Processing**: Parsing structured data like log files and system files
- **Shell Arithmetic**: Mathematical operations and modulo calculations
- **Parameter Expansion**: String manipulation and pattern matching

## Key Concepts

### Loop Types
- **for loops**: Best for iterating over sequences or ranges
- **while loops**: Execute while a condition is true
- **until loops**: Execute until a condition becomes true

### Conditional Statements
- **if/elif/else**: Multi-branch decision making
- **case statements**: Pattern matching for multiple conditions
- **Test operators**: File tests (`-e`, `-f`, `-s`) and numeric comparisons

### File Processing
- **IFS (Internal Field Separator)**: Controls how bash splits input
- **Reading files**: Line-by-line processing with `while read`
- **Field extraction**: Using `cut`, `awk` for structured data

## Scripts Description

### Basic Loop Exercises
- `1-for_best_school` - Displays "Best School" 10 times using a `for` loop
- `2-while_best_school` - Same output using a `while` loop
- `3-until_best_school` - Same output using an `until` loop

### Conditional Logic
- `4-if_9_say_hi` - Combines loops with `if` statements for special cases
- `5-4_bad_luck_8_is_your_chance` - Uses `if/elif/else` for multiple conditions
- `6-superstitious_numbers` - Demonstrates `case` statement usage

### Advanced Applications
- `7-clock` - Nested loops to display time format (hours and minutes)
- `8-for_ls` - Directory listing with string manipulation
- `9-to_file_or_not_to_file` - File existence and property testing
- `10-fizzbuzz` - Classic programming exercise with modulo arithmetic

### File Processing
- `11-read_and_cut` - Parsing `/etc/passwd` to extract specific fields
- `12-tell_the_story_of_passwd` - Creative formatting of system data
- `13-lets_parse_apache_logs` - Log file analysis with `awk`
- `14-dig_the-data` - Data aggregation and sorting

## Usage Examples

### Running Basic Scripts
```bash
# Make scripts executable
chmod +x script_name

# Execute
./1-for_best_school
./2-while_best_school
./3-until_best_school
```

### Testing Conditional Scripts
```bash
# Create test file for file operations
touch school
echo "content" > school

# Run file test script
./9-to_file_or_not_to_file

# Clean up
rm school
mkdir school
./9-to_file_or_not_to_file
```

### Log File Analysis
```bash
# Parse Apache logs
./13-lets_parse_apache_logs

# Get aggregated data
./14-dig_the-data | head -10
```

## Technical Implementation Details

### Loop Syntax Examples
```bash
# For loop with C-style syntax
for ((i=1; i<=10; i++))
do
    echo "Iteration $i"
done

# While loop with counter
i=1
while [ $i -le 10 ]
do
    echo "Count: $i"
    ((i++))
done

# Until loop
i=1
until [ $i -gt 10 ]
do
    echo "Until: $i"
    ((i++))
done
```

### Conditional Statements
```bash
# If/elif/else structure
if [ condition1 ]
then
    action1
elif [ condition2 ]
then
    action2
else
    default_action
fi

# Case statement
case $variable in
    pattern1)
        action1
        ;;
    pattern2)
        action2
        ;;
    *)
        default_action
        ;;
esac
```

### File Operations
```bash
# File existence and type tests
if [ -e "filename" ]    # File exists
if [ -f "filename" ]    # Regular file
if [ -s "filename" ]    # File not empty
if [ -d "filename" ]    # Directory
```

### Text Processing
```bash
# Reading files with IFS
while IFS=: read -r field1 field2 field3
do
    echo "$field1 -> $field3"
done < /etc/passwd

# AWK for field extraction
awk '{print $1 " " $9}' logfile

# Sorting and counting
sort | uniq -c | sort -rn
```

## Key Shell Features Demonstrated

### Arithmetic Operations
```bash
# Basic arithmetic
$((i + 1))
$((i * 2))
$((i % 3))    # Modulo for FizzBuzz

# Increment operators
((i++))
((i--))
```

### String Manipulation
```bash
# Parameter expansion
${filename#*-}     # Remove prefix up to first dash
${filename##*-}    # Remove prefix up to last dash
${filename%-*}     # Remove suffix from last dash
```

### Pattern Matching
```bash
# Wildcard matching in case
case $file in
    *.txt)
        echo "Text file"
        ;;
    *.log)
        echo "Log file"
        ;;
esac
```

## Real-World Applications

### System Administration
- **Log Analysis**: Processing web server logs for traffic patterns
- **User Management**: Parsing system files like `/etc/passwd`
- **Monitoring**: Creating scripts that check system status repeatedly

### Data Processing
- **Report Generation**: Aggregating data from multiple sources
- **File Organization**: Batch processing of files based on patterns
- **Automation**: Scheduled tasks that process data files

## Important Notes

- **Loop Selection**: Choose the right loop type for your use case
- **Error Handling**: Always test for file existence before processing
- **Performance**: `awk` is often faster than shell loops for text processing
- **Portability**: Use `#!/usr/bin/env bash` for better compatibility

## Troubleshooting Common Issues

### Loop Problems
- **Infinite loops**: Always ensure loop conditions eventually become false
- **Variable scope**: Be careful with variable modifications inside loops

### File Processing
- **Missing files**: Always check file existence with `-e` test
- **Permissions**: Ensure read permissions on files being processed
- **Empty files**: Test with `-s` to avoid processing empty files

## Resources

- Bash Manual: Loop Constructs and Conditional Commands
- Advanced Bash Scripting Guide: Control Structures
- AWK Programming Language for text processing
- Regular Expressions for pattern matching