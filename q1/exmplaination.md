whoami
- Command run: `whoami`
- Explanation: Shows the current username (`codespace`). I observed the account used for the lab is `codespace`.

groups
- Command run: `groups`
- Explanation: Lists group memberships for `codespace`. This shows which supplemental groups the user can access (e.g., `docker`).

echo "$SHELL"
- Command run: `echo "$SHELL"`
- Explanation: Prints the login shell in use. The shell is `/bin/bash`, so Bash-compatible commands apply.

pwd
- Command run: `pwd`
- Explanation: Displays the present working directory `/workspaces/Assingment` where the assignment files are located.

ls -ls
- Command run: `ls -ls`
- Explanation: Lists files with sizes and permissions; confirms presence of `q1`–`q5` and `README.md` in the workspace.

curl -s --max-time 10 https://youtube.com
- Command run: `curl -s --max-time 10 https://youtube.com > /dev/null && echo "Network: youtube.com reachable"`
- Explanation: Attempts a network connection to `youtube.com`. No "Network: ... reachable" message was printed, so the check did not confirm reachability from this environment.
