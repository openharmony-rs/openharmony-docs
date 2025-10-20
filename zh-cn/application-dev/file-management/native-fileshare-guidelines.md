# 授权持久化(C/C++)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie; @hongjin-li_admin-->
<!--Designer: @chenxi0605; @JerryH1011-->
<!--Tester: @leiyuqian-->
<!--Adviser: @foryourself-->

## 场景介绍

应用通过Picker获取临时授权，临时授权在应用退出后或者设备重启后会清除。如果应用重启或者设备重启后需要直接访问之前已访问过的文件，则对文件进行[持久化授权](file-persistPermission.md#场景介绍)。FileShare提供了支持基于uri的文件及目录授予持久化权限、权限激活、权限查询等方法。

## 接口说明

接口的详细介绍请参见[API参考](../reference/apis-core-file-kit/capi-oh-file-share-h.md)。

| 接口名称 | 描述 |
| -------- | -------- |
| OH_FileShare_PersistPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum) | 对所选择的多个文件或目录uri持久化授权。 |
| OH_FileShare_RevokePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum) | 对所选择的多个文件或目录uri取消持久化授权。 |
| OH_FileShare_ActivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum) | 使能多个已经永久授权过的文件或目录uri。 |
| OH_FileShare_DeactivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum) | 取消使能授权过的多个文件或目录uri。 |
| OH_FileShare_CheckPersistentPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, bool **result, unsigned int *resultNum) | 校验所选择的多个文件或目录uri的持久化权限结果。 |
| OH_FileShare_ReleasePolicyErrorResult(FileShare_PolicyErrorResult *errorResult, unsigned int resultNum) | 释放FileShare_PolicyErrorResult内存。 |

## 约束与限制

- 使用文件分享的相关接口，需确认设备具有以下系统能力：SystemCapability.FileManagement.AppFileService.FolderAuthorization。

- 在调用文件分享的相关接口前，需要申请权限："ohos.permission.FILE_ACCESS_PERSIST"，申请方式请参考[访问控制-申请应用权限](../security/AccessToken/determine-application-mode.md)。

## 开发步骤

以下步骤描述了如何使用`FileShare`提供的Native API接口。

**添加动态链接库**

CMakeLists.txt中添加以下lib。

```txt
target_link_libraries(sample PUBLIC libohfileshare.so)
```

**头文件**

```c++
#include <filemanagement/fileshare/oh_file_share.h>
#include <iostream>
```
1. 创建FileShare_PolicyInfo实例,调用OH_FileShare_PersistPermission接口，设置uri的持久化授权，接口入参policyNum最大上限为500。
<!-- @[persist_permission_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/UserFile/FileShareDevelopment_C/entry/src/main/cpp/napi_init.cpp) -->
2. 调用OH_FileShare_ActivatePermission接口，激活启用已授权过的uri，接口入参policyNum最大上限为500。
<!-- @[activate_permission_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/UserFile/FileShareDevelopment_C/entry/src/main/cpp/napi_init.cpp) -->
3. 调用OH_FileShare_DeactivatePermission接口，停止已启用授权过uri的访问权限，接口入参policyNum最大上限为500。
<!-- @[deactivate_permission_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/UserFile/FileShareDevelopment_C/entry/src/main/cpp/napi_init.cpp) -->
4. 调用OH_FileShare_RevokePermission接口，撤销已经授权的uri持久化权限，接口入参policyNum最大上限为500。
<!-- @[revoke_permission_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/UserFile/FileShareDevelopment_C/entry/src/main/cpp/napi_init.cpp) -->
5. 调用OH_FileShare_CheckPersistentPermission接口，检查uri持久化权限，接口入参policyNum最大上限为500。
<!-- @[check_persistent_permission_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/UserFile/FileShareDevelopment_C/entry/src/main/cpp/napi_init.cpp) -->