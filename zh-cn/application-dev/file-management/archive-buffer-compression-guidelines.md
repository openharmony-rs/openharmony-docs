# 缓冲区压缩解压缩(C/C++)

<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rl123567-->
<!--Designer: @selina_jiang; @RainbowLLL-->
<!--Tester: @zheng1368-->
<!--Adviser: @jinqiuheng-->

## 场景介绍

从API版本26.0.0开始，提供了缓冲区压缩解压缩能力，可以对内存中的整块数据进行一次性压缩或解压缩。主要适用于数据量较小且完整的场景，接口简单，操作快捷。

- 缓冲区压缩：对内存中的数据进行快速压缩，节省存储空间。
- 缓冲区解压缩：对已压缩的数据进行内存解压缩，还原原始数据。

## 接口说明

接口的详细说明，请参考[oh_archive.h](../reference/apis-core-file-kit/capi-oh-archive-h.md)。

| 接口名称 | 描述 |
| -------- | ---- |
| OH_Archive_BufferWriteCompressBound(OH_Archive_CompressMethod method, uint64_t sourceLen) | 计算缓冲区压缩所需输出缓冲区大小。 |
| OH_Archive_BufferWrite(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method, int32_t compressLevel) | 对缓冲区数据进行压缩。 |
| OH_Archive_BufferRead(uint8_t *dstBuffer, uint64_t *dstSize, const uint8_t *srcBuffer, uint64_t srcSize, OH_Archive_CompressMethod method) | 对缓冲区数据进行解压缩。 |

## 开发准备

**在CMake脚本中链接动态库**

CMakeLists.txt中添加以下lib。

```txt
target_link_libraries(sample PUBLIC liboharchive.so)
```

**添加头文件**

```c++
#include <filemanagement/archive/oh_archive.h>
```

## 开发步骤

### 缓冲区压缩

1. 调用OH_Archive_BufferWriteCompressBound计算输出缓冲区大小。压缩前先调用此接口获取输出缓冲区所需大小，确保输出缓冲区足够容纳压缩后的数据。
2. 调用OH_Archive_BufferWrite对缓冲区数据进行压缩。调用时需指定输入数据、输出缓冲区、数据长度、压缩算法和压缩级别。压缩后的实际数据大小通过dstSize参数返回。

<!--@[buffer_compress_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKCompressSample/entry/src/main/cpp/napi_init.cpp)-->

``` C++
static napi_value BufferCompress(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value argv[2] = {nullptr};
    napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);

    size_t inPathSize;
    size_t outPathSize;
    char inPathBuf[PATH_BUFFER_SIZE];
    char outPathBuf[PATH_BUFFER_SIZE];
    napi_get_value_string_utf8(env, argv[0], inPathBuf, sizeof(inPathBuf), &inPathSize);
    napi_get_value_string_utf8(env, argv[1], outPathBuf, sizeof(outPathBuf), &outPathSize);

    CreateRandomFile(inPathBuf, 1024 * 1024); // 1024K大小文件
    char *source = nullptr;
    uint64_t sourceLen;
    ReadFileData(inPathBuf, &source, &sourceLen);

    uint64_t destLen = 0;
    uint8_t *dest = nullptr;

    uint64_t bound = OH_Archive_BufferWriteCompressBound(OH_ARCHIVE_COMPRESS_DEFLATE, sourceLen);
    if (bound > MALLOC_THRESHOLD) {
        return nullptr;
    }
    dest = (uint8_t *)malloc(bound);
    if (dest == nullptr) {
        free(source);
        return nullptr;
    }
    destLen = bound;

    OH_Archive_ErrCode ret = OH_Archive_BufferWrite(dest, &destLen, reinterpret_cast<uint8_t *>(source), sourceLen,
                                                    OH_ARCHIVE_COMPRESS_DEFLATE, 0);

    free(source);
    free(dest);
    napi_value result = nullptr;
    napi_create_int32(env, ret, &result);
    return result;
}
```

### 缓冲区解压缩

准备输出缓冲区并调用OH_Archive_BufferRead解压缩数据。解压缩时需指定压缩数据缓冲区、输出缓冲区、数据长度和压缩算法，解压缩后的实际数据大小通过dstSize参数返回。建议压缩和解压缩使用相同的压缩算法参数。

<!--@[buffer_decompress_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKCompressSample/entry/src/main/cpp/napi_init.cpp)-->

``` C++
static napi_value BufferDecompress(napi_env env, napi_callback_info info)
{
    size_t argc = 0;
    napi_get_cb_info(env, info, &argc, nullptr, nullptr, nullptr);

    int ret;
    uint64_t dataSize = 1024 * 1024;
    uint8_t *srcBuffer = (uint8_t *)malloc(dataSize);
    if (srcBuffer == nullptr) {
        return nullptr;
    }

    for (size_t i = 0; i < dataSize; ++i) {
        srcBuffer[i] = static_cast<uint8_t>(TestRandomInt(0, 256)); // 小于256, byte范围内
    }

    uint64_t bound = OH_Archive_BufferWriteCompressBound(OH_ARCHIVE_COMPRESS_DEFLATE, dataSize);
    uint64_t compressedSize = bound;
    uint8_t *compressedBuffer = (uint8_t *)malloc(compressedSize);
    if (compressedBuffer == nullptr) {
        return nullptr;
    }
    ret = OH_Archive_BufferWrite(compressedBuffer, &compressedSize, srcBuffer, dataSize, OH_ARCHIVE_COMPRESS_DEFLATE,
                                 int32_t(6)); // 压缩等级为6
    uint8_t *decompressedBuffer = (uint8_t *)malloc(dataSize);
    if (decompressedBuffer == nullptr) {
        return nullptr;
    }
    uint64_t decompressedSize = dataSize;
    ret = OH_Archive_BufferRead(decompressedBuffer, &decompressedSize, compressedBuffer, compressedSize,
                                OH_ARCHIVE_COMPRESS_DEFLATE);
    bool isEqual = std::memcmp(decompressedBuffer, srcBuffer, dataSize) == 0;
    free(srcBuffer);
    free(compressedBuffer);
    free(decompressedBuffer);

    napi_value result = nullptr;
    napi_create_int32(env, !isEqual, &result);
    return result;
}
```

## 调测验证关键点

缓冲区压缩解压缩：验证压缩后再解压缩的数据与原始数据完全一致，无数据丢失。
