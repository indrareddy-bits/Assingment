rm -f original.txt hardlink.txt symlink.txt
- Command run: removed any pre-existing files to start clean.
- Explanation: Ensures the experiment starts from a known state.

echo "Linux link test file" > original.txt
- Command run: created `original.txt` with sample text.
- Explanation: This is the file that will be used to create links.

ln original.txt hardlink.txt
- Command run: created a hard link named `hardlink.txt` to `original.txt`.
- Explanation: Hard links create another directory entry pointing to the same inode; both names reference the same file data.

ln -s original.txt symlink.txt
- Command run: created a symbolic link `symlink.txt` -> `original.txt`.
- Explanation: Symlinks store a pathname pointing to the target; they are separate inodes and can point to non-existent targets.

ls -li
stat original.txt hardlink.txt symlink.txt
- Command run: inspected inode and metadata for each file.
- Explanation: Observed `original.txt` and `hardlink.txt` share the same inode and link count, while `symlink.txt` has its own inode and points to the target path.

cat original.txt; cat hardlink.txt; cat symlink.txt
- Command run: displayed contents via original, hard link, and symlink.
- Explanation: All three produced the same contents while the target existed.

rm original.txt
- Command run: removed the original filename.
- Explanation: This tests the behavior of hard vs symbolic links when the original entry is deleted.

ls -li; cat hardlink.txt; cat symlink.txt
- Command run: verified remaining entries.
- Explanation: `hardlink.txt` still contained data because the inode remained; `symlink.txt` failed because it referenced a now-missing pathname.
