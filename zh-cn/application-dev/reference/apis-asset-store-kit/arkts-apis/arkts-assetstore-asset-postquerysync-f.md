# postQuerySync

## 导入模块

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## postQuerySync

```TypeScript
function postQuerySync(handle: AssetMap): void
```

查询的后置处理，用于需要用户认证的关键资产。需与[asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md#prequerysync-1)函数成对出现。使用同步方式返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-asset-function postQuerySync(handle: AssetMap): void--><!--Device-asset-function postQuerySync(handle: AssetMap): void-End-->

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | 是 | 待处理的查询句柄，包含[asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md#prequerysync-1)执行成功返回的挑战值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

let handle: asset.AssetMap = new Map();
// 此处传入的new Uint8Array(32)仅作为示例，实际应传入asset.preQuerySync执行成功返回的挑战值。
handle.set(asset.Tag.AUTH_CHALLENGE, new Uint8Array(32));
asset.postQuerySync(handle)

```

