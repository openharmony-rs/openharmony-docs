# updateAsUser（系统接口）

## updateAsUser

```TypeScript
function updateAsUser(userId: number, query: AssetMap, attributesToUpdate: AssetMap): Promise<void>
```

在指定用户空间中更新符合条件的一条关键资产。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。取值范围大于等于100。 |
| query | AssetMap | 是 | 待更新关键资产的搜索条件，如关键资产别名、访问控制属性、自定义数据等。 |
| attributesToUpdate | AssetMap | 是 | 待更新关键资产的属性集合，如关键资产明文和自定义数据等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The caller doesn't have the permission. |
| [202](../../errorcode-universal.md#202-Nonsystem) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
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
| [24000015](../../errorcode-universal.md#24000015-Getting) | Getting the system time failed. |

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
let attrsToUpdate: asset.AssetMap = new Map();
attrsToUpdate.set(asset.Tag.SECRET, stringToArray('demo_pwd_new'));
asset.updateAsUser(userId, query, attrsToUpdate).then(() => {
  console.info(`Succeeded in updating Asset in user space.`);
});

```

