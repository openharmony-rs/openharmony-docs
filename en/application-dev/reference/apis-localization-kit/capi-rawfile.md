# rawfile

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:21:49.195Z pushedAt=2026-07-17T10:15:25.804Z -->

## Overview

Through the `rawfile` module, you can access the `rawfile` directory or resource files in the directory at the native layer, including traversing, opening, reading, seeking, and closing.<br> Traversing the directory: Open the `rawfile` directory, obtain the list of files under it, and iterate through the file names. Multi‑level directory traversal is supported.<br> Reading a file: Open a file, read file content, seek the file read/write position, obtain the file size and current offset, and obtain the file descriptor. Files larger than 2 GB are supported.

**Since**: 8

## Files

| Name| Description|
| -- | -- |
| [raw_file_manager.h](capi-raw-file-manager-h.md) | Provides functions for creating and releasing NativeResourceManager objects, as well as opening rawfiles and directories. |
| [raw_dir.h](capi-raw-dir-h.md) | Provides functions for rawfile directory operations, including traversing directories, obtaining the file count, obtaining file names, and closing directories. |
| [raw_file.h](capi-raw-file-h.md) | Provides the capabilities to operate on rawfiles, including reading files, obtaining the file length, obtaining the current offset, seeking to a specific position, obtaining the file descriptor, and closing the file descriptor. |