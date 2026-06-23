# oh_archive.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rl123567-->
<!--Designer: @selina_jiang; @RainbowLLL-->
<!--Tester: @zheng1368-->
<!--Adviser: @jinqiuheng-->

## 概述

压缩解压缩模块接口定义，提供文件压缩解压、数据的流式压缩及解压，缓冲区压缩及解压的native接口。

**引用文件：** <filemanagement/archive/oh_archive.h>

**库：** liboharchive.so

**系统能力：** SystemCapability.FileManagement.File.FileIO

**起始版本：** 26.0.0

**相关模块：** [Archive](capi-archive.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Archive_StreamInfo](capi-archive-oh-archive-streaminfo.md) | OH_Archive_StreamInfo | 流式压缩/解压信息结构体。 |
| [OH_Archive_Stream_Config](capi-archive-oh-archive-stream-config.md) | OH_Archive_Stream_Config | 流压缩配置结构体。 |
| [ArchiveWriteCtx*](capi-archive-archivewritectx.md) | OH_Archive_Writer_Ctx | 文件压缩器的上下文结构体。 |
| [ArchiveReadCtx*](capi-archive-archivereadctx.md) | OH_Archive_Reader_Ctx | 文件解压器的上下文结构体。 |
| [ArchiveStreamWriteCtx*](capi-archive-archivestreamwritectx.md) | OH_Archive_StreamWrite_Ctx | 流式压缩器的上下文结构体。 |
| [ArchiveStreamReadCtx*](capi-archive-archivestreamreadctx.md) | OH_Archive_StreamRead_Ctx | 流式解压器的上下文结构体。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Archive_Format](#oh_archive_format) | OH_Archive_Format | 文件格式枚举。 |
| [OH_Archive_CompressMethod](#oh_archive_compressmethod) | OH_Archive_CompressMethod | 压缩方法枚举。 |
| [OH_Archive_OpenMode](#oh_archive_openmode) | OH_Archive_OpenMode | 文件打开模式枚举。 |
| [OH_Archive_ProgressType](#oh_archive_progresstype) | OH_Archive_ProgressType | 文件进度控制类型枚举。 |
| [OH_Archive_StreamChecksumAlg](#oh_archive_streamchecksumalg) | OH_Archive_StreamChecksumAlg | 用于校验和的哈希算法。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef OH_Archive_ProgressType (\*OH_Archive_ProgressHandlerWithData)(int32_t progress, void *userData)](#oh_archive_progresshandlerwithdata) | OH_Archive_ProgressHandlerWithData | 定义进度处理回调函数的类型。 |
| [typedef uint64_t (\*OH_Archive_Stream_OutputHandler)(const void* data, uint64_t size, void* userData)](#oh_archive_stream_outputhandler) | OH_Archive_Stream_OutputHandler | 用户自定义回调函数指针类型，用于处理压缩后的数据。 |
| [OH_Archive_Reader_Ctx OH_Archive_Reader_OpenFile(const char *infile)](#oh_archive_reader_openfile) | - | 打开文件进行读取。 |
| [OH_Archive_ErrCode OH_Archive_Reader_SetProgressHandlerWithData(OH_Archive_Reader_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData)](#oh_archive_reader_setprogresshandlerwithdata) | - | 设置文件解压器的进度回调函数及用户数据。 |
| [OH_Archive_ErrCode OH_Archive_Reader_ExtractAllFile(OH_Archive_Reader_Ctx arc, const char *outDir)](#oh_archive_reader_extractallfile) | - | 从归档中提取所有文件。 |
| [OH_Archive_ErrCode OH_Archive_Reader_Close(OH_Archive_Reader_Ctx arc)](#oh_archive_reader_close) | - | 关闭已打开的压缩文件并释放相关资源。 |
| [OH_Archive_Writer_Ctx OH_Archive_Writer_OpenFile(const char *outfile, OH_Archive_OpenMode openMode, OH_Archive_Format fmt)](#oh_archive_writer_openfile) | - | 创建并打开压缩文件。 |
| [OH_Archive_ErrCode OH_Archive_Writer_SetCompressMethod(OH_Archive_Writer_Ctx arc, OH_Archive_CompressMethod method, int32_t compressLevel)](#oh_archive_writer_setcompressmethod) | - | 设置压缩文件的压缩方法。 |
| [OH_Archive_ErrCode OH_Archive_Writer_SetProgressHandlerWithData(OH_Archive_Writer_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData)](#oh_archive_writer_setprogresshandlerwithdata) | - | 设置文件压缩器的进度回调函数及用户数据。 |
| [OH_Archive_ErrCode OH_Archive_Writer_Add(OH_Archive_Writer_Ctx arc, const char **infiles, uint64_t fileNum)](#oh_archive_writer_add) | - | 向归档中添加文件列表。 |
| [OH_Archive_ErrCode OH_Archive_Writer_Close(OH_Archive_Writer_Ctx arc)](#oh_archive_writer_close) | - | 关闭文件压缩器。该函数完成归档写入过程，将缓冲数据刷新到输出，并释放与文件压缩器的上下文结构体相关的资源。 |
| [uint64_t OH_Archive_BufferWriteCompressBound(OH_Archive_CompressMethod method, uint64_t sourceLen)](#oh_archive_bufferwritecompressbound) | - | 计算给定源数据长度的最大压缩后数据大小。 |
| [OH_Archive_ErrCode OH_Archive_BufferWrite(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method, int32_t compressLevel)](#oh_archive_bufferwrite) | - | 向缓冲区写入数据并进行压缩。 |
| [OH_Archive_ErrCode OH_Archive_BufferRead(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method)](#oh_archive_bufferread) | - | 从缓冲区读取数据并进行解压缩。 |
| [OH_Archive_StreamWrite_Ctx OH_Archive_StreamWrite_Create(OH_Archive_Stream_Config config)](#oh_archive_streamwrite_create) | - | 创建流式压缩的上下文结构体。 |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_Start(OH_Archive_StreamWrite_Ctx ctx, OH_Archive_Stream_OutputHandler outputHandler, void* userData)](#oh_archive_streamwrite_start) | - | 启动压缩任务，初始化用户回调函数和用户数据。 |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_SetCompressLevel(OH_Archive_StreamWrite_Ctx ctx, int32_t compressLevel)](#oh_archive_streamwrite_setcompresslevel) | - | 设置流压缩的压缩级别。 |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_Cancel(OH_Archive_StreamWrite_Ctx ctx)](#oh_archive_streamwrite_cancel) | - | 强制取消当前压缩操作。 |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_Update(OH_Archive_StreamWrite_Ctx ctx, const uint8_t* data, uint64_t size)](#oh_archive_streamwrite_update) | - | 提交压缩数据。 |
| [OH_Archive_ErrCode OH_Archive_StreamWrite_End(OH_Archive_StreamWrite_Ctx ctx, OH_Archive_StreamInfo *streamInfo)](#oh_archive_streamwrite_end) | - | 结束压缩，刷新所有剩余数据。 |
| [void OH_Archive_StreamWrite_Destroy(OH_Archive_StreamWrite_Ctx ctx)](#oh_archive_streamwrite_destroy) | - | 销毁压缩实例并释放相关资源。 |
| [OH_Archive_StreamRead_Ctx OH_Archive_StreamRead_Create(OH_Archive_Stream_Config config)](#oh_archive_streamread_create) | - | 创建流式解压的上下文结构体。 |
| [OH_Archive_ErrCode OH_Archive_StreamRead_Start(OH_Archive_StreamRead_Ctx ctx, OH_Archive_Stream_OutputHandler outputHandler, void* userData)](#oh_archive_streamread_start) | - | 启动解压缩任务，初始化用户回调函数和用户数据。 |
| [OH_Archive_ErrCode OH_Archive_StreamRead_Cancel(OH_Archive_StreamRead_Ctx ctx)](#oh_archive_streamread_cancel) | - | 强制取消当前解压操作。 |
| [OH_Archive_ErrCode OH_Archive_StreamRead_Update(OH_Archive_StreamRead_Ctx ctx, const uint8_t* data, uint64_t size)](#oh_archive_streamread_update) | - | 提交解压缩数据。 |
| [OH_Archive_ErrCode OH_Archive_StreamRead_End(OH_Archive_StreamRead_Ctx ctx, OH_Archive_StreamInfo *streamInfo)](#oh_archive_streamread_end) | - | 结束解压缩，刷新所有剩余数据并清理内存。 |
| [void OH_Archive_StreamRead_Destroy(OH_Archive_StreamRead_Ctx ctx)](#oh_archive_streamread_destroy) | - | 销毁解压缩实例并释放相关资源。 |

## 枚举类型说明

### OH_Archive_Format

```c
enum OH_Archive_Format
```

**描述**

文件格式枚举。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARCHIVE_FMT_ZIP = 0 | ZIP格式。<br>**起始版本：** 26.0.0 |

### OH_Archive_CompressMethod

```c
enum OH_Archive_CompressMethod
```

**描述**

压缩方法枚举。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARCHIVE_NO_COMPRESSION = 0 | 不压缩。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_COMPRESS_DEFLATE = 8 | DEFLATE压缩方法。<br>**起始版本：** 26.0.0 |

### OH_Archive_OpenMode

```c
enum OH_Archive_OpenMode
```

**描述**

文件打开模式枚举。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARCHIVE_OPEN_MODE_CREATE = 0 | 创建模式。<br>**起始版本：** 26.0.0 |

### OH_Archive_ProgressType

```c
enum OH_Archive_ProgressType
```

**描述**

文件进度控制类型枚举。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARCHIVE_PROGRESS_CONTINUE = 0 | 继续压缩/解压缩操作。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_PROGRESS_CANCEL = 1 | 取消压缩/解压缩操作。<br>**起始版本：** 26.0.0 |

### OH_Archive_StreamChecksumAlg

```c
enum OH_Archive_StreamChecksumAlg
```

**描述**

用于校验和的哈希算法。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARCHIVE_NO_CHECKSUM = 0 | 不额外计算哈希值。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_CRC32 = 1 | 使用CRC32（Cyclic Redundancy Check，循环冗余校验）计算校验和。<br>**起始版本：** 26.0.0 |


## 函数说明

### OH_Archive_ProgressHandlerWithData()

```c
typedef OH_Archive_ProgressType (*OH_Archive_ProgressHandlerWithData)(int32_t progress, void *userData)
```

**描述**

定义进度处理回调函数的类型。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t progress | 处理进度百分比，取值范围为[0, 100]。 |
| void \*userData | 指向用户自定义数据的指针，在调用回调时传入。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ProgressType](capi-oh-archive-h.md#oh_archive_progresstype) | <ul><br>         <li>OH_ARCHIVE_PROGRESS_CONTINUE - 继续当前压缩/解压缩操作。</li><br>         <li>OH_ARCHIVE_PROGRESS_CANCEL - 取消当前压缩/解压缩操作。</li><br>         </ul> |

### OH_Archive_Stream_OutputHandler()

```c
typedef uint64_t (*OH_Archive_Stream_OutputHandler)(const void* data, uint64_t size, void* userData)
```

**描述**

用户自定义回调函数指针类型，用于处理压缩后的数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const void\* data | 指向压缩数据的指针。 |
| uint64_t size | 压缩数据的长度。 |
| void\* userData | 用户自定义上下文，将在回调中传回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint64_t | 成功处理的字节数。 |

### OH_Archive_Reader_OpenFile()

```c
OH_Archive_Reader_Ctx OH_Archive_Reader_OpenFile(const char *infile)
```

**描述**

打开文件进行读取。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *infile | 源文件的路径，应用需要有读取权限，绝对路径长度需不超过4096bytes。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_Reader_Ctx](capi-archive-archivereadctx.md) | 返回文件读取器的上下文结构体，操作失败时返回NULL。 |

### OH_Archive_Reader_SetProgressHandlerWithData()

```c
OH_Archive_ErrCode OH_Archive_Reader_SetProgressHandlerWithData(OH_Archive_Reader_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData)
```

**描述**

设置文件解压器的进度回调函数及用户数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Reader_Ctx](capi-archive-archivereadctx.md) arc | 文件解压器上下文句柄。 |
| [OH_Archive_ProgressHandlerWithData](capi-oh-archive-h.md#oh_archive_progresshandlerwithdata) progressHandler | 用于处理进度更新的回调函数。 |
| void *userData | 用户处理进度回调时自定义的上下文数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_Reader_ExtractAllFile()

```c
OH_Archive_ErrCode OH_Archive_Reader_ExtractAllFile(OH_Archive_Reader_Ctx arc, const char *outDir)
```

**描述**

从归档中提取所有文件。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Reader_Ctx](capi-archive-archivereadctx.md) arc | 文件解压器上下文句柄。 |
| const char *outDir | 输出目录路径，应用需要有写入权限。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_Reader_Close()

```c
OH_Archive_ErrCode OH_Archive_Reader_Close(OH_Archive_Reader_Ctx arc)
```

**描述**

关闭已打开的压缩文件并释放相关资源。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Reader_Ctx](capi-archive-archivereadctx.md) arc | 文件解压器上下文句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_Writer_OpenFile()

```c
OH_Archive_Writer_Ctx OH_Archive_Writer_OpenFile(const char *outfile, OH_Archive_OpenMode openMode, OH_Archive_Format fmt)
```

**描述**

创建并打开压缩文件。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *outfile | 目标压缩文件的路径，应用需有写入权限，绝对路径长度需不超过4096bytes。 |
| [OH_Archive_OpenMode](capi-oh-archive-h.md#oh_archive_openmode) openMode | 文件打开模式。 |
| [OH_Archive_Format](capi-oh-archive-h.md#oh_archive_format) fmt | 归档格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_Writer_Ctx](capi-archive-archivewritectx.md) | 返回文件压缩器上下文句柄，操作失败时返回NULL。 |

### OH_Archive_Writer_SetCompressMethod()

```c
OH_Archive_ErrCode OH_Archive_Writer_SetCompressMethod(OH_Archive_Writer_Ctx arc, OH_Archive_CompressMethod method, int32_t compressLevel)
```

**描述**

设置压缩文件的压缩方法。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Writer_Ctx](capi-archive-archivewritectx.md) arc | 文件压缩器的上下文句柄。 |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | 压缩方法。 |
| int32_t compressLevel | 压缩等级。对于OH_ARCHIVE_COMPRESS_DEFLATE，压缩级别为0到9，默认等级为6。0表示不压缩，压缩等级越高，压缩率越高，速度越慢。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_Writer_SetProgressHandlerWithData()

```c
OH_Archive_ErrCode OH_Archive_Writer_SetProgressHandlerWithData(OH_Archive_Writer_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData)
```

**描述**

设置文件压缩器的进度回调函数及用户数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Writer_Ctx](capi-archive-archivewritectx.md) arc | 文件压缩器上下文句柄。 |
| [OH_Archive_ProgressHandlerWithData](capi-oh-archive-h.md#oh_archive_progresshandlerwithdata) progressHandler | 用于处理进度更新的回调函数。 |
| void *userData | 用户处理进度回调时自定义的上下文数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_Writer_Add()

```c
OH_Archive_ErrCode OH_Archive_Writer_Add(OH_Archive_Writer_Ctx arc, const char **infiles, uint64_t fileNum)
```

**描述**

向归档中添加文件列表。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Writer_Ctx](capi-archive-archivewritectx.md) arc | 文件压缩器上下文句柄。 |
| const char **infiles | 待压缩的文件。 |
| uint64_t fileNum | 文件数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_Writer_Close()

```c
OH_Archive_ErrCode OH_Archive_Writer_Close(OH_Archive_Writer_Ctx arc)
```

**描述**

关闭文件压缩器。该函数完成归档写入过程，将缓冲数据刷新到输出，并释放与文件压缩器的上下文结构体相关的资源。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Writer_Ctx](capi-archive-archivewritectx.md) arc | 文件压缩器上下文句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_BufferWriteCompressBound()

```c
uint64_t OH_Archive_BufferWriteCompressBound(OH_Archive_CompressMethod method, uint64_t sourceLen)
```

**描述**

计算给定源数据长度的最大压缩后数据大小。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | 压缩方法类型。 |
| uint64_t sourceLen | 待压缩源数据的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint64_t | 返回压缩后数据大小的最大值。 |

### OH_Archive_BufferWrite()

```c
OH_Archive_ErrCode OH_Archive_BufferWrite(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method, int32_t compressLevel)
```

**描述**

向缓冲区写入数据并进行压缩。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t *dstBuffer | 指向目标缓冲区的指针，用于存储压缩后的数据。 |
| uint64_t *dstSize | 指向目标缓冲区大小的指针，传入缓冲区大小，输出实际写入的大小。 |
| const uint8_t *srcBuffer | 指向包含待压缩数据的源缓冲区的指针。 |
| uint64_t srcSize | 源缓冲区数据的大小。 |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | 压缩方法类型。 |
| int32_t compressLevel | 压缩等级。对于OH_ARCHIVE_COMPRESS_DEFLATE，压缩级别为0到9，默认等级为6。0表示不压缩，压缩等级越高，压缩率越高，速度越慢。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_BufferRead()

```c
OH_Archive_ErrCode OH_Archive_BufferRead(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method)
```

**描述**

从缓冲区读取数据并进行解压缩。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint8_t *dstBuffer | 指向目标缓冲区的指针，用于存储解压缩后的数据。 |
| uint64_t *dstSize | 指向目标缓冲区大小的指针，传入缓冲区大小，输出实际解压缩后的大小。 |
| const uint8_t *srcBuffer | 指向包含待解压缩数据的源缓冲区的指针。 |
| uint64_t srcSize | 源缓冲区数据的大小。 |
| [OH_Archive_CompressMethod](capi-oh-archive-h.md#oh_archive_compressmethod) method | 解压缩方法类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamWrite_Create()

```c
OH_Archive_StreamWrite_Ctx OH_Archive_StreamWrite_Create(OH_Archive_Stream_Config config)
```

**描述**

创建流式压缩的上下文结构体。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Stream_Config](capi-archive-oh-archive-stream-config.md) config | 压缩配置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_StreamWrite_Ctx](capi-archive-archivestreamwritectx.md) | 返回流式压缩的上下文结构体。创建失败时返回NULL。 |

### OH_Archive_StreamWrite_Start()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_Start(OH_Archive_StreamWrite_Ctx ctx, OH_Archive_Stream_OutputHandler outputHandler, void* userData)
```

**描述**

启动压缩任务，初始化用户回调函数和用户数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamWrite_Ctx](capi-archive-archivestreamwritectx.md) ctx | 流式压缩的上下文结构体。 |
| [OH_Archive_Stream_OutputHandler](capi-oh-archive-h.md#oh_archive_stream_outputhandler) outputHandler | 用户自定义的压缩数据回调函数。 |
| void* userData | 用户自定义上下文，将在回调中传回。userData由调用方持有，在[OH_Archive_StreamWrite_End](capi-oh-archive-h.md#oh_archive_streamwrite_end)完成前必须保持有效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamWrite_SetCompressLevel()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_SetCompressLevel(OH_Archive_StreamWrite_Ctx ctx, int32_t compressLevel)
```

**描述**

设置流压缩的压缩级别。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamWrite_Ctx](capi-archive-archivestreamwritectx.md) ctx | 流式压缩的上下文结构体。 |
| int32_t compressLevel | 压缩等级。对于OH_ARCHIVE_COMPRESS_DEFLATE，压缩级别为0到9，默认等级为6。0表示不压缩，压缩等级越高，压缩率越高，速度越慢。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamWrite_Cancel()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_Cancel(OH_Archive_StreamWrite_Ctx ctx)
```

**描述**

强制取消当前压缩操作。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamWrite_Ctx](capi-archive-archivestreamwritectx.md) ctx | 流式压缩的上下文结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。取消成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamWrite_Update()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_Update(OH_Archive_StreamWrite_Ctx ctx, const uint8_t* data, uint64_t size)
```

**描述**

提交压缩数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamWrite_Ctx](capi-archive-archivestreamwritectx.md) ctx | 流式压缩的上下文结构体。 |
| const uint8_t* data | 待压缩的原始数据。 |
| uint64_t size | 待压缩数据的大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。压缩成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamWrite_End()

```c
OH_Archive_ErrCode OH_Archive_StreamWrite_End(OH_Archive_StreamWrite_Ctx ctx, OH_Archive_StreamInfo *streamInfo)
```

**描述**

结束压缩，刷新所有剩余数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamWrite_Ctx](capi-archive-archivestreamwritectx.md) ctx | 流式压缩的上下文结构体。 |
| [OH_Archive_StreamInfo](capi-archive-oh-archive-streaminfo.md) *streamInfo | 压缩信息，包括原始数据大小、压缩后数据大小和CRC32值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。压缩成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamWrite_Destroy()

```c
void OH_Archive_StreamWrite_Destroy(OH_Archive_StreamWrite_Ctx ctx)
```

**描述**

销毁压缩实例并释放相关资源。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamWrite_Ctx](capi-archive-archivestreamwritectx.md) ctx | 流式压缩的上下文结构体。 |

### OH_Archive_StreamRead_Create()

```c
OH_Archive_StreamRead_Ctx OH_Archive_StreamRead_Create(OH_Archive_Stream_Config config)
```

**描述**

创建流式解压的上下文结构体。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_Stream_Config](capi-archive-oh-archive-stream-config.md) config | 解压缩配置信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_StreamRead_Ctx](capi-archive-archivestreamreadctx.md) | 返回流式解压的上下文结构体。创建失败时返回NULL。 |

### OH_Archive_StreamRead_Start()

```c
OH_Archive_ErrCode OH_Archive_StreamRead_Start(OH_Archive_StreamRead_Ctx ctx, OH_Archive_Stream_OutputHandler outputHandler, void* userData)
```

**描述**

启动解压缩任务，初始化用户回调函数和用户数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamRead_Ctx](capi-archive-archivestreamreadctx.md) ctx | 流式解压的上下文结构体。 |
| [OH_Archive_Stream_OutputHandler](capi-oh-archive-h.md#oh_archive_stream_outputhandler) outputHandler | 用户自定义的解压缩数据回调函数。 |
| void* userData | 用户自定义上下文数据，将在回调中传回。userData由调用方拥有，在[OH_Archive_StreamRead_End](capi-oh-archive-h.md#oh_archive_streamread_end)完成前必须保持有效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamRead_Cancel()

```c
OH_Archive_ErrCode OH_Archive_StreamRead_Cancel(OH_Archive_StreamRead_Ctx ctx)
```

**描述**

强制取消当前解压操作。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamRead_Ctx](capi-archive-archivestreamreadctx.md) ctx | 流式解压的上下文结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。取消成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamRead_Update()

```c
OH_Archive_ErrCode OH_Archive_StreamRead_Update(OH_Archive_StreamRead_Ctx ctx, const uint8_t* data, uint64_t size)
```

**描述**

提交解压缩数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamRead_Ctx](capi-archive-archivestreamreadctx.md) ctx | 流式解压的上下文结构体。 |
| const uint8_t* data | 待解压缩的数据。 |
| uint64_t size | 数据大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamRead_End()

```c
OH_Archive_ErrCode OH_Archive_StreamRead_End(OH_Archive_StreamRead_Ctx ctx, OH_Archive_StreamInfo *streamInfo)
```

**描述**

结束解压缩，刷新所有剩余数据并清理内存。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamRead_Ctx](capi-archive-archivestreamreadctx.md) ctx | 流式解压的上下文结构体。 |
| [OH_Archive_StreamInfo](capi-archive-oh-archive-streaminfo.md) *streamInfo | 解压缩信息，包括原始数据大小、压缩后数据大小和CRC32值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Archive_ErrCode](capi-oh-archive-errcode-h.md#oh_archive_errcode) | 返回接口执行的结果。成功返回OH_ARCHIVE_OK。 |

### OH_Archive_StreamRead_Destroy()

```c
void OH_Archive_StreamRead_Destroy(OH_Archive_StreamRead_Ctx ctx)
```

**描述**

销毁解压缩实例并释放相关资源。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Archive_StreamRead_Ctx](capi-archive-archivestreamreadctx.md) ctx | 流式解压的上下文结构体。 |


