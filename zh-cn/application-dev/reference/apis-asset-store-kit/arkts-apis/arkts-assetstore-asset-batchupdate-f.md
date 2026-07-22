# batchUpdate

## 导入模块

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## batchUpdate

```TypeScript
function batchUpdate(sourceAttributes: Array<AssetMap>, destAttributes: Array<AssetMap>): Promise<BatchResult>
```

批量更新符合条件的关键资产。使用Promise异步回调。

批量更新的关键资产必须具有相同的[Tag.GROUP_ID](arkts-assetstore-asset-tagtype-e.md)和[Tag.REQUIRE_ATTR_ENCRYPTED](arkts-assetstore-asset-tagtype-e.md)属性。

批量更新的关键资产数量最大值为100。

**起始版本：** 26.0.0

<!--Device-asset-function batchUpdate(sourceAttributes: Array<AssetMap>, destAttributes: Array<AssetMap>): Promise<BatchResult>--><!--Device-asset-function batchUpdate(sourceAttributes: Array<AssetMap>, destAttributes: Array<AssetMap>): Promise<BatchResult>-End-->

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceAttributes | Array&lt;AssetMap&gt; | 是 | 待更新关键资产的搜索条件数组。 |
| destAttributes | Array&lt;AssetMap&gt; | 是 | 待更新关键资产的属性集合数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BatchResult&gt; | Promise对象，返回批量操作结果，包含失败关键资产的错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24000001](../errorcode-asset.md#24000001-关键资产服务不可用) | The ASSET service is unavailable. |
| [24000006](../errorcode-asset.md#24000006-系统内存不足) | Insufficient memory. |
| [24000007](../errorcode-asset.md#24000007-关键资产损坏) | The asset is corrupted. |
| [24000008](../errorcode-asset.md#24000008-数据库操作失败) | The database operation failed. |
| [24000010](../errorcode-asset.md#24000010-进程通信错误) | IPC failed. |
| [24000011](../errorcode-asset.md#24000011-包管理服务异常) | Calling the Bundle Manager service failed. |
| [24000012](../errorcode-asset.md#24000012-账号系统服务异常) | Calling the OS Account service failed. |
| [24000013](../errorcode-asset.md#24000013-访问控制服务异常) | Calling the Access Token service failed. |
| [24000015](../errorcode-asset.md#24000015-获取系统时间失败) | Getting the system time failed. |
| [24000019](../errorcode-asset.md#24000019-属性值不一致) | Each value of {@link Tag.GROUP_ID} and {@link Tag.REQUIRE_ATTR_ENCRYPTED}in the array is not consistent. |

**示例：**

```TypeScript
import { asset } from '@kit.AssetStoreKit';
import { util } from '@kit.ArkTS';

function stringToArray(str: string): Uint8Array {
  let textEncoder = new util.TextEncoder();
  return textEncoder.encodeInto(str);
}

let srcAttrs: Array<asset.AssetMap> = [];
let srcAttr1: asset.AssetMap = new Map();
srcAttr1.set(asset.Tag.ALIAS, stringToArray('demo_alias1'));
srcAttrs.push(srcAttr1);
let srcAttr2: asset.AssetMap = new Map();
srcAttr2.set(asset.Tag.ALIAS, stringToArray('demo_alias2'));
srcAttrs.push(srcAttr2);

let destAttrs: Array<asset.AssetMap> = [];
let destAttr1: asset.AssetMap = new Map();
destAttr1.set(asset.Tag.SECRET, stringToArray('demo_pwd_new1'));
destAttrs.push(destAttr1);
let destAttr2: asset.AssetMap = new Map();
destAttr2.set(asset.Tag.SECRET, stringToArray('demo_pwd_new2'));
destAttrs.push(destAttr2);

asset.batchUpdate(srcAttrs, destAttrs).then((res: asset.BatchResult) => {
  console.info(`Succeeded in batch updating Asset, failedCount: ${res.failedCount}`);
});

```

