# Obtaining the User Directory Environment (C/C++)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @foryourself-->

## When to Use

You can use [Environment](../reference/apis-core-file-kit/capi-oh-environment-h.md) to allow a third-party application to access files in a user directory.

## Constraints

- Before using the APIs of the **Environment** module, ensure that the device has SystemCapability.FileManagement.File.Environment.FolderObtain.
- The APIs provided by the **Environment** module can be used to obtain the application sandbox paths of the user directories. To operate the related directory and its subdirectories, user authorization is required via a dialog box. For details, see [Requesting User Authorization](../security/AccessToken/request-user-authorization.md).

## Available APIs

For details about the APIs, see [API Reference](../reference/apis-core-file-kit/capi-oh-environment-h.md).

| API| Description|
| -------- | -------- |
| FileManagement_ErrCode OH_Environment_GetUserDownloadDir (char **result)| Obtains the sandbox path of the **Download** directory. This function supports only 2-in-1 devices.|
| FileManagement_ErrCode OH_Environment_GetUserDesktopDir (char **result) | Obtains the sandbox path of the **Desktop** directory. This function supports only 2-in-1 devices.|
| FileManagement_ErrCode OH_Environment_GetUserDocumentDir (char **result) | Obtains the sandbox path of the **Documents** directory. This function supports only 2-in-1 devices.|

## How to Develop

**Adding the Dynamic Link Library**

Add the following library to **CMakeLists.txt**.

```txt
target_link_libraries(sample PUBLIC libohenvironment.so libhilog_ndk.z.so)
```

**Adding Header Files**

```c++
#include <cstdlib>
#include <filemanagement/environment/oh_environment.h>
#include <filemanagement/fileio/oh_fileio.h>
#include <hilog/log.h>
```

1. Call **OH_Environment_GetUserDownloadDir** to obtain the sandbox path of the user **Download** directory. The memory allocated must be released using **free()**. <br>Example:

<!--@[get_user_download_dir_path_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKEnvironmentSample/entry/src/main/cpp/napi_init.cpp)-->

``` C++
void GetUserDownloadDirPathExample()
{
    char *downloadPath = nullptr;
    FileManagement_ErrCode ret = OH_Environment_GetUserDownloadDir(&downloadPath);
    if (ret == 0) {
        OH_LOG_INFO(LOG_APP, "Download Path=%{public}s", downloadPath);
        free(downloadPath);
    } else {
        OH_LOG_ERROR(LOG_APP, "GetDownloadPath fail, error code is %{public}d", ret);
    }
}
```


2. Call **OH_Environment_GetUserDesktopDir** to obtain the sandbox path of the user **Desktop** directory. The memory allocated must be released using **free()**. <br>Example:

<!--@[get_user_desktop_dir_path_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKEnvironmentSample/entry/src/main/cpp/napi_init.cpp)-->

``` C++
void GetUserDesktopDirPathExample()
{
    char *desktopPath = nullptr;
    FileManagement_ErrCode ret = OH_Environment_GetUserDesktopDir(&desktopPath);
    if (ret == 0) {
        OH_LOG_INFO(LOG_APP, "Desktop Path=%{public}s", desktopPath);
        free(desktopPath);
    } else {
        OH_LOG_ERROR(LOG_APP, "GetDesktopPath fail, error code is %{public}d", ret);
    }
}
```


3. Call **OH_Environment_GetUserDocumentDir** to obtain the sandbox path of the user **Document** directory. The memory allocated must be released using **free()**. <br>Example:

<!--@[get_user_document_dir_path_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKEnvironmentSample/entry/src/main/cpp/napi_init.cpp)-->

``` C++
void GetUserDocumentDirPathExample()
{
    char *documentPath = nullptr;
    FileManagement_ErrCode ret = OH_Environment_GetUserDocumentDir(&documentPath);
    if (ret == 0) {
        OH_LOG_INFO(LOG_APP, "Document Path=%{public}s", documentPath);
        free(documentPath);
    } else {
        OH_LOG_ERROR(LOG_APP, "GetDocumentPath fail, error code is %{public}d", ret);
    }
}
```
