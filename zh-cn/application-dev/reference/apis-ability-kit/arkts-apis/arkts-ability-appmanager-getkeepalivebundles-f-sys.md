# getKeepAliveBundles（系统接口）

## getKeepAliveBundles

```TypeScript
function getKeepAliveBundles(type: KeepAliveAppType, userId?: number): Promise<Array<KeepAliveBundleInfo>>
```

获取指定用户下指定类型的保活应用信息。该应用信息由[KeepAliveBundleInfo](arkts-ability-appmanager-keepalivebundleinfo-i-sys.md#KeepAliveBundleInfo)定义。使用Promise异步回调。
该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。
**需要权限**：ohos.permission.MANAGE_APP_KEEP_ALIVE

**起始版本：** 14

**需要权限：** ohos.permission.MANAGE_APP_KEEP_ALIVE

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | KeepAliveAppType | 是 | 表示要查询的保活应用类型。 |
| userId | number | 否 | 表示要设置保活应用所属的用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;KeepAliveBundleInfo&gt;&gt; | Promise对象，返回用户保活应用信息的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId = 100;
let type: appManager.KeepAliveAppType = appManager.KeepAliveAppType.THIRD_PARTY;
try {
  appManager.getKeepAliveBundles(type, userId).then((data) => {
    console.info(`getKeepAliveBundles success, data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`getKeepAliveBundles fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] getKeepAliveBundles error: ${code}, ${message}`);
}

```

