# getPersistentPolicy（系统接口）

## 导入模块

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## getPersistentPolicy

```TypeScript
function getPersistentPolicy(tokenID: int): Promise<Array<PolicyInfo>>
```

获取应用程序的持久化授权策略，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_FILE_ACCESS_PERSIST

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileShare-function getPersistentPolicy(tokenID: int): Promise<Array<PolicyInfo>>--><!--Device-fileShare-function getPersistentPolicy(tokenID: int): Promise<Array<PolicyInfo>>-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | int | 是 | 目标应用的访问令牌标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md)&gt;&gt; | Promise对象，返回应用的持久化策略信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid tokenID |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| 13900001 | Operation not permitted. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900011 | Out of memory |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function getPersistentPolicyExample() {
  try {
    let tokenID = 537688848; // 系统应用可以通过bundleManager.getApplicationInfo获取，普通应用可以通过bundleManager.getBundleInfoForSelf获取。
    fileShare.getPersistentPolicy(tokenID).then((result: Array<fileShare.PolicyInfo>) => {
      for (let policy of result) {
        console.info(`get persist policy URI: ${policy.uri}, operationMode: ${policy.operationMode}`);
      }
    }).catch((err: BusinessError) => {
      console.error(`get persist policy failed with error, Code: ${err.code}, message: ${err.message}`);
    });
  } catch (error) {
    console.error(`get persist policy failed with error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function getPersistentPolicyExample() {
  let tokenID = 537688848; // 系统应用可以通过bundleManager.getApplicationInfo获取。
  try {
    let policies = await fileShare.getPersistentPolicy(tokenID);
    console.info("get persist policy success, policies count: " + policies.length + ".");
    for (let policy of policies) {
      console.info("Policy uri: " + policy.uri + ", operationMode: " + policy.operationMode);
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error("get persist policy failed with error:" + JSON.stringify(err));
  }
}
```

