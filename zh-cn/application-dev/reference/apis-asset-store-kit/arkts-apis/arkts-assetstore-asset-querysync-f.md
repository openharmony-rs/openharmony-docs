# querySync

## querySync

```TypeScript
function querySync(query: AssetMap): Array<AssetMap>
```

查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md#preQuerySync-1)，在本函数后调用
[asset.postQuerySync](arkts-assetstore-asset-postquerysync-f.md#postQuerySync-1)，开发步骤请参考
[开发指导](../../../../security/AssetStoreKit/asset-js-query-auth.md)。使用同步方式返回结果。

如果未查询到符合条件的关键资产，将抛出“未找到关键资产”的异常，而非返回空的查询结果列表。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | AssetMap | 是 | 关键资产的查询条件，如别名、访问控制属性、自定义数据等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;AssetMap&gt; | 查询结果列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Incorrect parameter types.<br/>2. Parameter verification failed. |
| [24000001](../../errorcode-universal.md#24000001-The) | The ASSET service is unavailable. |
| [24000002](../../errorcode-universal.md#24000002-The) | The asset is not found. |
| [24000004](../../errorcode-universal.md#24000004-Access) | Access denied. |
| [24000005](../../errorcode-universal.md#24000005-The) | The screen lock status does not match. |
| [24000006](../../errorcode-universal.md#24000006-Insufficient) | Insufficient memory. |
| [24000007](../../errorcode-universal.md#24000007-The) | The asset is corrupted. |
| [24000008](../../errorcode-universal.md#24000008-The) | The database operation failed. |
| [24000009](../../errorcode-universal.md#24000009-The) | The cryptography operation failed. |
| [24000010](../../errorcode-universal.md#24000010-IPC) | IPC failed. |
| [24000011](../../errorcode-universal.md#24000011-Calling) | Calling the Bundle Manager service failed. |
| [24000012](../../errorcode-universal.md#24000012-Calling) | Calling the OS Account service failed. |
| [24000013](../../errorcode-universal.md#24000013-Calling) | Calling the Access Token service failed. |
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
// 如果只需要返回关键资产的属性，可以将RETURN_TYPE设置为ATTRIBUTES。返回属性不需解密，查询时间较短。
query.set(asset.Tag.RETURN_TYPE, asset.ReturnType.ALL); // 此处表示需要返回关键资产的所有信息，即属性+明文。返回明文需要解密，查询时间较长。
let res: Array<asset.AssetMap> = asset.querySync(query);
for (let i = 0; i < res.length; i++) {
  // 解析属性。
  let accessibility: number = res[i].get(asset.Tag.ACCESSIBILITY) as number;
  console.info(`Succeeded in getting accessibility, which is: ${accessibility}.`);
}
console.info(`Succeeded in querying Asset.`);

```

