# getPermissionUsedTypeInfos（系统接口）

## getPermissionUsedTypeInfos

```TypeScript
function getPermissionUsedTypeInfos(
    tokenId?: number | null,
    permissionName?: Permissions): Promise<Array<PermissionUsedTypeInfo>>
```

查询设备上指定应用访问敏感权限时的信息（包括敏感权限名称、敏感权限访问方式）。

**起始版本：** 12

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | number \| null | 否 | 访问敏感权限的应用身份标识。可通过应用[BundleInfo](arkts-ability-bundleinfo-i.md)中的[ApplicationInfo](arkts-ability-applicationinfo-i.md)的accessTokenId字段获取。当需要查询特定应用的敏感权限访问类型信息时传入具体的tokenId；为0或null时表示查询所有应用的敏感权限访问类型信息。从API version 20开始，新增支持null类型。<br>默认值：0。 |
| permissionName | Permissions | 否 | 被访问的敏感权限名称。当需要查询特定敏感权限的访问类型信息时传入具体的权限名；为空时表示查询所有敏感权限的访问类型信息。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。默认值：空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PermissionUsedTypeInfo&gt;&gt; | Promise used to return the list of permission access typeinformation. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. PermissionName exceeds 256 characters. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The input tokenId does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The input permissionName does not exist. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. A database error occurs. |

**示例：**

```TypeScript
import { privacyManager, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenId: number = 0; // 可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
let permissionName: Permissions = 'ohos.permission.CAMERA';
// without any param
privacyManager.getPermissionUsedTypeInfos().then((data: Array<privacyManager.PermissionUsedTypeInfo>) => {
  console.info('getPermissionUsedTypeInfos success, result: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedTypeInfos fail, code: ${err.code}, message: ${err.message}`);
});
// only tokenId
privacyManager.getPermissionUsedTypeInfos(tokenId).then((data: Array<privacyManager.PermissionUsedTypeInfo>) => {
  console.info('getPermissionUsedTypeInfos success, result: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedTypeInfos fail, code: ${err.code}, message: ${err.message}`);
});
// only permissionName
privacyManager.getPermissionUsedTypeInfos(null, permissionName).then((data: Array<privacyManager.PermissionUsedTypeInfo>) => {
  console.info('getPermissionUsedTypeInfos success, result: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedTypeInfos fail, code: ${err.code}, message: ${err.message}`);
});
// tokenId and permissionName
privacyManager.getPermissionUsedTypeInfos(tokenId, permissionName).then((data: Array<privacyManager.PermissionUsedTypeInfo>) => {
  console.info('getPermissionUsedTypeInfos success, result: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getPermissionUsedTypeInfos fail, code: ${err.code}, message: ${err.message}`);
});

```

