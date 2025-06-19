# Shell Processes and Signals

This project focuses on understanding and managing Linux processes and signals through shell scripting. You'll learn to monitor processes, send signals, handle signal trapping, and create process management scripts.

## Learning Objectives

By completing this project, you will understand:

- **Process Management**: What are PIDs, processes, and how to find and manage them
- **Signal Handling**: Understanding Linux signals and how to send/receive them
- **Process Control**: Starting, stopping, and restarting processes programmatically
- **Signal Trapping**: Catching and handling signals in shell scripts
- **Daemon Creation**: Building background processes and init scripts
- **Process Monitoring**: Using tools like `ps`, `pgrep`, `pkill`, and `kill`

## Key Concepts

### Processes
- **PID (Process ID)**: Unique identifier for each running process
- **Process Hierarchy**: Parent-child relationships between processes
- **Process States**: Running, sleeping, stopped, zombie
- **Background Processes**: Daemons and detached processes

### Signals
- **SIGTERM (15)**: Polite termination request (can be caught)
- **SIGKILL (9)**: Forceful termination (cannot be ignored)
- **SIGINT (2)**: Interrupt signal (Ctrl+C)
- **SIGQUIT (3)**: Quit signal (Ctrl+\)
- **SIGHUP (1)**: Hangup signal
- **SIGUSR1/SIGUSR2**: User-defined signals

### Signal Handling
- **trap**: Command to catch and handle signals
- **Ignoring Signals**: Only SIGKILL and SIGSTOP cannot be ignored
- **Custom Handlers**: Execute specific actions when receiving signals

## Scripts Description

### Basic Process Operations
- `0-what-is-my-pid` - Displays the script's own PID using `$$`
- `1-list_your_processes` - Shows all running processes with hierarchy
- `2-show_your_bash_pid` - Filters processes to show bash instances
- `3-show_your_bash_pid_made_easy` - Uses `pgrep` for cleaner bash PID listing

### Process Control
- `4-to_infinity_and_beyond` - Creates an infinite loop process for testing
- `5-dont_stop_me_now` - Terminates the infinity process using `kill`
- `6-stop_me_if_you_can` - Terminates process using `pkill` (no kill/killall)
- `8-beheaded_process` - Forcefully kills process with SIGKILL

### Signal Handling
- `7-highlander` - Demonstrates signal trapping with custom responses
- `67-stop_me_if_you_can` - Modified version targeting highlander process
- `10-process_and_pid_file` - Advanced signal handling with PID file management

### Process Management System
- `manage_my_process` - Background daemon that writes to log file
- `11-manage_my_process` - Init script for starting/stopping/restarting daemon

## Usage Examples

### Basic Process Information
```bash
# Get current script PID
./0-what-is-my-pid

# List all processes
./1-list_your_processes

# Find bash processes
./2-show_your_bash_pid
./3-show_your_bash_pid_made_easy
```

### Process Control Testing
```bash
# Terminal 1: Start infinite process
./4-to_infinity_and_beyond

# Terminal 2: Stop the process
./5-dont_stop_me_now
# or
./6-stop_me_if_you_can
```

### Signal Handling Demo
```bash
# Terminal 1: Start signal-aware process
./7-highlander

# Terminal 2: Send SIGTERM (shows "I am invincible!!!")
./67-stop_me_if_you_can

# Terminal 2: Force kill with SIGKILL
./8-beheaded_process
```

### Daemon Management
```bash
# Start the daemon
sudo ./11-manage_my_process start

# Check if it's writing to log
tail -f /tmp/my_process

# Stop the daemon
sudo ./11-manage_my_process stop

# Restart the daemon
sudo ./11-manage_my_process restart
```

## Technical Implementation Details

### Process Identification
```bash
# Get current script PID
echo $$

# List all processes with hierarchy
ps auxf

# Find processes by name
pgrep bash
pgrep -f "script_name"
```

### Signal Operations
```bash
# Send SIGTERM (polite termination)
kill PID
kill -15 PID

# Send SIGKILL (force termination)
kill -9 PID

# Send signal by process name
pkill process_name
pkill -f "full_command"
```

### Signal Trapping
```bash
# Basic trap syntax
trap 'echo "Signal received"' SIGTERM

# Multiple signals
trap 'cleanup_function' SIGTERM SIGINT SIGQUIT

# Remove trap
trap - SIGTERM
```

### Background Processes
```bash
# Run in background
command &

# Detach from terminal
nohup command &

# Create daemon-like process
(command) &
```

## Key Shell Features Demonstrated

### Process Management Functions
```bash
# Get process info
ps aux | grep process_name

# Kill by PID file
kill $(cat /var/run/process.pid)

# Check if process exists
if kill -0 $PID 2>/dev/null; then
    echo "Process is running"
fi
```

### Signal Handling Patterns
```bash
# Cleanup on exit
cleanup() {
    rm -f /var/run/myscript.pid
    exit 0
}
trap cleanup SIGTERM SIGQUIT

# Ignore specific signals
trap '' SIGTERM  # Empty action ignores signal

# Default signal handling
trap - SIGTERM   # Restore default behavior
```

### PID File Management
```bash
# Create PID file
echo $$ > /var/run/myscript.pid

# Read PID from file
PID=$(cat /var/run/myscript.pid)

# Remove PID file on cleanup
rm -f /var/run/myscript.pid
```

## Real-World Applications

### System Administration
- **Service Management**: Creating init scripts for custom services
- **Process Monitoring**: Automated process health checking
- **Graceful Shutdowns**: Handling system shutdown signals properly
- **Log Rotation**: Signal-based log file management

### Development
- **Application Lifecycle**: Start, stop, restart functionality
- **Debug Tools**: Process introspection and control
- **Testing Frameworks**: Process isolation and cleanup
- **CI/CD Pipelines**: Process management in automated environments

## Important Notes

### Signal Restrictions
- **SIGKILL (9)** and **SIGSTOP (19)** cannot be caught, blocked, or ignored
- Always use SIGTERM before SIGKILL for graceful termination
- Different signals have different default behaviors

### Best Practices
- **PID Files**: Store process IDs for reliable process management
- **Signal Handlers**: Always clean up resources in signal handlers
- **Error Handling**: Check if processes exist before sending signals
- **Permissions**: Some operations require sudo privileges

### Security Considerations
- **Process Visibility**: Users can only manage their own processes (unless root)
- **Signal Permissions**: Sending signals to other users' processes requires privileges
- **PID File Locations**: Use appropriate directories (`/var/run/` for system services)

## Troubleshooting Common Issues

### Process Management
- **Process Not Found**: Check if PID still exists with `kill -0 $PID`
- **Permission Denied**: Ensure proper user privileges for signal operations
- **Stale PID Files**: Always validate PID file contents before use

### Signal Handling
- **Signals Not Caught**: Ensure trap is set before process starts waiting
- **Infinite Loops**: Use sleep or other blocking operations for signal delivery
- **Signal Delivery**: Signals are delivered when process is not in system call

## Resources

- Linux Signal Manual: `man 7 signal`
- Process Control: `man ps`, `man kill`, `man pgrep`
- Shell Job Control: `man bash` (Job Control section)
- Init Scripts: `/etc/init.d/` examples