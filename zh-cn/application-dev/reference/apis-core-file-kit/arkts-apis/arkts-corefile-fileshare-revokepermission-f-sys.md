# revokePermission（系统接口）

## revokePermission

```TypeScript
function revokePermission(tokenID: int): Promise<void>
```

撤销指定应用的全部持久化文件授权，使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.REVOKE_FILE_ACCESS_PERSIST

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileShare-function revokePermission(tokenID: int): Promise<void>--><!--Device-fileShare-function revokePermission(tokenID: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | int | 是 | 目标应用的访问令牌标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid tokenID |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900001 | Operation not permitted. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokeAllPermissionExample() {
  try {
    let tokenID = 537688848; // 系统应用可以通过bundleManager.getApplicationInfo获取，普通应用可以通过bundleManager.getBundleInfoForSelf获取。
    fileShare.revokePermission(tokenID).then(() => {
      console.info('revoke persist permission successfully.');
    }).catch((err: BusinessError) => {
      console.error(`revoke persist permission failed, Code: ${err.code}, message: ${err.message}`);
    });
  } catch (error) {
    console.error(`revoke persist permission failed error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokePermissionExample() {
  let tokenID = 537688848; // 系统应用可以通过bundleManager.getApplicationInfo获取。
  try {
    await fileShare.revokePermission(tokenID);
    console.info("revoke persist permission successfully.");
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error("revoke persist permission failed with error:" + JSON.stringify(err));
  }
}
```


## revokePermission

```TypeScript
function revokePermission(tokenID: int, policies: Array<PolicyInfo>): Promise<void>
```

撤销指定应用对URI的持久化授权，使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.REVOKE_FILE_ACCESS_PERSIST

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileShare-function revokePermission(tokenID: int, policies: Array<PolicyInfo>): Promise<void>--><!--Device-fileShare-function revokePermission(tokenID: int, policies: Array<PolicyInfo>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | int | 是 | 目标应用的访问令牌标识。 |
| policies | Array&lt;[PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md)&gt; | 是 | 需要撤销持久化授权的URI策略信息数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid tokenID |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types; 3.Invalid policy size. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900001 | Operation not permitted. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900011 | Out of memory |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokeSpecificPermissionExample() {
  try {
    let tokenID = 537688848; // 系统应用可以通过bundleManager.getApplicationInfo获取，普通应用可以通过bundleManager.getBundleInfoForSelf获取。
    let policyInfo: fileShare.PolicyInfo = {
      uri: 'file://docs/storage/Users/currentUser/Documents/1.txt',
      operationMode: fileShare.OperationMode.READ_MODE | fileShare.OperationMode.WRITE_MODE,
    };
    let policies: Array<fileShare.PolicyInfo> = [policyInfo];
    fileShare.revokePermission(tokenID, policies).then(() => {
      console.info('revoke persist permission successfully.');
    }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
      console.error(`revoke persist permission failed. Code: ${err.code}, message: ${err.message}`);
      if (err.code === 13900001 && err.data) {
        for (let i = 0; i < err.data.length; i++) {
          console.error(`error code: ${JSON.stringify(err.data[i].code)}`);
          console.error(`error URI: ${JSON.stringify(err.data[i].uri)}`);
          console.error(`error reason: ${JSON.stringify(err.data[i].message)}`);
        }
      }
    });
  } catch (error) {
    console.error(`revokePermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokePermissionWithPoliciesExample() {
  let tokenID = 537688848; // 系统应用可以通过bundleManager.getApplicationInfo获取。
  let uri = "file://docs/storage/Users/currentUser/Documents/1.txt";
  let policyInfo: fileShare.PolicyInfo = {
    uri: uri,
    operationMode: fileShare.OperationMode.CREATE_MODE | fileShare.OperationMode.READ_MODE,
  };
  let policies: Array<fileShare.PolicyInfo> = [policyInfo];

  try {
    await fileShare.revokePermission(tokenID, policies);
    console.info("revoke persist permission with policies successfully.");
  } catch (error) {
    let err: BusinessError<Array<fileShare.PolicyErrorResult>> = error as BusinessError<Array<fileShare.PolicyErrorResult>>;
    console.error("revoke persist permission failed with error message: " + err.message + ", error code: " + err.code);
    if (err && err.data && err.code == 13900001) {
      const data = err.data!;
      for (let i = 0; i < data.length; i++) {
        console.error("error code : " + data[i].code);
        console.error("error uri : " + data[i].uri);
        console.error("error reason : " + data[i].message);
      }
    }
  }
}
```

