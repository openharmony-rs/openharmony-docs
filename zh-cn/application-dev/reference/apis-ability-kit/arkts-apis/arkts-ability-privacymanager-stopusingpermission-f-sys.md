# stopUsingPermission（系统接口）

## stopUsingPermission

```TypeScript
function stopUsingPermission(tokenID: int, permissionName: Permissions): Promise<void>
```

系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。 适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。 该接口需与[startUsingPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_配套使用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**需要权限：** ohos.permission.PERMISSION_USED_STATS

<!--Device-privacyManager-function stopUsingPermission(tokenID: int, permissionName: Permissions): Promise<void>--><!--Device-privacyManager-function stopUsingPermission(tokenID: int, permissionName: Permissions): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | int | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_字段获取。传入无效值时返回错误码12100001。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值限定为整数。取值约束：该参数必须为大于0的整数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_BundleInfo获取可参考：[bundleManager.getBundleInfoSync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| permissionName | Permissions | 是 | 需要停止使用的权限名称。传入无效值时返回错误码12100001。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION\_\_\_ESCAPED\_UNDERSCORE\_\_\_USED\_\_\_ESCAPED\_UNDERSCORE\_\_\_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256characters, or the type of the specified tokenID is not of the application type. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user\_\_\_ESCAPED\_UNDERSCORE\_\_\_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is not used in pair with 'startUsingPermission'. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenID: number = 0; // 可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
// 停止使用指定权限
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
```


## stopUsingPermission

```TypeScript
function stopUsingPermission(tokenID: int, permissionName: Permissions, callback: AsyncCallback<void>): void
```

系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。 适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用callback异步回调。 该接口需与[startUsingPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_配套使用。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.PERMISSION_USED_STATS

<!--Device-privacyManager-function stopUsingPermission(tokenID: int, permissionName: Permissions, callback: AsyncCallback<void>): void--><!--Device-privacyManager-function stopUsingPermission(tokenID: int, permissionName: Permissions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_字段获取。传入无效值时返回错误码12100001。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值限定为整数。取值约束：该参数必须为大于0的整数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_BundleInfo获取可参考：[bundleManager.getBundleInfoSync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| permissionName | Permissions | 是 | 需要停止使用的权限名称。传入无效值时返回错误码12100001。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值约束：权限名长度不能超过256个字符。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当停止使用权限成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION\_\_\_ESCAPED\_UNDERSCORE\_\_\_USED\_\_\_ESCAPED\_UNDERSCORE\_\_\_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256characters, or the type of the specified tokenID is not of the application type. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user\_\_\_ESCAPED\_UNDERSCORE\_\_\_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is not used in pair with 'startUsingPermission'. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenID: number = 0; // 可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
// 停止使用指定权限
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', (err: BusinessError, data: void) => {
  if (err) {
    console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('stopUsingPermission success');
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenID: int = 0; // 可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', (err: BusinessError | null): void => {
  if (err) {
    console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('stopUsingPermission success');
  }
});
```


## stopUsingPermission

```TypeScript
function stopUsingPermission(
    tokenID: int,
    permissionName: Permissions,
    pid?: int,
    options?: PermissionUsingOptions
  ): Promise<void>
```

系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。 适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。 pid需要与[startUsingPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_传入的pid相同。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-privacyManager-function stopUsingPermission(    tokenID: int,    permissionName: Permissions,    pid?: int,    options?: PermissionUsingOptions  ): Promise<void>--><!--Device-privacyManager-function stopUsingPermission(    tokenID: int,    permissionName: Permissions,    pid?: int,    options?: PermissionUsingOptions  ): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_字段获取。传入无效值时返回错误码12100001。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值限定为整数。取值约束：该参数必须为大于0的整数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_BundleInfo获取可参考：[bundleManager.getBundleInfoSync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| permissionName | Permissions | 是 | 需要停止使用的权限名称。传入无效值时返回错误码12100001。 |
| pid | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | 调用方的进程pid，需与[startUsingPermission]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传入的pid相同。不满足配套关系可能导致API调用失败（错误码12100004）。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值限定为整数。默认值：-1，表示不根据进程生命周期响应。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 权限使用可选参数，用于指定扩展身份。当需要标识调用方的扩展身份信息时传入此参数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：结构内每个属性的默认值请参考 [PermissionUsingOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION\_\_\_ESCAPED\_UNDERSCORE\_\_\_USED\_\_\_ESCAPED\_UNDERSCORE\_\_\_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds256 characters, the type of the specified tokenID is not of the application type, or the enhancedIdentity in PermissionUsingOptions exceeds 48 characters. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user\_\_\_ESCAPED\_UNDERSCORE\_\_\_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is not used in pair with 'startUsingPermission'. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let tokenID: number = rpc.IPCSkeleton.getCallingTokenId(); // 也可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
let pid: number = rpc.IPCSkeleton.getCallingPid();

// 不带pid参数
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

// 带pid参数
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid).then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

// 带扩展身份标识
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid, {enhancedIdentity: 'test'}).then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import rpc from '@ohos.rpc';

let tokenID: int = rpc.IPCSkeleton.getCallingTokenId() as int; // 也可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
let pid: int = rpc.IPCSkeleton.getCallingPid() as int;

// 不带pid参数
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

// 带pid参数
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid).then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

// 带pid和enhancedIdentity参数
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid, {enhancedIdentity: "test"}).then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
```


## stopUsingPermission

```TypeScript
function stopUsingPermission(
    tokenID: int,
    permissionName: Permissions,
    pid?: int
  ): Promise<void>
```

系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。 pid需要与 [startUsingPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 传入的pid相同。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.PERMISSION_USED_STATS

<!--Device-privacyManager-function stopUsingPermission(    tokenID: int,    permissionName: Permissions,    pid?: int  ): Promise<void>--><!--Device-privacyManager-function stopUsingPermission(    tokenID: int,    permissionName: Permissions,    pid?: int  ): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_字段获取。传入无效值时返回错误码12100001。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值限定为整数。取值约束：该参数必须为大于0的整数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_BundleInfo获取可参考：[bundleManager.getBundleInfoSync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| permissionName | Permissions | 是 | 需要停止使用的权限名称。传入无效值时返回错误码12100001。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值约束：权限名长度不能超过256个字符。 |
| pid | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | Process PID of the caller. Must be the same as the pid passed to [startUsingPermission]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. A mismatch may cause the API call to fail(error code 12100004).\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_The value should be an integer. Default value: -1, indicating no response based on process lifecycle. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION\_\_\_ESCAPED\_UNDERSCORE\_\_\_USED\_\_\_ESCAPED\_UNDERSCORE\_\_\_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256characters, or the type of the specified tokenID is not of the application type. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user\_\_\_ESCAPED\_UNDERSCORE\_\_\_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is not used in pair with 'startUsingPermission'. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let tokenID: number = rpc.IPCSkeleton.getCallingTokenId(); // 也可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
let pid: number = rpc.IPCSkeleton.getCallingPid();

// without pid
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

// with pid
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid).then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import rpc from '@ohos.rpc';

let tokenID: int = rpc.IPCSkeleton.getCallingTokenId() as int; // 也可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
let pid: int = rpc.IPCSkeleton.getCallingPid() as int;

// without pid
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

// with pid
privacyManager.stopUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid).then(() => {
  console.info('stopUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`stopUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
```

