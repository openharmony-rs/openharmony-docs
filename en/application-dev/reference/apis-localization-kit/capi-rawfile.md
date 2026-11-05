# rawfile

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-04T04:07:29.294Z pushedAt=2026-11-04T10:13:14.905Z nl=1 -->

## Overview

Through the rawfile module, developers can access the rawfile directory or resource files in the directory on the native layer, including traversing, opening, reading, seeking, and closing.<br> Traverse a directory: Open the rawfile directory, obtain the file list in the directory, traverse file names, and support multi-level directory traversal.<br> Read a file: Open a rawfile, read the file content, seek the file read/write position, obtain the file size and current offset, obtain the file descriptor, and support large files over 2 GB.

**Since**: 8
## Files

| Name| Description|
| -- | -- |
| [raw_file_manager.h](capi-raw-file-manager-h.md) | Creates and releases a NativeResourceManager object, and opens rawfile files and directories. |
| [raw_dir.h](capi-raw-dir-h.md) | Provides functions for rawfile directory operations, including traversing a directory, obtaining the number of files, obtaining file names, and closing a directory. |
| [raw_file.h](capi-raw-file-h.md) | Provides capabilities for operating rawfile files, including reading a file, obtaining the file length, obtaining the offset, adjusting the offset, obtaining the file descriptor, and closing the file descriptor. |
