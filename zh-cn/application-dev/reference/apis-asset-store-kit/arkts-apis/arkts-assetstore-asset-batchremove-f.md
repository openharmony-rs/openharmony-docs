# batchRemove

## batchRemove

```TypeScript
function batchRemove(assetsToBeRemoved: Array<AssetMap>): Promise<void>
```

批量删除符合条件的关键资产。使用Promise异步回调。

批量删除的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-asset-tagtype-e.md#TagType)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tagtype-e.md#TagType)属性。

批量删除的关键资产数量最大值为100。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetsToBeRemoved | Array&lt;AssetMap&gt; | 是 | 待删除关键资产的搜索条件数组，如别名、访问控制属性、自定义数据等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24000001](../../errorcode-universal.md#24000001-The) | The ASSET service is unavailable. |
| [24000006](../../errorcode-universal.md#24000006-Insufficient) | Insufficient memory. |
| [24000007](../../errorcode-universal.md#24000007-The) | The asset is corrupted. |
| [24000008](../../errorcode-universal.md#24000008-The) | The database operation failed. |
| [24000010](../../errorcode-universal.md#24000010-IPC) | IPC failed. |
| [24000011](../../errorcode-universal.md#24000011-Calling) | Calling the Bundle Manager service failed. |
| [24000012](../../errorcode-universal.md#24000012-Calling) | Calling the OS Account service failed. |
| [24000013](../../errorcode-universal.md#24000013-Calling) | Calling the Access Token service failed. |
| [24000015](../../errorcode-universal.md#24000015-Getting) | Getting the system time failed. |
| [24000019](../../errorcode-universal.md#24000019-Each) | Each value of {@link Tag.GROUP_ID} and {@link Tag.REQUIRE_ATTR_ENCRYPTED}<br/>in the array is not consistent. |

**示例：**

```TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

let assetsToBeRemoved: Array<asset.AssetMap> = [];
let query1: asset.AssetMap = new Map();
query1.set(asset.Tag.ALIAS, stringToArray('demo_alias1'));
assetsToBeRemoved.push(query1);

let query2: asset.AssetMap = new Map();
query2.set(asset.Tag.ALIAS, stringToArray('demo_alias2'));
assetsToBeRemoved.push(query2);

asset.batchRemove(assetsToBeRemoved).then(() => {
  console.info(`Succeeded in batch removing Asset.`);
});

```

