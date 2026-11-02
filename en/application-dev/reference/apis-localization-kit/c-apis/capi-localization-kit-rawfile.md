# rawfile

## Overview

Through the `rawfile` module, you can access the `rawfile` directory or resource files in the directory at the native layer, including traversing, opening, reading, seeking, and closing. <br>Traversing the directory: Open the `rawfile` directory, obtain the list of files under it, and iterate through the file names. Multi‑level directory traversal is supported. <br> Reading a file: Open a file, read file content, adjust the offset position of the file, obtain the file size and current offset, and obtain the file descriptor. Files larger than 2 GB are supported.

**System capability**: SystemCapability.Global.ResourceManager

**Since**: 8

## Files

| Name | Description |
| -- | -- |
| [raw_file_manager.h](capi-raw-file-manager-h.md) | This module allows you to create and release `NativeResourceManager` objects, and open rawfiles and directories. |
| [raw_dir.h](capi-raw-dir-h.md) | Provides functions related to `rawfile` directory operations, including directory traversal, file count retrieval, file name retrieval, and directory closing. |
| [raw_file.h](capi-raw-file-h.md) | Provides the capabilities to operate on rawfiles, including reading files, obtaining the file length, obtaining the current offset, seeking to a specific position, obtaining the file descriptor, and closing the file descriptor. |
