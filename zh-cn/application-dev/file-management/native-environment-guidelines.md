# 获取用户目录环境(C/C++)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @foryourself-->

## 场景介绍

[Environment](../reference/apis-core-file-kit/capi-oh-environment-h.md)提供了获取公共文件用户目录路径的能力，以支持三方应用在公共文件用户目录下进行文件访问操作。

## 约束限制

- 使用此接口，需确认设备具有以下系统能力：SystemCapability.FileManagement.File.Environment.FolderObtain。
- 此接口仅用作公共沙箱目录路径的获取接口，操作对应的公共目录及其子目录需获取通过弹窗授权方式向用户申请授予对应目录的权限，具体参考[访问控制-向用户申请授权](../security/AccessToken/request-user-authorization.md)。

## 接口说明

接口的详细说明，请参考[API参考](../reference/apis-core-file-kit/capi-oh-environment-h.md)。

| 接口名称 | 描述 |
| -------- | -------- |
| FileManagement_ErrCode OH_Environment_GetUserDownloadDir (char **result)| 获取用户Download目录沙箱路径。只支持2in1设备。 |
| FileManagement_ErrCode OH_Environment_GetUserDesktopDir (char **result) | 获取用户Desktop目录沙箱路径。只支持2in1设备。 |
| FileManagement_ErrCode OH_Environment_GetUserDocumentDir (char **result) | 获取用户Document目录沙箱路径。只支持2in1设备。 |

## 开发步骤

**在CMake脚本中链接动态库**

CMakeLists.txt中添加以下lib。

```txt
target_link_libraries(sample PUBLIC libohenvironment.so libhilog_ndk.z.so)
```

**添加头文件**

```c++
#include <cstdlib>
#include <filemanagement/environment/oh_environment.h>
#include <filemanagement/fileio/oh_fileio.h>
#include <hilog/log.h>
```

1. 调用OH_Environment_GetUserDownloadDir接口获取用户Download目录沙箱路径，在接口中使用malloc申请的内存需要在使用完后释放因此需要free对应的内存。示例代码如下所示：

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


2. 调用OH_Environment_GetUserDesktopDir接口获取用户Desktop目录沙箱路径，在接口中使用malloc申请的内存需要在使用完后释放因此需要free对应的内存。示例代码如下所示：

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


3. 调用OH_Environment_GetUserDocumentDir接口获取用户Document目录沙箱路径，在接口中使用malloc申请的内存需要在使用完后释放因此需要free对应的内存。示例代码如下所示：

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


4. 调用OH_Environment_GetUserDocumentDir接口获取用户Document目录沙箱路径，使用stat函数判断Document目录空间大小。示例代码如下所示：

   使用前需要引入如下头文件：
   ``` C++
   #include <sys/stat.h>
   ```
   <!--@[get_user_download_dir_size_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKEnvironmentSample/entry/src/main/cpp/napi_init.cpp)-->    
   
   ``` C++
   void GetUserDownloadDirSizeExample()
   {
       char *documentPath = nullptr;
       FileManagement_ErrCode ret = OH_Environment_GetUserDocumentDir(&documentPath);
       if (ret == 0) {
           OH_LOG_INFO(LOG_APP, "Document Path=%{public}s", documentPath);
           struct stat fileStat;
           int result = stat(documentPath, &fileStat);
           if (result == 0) {
               OH_LOG_INFO(LOG_APP, "Document Size=%{public}ld", fileStat.st_size);
           } else {
               OH_LOG_ERROR(LOG_APP, "GetDocumentSize fail, error code is %{public}ld", result);
           }
           free(documentPath);
       } else {
           OH_LOG_ERROR(LOG_APP, "GetDocumentPath fail, error code is %{public}d", ret);
       }
   }
   ```
