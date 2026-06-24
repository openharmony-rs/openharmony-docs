# postQuery

## postQuery

```TypeScript
function postQuery(handle: AssetMap): Promise<void>
```

查询的后置处理，用于需要用户认证的关键资产（与[asset.preQuery](arkts-assetstore-asset-prequery-f.md#preQuery-1)函数成对出现）。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | AssetMap | 是 | 待处理的查询句柄，包含[asset.preQuery](arkts-assetstore-asset-prequery-f.md#preQuery-1)执行成功返回的挑战值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [24000001](../../errorcode-universal.md#24000001-The) | The ASSET service is unavailable. |
| [24000006](../../errorcode-universal.md#24000006-Insufficient) | Insufficient memory. |
| [24000010](../../errorcode-universal.md#24000010-IPC) | IPC failed. |
| [24000011](../../errorcode-universal.md#24000011-Calling) | Calling the Bundle Manager service failed. |
| [24000012](../../errorcode-universal.md#24000012-Calling) | Calling the OS Account service failed. |
| [24000013](../../errorcode-universal.md#24000013-Calling) | Calling the Access Token service failed. |

**示例：**

```TypeScript
import { asset } from '@kit.AssetStoreKit';

let handle: asset.AssetMap = new Map();
// 此处传入的new Uint8Array(32)仅作为示例，实际应传入asset.preQuery执行成功返回的挑战值。
handle.set(asset.Tag.AUTH_CHALLENGE, new Uint8Array(32));
asset.postQuery(handle).then(() => {
  console.info(`Succeeded in post-querying Asset.`);
});

```

