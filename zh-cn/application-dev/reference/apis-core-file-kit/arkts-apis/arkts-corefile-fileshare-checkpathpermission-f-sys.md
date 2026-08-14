# checkPathPermission（系统接口）

## checkPathPermission

```TypeScript
function checkPathPermission(tokenID: int, policies: Array<PathPolicyInfo>, policyType: PolicyType): Promise<Array<boolean>>
```

异步方法校验所选择的多个文件或目录是否有临时或持久化授权，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.CHECK_SANDBOX_POLICY

<!--Device-fileShare-function checkPathPermission(tokenID: int, policies: Array<PathPolicyInfo>, policyType: PolicyType): Promise<Array<boolean>>--><!--Device-fileShare-function checkPathPermission(tokenID: int, policies: Array<PathPolicyInfo>, policyType: PolicyType): Promise<Array<boolean>>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | int | 是 | 目标应用的访问令牌标识。 |
| policies | Array&lt;[PathPolicyInfo](arkts-corefile-fileshare-pathpolicyinfo-i.md)&gt; | 是 | 需要查询授权状态的路径策略信息数组。 |
| policyType | PolicyType | 是 | 要查询的授权类型，使用TEMPORARY_TYPE查询临时授权，使用PERSISTENT_TYPE查询持久化授权。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise对象，返回授权状态校验结果数组。返回true表示授权类型匹配policyType的查询类型，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application |
| 13900042 | Out of memory. |

## 示例

```TypeScript
import { fileShare } from '@kit.CoreFileKit';

async function checkPersistentPermissionExample() {
  try {
    let pathPolicyInfo1: fileShare.PathPolicyInfo = {
      path: '/storage/Users/currentUser/Documents/1.txt',
      operationMode: fileShare.OperationMode.READ_MODE,
    }
    let pathPolicyInfo2: fileShare.PathPolicyInfo = {
      path: '/storage/Users/currentUser/Desktop/2.txt',
      operationMode: fileShare.OperationMode.READ_MODE,
    }

    let policies: Array<fileShare.PathPolicyInfo> = [pathPolicyInfo1, pathPolicyInfo2];
    let policyType: fileShare.PolicyType = fileShare.PolicyType.PERSISTENT_TYPE;
    let tokenID = 537688848; // 系统应用可以通过bundleManager.getApplicationInfo获取，普通应用可以通过bundleManager.getBundleInfoForSelf获取。

    fileShare.checkPathPermission(tokenID, policies, policyType).then((result: Array<boolean>) => {
      for (let hasPermission of result) {
        console.info('check permission result is', hasPermission);
      }
    });
    console.info('checkPathPermission finish');
  } catch (error) {
    console.info(`checkPathPermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

