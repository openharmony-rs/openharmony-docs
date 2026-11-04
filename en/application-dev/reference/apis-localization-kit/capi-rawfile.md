# rawfile

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=d1ed4ce8d034cfba750330bf06dcd3a9995f70ce translatedAt=2026-11-03T13:33:29.872Z pushedAt=2026-11-04T08:47:59.717Z nl=1 -->

## Overview

The rawfile module allows developers to access the rawfile directory or resource files in the directory at the Native layer, including traversing, opening, reading, seeking, and closing.<br> Traverse a directory: open the rawfile directory, obtain the file list in the directory, traverse file names, and support multi-level directory traversal.<br> Read a file: open a rawfile, read the file content, seek the read/write position, obtain the file size and current offset, get the file descriptor, and support files larger than 2GB.

**Since**: 8
## Files

| Name| Description|
| -- | -- |
| [raw_file_manager.h](capi-raw-file-manager-h.md) | This module can be used to create and release NativeResourceManager objects, and open rawfile files and directories. |
| [raw_dir.h](capi-raw-dir-h.md) | Provides functions related to rawfile directory operations, including traversing directories, obtaining the number of files, obtaining file names, and closing directories. |
| [raw_file.h](capi-raw-file-h.md) | Provides capabilities for operating rawfile files, including reading files, obtaining the file length, obtaining the offset position, adjusting the offset position, obtaining file descriptors, and closing file descriptors. |
