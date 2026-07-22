# postQueryAsUser（系统接口）

## 导入模块

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## postQueryAsUser

```TypeScript
function postQueryAsUser(userId:number, handle: AssetMap): Promise<void>
```

在指定用户空间中查询的后置处理，用于需要用户认证的关键资产（与[asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#prequeryasuser)函数成对出现）。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-asset-function postQueryAsUser(userId:number, handle: AssetMap): Promise<void>--><!--Device-asset-function postQueryAsUser(userId:number, handle: AssetMap): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。取值范围大于等于100。 |
| handle | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | 是 | 待处理的查询句柄，当前包含[asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#prequeryasuser)执行成功返回的挑战值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The caller doesn't have the permission. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [24000001](../errorcode-asset.md#24000001-关键资产服务不可用) | The ASSET service is unavailable. |
| [24000006](../errorcode-asset.md#24000006-系统内存不足) | Insufficient memory. |
| [24000010](../errorcode-asset.md#24000010-进程通信错误) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-包管理服务异常) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-账号系统服务异常) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-访问控制服务异常) | Calling the Access Token service failed. |

**示例：**

```TypeScript
import { asset } from '@kit.AssetStoreKit';

let userId: number = 100;
let handle: asset.AssetMap = new Map();
// 此处传入的new Uint8Array(32)仅作为示例，实际应传入asset.preQueryAsUser执行成功返回的挑战值
handle.set(asset.Tag.AUTH_CHALLENGE, new Uint8Array(32));
asset.postQueryAsUser(userId, handle).then(() => {
  console.info(`Succeeded in post-querying Asset from user space.`);
});

```

