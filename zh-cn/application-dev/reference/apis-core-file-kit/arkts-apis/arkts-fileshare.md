# @ohos.fileshare

提供文件分享能力。

**起始版本：** 23

<!--Device-unnamed-declare namespace fileShare--><!--Device-unnamed-declare namespace fileShare-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

## 导入模块

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [activatePermission](arkts-corefile-fileshare-activatepermission-f.md) | 激活多个已持久化授权的文件或目录，使用Promise异步回调。 |
| [checkPersistentPermission](arkts-corefile-fileshare-checkpersistentpermission-f.md) | 校验所选择的多个文件或目录URI是否已持久化授权，使用Promise异步回调。 |
| [deactivatePermission](arkts-corefile-fileshare-deactivatepermission-f.md) | 取消激活多个已持久化授权的文件或目录，使用Promise异步回调。 |
| [persistPermission](arkts-corefile-fileshare-persistpermission-f.md) | 对所选择的多个文件或目录URI进行持久化授权，使用Promise异步回调。 |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f.md) | 对所选择的多个文件或目录URI取消持久化授权，使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [checkPathPermission](arkts-corefile-fileshare-checkpathpermission-f-sys.md) | 异步方法校验所选择的多个文件或目录是否有临时或持久化授权，使用Promise异步回调。 |
| [getPersistentPolicy](arkts-corefile-fileshare-getpersistentpolicy-f-sys.md) | 获取应用程序的持久化授权策略，使用Promise异步回调。 |
| [getSharedDirectoryInfo](arkts-corefile-fileshare-getshareddirectoryinfo-f-sys.md) | 获取所有应用捐献的沙箱目录。使用Promise异步回调。 |
| [grantSharedDirectoryPermission](arkts-corefile-fileshare-grantshareddirectorypermission-f-sys.md) | 授予应用捐献目录的临时访问权限。使用Promise异步回调。 |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md) | 为应用授予公共目录文件URI的临时访问权限，使用Callback异步回调。 |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md) | 为应用授予公共目录文件URI的临时访问权限，使用Promise异步回调。 |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md) | 给应用授予目标文件临时权限，使用Promise异步回调。 |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f-sys.md) | 撤销指定应用的全部持久化文件授权，使用Promise异步回调。 |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f-sys.md) | 撤销指定应用对URI的持久化授权，使用Promise异步回调。 |
| [revokeSharedDirectoryPermission](arkts-corefile-fileshare-revokeshareddirectorypermission-f-sys.md) | 撤销应用的捐献目录临时访问权限。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PathPolicyInfo](arkts-corefile-fileshare-pathpolicyinfo-i.md) | 需要查询的文件或目录的信息。 |
| [PolicyErrorResult](arkts-corefile-fileshare-policyerrorresult-i.md) | 授予或激活权限失败的URI策略结果。 |
| [PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md) | 需要授予或激活URI访问权限的策略信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SharedDirectoryInfo](arkts-corefile-fileshare-shareddirectoryinfo-i-sys.md) | 应用程序向系统捐献的目录信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [OperationMode](arkts-corefile-fileshare-operationmode-e.md) | 枚举授予或激活权限的URI访问模式。 |
| [PolicyErrorCode](arkts-corefile-fileshare-policyerrorcode-e.md) | 枚举授予或激活权限策略失败的URI对应的错误码。 |
| [PolicyType](arkts-corefile-fileshare-policytype-e.md) | 枚举所查询策略信息对应的授权模式。 |

