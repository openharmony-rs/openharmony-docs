# query

## 导入模块

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

<a id="query"></a>
## query

```TypeScript
function query(query: AssetMap): Promise<Array<AssetMap>>
```

查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQuery](arkts-assetstore-asset-prequery-f.md#prequery-1)接口，在本函数后调用[asset.postQuery](arkts-assetstore-asset-postquery-f.md#postquery-1)接口，开发步骤请参考[开发指导](../../../security/AssetStoreKit/asset-js-query-auth.md)。使用Promise异步回调。

如果未查询到符合条件的关键资产，将抛出“未找到关键资产”的异常，而非返回空的查询结果列表。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-asset-function query(query: AssetMap): Promise<Array<AssetMap>>--><!--Device-asset-function query(query: AssetMap): Promise<Array<AssetMap>>-End-->

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | 是 | 关键资产的查询条件，如别名、访问控制属性、自定义数据等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AssetMap&gt;&gt; | Promise对象，返回查询结果列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1. Incorrect parameter types.2. Parameter verification failed. |
| [24000001](../errorcode-asset.md#24000001-关键资产服务不可用) | The ASSET service is unavailable. |
| [24000002](../errorcode-asset.md#24000002-未找到关键资产) | The asset is not found. |
| [24000004](../errorcode-asset.md#24000004-访问被拒绝) | Access denied. |
| [24000005](../errorcode-asset.md#24000005-锁屏状态不匹配) | The screen lock status does not match. |
| [24000006](../errorcode-asset.md#24000006-系统内存不足) | Insufficient memory. |
| [24000007](../errorcode-asset.md#24000007-关键资产损坏) | The asset is corrupted. |
| [24000008](../errorcode-asset.md#24000008-数据库操作失败) | The database operation failed. |
| [24000009](../errorcode-asset.md#24000009-算法库操作失败) | The cryptography operation failed. |
| [24000010](../errorcode-asset.md#24000010-进程通信错误) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-包管理服务异常) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-账号系统服务异常) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-访问控制服务异常) | Calling the Access Token service failed. |
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
// 如果只需要返回关键资产的属性，可以将RETURN_TYPE设置为ATTRIBUTES。返回属性不需解密，查询时间较短。
query.set(asset.Tag.RETURN_TYPE, asset.ReturnType.ALL); // 此处表示需要返回关键资产的所有信息，即属性+明文。返回明文需要解密，查询时间较长。
asset.query(query).then((res: Array<asset.AssetMap>) => {
  for (let i = 0; i < res.length; i++) {
    // 解析属性。
    let accessibility: number = res[i].get(asset.Tag.ACCESSIBILITY) as number;
    console.info(`Succeeded in getting accessibility, which is: ${accessibility}.`);
  }
  console.info(`Succeeded in querying Asset.`);
});

```

