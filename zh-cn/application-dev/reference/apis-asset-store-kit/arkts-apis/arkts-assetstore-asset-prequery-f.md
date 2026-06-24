# preQuery

## preQuery

```TypeScript
function preQuery(query: AssetMap): Promise<Uint8Array>
```

查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.query](arkts-assetstore-asset-query-f.md#query-1)和[asset.postQuery](arkts-assetstore-asset-postquery-f.md#postQuery-1)接口。使用
Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | AssetMap | 是 | 关键资产的查询条件，如别名、访问控制属性、自定义数据等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回挑战值。<br/><br/>**说明：** 挑战值用于后续的用户认证。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Incorrect parameter types.<br/>2. Parameter verification failed. |
| [24000001](../../errorcode-universal.md#24000001-The) | The ASSET service is unavailable. |
| [24000002](../../errorcode-universal.md#24000002-The) | The asset is not found. |
| [24000005](../../errorcode-universal.md#24000005-The) | The screen lock status does not match. |
| [24000006](../../errorcode-universal.md#24000006-Insufficient) | Insufficient memory. |
| [24000007](../../errorcode-universal.md#24000007-The) | The asset is corrupted. |
| [24000008](../../errorcode-universal.md#24000008-The) | The database operation failed. |
| [24000009](../../errorcode-universal.md#24000009-The) | The cryptography operation failed. |
| [24000010](../../errorcode-universal.md#24000010-IPC) | IPC failed. |
| [24000011](../../errorcode-universal.md#24000011-Calling) | Calling the Bundle Manager service failed. |
| [24000012](../../errorcode-universal.md#24000012-Calling) | Calling the OS Account service failed. |
| [24000013](../../errorcode-universal.md#24000013-Calling) | Calling the Access Token service failed. |
| [24000016](../../errorcode-universal.md#24000016-The) | The cache exceeds the limit. |
| [24000017](../../errorcode-universal.md#24000017-The) | The capability is not supported. |

**示例：**

```TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

let query: asset.AssetMap = new Map();
query.set(asset.Tag.ALIAS, stringToArray('demo_alias'));
asset.preQuery(query).then((challenge: Uint8Array) => {
  console.info(`Succeeded in pre-querying Asset, the challenge is: `, challenge);
});

```

