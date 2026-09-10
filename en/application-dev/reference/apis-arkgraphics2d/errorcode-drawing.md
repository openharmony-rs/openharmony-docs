# Drawing and Display Error Codes

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4e50217bab17d31bea74ffd285654969c1ffbf06 translatedAt=2026-08-24T09:19:50.171Z pushedAt=2026-08-31T11:58:44.069Z -->

The graphics drawing and display error codes define the exceptions that may occur during 2D graphics drawing, including error identifiers for parameter verification and file operations. Developers can use these error codes to quickly locate and troubleshoot drawing-related issues, improving development and debugging efficiency. They apply to scenarios where ArkGraphics 2D is used for graphics drawing.

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 25900001 Abnormal Parameter Value

**Error Message**

Parameter error. Possible causes: Incorrect parameter range.

**Description**

This error code is reported when the parameter value exceeds the allowable range.

**Possible Causes**

The parameter value exceeds the valid range. For example, an enumerated value exceeds the defined range.

**Solution**

Pass parameter values that meet the requirements in the API.

## 25900002 File Not Found

**Error Message**

File not found. The specified file does not exist or the path is incorrect.

**Description**

The file is not found. The specified file does not exist or the path is incorrect.

**Possible Causes**

1. The file path is incorrect or the file does not exist.

2. The file path case is incorrect.

**Solution**

1. Check whether the file path format is correct and confirm that the file exists at the specified location.

2. Check whether the file path case exactly matches the actual file name.

## 25900003 Failed to Open the File

**Error Message**

Failed to open file. The file cannot be opened due to permission or I/O issues.

**Description**

Failed to open the file. The file cannot be opened due to permission or I/O issues.

**Possible Causes**

1. The user does not have the permission to read the file.

2. The file is occupied by another process.

**Solution**

1. Verify the file permission settings and confirm that the current user has read permission on the file.

2. Ensure that the file is not occupied by another process.

## 25900004 Failed to Locate the File

**Error Message**

File seek failed. The system failed to reposition the file read pointer.

**Description**

Failed to locate the file. The system cannot reposition the file read pointer.

**Possible Causes**

The file type (such as pipe and socket) does not support random access.

**Solution**

Ensure that the file type supports random access.

## 25900005 Failed to Obtain the File Size

**Error Message**

Failed to get the file size. The system was unable to obtain the file size information.

**Description**

Failed to obtain the file size. The system cannot obtain the file size.

**Possible Causes**

The file type (such as pipe and socket) does not support size query.

**Solution**

Ensure that the file type supports size query.

## 25900006 Failed to Read the File

**Error Message**

Failed to read file. The file could not be read completely or contains unreadable data.

**Description**

Failed to read the file. The file cannot be completely read or contains unreadable data.

**Possible Causes**

1. An I/O error occurs in the file.

2. The memory is insufficient.

**Solution**

1. Ensure that the disk or storage device is normal.

2. Ensure that the memory is sufficient for reading.

## 25900007 Empty File

**Error Message**

Empty file. The specified file is empty.

**Description**

The specified file is empty.

**Possible Causes**

The file size is 0 bytes.

**Solution**

Check the file size attribute and confirm that the file content is not empty (the size is greater than 0 bytes).

## 25900008 File Damaged

**Error Message**

Corrupted file. The file content is invalid, damaged, or an index out of bounds occurs when accessing TTC/OTC files, making it impossible to parse.

**Description**

The file is damaged. The file content is invalid or damaged, or an index out of bounds occurs when accessing TTC/OTC files, making it impossible to parse.

**Possible Causes**

1. The file format is incorrect.

2. The file content is damaged.

3. The TTC/OTC file index is out of bounds.

**Solution**

1. Ensure that the file format is correct.

2. Ensure that the file content is normal.

3. Ensure that the index is within the supported range of TTC/OTC.