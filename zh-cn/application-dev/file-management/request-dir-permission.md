# 获取并使用公共目录
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @foryourself-->

## 通过 ArkTS 接口获取并访问公共目录

目录环境能力接口（[ohos.file.environment](../reference/apis-core-file-kit/js-apis-file-environment.md)）提供获取公共目录路径的能力，支持三方应用在公共文件用户目录下进行文件访问操作。

 **约束限制**
 - 使用此方式，需确认设备具有以下系统能力：SystemCapability.FileManagement.File.Environment.FolderObtain，当前仅支持2in1设备。
   ```ts
   if (!canIUse('SystemCapability.FileManagement.File.Environment.FolderObtain')) {
       console.error('this api is not supported on this device');
       return;
   }
   ```
 - 公共目录获取接口仅用于获取公共目录路径，不对公共目录访问权限进行校验。若需访问公共目录需申请对应的公共目录访问权限。三方应用需要访问公共目录时，需通过弹窗授权向用户申请授予 Download 目录权限、Documents 目录权限或 Desktop 目录权限，具体参考[访问控制-向用户申请授权](../security/AccessToken/request-user-authorization.md)。
   <!--RP1-->
   ```json
   "requestPermissions" : [
       "ohos.permission.READ_WRITE_DOWNLOAD_DIRECTORY",
       "ohos.permission.READ_WRITE_DOCUMENTS_DIRECTORY",
       "ohos.permission.READ_WRITE_DESKTOP_DIRECTORY",
   ]
   ```
   <!--RP1End-->

### 示例

1.获取公共目录路径。

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { Environment } from '@kit.CoreFileKit';

```
<!--@[get_user_dir_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/EnvironmentSample/entry/src/main/ets/pages/Index.ets)-->


2.以 Download 目录为例，访问 Download 目录下的文件。

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { Environment } from '@kit.CoreFileKit';
import { fileIo as fs } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

```
<!--@[read_user_download_dir_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/EnvironmentSample/entry/src/main/ets/pages/Index.ets)-->

3.以 Download 目录为例，保存文件到 Download 目录。

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { Environment } from '@kit.CoreFileKit';
import { fileIo as fs } from '@kit.CoreFileKit';

```
<!--@[write_user_download_dir_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/EnvironmentSample/entry/src/main/ets/pages/Index.ets)-->


## 通过 C/C++ 接口获取并使用公共目录

除了通过 ArkTS 访问公共目录的方式，也可通过 C/C++ 接口进行目录访问，具体可以参考 [Environment](../reference/apis-core-file-kit/capi-oh-environment-h.md)。

 **约束限制**
 - 使用此接口，需确认设备具有以下系统能力：SystemCapability.FileManagement.File.Environment.FolderObtain。
 - 三方应用需要访问公共目录时，需通过弹窗授权向用户申请授予 Download 目录权限、Documents 目录权限或 Desktop 目录权限，具体参考[访问控制-向用户申请授权](../security/AccessToken/request-user-authorization.md)。

### 接口说明

接口的详细说明，请参考[API参考](../reference/apis-core-file-kit/capi-oh-environment-h.md)。

| 接口名称                                                                 | 描述                           |
| ------------------------------------------------------------------------ | ------------------------------ |
| FileManagement_ErrCode OH_Environment_GetUserDownloadDir (char **result) | 获取用户Download目录沙箱路径。只支持2in1设备 |
| FileManagement_ErrCode OH_Environment_GetUserDesktopDir (char **result)  | 获取用户Desktop目录沙箱路径。只支持2in1设备  |
| FileManagement_ErrCode OH_Environment_GetUserDocumentDir (char **result) | 获取用户Document目录沙箱路径。只支持2in1设备 |

### 开发步骤

**在CMake脚本中链接动态库**

CMakeLists.txt中添加以下lib。

```txt
target_link_libraries(sample PUBLIC libohenvironment.so libhilog_ndk.z.so)
```

**添加头文件**

```c++
#include <filemanagement/environment/oh_environment.h>
#include <filemanagement/fileio/oh_fileio.h>
#include <hilog/log.h>
```

1.调用 OH_Environment_GetUserDownloadDir 接口获取用户 Download 目录沙箱路径，在接口中使用malloc申请的内存需要在使用完后释放因此需要free对应的内存。示例代码如下所示：

```c++
#include <cstdlib>

```
<!--@[get_user_download_dir_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKEnvironmentSample/entry/src/main/cpp/napi_init.cpp)-->

2.调用 OH_Environment_GetUserDownloadDir 接口获取用户 Download 目录沙箱路径，并查看 Download 目录下的文件。示例代码如下所示：

```c++
#include <cstdlib>
#include <dirent.h>

```
<!--@[scan_user_download_dir_path_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKEnvironmentSample/entry/src/main/cpp/napi_init.cpp)-->

3.调用 OH_Environment_GetUserDownloadDir 接口获取用户 Download 目录沙箱路径，并保存 temp.txt 到 Download 目录下。示例代码如下所示：

```c++
#include <fstream>

```
<!--@[write_user_download_dir_path_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/NDKEnvironmentSample/entry/src/main/cpp/napi_init.cpp)-->
