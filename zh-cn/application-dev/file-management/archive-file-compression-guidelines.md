# 文件归档类压缩解压缩(C/C++)

<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rl123567-->
<!--Designer: @selina_jiang; @RainbowLLL-->
<!--Tester: @zheng1368-->
<!--Adviser: @jinqiuheng-->

## 场景介绍

从API版本26.0.0开始支持文件归档类压缩解压缩，适用于将多个文件和目录打包为一个归档文件，或者从归档文件中提取文件到指定目录的场景。主要应用场景包括：

- 将多个文件或目录打包压缩为一个归档文件，便于存储和传输。
- 解压缩归档文件，将压缩包中的文件提取到指定目录。

## 约束限制

- 压缩解压缩接口的输入输出路径均为沙箱路径，具体请参考[应用沙箱目录](app-sandbox-directory.md)。
- 当前仅支持ZIP格式的归档文件。

## 接口说明

接口的详细说明，请参考[oh_archive.h](../reference/apis-core-file-kit/capi-oh-archive-h.md)。

### 归档文件压缩接口

| 接口名称 | 描述 |
| -------- | ---- |
| OH_Archive_Writer_OpenFile(const char *outFile, OH_Archive_OpenMode openMode, OH_Archive_Format fmt) | 打开归档文件并创建写入器。 |
| OH_Archive_Writer_SetCompressMethod(OH_Archive_Writer_Ctx arc, OH_Archive_CompressMethod method, int32_t compressLevel) | 设置归档压缩算法及压缩级别。 |
| OH_Archive_Writer_SetProgressHandlerWithData(OH_Archive_Writer_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData) | 设置归档写入进度回调。 |
| OH_Archive_Writer_Add(OH_Archive_Writer_Ctx arc, const char **infiles, uint64_t fileNum) | 向归档文件中添加文件或目录。 |
| OH_Archive_Writer_Close(OH_Archive_Writer_Ctx arc) | 关闭归档写入器。 |

### 归档文件解压缩接口

| 接口名称 | 描述 |
| -------- | ---- |
| OH_Archive_Reader_OpenFile(const char *inFile) | 打开归档文件并创建读取器。 |
| OH_Archive_Reader_SetProgressHandlerWithData(OH_Archive_Reader_Ctx arc, OH_Archive_ProgressHandlerWithData progressHandler, void *userData) | 设置归档解压缩进度回调。 |
| OH_Archive_Reader_ExtractAllFile(OH_Archive_Reader_Ctx arc, const char *outDir) | 解压缩归档文件中的所有文件到指定目录。 |
| OH_Archive_Reader_Close(OH_Archive_Reader_Ctx arc) | 关闭归档读取器。 |

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

### 归档文件压缩

1. 调用OH_Archive_Writer_OpenFile创建归档写入器。需指定输出文件路径、打开模式（如OH_ARCHIVE_OPEN_MODE_CREATE）和归档格式（如OH_ARCHIVE_FMT_ZIP）。
2. （可选）调用OH_Archive_Writer_SetCompressMethod设置压缩算法和压缩级别。默认使用DEFLATE压缩算法，压缩级别为6，开发者可根据需要调整。
3. （可选）调用OH_Archive_Writer_SetProgressHandlerWithData设置进度回调，用于获取压缩进度信息。
4. 调用OH_Archive_Writer_Add向归档中添加文件或目录，支持同时添加多个文件或目录。
5. 调用OH_Archive_Writer_Close完成归档写入并释放资源。压缩完成后必须调用此接口释放资源。

<!--@[zip_file_compress_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKCompressSample/entry/src/main/cpp/napi_init.cpp)-->

``` C++
static napi_value ZipFileCompress(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value argv[2] = {nullptr};
    napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);

    size_t inPathSize;
    size_t zipPathSize;
    char inPathBuf[PATH_BUFFER_SIZE];
    char zipPathBuf[PATH_BUFFER_SIZE];
    napi_get_value_string_utf8(env, argv[0], inPathBuf, sizeof(inPathBuf), &inPathSize);
    napi_get_value_string_utf8(env, argv[1], zipPathBuf, sizeof(zipPathBuf), &zipPathSize);

    std::string content = "test content这是测试内容Hello, hello!第一行数据";
    std::string file(inPathBuf);
    std::ofstream stdfile(file, std::ios::out | std::ios::trunc);
    if (stdfile.is_open()) {
        stdfile << content;
        stdfile.close();
    }
    std::vector<const char *> srcFiles;
    srcFiles.push_back(file.c_str());

    int ret;
    OH_Archive_Writer_Ctx arc = OH_Archive_Writer_OpenFile(zipPathBuf, OH_ARCHIVE_OPEN_MODE_CREATE, OH_ARCHIVE_FMT_ZIP);
    ret = OH_Archive_Writer_SetCompressMethod(arc, OH_ARCHIVE_COMPRESS_DEFLATE, int32_t(6)); // 压缩等级为6

    OH_Archive_ProgressHandlerWithData progressHandlerFunc = ProgressHandler;
    ret = OH_Archive_Writer_SetProgressHandlerWithData(arc, progressHandlerFunc, nullptr);
    ret = OH_Archive_Writer_Add(arc, srcFiles.data(), srcFiles.size());
    ret = OH_Archive_Writer_Close(arc);
    napi_value retVal = nullptr;
    napi_create_int32(env, ret, &retVal);
    return retVal;
}
```

### 归档文件解压缩

1. 调用OH_Archive_Reader_OpenFile打开归档文件并创建读取器。需指定ZIP文件路径。
2. （可选）调用OH_Archive_Reader_SetProgressHandlerWithData设置解压缩进度回调。
3. 调用OH_Archive_Reader_ExtractAllFile将归档文件解压缩到指定目录。解压缩后的文件将保持原有的目录结构。
4. 调用OH_Archive_Reader_Close关闭归档读取器。解压缩完成后必须调用此接口释放资源。

<!--@[zip_file_decompress_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKCompressSample/entry/src/main/cpp/napi_init.cpp)-->

``` C++
static napi_value ZipFileDecompress(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value argv[3] = {nullptr};
    napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);

    size_t inPathSize;
    size_t zipPathSize;
    size_t outDirSize;
    char inPathBuf[PATH_BUFFER_SIZE];
    char zipPathBuf[PATH_BUFFER_SIZE];
    char outDirBuf[PATH_BUFFER_SIZE];
    napi_get_value_string_utf8(env, argv[0], inPathBuf, sizeof(inPathBuf), &inPathSize);
    napi_get_value_string_utf8(env, argv[1], zipPathBuf, sizeof(zipPathBuf), &zipPathSize);
    napi_get_value_string_utf8(env, argv[2], outDirBuf, sizeof(outDirBuf), &outDirSize); // 第2个参数

    int ret = ArchiveCompressFile(inPathBuf, zipPathBuf);
    OH_Archive_Reader_Ctx ctx = OH_Archive_Reader_OpenFile(zipPathBuf);
    int userData[2] = {0};
    ret = OH_Archive_Reader_SetProgressHandlerWithData(ctx, ProgressHandler, (void *)userData);
    ret = OH_Archive_Reader_ExtractAllFile(ctx, outDirBuf);
    ret = OH_Archive_Reader_Close(ctx);

    napi_value result = nullptr;
    napi_create_int32(env, ret, &result);
    return result;
}
```

## 调测验证关键点

- 归档文件压缩：验证生成的ZIP文件可以使用标准解压缩工具打开，文件内容完整，目录结构正确。
- 归档文件解压缩：验证解压缩后的文件和目录结构与压缩前一致，文件内容无损坏。
