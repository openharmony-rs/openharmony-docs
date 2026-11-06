# Accessing Application Files (C/C++)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=36751a8fb1b3914f9a180e1bf038d8da0174fbd0 translatedAt=2026-10-29T10:30:53.821Z pushedAt=2026-10-29T10:30:53.821Z nl=1 -->

## When to Use

The FileIO module provides some basic file operation capabilities. For other capabilities, refer to the [libc standard library](../reference/native-lib/musl.md) and [C++ standard library](../reference/native-lib/cpp.md).

## Constraints

Before performing file operations, ensure that the URI or path passed in is correct and valid.

## Available APIs

For details about the APIs, see [FileIO](../reference/apis-core-file-kit/capi-oh-fileio-h.md).

| Name | Description|
| -------- | -------- |
| FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location) | Obtains the location of a file.|
| enum FileIO_FileLocation FileIO_FileLocation | Enumerates the file locations.|
| enum FileManagement_ErrCode FileManagement_ErrCode | Enumerates the error codes used in the **FileIO** module.|

## How to Develop

**Linking the Dynamic Library in the CMake Script**

Add the following library to **CMakeLists.txt**.

```txt
target_link_libraries(sample PUBLIC libohfileio.so)
```

**Adding the Header File**

```c++
#include <cstdio>
#include <cstring>
#include <filemanagement/fileio/oh_fileio.h>
```

Call **OH_FileIO_GetFileLocation** to obtain the location of a file. <br>Example:

<!--@[get_file_location_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKAppFileSample/entry/src/main/cpp/napi_init.cpp)-->    

``` C++
void GetFileLocationExample(char *uri)
{
    FileIO_FileLocation location;
    int uriLength = static_cast<int>(strlen(uri));
    FileManagement_ErrCode ret = OH_FileIO_GetFileLocation(uri, uriLength, &location);
    if (ret == 0) {
        if (location == FileIO_FileLocation::LOCAL) {
            printf("Succeeded in getting file location, this file is on local.");
        } else if (location == FileIO_FileLocation::CLOUD) {
            printf("Succeeded in getting file location, this file is on cloud.");
        } else if (location == FileIO_FileLocation::LOCAL_AND_CLOUD) {
            printf("Succeeded in getting file location, this file is on  local and cloud.");
        }
    } else {
        printf("Failed to get file location, error code is %d", ret);
    }
}
```
