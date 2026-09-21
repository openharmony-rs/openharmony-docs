# @ohos.zlib(Zip)

The **Zip** module provides APIs for file compression and decompression.

**Since:** 7

**System capability:** SystemCapability.BundleManager.Zlib

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [compressFile](arkts-basicservices-zlib-compressfile-f.md#compressfile) | Compresses a file. This API uses an asynchronous callback to return the result. |
| [compressFile](arkts-basicservices-zlib-compressfile-f.md#compressfile-1) | Compresses a file. This API uses a promise to return the result. |
| [compressFiles](arkts-basicservices-zlib-compressfiles-f.md) | Compresses multiple specified files. This API uses a promise to return the result. |
| [createChecksum](arkts-basicservices-zlib-createchecksum-f.md) | Creates this checksum object. This API uses a promise to return the result. |
| [createChecksumSync](arkts-basicservices-zlib-createchecksumsync-f.md) | Creates this checksum object. A checksum instance is returned upon a success. |
| [createGZip](arkts-basicservices-zlib-creategzip-f.md) | Creates this **GZip** object. This API uses a promise to return the result. |
| [createGZipSync](arkts-basicservices-zlib-creategzipsync-f.md) | Creates this **GZip** object. A **GZip** instance is returned upon a success. |
| [createZip](arkts-basicservices-zlib-createzip-f.md) | Creates this **Zip** instance. This API uses a promise to return the result. |
| [createZipSync](arkts-basicservices-zlib-createzipsync-f.md) | Creates this **Zip** instance. A **Zip** instance is returned upon a success. |
| [decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressfile) | Decompresses a file. This API uses an asynchronous callback to return the result. |
| [decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressfile-1) | Decompresses a file. This API uses an asynchronous callback to return the result. |
| [decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressfile-2) | Decompresses a file. This API uses a promise to return the result. |
| [getOriginalSize](arkts-basicservices-zlib-getoriginalsize-f.md) | Obtains the original size of a compressed file. This API uses a promise to return the result. |
| [unzipFile](arkts-basicservices-zlib-unzipfile-f.md) | Unzips a file. The execution result is returned after the decompression is complete. This API uses a promise to return the result. |
| [zipFile](arkts-basicservices-zlib-zipfile-f.md) | Zips a file. The execution result is returned after the compression is complete. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [Checksum](arkts-basicservices-zlib-checksum-i.md) | Checksum object. |
| [DecompressionOutputInfo](arkts-basicservices-zlib-decompressionoutputinfo-i.md) | Uncompress2 return value information. |
| [DeflatePendingOutputInfo](arkts-basicservices-zlib-deflatependingoutputinfo-i.md) | DeflatePending return value information. |
| [DictionaryOutputInfo](arkts-basicservices-zlib-dictionaryoutputinfo-i.md) | InflateGetDictionary and deflateGetDictionary return value information. |
| [GzErrorOutputInfo](arkts-basicservices-zlib-gzerroroutputinfo-i.md) | GzError return value information. |
| [GzHeader](arkts-basicservices-zlib-gzheader-i.md) | Gzip header information passed to and from zlib routines. |
| [GZip](arkts-basicservices-zlib-gzip-i.md) | Describes gzip-related APIs. |
| [Options](arkts-basicservices-zlib-options-i.md) | Defines options used to compress or decompress a ZIP file. |
| [Zip](arkts-basicservices-zlib-zip-i.md) | Defines the **Zip** instance. It provides APIs to zip or unzip data in Zlib, Deflate, or Gzip format. |
| [ZipOutputInfo](arkts-basicservices-zlib-zipoutputinfo-i.md) | Compression and decompression return value information. |
| [ZStream](arkts-basicservices-zlib-zstream-i.md) | Process all the information required for compression and decompression. |

### Enums

| Name | Description |
| --- | --- |
| [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md) | [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md) |
| [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) |
| [CompressMethod](arkts-basicservices-zlib-compressmethod-e.md) | The deflate compression method (the only one supported in this version). |
| [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md) | [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md) |
| [ErrorCode](arkts-basicservices-zlib-errorcode-e.md) | ErrorCode |
| [MemLevel](arkts-basicservices-zlib-memlevel-e.md) | [MemLevel](arkts-basicservices-zlib-memlevel-e.md) |
| [OffsetReferencePoint](arkts-basicservices-zlib-offsetreferencepoint-e.md) | Defines the reference point for the offset. |
| [ParallelStrategy](arkts-basicservices-zlib-parallelstrategy-e.md) | [ParallelStrategy](arkts-basicservices-zlib-parallelstrategy-e.md) |
| [PathSeparatorStrategy](arkts-basicservices-zlib-pathseparatorstrategy-e.md) | Defines **PathSeparatorStrategy**, a property of [Options](arkts-basicservices-zlib-options-i.md), used to specify the separator strategy for the file path in the compressed package specified for decompression. |
| [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md) | Return codes for the compression/decompression functions. |

### Types

| Name | Description |
| --- | --- |
| [InflateBackInputCallback](arkts-basicservices-zlib-inflatebackinputcallback-t.md) | A callback function for reading input data provided by a user. When the decompression process requires more input data, zlib will call this function. This function should read data from the data source to the buffer. |
| [InflateBackOutputCallback](arkts-basicservices-zlib-inflatebackoutputcallback-t.md) | The output data provided by the user is written into the callback function. Whenever decompressed data is ready for output, zlib calls this function to write the data from the buffer to the target location. |
