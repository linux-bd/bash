# [Recursively copy file to every subfolders](https://unix.stackexchange.com/questions/94207/recursively-add-a-file-to-all-sub-directories)
```sh
find . -type d -exec cp file {} \;
```
