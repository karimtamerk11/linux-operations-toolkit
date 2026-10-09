# Linux Process Management

## What Is a Process?

A process is a program or command currently running in Linux.

Examples include:

- Firefox
- The Terminal
- The SSH server
- A Python program
- A Bash command

Every process receives a unique number called a **PID**, which means **Process ID**.

---

## Viewing Processes

### `ps`

```bash
ps
```

Displays processes connected to the current terminal session.

Important columns:

- `PID`: Process ID
- `TTY`: Terminal connected to the process
- `TIME`: CPU time used by the process
- `CMD`: Command that started the process

### `ps aux`

```bash
ps aux
```

Displays processes running across the system.

Important columns:

- `USER`: User who owns the process
- `PID`: Process ID
- `%CPU`: CPU usage
- `%MEM`: Memory usage
- `COMMAND`: Command that started the process

---

## Finding a Process

### `pgrep`

```bash
pgrep -a process_name
```

Searches for processes by name.

The `-a` option also displays the full command associated with each matching process.

Example:

```bash
pgrep -a ssh
```

---

## Monitoring Processes

### `top`

```bash
top
```

Displays live information about processes, CPU usage, memory usage, and system load.

Press `q` to exit.

### `htop`

```bash
htop
```

Provides an interactive process-monitoring interface.

Useful controls:

- `F3`: Search for a process
- `F6`: Change the sorting method
- `q`: Exit

---

## Foreground and Background Processes

### Start a process in the background

```bash
sleep 300 &
```

The `&` symbol starts the command in the background, allowing the terminal to remain available.

### View terminal jobs

```bash
jobs
```

Displays processes started from the current terminal session.

A job number such as `%1` is different from a PID.

- Job number: Used by the current shell
- PID: Used by the Linux operating system

### Pause a foreground process

Press:

```text
Ctrl + Z
```

This suspends the foreground process. It does not terminate it.

### Continue a job in the background

```bash
bg %1
```

Continues job 1 in the background.

### Bring a job to the foreground

```bash
fg %1
```

Moves job 1 back to the foreground.

---

## Stopping Processes

### Normal termination

```bash
kill PID
```

Sends the `SIGTERM` signal to the process.

`SIGTERM` asks the process to shut down normally, allowing the process to save data, close files, and release resources.

### Stop a shell job

```bash
kill %1
```

Stops job 1 from the current terminal.

### Force termination

```bash
kill -9 PID
```

Sends the `SIGKILL` signal and immediately forces the process to stop.

`kill -9` should only be used when normal termination fails because the process cannot perform cleanup or save data.

### Stop processes by name

```bash
pkill process_name
```

Stops processes matching the provided name.

---

## Memory and System Load

### `free -h`

```bash
free -h
```

Displays total, used, free, and available memory.

The `-h` option displays sizes in a human-readable format such as MB and GB.

### `uptime`

```bash
uptime
```

Displays:

- How long the system has been running
- Number of logged-in users
- Load averages for the last 1, 5, and 15 minutes

For a virtual machine with four CPU cores, a load near `4.00` means the four cores are approximately fully occupied.

---

## Commands Practised

```bash
ps
ps aux
pgrep -a process_name
top
htop
sleep 300 &
jobs
fg %1
bg %1
kill PID
kill %1
kill -9 PID
pkill process_name
free -h
uptime
```

---

## Quick Memory Notes

```text
Process     A running program or command
PID         Unique process identification number
ps          Show current terminal processes
ps aux      Show system processes
pgrep       Find a process by name
top         Monitor processes and resources
htop        Interactive process monitor
&           Start a command in the background
jobs        Show jobs started by the current shell
Ctrl + Z    Suspend the foreground process
bg          Continue a job in the background
fg          Bring a job to the foreground
kill        Request normal process termination
kill -9     Force immediate termination
free -h     Show memory usage
uptime      Show running time and load averages
```

## What I Learned

Linux treats every running program as a process with its own PID.

Processes can run in the foreground or background. Shell job numbers are used with commands such as `fg`, `bg`, and `kill %1`, while PIDs are used with commands such as `kill 5989`.

Normal `kill` should be attempted before `kill -9` because normal termination allows the process to shut down safely.
