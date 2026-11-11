# zlib Error Codes
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b14ac3cf36ce096474879f8a233b4331a09dac0e translatedAt=2026-11-10T04:00:32.702Z pushedAt=2026-11-10T06:10:47.131Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 900001 Invalid Source File

**Error Message**

The input source file is invalid.

**Description**

This error code is reported when the source file passed in the **compressFile()** or **decompressFile()** API is invalid.

**Possible Causes**

1. The input source file path is empty, contains a relative path, or is not a valid application sandbox path.
2. The input source file does not exist, or the application does not have the access permission to the source file.
3. When calling the decompressFile API, the source file cannot be opened.

**Solution**

1. Check the source file path.

   Ensure that the path is not empty, does not contain relative paths such as "../", and is located in the correct application sandbox path.

2. Check whether the source file exists and whether the application has the read permission on the source file.

3. When calling the decompressFile API, check whether the source file can be opened normally and ensure that the file extension is .zip.

## 900002 Invalid Destination File

**Error Message**

The input destination file is invalid.

**Description**

This error code is reported when the destination file passed in the **compressFile()** or **decompressFile()** API is invalid.

**Possible Causes**

1. The input destination path is empty, contains a relative path, or is not a valid application sandbox path.
2. When calling the decompressFile API, the input destination path does not exist or is not a directory.
3. The application does not have the write permission on the destination directory.
4. The output directory cannot be created, or the target file cannot be created or opened during decompression.

**Solution**

1. Check the target path.

   Ensure that the path is not empty, does not contain relative paths such as "../", and is located in the correct application sandbox path.

2. Before calling the decompressFile API, check whether the target path is an existing directory. If the directory does not exist, create it first.

3. Check whether the application has the write permission on the target directory.

4. Check whether there are abnormal entries in the target directory that prevent the creation of a directory or file with the same name, and ensure that the target directory has sufficient available storage space.

## 900003 Source File in Incorrect Format or Damaged

**Error Message**

The input source file is not in ZIP format or is damaged.

**Description**

This error code is reported when the format of the source file is incorrect or the source file is damaged when the **decompressFile** API is called.

**Possible Causes**

1. The input source file is not in ZIP format, or the file is incomplete or corrupted.
2. The entry paths in the ZIP file contain relative paths such as "../".
3. The entry information or entry data of the ZIP file is corrupted, causing the entry to fail to be read or decompressed.

**Solution**

1. Check whether the source file is a valid and complete ZIP file.

   If the source file is downloaded over the network, ensure that the file download is complete before calling the decompressFile API. If the file is corrupted, regenerate or obtain the ZIP file.

2. Check the entry paths in the ZIP file to ensure that the paths do not contain relative paths such as "../". If such entries exist, remove the related entries and regenerate the ZIP file.

3. Check whether each entry in the ZIP file can be read and decompressed normally. If an entry is corrupted, regenerate or obtain the ZIP file.

## 17800002 Incorrect File or Access Mode

**Error Message**

No such file or access mode error.

**Description**

This error code is reported when the input file path, file descriptor, or file access mode is incorrect when the **gzopen** or **gzdopen** API is called.

**Possible Causes**

1. When the **gzopen** API is called, the input file path or file access mode is incorrect.
2. When the **gzdopen** API is called, the input file descriptor or file access mode is incorrect.

**Solution**

1. Check whether the .gz file path or file descriptor is correct. If a .gz file is created, ensure that the file access is in compression mode (such as **w** or **wb**).
2. Check whether the file access mode is **w**, **wb**, **r**, **rb**, **a**, and **ab**.

## 17800004 Compressed or Decompressed Flow Error

**Error Message**

Compression or decompression stream error, which may be caused by an initialization error in the zlib stream structure or a modified structure.

**Description**

This error code is reported when an error occurs in compression or decompression stream when the **deflate** or **inflate** API is called.

**Possible Causes**

1. When the **deflate** or **inflate** API is called, the **deflateInit** or **inflateInit** API is not used to initialize the compression or decompression stream.
2. When the **gzsetparams**, **gzclose**, or **gzflush** API is called, the input refresh mode is incorrect. When the API for opening a .gz file is called, the input file access mode is incorrect.

**Solution**

1. Before calling the **deflate** or **inflate** API, use the **deflateInit** or **inflateInit** API to initialize the compression or decompression stream.
2. Check whether the API for opening the .gz file is not called or fails to be called.
3. Check whether the input access mode matches the API when the API for opening the .gz file is called. For example, **gzprintf** is a compression API. When the API for opening a .gz file is called, the input access mode must be the compression mode (such as **w** or **wb**).
4. Check whether the input enum parameter is correct.

## 17800005 Incorrect Input Data

**Error Message**

The input data is incorrect. For example, the data does not conform to the zlib compression format, the compressed data is corrupted, or the data is not compressed.

**Description**

This error code is reported when the input data is incorrect when the **uncompress** or **uncompress2** API is called.

**Possible Causes**

When the **uncompress** or **uncompress2** API is called, the **compress** API is not used for compression.

**Solution**

Use the **compress** API to compress the file before using the **uncompress2** or **uncompress** API to decompress the file.

## 17800006 Memory Allocation Failure

**Error Message**

Memory allocation failed.

**Description**

This error code is reported when the memory allocation fails when the **gzclose** or **gzclosew** API is called.

**Possible Causes**

The **gzsetparams** API is called before calling the **gzclose** or **gzclosew** API. As a result, an incorrect compression level or compression strategy is passed in.

**Solution**

Check whether the **gzsetparams** API is called and pass in the correct compression level and compression strategy.

## 17800007 Incorrect Input Buffer

**Error Message**

The input buffer is incorrect, and the output buffer is too small to accommodate the compressed or decompressed data.

**Description**

This error code is reported when the input buffer is incorrect when the **compress**, **compress2**, **uncompress**, or **uncompress2** API is called.

**Possible Causes**

1. When the **uncompress** or **uncompress2** API is called, the input buffer size is greater than the output buffer size after decompression.
2. When the **compress** or **compress2** API is called, the input buffer size is greater than the output buffer size after compression.
3. When the **compress**, **compress2**, **uncompress**, or **uncompress2** API is called, the input buffer size is 0.

**Solution**

Increase the size of the corresponding buffer.

## 17800009 Internal Structure Error

**Error Message**

Internal structure error.

**Description**

This error code is reported when the input parameter is incorrect when the **gzputc**, **gzwrite**, or **gzread** API is called, or when the input file access mode is incorrect when the API for opening the .gz file is called.

**Possible Causes**

1. The API for opening the .gz file is not called or fails to be called.
2. When the API for opening the .gz file is called, the input file access mode is incorrect.
3. When the **gzwrite** API is called, the length of the input uncompressed byte is 0.
4. When the **gzfwrite** or **gzfread** API is called, the size or number of input data blocks is 0.
5. When the **gzprintf** API is called, the input format descriptor and plain text are empty strings.
6. When the **gzgets** API is called, the input **ArrayBuffer** is empty.
7. When the **gzgetc** API is called, the .gz file is empty.

**Solution**

1. Check whether the API for opening the .gz file is not called or fails to be called.
2. Check whether the input access mode matches the API when the API for opening the .gz file is called. For example, **gzgetc** is a decompression API, so the input access mode should be decompression mode (such **r** or **rb**).
3. Check whether the input parameter is correct.
