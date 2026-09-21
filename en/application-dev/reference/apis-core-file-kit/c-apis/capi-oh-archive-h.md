# oh_archive.h

## Overview

Provides archive APIs.

**Library**: liboharchive.so

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Related module**: [Archive](capi-archive.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Archive_StreamInfo](capi-archive-oh-archive-streaminfo.md) | OH_Archive_StreamInfo | Stream compression information structure. |
| [OH_Archive_Stream_Config](capi-archive-oh-archive-stream-config.md) | OH_Archive_Stream_Config | Stream compression configuration structure. |
| [ArchiveWriteCtx](capi-archive-archivewritectx.md) | *OH_Archive_Writer_Ctx | Archive Writer context structure. |
| [ArchiveReadCtx](capi-archive-archivereadctx.md) | *OH_Archive_Reader_Ctx | Archive Reader context structure. |
| [ArchiveStreamWriteCtx](capi-archive-archivestreamwritectx.md) | *OH_Archive_StreamWrite_Ctx | Archive streamWrite context structure. |
| [ArchiveStreamReadCtx](capi-archive-archivestreamreadctx.md) | *OH_Archive_StreamRead_Ctx | Archive streamRead context structure. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Archive_Format](#oh_archive_format) | OH_Archive_Format | Archive format enumeration. |
| [OH_Archive_CompressMethod](#oh_archive_compressmethod) | OH_Archive_CompressMethod | Archive compression method enumeration. |
| [OH_Archive_OpenMode](#oh_archive_openmode) | OH_Archive_OpenMode | Archive open mode enumeration. |
| [OH_Archive_ProgressType](#oh_archive_progresstype) | OH_Archive_ProgressType | Archive progress type enumeration. |
| [OH_Archive_StreamChecksumAlg](#oh_archive_streamchecksumalg) | OH_Archive_StreamChecksumAlg | Hash algorithm used for checksum. |

### Macro

| Name | Description |
| -- | -- |
| FILE_MANAGEMENT_ARCHIVE_OH_ARCHIVE_H | Provides archive APIs.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.FileManagement.File.FileIO |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef OH_Archive_ProgressType (\*OH_Archive_ProgressHandlerWithData)(int32_t progress, void *userData)](#oh_archive_progresshandlerwithdata) | OH_Archive_ProgressHandlerWithData | Defines a function pointer type OH_Archive_ProgressHandlerWithData for specifying the progress display handler. |
| [typedef uint64_t (\*OH_Archive_Stream_OutputHandler)(const void* data, uint64_t size, void* userData)](#oh_archive_stream_outputhandler) | OH_Archive_Stream_OutputHandler | Function pointer type for user-defined callback function to handle compressed data. |
| [OH_Archive_Reader_Ctx OH_Archive_Reader_OpenFile(const char *infile)](#oh_archive_reader_openfile) | - | Opens an archive file for reading. |
| [OH_Archive_ErrCode OH_Archive_Reader_SetProgressHandlerWithData(OH_Archive_Reader_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData)](#oh_archive_reader_setprogresshandlerwithdata) | - | Sets the progress callback function with user data for the archive reader. |
| [OH_Archive_ErrCode OH_Archive_Reader_ExtractAllFile(OH_Archive_Reader_Ctx arc, const char *outDir)](#oh_archive_reader_extractallfile) | - | Extract all files from the archive. |
| [OH_Archive_ErrCode OH_Archive_Reader_Close(OH_Archive_Reader_Ctx arc)](#oh_archive_reader_close) | - | Closes an opened archive file and releases associated resources. |
| [OH_Archive_Writer_Ctx OH_Archive_Writer_OpenFile(const char *outfile, OH_Archive_OpenMode openMode, OH_Archive_Format fmt)](#oh_archive_writer_openfile) | - | Creates and opens an archive file. |
| [OH_Archive_ErrCode OH_Archive_Writer_SetCompressMethod(OH_Archive_Writer_Ctx arc, OH_Archive_CompressMethod method, int32_t compressLevel)](#oh_archive_writer_setcompressmethod) | - | Set the compression method for the archive file |
| [OH_Archive_ErrCode OH_Archive_Writer_SetProgressHandlerWithData(OH_Archive_Writer_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData)](#oh_archive_writer_setprogresshandlerwithdata) | - | Set the compression progress function for the archive file. |
| [OH_Archive_ErrCode OH_Archive_Writer_Add(OH_Archive_Writer_Ctx arc, const char **infiles, uint64_t fileNum)](#oh_archive_writer_add) | - | Adds a list of files to the archive. |
| [OH_Archive_ErrCode OH_Archive_Writer_Close(OH_Archive_Writer_Ctx arc)](#oh_archive_writer_close) | - | Closes the archive writer. This function finalizes the archive writing process, flushes any buffered data to the output, and releases the resources associated with the archive context. |
| [uint64_t OH_Archive_BufferWriteCompressBound(OH_Archive_CompressMethod method, uint64_t sourceLen)](#oh_archive_bufferwritecompressbound) | - | Calculates the maximum compressed data size for a given source length. |
| [OH_Archive_ErrCode OH_Archive_BufferWrite(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method, int32_t compressLevel)](#oh_archive_bufferwrite) | - | Writes data to buffer and compresses it. |
| [OH_Archive_ErrCode OH_Archive_BufferRead(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method)](#oh_archive_bufferread) | - | Reads data from buffer and decompresses it. |
| [OH_Archive_StreamWrite_Ctx OH_Archive_StreamWrite_Create(OH_Archive_Stream_Config config)](#oh_archive_streamwrite_create) | - | Creates a compression instance. |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_Start(OH_Archive_StreamWrite_Ctx ctx, OH_Archive_Stream_OutputHandler outputHandler, void* userData)](#oh_archive_streamwrite_start) | - | Starts a compression task, initializing user callback function and user data. |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_SetCompressLevel(OH_Archive_StreamWrite_Ctx ctx, int32_t compressLevel)](#oh_archive_streamwrite_setcompresslevel) | - | Sets the compression level for StreamCompress. |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_Cancel(OH_Archive_StreamWrite_Ctx ctx)](#oh_archive_streamwrite_cancel) | - | Forces cancellation of the current blocking operation and wakes up all waiting threads. |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_Update(OH_Archive_StreamWrite_Ctx ctx, const uint8_t* data, uint64_t size)](#oh_archive_streamwrite_update) | - | Submits compression data. This interface will block when the memory pool is full. |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_End(OH_Archive_StreamWrite_Ctx ctx, OH_Archive_StreamInfo *streamInfo)](#oh_archive_streamwrite_end) | - | Ends the compression, flushes all remaining data, and cleans up memory. |
| [void OH_Archive_StreamWrite_Destroy(OH_Archive_StreamWrite_Ctx ctx)](#oh_archive_streamwrite_destroy) | - | Destroys the compression instance and releases associated resources. |
| [OH_Archive_StreamRead_Ctx OH_Archive_StreamRead_Create(OH_Archive_Stream_Config config)](#oh_archive_streamread_create) | - | Create a decompression instance |
| [OH_Archive_ErrCode OH_Archive_StreamRead_Start(OH_Archive_StreamRead_Ctx ctx, OH_Archive_Stream_OutputHandler outputHandler, void* userData)](#oh_archive_streamread_start) | - | Start a decompression task, initialize user callback function and user data |
| [OH_Archive_ErrCode OH_Archive_StreamRead_Cancel(OH_Archive_StreamRead_Ctx ctx)](#oh_archive_streamread_cancel) | - | Force cancellation of the current blocking operation and wake up all waiting threads |
| [OH_Archive_ErrCode OH_Archive_StreamRead_Update(OH_Archive_StreamRead_Ctx ctx, const uint8_t* data, uint64_t size)](#oh_archive_streamread_update) | - | Submit decompression data. This interface will block when the memory pool is full |
| [OH_Archive_ErrCode OH_Archive_StreamRead_End(OH_Archive_StreamRead_Ctx ctx, OH_Archive_StreamInfo *streamInfo)](#oh_archive_streamread_end) | - | End the decompression, flush all remaining data, and clean up memory |
| [void OH_Archive_StreamRead_Destroy(OH_Archive_StreamRead_Ctx ctx)](#oh_archive_streamread_destroy) | - | Destroy the decompression instance and release associated resources |

### Variable

| Name | Description |
| -- | -- |
| OH_Archive_ProgressType (*OH_Archive_ProgressHandlerWithData)(int32_t progress, void *userData) | Defines a function pointer type OH_Archive_ProgressHandlerWithData for specifying the progress display handler.<br>**Since**: 26.0.0 |
| uint64_t (*OH_Archive_Stream_OutputHandler)(const void* data, uint64_t size, void* userData) | Function pointer type for user-defined callback function to handle compressed data.<br>**Since**: 26.0.0 |

## Enum type description

### OH_Archive_Format

```c
enum OH_Archive_Format
```

**Description**

Archive format enumeration.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARCHIVE_FMT_ZIP = 0 | ZIP format.<br>**Since**: 26.0.0 |

### OH_Archive_CompressMethod

```c
enum OH_Archive_CompressMethod
```

**Description**

Archive compression method enumeration.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARCHIVE_NO_COMPRESSION = 0 | No compression.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_COMPRESS_DEFLATE = 8 | Deflate compression method.<br>**Since**: 26.0.0 |

### OH_Archive_OpenMode

```c
enum OH_Archive_OpenMode
```

**Description**

Archive open mode enumeration.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARCHIVE_OPEN_MODE_CREATE = 0 | Create mode.<br>**Since**: 26.0.0 |

### OH_Archive_ProgressType

```c
enum OH_Archive_ProgressType
```

**Description**

Archive progress type enumeration.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARCHIVE_PROGRESS_CONTINUE = 0 | Continue compression/decompression operation.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_PROGRESS_CANCEL = 1 | Cancel compression/decompression operation.<br>**Since**: 26.0.0 |

### OH_Archive_StreamChecksumAlg

```c
enum OH_Archive_StreamChecksumAlg
```

**Description**

Hash algorithm used for checksum.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARCHIVE_NO_CHECKSUM = 0 | Do not calculate the hash value additionally.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_CRC32 = 1 | Use CRC32 calculate the hash value.<br>**Since**: 26.0.0 |


## Function description

### OH_Archive_ProgressHandlerWithData()

```c
typedef OH_Archive_ProgressType (*OH_Archive_ProgressHandlerWithData)(int32_t progress, void *userData)
```

**Description**

Defines a function pointer type OH_Archive_ProgressHandlerWithData for specifying the progress display handler.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t progress | Processing progress percentage. |
| void \*userData | A pointer to user-defined data, passed when calling the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Archive_ProgressType](capi-oh-archive-h.md#oh_archive_progresstype) | Returns a compression/decompression Archive_ProgressType value.          [OH_ARCHIVE_PROGRESS_CONTINUE](capi-oh-archive-h.md#oh_archive_progresstype) - continue current compression/decompression operation.          [OH_ARCHIVE_PROGRESS_CANCEL](capi-oh-archive-h.md#oh_archive_progresstype) - cancel current compression/decompression operation. |

### OH_Archive_Stream_OutputHandler()

```c
typedef uint64_t (*OH_Archive_Stream_OutputHandler)(const void* data, uint64_t size, void* userData)
```

**Description**

Function pointer type for user-defined callback function to handle compressed data.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void\* userData | User-defined context that will be passed back in the callback. |
| const void\* data | Pointer to the compressed data. |
| uint64_t size | Length of the compressed data. |

**Returns**:

| Type | Description |
| -- | -- |
| uint64_t | Number of bytes successfully processed (typically equal to size for success). |

### OH_Archive_Reader_OpenFile()

```c
OH_Archive_Reader_Ctx OH_Archive_Reader_OpenFile(const char *infile)
```

**Description**

Opens an archive file for reading.

> **Note**:
>
> The returned context must be freed by calling OH_Archive_Reader_Close() to release allocated resources.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *infile | Path to the source archive file. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_Reader_Ctx | Returns a handle to the archive reader context, or NULL if the operation fails. |

### OH_Archive_Reader_SetProgressHandlerWithData()

```c
OH_Archive_ErrCode OH_Archive_Reader_SetProgressHandlerWithData(OH_Archive_Reader_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData)
```

**Description**

Sets the progress callback function with user data for the archive reader.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_Reader_Ctx arc | Handle to the archive reader context. |
| [OH_Archive_ProgressHandlerWithData](capi-oh-archive-h.md#oh_archive_progresshandlerwithdata) progressHandler | The callback function to handle progress updates. |
| void *userData | User data, passed when calling the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if successful.          [OH_ARCHIVE_OK](capi-oh-archive-errcode-h.md#oh_archive_errcode) - Execution successful          [OH_ARCHIVE_PARAM_ERROR](capi-oh-archive-errcode-h.md#oh_archive_errcode) - Invalid input parameters. |

### OH_Archive_Reader_ExtractAllFile()

```c
OH_Archive_ErrCode OH_Archive_Reader_ExtractAllFile(OH_Archive_Reader_Ctx arc, const char *outDir)
```

**Description**

Extract all files from the archive.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_Reader_Ctx arc | Handle to the archive reader context. |
| const char *outDir | Output directory path. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if successful. |

### OH_Archive_Reader_Close()

```c
OH_Archive_ErrCode OH_Archive_Reader_Close(OH_Archive_Reader_Ctx arc)
```

**Description**

Closes an opened archive file and releases associated resources.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_Reader_Ctx arc | Handle to the archive reader context. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if successful. |

### OH_Archive_Writer_OpenFile()

```c
OH_Archive_Writer_Ctx OH_Archive_Writer_OpenFile(const char *outfile, OH_Archive_OpenMode openMode, OH_Archive_Format fmt)
```

**Description**

Creates and opens an archive file.

> **Note**:
>
> The returned context must be freed by calling OH_Archive_Writer_Close() to release allocated resources.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *outfile | outfile Path to the destination archive file. |
| [OH_Archive_OpenMode](capi-oh-archive-h.md#oh_archive_openmode) openMode | Append mode. |
| [OH_Archive_Format](capi-oh-archive-h.md#oh_archive_format) fmt | Archive format. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_Writer_Ctx | Returns a handle to the archive writer context, or NULL if the operation fails. |

### OH_Archive_Writer_SetCompressMethod()

```c
OH_Archive_ErrCode OH_Archive_Writer_SetCompressMethod(OH_Archive_Writer_Ctx arc, OH_Archive_CompressMethod method, int32_t compressLevel)
```

**Description**

Set the compression method for the archive file

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_Writer_Ctx arc | Handle to the archive writer context. |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | Compression method. |
| int32_t compressLevel | Compression level. The value -1 indicates the default compression level. For OH_ARCHIVE_COMPRESS_DEFLATE, compression level is between 0 and 9. 1 gives best speed, 9 gives best compression, 0 gives no compression, and 6 is default. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns ARCHIVE_OK if successful.          [OH_ARCHIVE_OK](capi-oh-archive-errcode-h.md#oh_archive_errcode) - Execution successful.          [OH_ARCHIVE_PARAM_ERROR](capi-oh-archive-errcode-h.md#oh_archive_errcode) - Invalid input parameters. |

### OH_Archive_Writer_SetProgressHandlerWithData()

```c
OH_Archive_ErrCode OH_Archive_Writer_SetProgressHandlerWithData(OH_Archive_Writer_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData)
```

**Description**

Set the compression progress function for the archive file.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_Writer_Ctx arc | Handle to the archive writer context. |
| [OH_Archive_ProgressHandlerWithData](capi-oh-archive-h.md#oh_archive_progresshandlerwithdata) progressHandler | The callback function to handle progress updates. |
| void *userData | User data, passed when calling the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if successful.          [OH_ARCHIVE_OK](capi-oh-archive-errcode-h.md#oh_archive_errcode) - Execution successful          [OH_ARCHIVE_PARAM_ERROR](capi-oh-archive-errcode-h.md#oh_archive_errcode) - Invalid input parameters. |

### OH_Archive_Writer_Add()

```c
OH_Archive_ErrCode OH_Archive_Writer_Add(OH_Archive_Writer_Ctx arc, const char **infiles, uint64_t fileNum)
```

**Description**

Adds a list of files to the archive.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_Writer_Ctx arc | Handle to the archive writer context. |
| const char **infiles | Files to be compressed. |
| uint64_t fileNum | Number of files. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if successful. |

### OH_Archive_Writer_Close()

```c
OH_Archive_ErrCode OH_Archive_Writer_Close(OH_Archive_Writer_Ctx arc)
```

**Description**

Closes the archive writer. This function finalizes the archive writing process, flushes any buffered data to the output, and releases the resources associated with the archive context.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_Writer_Ctx arc | Handle to the archive writer context. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if successful. |

### OH_Archive_BufferWriteCompressBound()

```c
uint64_t OH_Archive_BufferWriteCompressBound(OH_Archive_CompressMethod method, uint64_t sourceLen)
```

**Description**

Calculates the maximum compressed data size for a given source length.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | Compression method type. |
| uint64_t sourceLen | Length of the source data to be compressed. |

**Returns**:

| Type | Description |
| -- | -- |
| uint64_t | Returns the maximum possible compressed data size. |

### OH_Archive_BufferWrite()

```c
OH_Archive_ErrCode OH_Archive_BufferWrite(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method, int32_t compressLevel)
```

**Description**

Writes data to buffer and compresses it.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *dstBuffer | Pointer to the destination buffer for storing compressed data. |
| uint64_t *dstSize | Pointer to the destination buffer size, input the buffer size, output the actual written size. |
| const uint8_t *srcBuffer | Pointer to the source buffer containing data to be compressed. |
| uint64_t srcSize | Size of the source buffer data. |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | Compression method type. |
| int32_t compressLevel | Compression level. The value -1 indicates the default compression level. For OH_ARCHIVE_COMPRESS_DEFLATE, compression level is between 0 and 9. 1 gives best speed, 9 gives best compression, 0 gives no compression, and 6 is default. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns error code, returns OH_ARCHIVE_OK on success. |

### OH_Archive_BufferRead()

```c
OH_Archive_ErrCode OH_Archive_BufferRead(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method)
```

**Description**

Reads data from buffer and decompresses it.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t *dstBuffer | Pointer to the destination buffer for storing decompressed data. |
| uint64_t *dstSize | Pointer to the destination buffer size, input the buffer size, output the actual decompressed size. |
| const uint8_t *srcBuffer | Pointer to the source buffer containing data to be decompressed. |
| uint64_t srcSize | Size of the source buffer data. |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | Decompression method type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns error code, returns OH_ARCHIVE_OK on success. |

### OH_Archive_StreamWrite_Create()

```c
OH_Archive_StreamWrite_Ctx OH_Archive_StreamWrite_Create(OH_Archive_Stream_Config config)
```

**Description**

Creates a compression instance.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Archive_Stream_Config](capi-archive-oh-archive-stream-config.md) config | Compression configuration. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_StreamWrite_Ctx | Returns a pointer to the context compression, or NULL if creation fails. |

### OH_Archive_StreamWrite_Start()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_Start(OH_Archive_StreamWrite_Ctx ctx, OH_Archive_Stream_OutputHandler outputHandler, void* userData)
```

**Description**

Starts a compression task, initializing user callback function and user data.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamWrite_Ctx ctx | Compression context. |
| [OH_Archive_Stream_OutputHandler](capi-oh-archive-h.md#oh_archive_stream_outputhandler) outputHandler | Callback function for compressed data, user-defined. |
| void* userData | User-defined context that will be passed back in the callback. The userData is owned by the caller and must remain valid until OH_Archive_StreamWrite_End is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if successful. |

### OH_Archive_StreamWrite_SetCompressLevel()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_SetCompressLevel(OH_Archive_StreamWrite_Ctx ctx, int32_t compressLevel)
```

**Description**

Sets the compression level for StreamCompress.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamWrite_Ctx ctx | Compression context. |
| int32_t compressLevel | Compression level. For OH_ARCHIVE_COMPRESS_DEFLATE, compression level is between 0 and 9. 1 gives best speed, 9 gives best compression, 0 gives no compression, and 6 is default. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if successful. |

### OH_Archive_StreamWrite_Cancel()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_Cancel(OH_Archive_StreamWrite_Ctx ctx)
```

**Description**

Forces cancellation of the current blocking operation and wakes up all waiting threads.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamWrite_Ctx ctx | Compression context. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if cancellation is successful. |

### OH_Archive_StreamWrite_Update()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_Update(OH_Archive_StreamWrite_Ctx ctx, const uint8_t* data, uint64_t size)
```

**Description**

Submits compression data. This interface will block when the memory pool is full.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamWrite_Ctx ctx | Compression context. |
| const uint8_t* data | Original data to be compressed. |
| uint64_t size | Size of the data to be compressed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if compression is successful. |

### OH_Archive_StreamWrite_End()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_End(OH_Archive_StreamWrite_Ctx ctx, OH_Archive_StreamInfo *streamInfo)
```

**Description**

Ends the compression, flushes all remaining data, and cleans up memory.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamWrite_Ctx ctx | Compression context. |
| [OH_Archive_StreamInfo](capi-archive-oh-archive-streaminfo.md) *streamInfo | Compression information including original data size, compressed data size, and CRC32 value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns the error code. Returns OH_ARCHIVE_OK if compression is successful. |

### OH_Archive_StreamWrite_Destroy()

```c
void OH_Archive_StreamWrite_Destroy(OH_Archive_StreamWrite_Ctx ctx)
```

**Description**

Destroys the compression instance and releases associated resources.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamWrite_Ctx ctx | Compression context to be destroyed. |

### OH_Archive_StreamRead_Create()

```c
OH_Archive_StreamRead_Ctx OH_Archive_StreamRead_Create(OH_Archive_Stream_Config config)
```

**Description**

Create a decompression instance

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Archive_Stream_Config](capi-archive-oh-archive-stream-config.md) config | Decompression configuration information |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_StreamRead_Ctx | Returns a pointer to the decompression context, or NULL if creation fails |

### OH_Archive_StreamRead_Start()

```c
OH_Archive_ErrCode OH_Archive_StreamRead_Start(OH_Archive_StreamRead_Ctx ctx, OH_Archive_Stream_OutputHandler outputHandler, void* userData)
```

**Description**

Start a decompression task, initialize user callback function and user data

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamRead_Ctx ctx | Decompression context |
| [OH_Archive_Stream_OutputHandler](capi-oh-archive-h.md#oh_archive_stream_outputhandler) outputHandler | User-defined callback function for handling decompressed data |
| void* userData | User-defined context data that will be passed back in the callback. The userData is owned by the caller and must remain valid until OH_Archive_StreamRead_End is complete. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns error code, returns OH_ARCHIVE_OK if successful |

### OH_Archive_StreamRead_Cancel()

```c
OH_Archive_ErrCode OH_Archive_StreamRead_Cancel(OH_Archive_StreamRead_Ctx ctx)
```

**Description**

Force cancellation of the current blocking operation and wake up all waiting threads

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamRead_Ctx ctx | Decompression context |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns error code, returns OH_ARCHIVE_OK if cancellation is successful |

### OH_Archive_StreamRead_Update()

```c
OH_Archive_ErrCode OH_Archive_StreamRead_Update(OH_Archive_StreamRead_Ctx ctx, const uint8_t* data, uint64_t size)
```

**Description**

Submit decompression data. This interface will block when the memory pool is full

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamRead_Ctx ctx | Decompression context |
| const uint8_t* data | Data to be decompressed |
| uint64_t size | Size of the data |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns error code, returns OH_ARCHIVE_OK if successful |

### OH_Archive_StreamRead_End()

```c
OH_Archive_ErrCode OH_Archive_StreamRead_End(OH_Archive_StreamRead_Ctx ctx, OH_Archive_StreamInfo *streamInfo)
```

**Description**

End the decompression, flush all remaining data, and clean up memory

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamRead_Ctx ctx | Decompression context |
| [OH_Archive_StreamInfo](capi-archive-oh-archive-streaminfo.md) *streamInfo | Decompression information including original data size, compressed data size, and CRC32 value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Archive_ErrCode | Returns error code, returns OH_ARCHIVE_OK if successful |

### OH_Archive_StreamRead_Destroy()

```c
void OH_Archive_StreamRead_Destroy(OH_Archive_StreamRead_Ctx ctx)
```

**Description**

Destroy the decompression instance and release associated resources

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Archive_StreamRead_Ctx ctx | Decompression context to be destroyed |


