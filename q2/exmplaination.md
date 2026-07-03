mkdir -p secure_workspace/{docs,src,logs}
- Command run: created the `secure_workspace` directory tree with `docs`, `src`, and `logs` subfolders.
- Explanation: Sets up the folder structure to organize documentation, source, and logs.

touch secure_workspace/docs/plan.txt secure_workspace/src/app.txt secure_workspace/logs/activity.log
- Command run: created empty files `plan.txt`, `app.txt`, and `activity.log`.
- Explanation: Creates placeholder files that will hold project plans, source notes, and activity logs.

ls -ld secure_workspace secure_workspace/*
- Command run: listed directory entries and their permissions before permission changes.
- Explanation: Verified the directories exist and inspected initial permissions and ownership (`codespace:codespace`).

chmod 750 secure_workspace
chmod 750 secure_workspace/docs secure_workspace/src secure_workspace/logs
- Command run: applied `750` to the workspace and subdirectories.
- Explanation: Restricts access so owner has full access, group can read/traverse, others have no access.

chmod 640 secure_workspace/docs/plan.txt secure_workspace/src/app.txt secure_workspace/logs/activity.log
- Command run: attempted to set files to `640`.
- Explanation: Intended to restrict files to owner read/write and group read only; note `activity.log` remained `rw-rw-rw-` due to a typos in the original chmod command in the session which targeted an incorrect filename earlier.

ls -ld secure_workspace secure_workspace/*
ls -l secure_workspace/*
- Command run: inspected directory and file permissions after changes.
- Explanation: Confirmed directories now show `drwxr-x---` and files `plan.txt`/`app.txt` show `-rw-r-----`; `activity.log` still had global write/read (seen in listing).

umask
- Command run: `umask`
- Explanation: Shows the default file-creation mask `0022` which influenced default permissions when files were created.
