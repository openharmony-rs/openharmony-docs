# preQuerySync

## 导入模块

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

<a id="prequerysync"></a>
## preQuerySync

```TypeScript
function preQuerySync(query: AssetMap): Uint8Array
```

查询的预处理，用于需要用户认证的关键资产。在用户认证成功后，应当随后调用[asset.querySync](arkts-assetstore-asset-querysync-f.md#querysync-1)、[asset.postQuerySync](arkts-assetstore-asset-postquerysync-f.md#postquerysync-1)。使用同步方式返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-asset-function preQuerySync(query: AssetMap): Uint8Array--><!--Device-asset-function preQuerySync(query: AssetMap): Uint8Array-End-->

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | 是 | 关键资产的查询条件，如别名、访问控制属性、自定义数据等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 挑战值。<br>**说明：** 挑战值用于后续用户认证。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types.2. Parameter verification failed. |
| [24000001](../errorcode-asset.md#24000001-关键资产服务不可用) | The ASSET service is unavailable. |
| [24000002](../errorcode-asset.md#24000002-未找到关键资产) | The asset is not found. |
| [24000005](../errorcode-asset.md#24000005-锁屏状态不匹配) | The screen lock status does not match. |
| [24000006](../errorcode-asset.md#24000006-系统内存不足) | Insufficient memory. |
| [24000007](../errorcode-asset.md#24000007-关键资产损坏) | The asset is corrupted. |
| [24000008](../errorcode-asset.md#24000008-数据库操作失败) | The database operation failed. |
| [24000009](../errorcode-asset.md#24000009-算法库操作失败) | The cryptography operation failed. |
| [24000010](../errorcode-asset.md#24000010-进程通信错误) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-包管理服务异常) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-账号系统服务异常) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-访问控制服务异常) | Calling the Access Token service failed. |
| [24000016](../errorcode-asset.md#24000016-缓存数量超限) | The cache exceeds the limit. |
| [24000017](../errorcode-asset.md#24000017-该子功能不支持) | The capability is not supported. |

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
let challenge: Uint8Array = asset.preQuerySync(query);
console.info(`Succeeded in pre-querying with sync, the challenge is: `, challenge);

```

