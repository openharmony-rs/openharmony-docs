# updateAsUser（系统接口）

## 导入模块

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

<a id="updateasuser"></a>
## updateAsUser

```TypeScript
function updateAsUser(userId: number, query: AssetMap, attributesToUpdate: AssetMap): Promise<void>
```

在指定用户空间中更新符合条件的一条关键资产。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-asset-function updateAsUser(userId: number, query: AssetMap, attributesToUpdate: AssetMap): Promise<void>--><!--Device-asset-function updateAsUser(userId: number, query: AssetMap, attributesToUpdate: AssetMap): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。取值范围大于等于100。 |
| query | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | 是 | 待更新关键资产的搜索条件，如关键资产别名、访问控制属性、自定义数据等。 |
| attributesToUpdate | [AssetMap](arkts-assetstore-asset-assetmap-t.md) | 是 | 待更新关键资产的属性集合，如关键资产明文和自定义数据等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The caller doesn't have the permission. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
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
| [24000015](../errorcode-asset.md#24000015-获取系统时间失败) | Getting the system time failed. |

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

