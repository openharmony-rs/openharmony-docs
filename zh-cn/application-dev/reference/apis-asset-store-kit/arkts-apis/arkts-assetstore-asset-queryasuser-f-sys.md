# queryAsUser（系统接口）

## queryAsUser

```TypeScript
function queryAsUser(userId: number, query: AssetMap): Promise<Array<AssetMap>>
```

在指定用户空间中查询一条或多条符合条件的关键资产。若查询需要用户认证的关键资产，则需要在本函数前调用[asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md#preQueryAsUser-1)接口，在本函数后调用
[asset.postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md#postQueryAsUser-1)接口，开发步骤请参考
[开发指导](../../../../security/AssetStoreKit/asset-js-query-auth.md)。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。取值范围大于等于100。 |
| query | AssetMap | 是 | 关键资产的查询条件，如别名、访问控制属性、自定义数据等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AssetMap&gt;&gt; | Promise对象，返回查询结果列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The caller doesn't have the permission. |
| [202](../../errorcode-universal.md#202-Nonsystem) | Non-system applications use system APIs. |
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

let userId: number = 100;
let query: asset.AssetMap = new Map();
query.set(asset.Tag.ALIAS, stringToArray('demo_alias'));
asset.queryAsUser(userId, query).then((res: Array<asset.AssetMap>) => {
  for (let i = 0; i < res.length; i++) {
    // 解析属性。
    let accessibility: number = res[i].get(asset.Tag.ACCESSIBILITY) as number;
    console.info(`Succeeded in getting accessibility, which is: ${accessibility}.`);
  }
  console.info(`Succeeded in querying Asset from user space.`);
});

```

