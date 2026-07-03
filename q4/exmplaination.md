rm -f app.log stdout.txt stderr.txt combined.txt
- Command run: removed existing artifacts to start clean.
- Explanation: Ensures previous files do not affect the investigation.

echo "sample log line" > app.log
- Command run: created `app.log` with one sample line.
- Explanation: Provides a file to open and inspect with file descriptors.

lsof | head -n 20
- Command run: listed a subset of open files system-wide.
- Explanation: Identified processes and open file descriptors, useful to find which processes have files open.

exec 3<app.log
- Command run: opened `app.log` on file descriptor 3 for the current shell.
- Explanation: Demonstrates how to attach a file descriptor to an open file for input.

lsof -p $$ | grep app.log
- Command run: filtered `lsof` output for the current shell process and `app.log`.
- Explanation: Confirmed the shell process has fd `3` open on `app.log`.

ls -l /proc/$$/fd | grep app.log
ls -l /proc/$$/fd
- Command run: inspected `/proc/<pid>/fd` to see file descriptor symlinks.
- Explanation: `/proc` reveals the actual filesystem targets for each file descriptor; fd `3` pointed to `app.log`.

ls -l > stdout.txt
- Command run: redirected the output of `ls -l` into `stdout.txt`.
- Explanation: Demonstrates capturing standard output into a file.

ls /not_a_real_path 2> stderr.txt
- Command run: attempted to list a non-existent path and redirected stderr into `stderr.txt`.
- Explanation: Shows capturing error messages separately.

(ls -l && ls /not_a_real_path) > combined.txt 2>&1
- Command run: ran a combined command and redirected both stdout and stderr into `combined.txt`.
- Explanation: Demonstrates merging stdout and stderr into a single file for combined logs.

ulimit -a
- Command run: displayed resource limits for the shell.
- Explanation: Records system limits (like `open files`) that affect how many file descriptors/processes can be used.

exec 3<&-
- Command run: closed file descriptor 3.
- Explanation: Cleans up by releasing the open descriptor attached to `app.log`.
