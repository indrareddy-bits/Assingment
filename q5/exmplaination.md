lsblk
- Command run: `lsblk`
- Explanation: Lists block devices and partitions to show available storage devices and their mountpoints.

mount | head -5
- Command run: `mount | head -5`
- Explanation: Displays mounted filesystems; confirms overlay and other system mounts present in this environment.

df -h
- Command run: `df -h`
- Explanation: Shows human-readable disk usage; observed `/dev/root` at ~81% usage and other mounts with available space.

df -i
- Command run: `df -i`
- Explanation: Shows inode utilization; inode usage is low (single-digit percentages) on the reported filesystems.

Recommendations
- Explanation: Recommend cleaning large files on `/vscode`, rotating logs, and adding monitoring or quotas to prevent production issues.
