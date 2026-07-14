# startUsingPermission（系统接口）

## startUsingPermission

```TypeScript
function startUsingPermission(tokenID: number, permissionName: Permissions): Promise<void>
```

系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](privacyManager.on)）。使用Promise异步回调。

开始使用权限后，需要在权限使用结束时调用[stopUsingPermission](arkts-ability-stopusingpermission-f-sys.md#stopusingpermission-1)停止使用权限。

**起始版本：** 9

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId]{@link./bundleManager/ApplicationInfo:ApplicationInfo.accessTokenId}字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 需要使用的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionNameexceeds 256 characters, or the type of the specified tokenID is not of the application type. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | (Deprecated in 12) The specified tokenID does not exist or refer to anapplication process. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is used repeatedly with the same input.It means the application specified by the tokenID has been using the specified permission. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenID: number = 0; // 可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
// 开始使用指定权限
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

```


## startUsingPermission

```TypeScript
function startUsingPermission(
    tokenID: number,
    permissionName: Permissions,
    pid?: number,
    usedType?: PermissionUsedType
  ): Promise<void>
```

系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考
[on](arkts-ability-on-f-sys.md#on-1)）。
使用Promise异步回调。

开始使用权限后，需要在权限使用结束时调用
[stopUsingPermission](privacyManager.stopUsingPermission(tokenID: int, permissionName: Permissions, pid?: int))
停止使用权限。

**起始版本：** 18

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId]{@link./bundleManager/ApplicationInfo:ApplicationInfo.accessTokenId}字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 需要使用的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| pid | number | 否 | 调用方的进程pid，用于根据进程生命周期管理权限使用状态。当需要精确控制特定进程的权限使用状态（例如进程退出时自动停止权限使用）时传入此参数。需要与[stopUsingPermission]{@linkprivacyManager.stopUsingPermission}传入的pid相同。<br>取值限定为整数。默认值：-1，表示不根据进程生命周期响应。 |
| usedType | PermissionUsedType | 否 | 敏感权限访问方式。<br>默认值：NORMAL_TYPE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds256 characters, the type of the specified tokenID is not of the application type, or usedType is invalid. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is used repeatedly with the same input.It means the application specified by the tokenID has been using the specified permission. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let tokenID: number = rpc.IPCSkeleton.getCallingTokenId(); // 也可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
let pid: number = rpc.IPCSkeleton.getCallingPid();
let usedType: privacyManager.PermissionUsedType = privacyManager.PermissionUsedType.PICKER_TYPE;

// 开始使用指定权限
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// with pid
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid).then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// with usedType
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', -1, usedType).then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// with pid and usedType
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid, usedType).then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

```


## startUsingPermission

```TypeScript
function startUsingPermission(
     tokenID: number,
     permissionName: Permissions,
     pid?: number,
     usedType?: PermissionUsedType,
     options?: PermissionUsingOptions
   ): Promise<void>
```

系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考
[on](privacyManager.on(type: 'activeStateChange', permissionList: Array<Permissions>, callback:
Callback<ActiveChangeResponse>))
）。使用Promise异步回调。

开始使用权限后，需要在权限使用结束时调用
[stopUsingPermission](privacyManager.stopUsingPermission(tokenID: int, permissionName: Permissions, pid?:
int, options?: PermissionUsingOptions))
停止使用权限。

当传入pid时，pid需要与
[stopUsingPermission](privacyManager.stopUsingPermission(tokenID: int, permissionName: Permissions, pid?:
int, options?: PermissionUsingOptions))
传入的pid相同，不满足配套关系返回错误码12100004。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId]{@link./bundleManager/ApplicationInfo:ApplicationInfo.accessTokenId}字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 需要使用的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| pid | number | 否 | 调用方的进程pid，用于根据进程生命周期管理权限使用状态。当需要精确控制特定进程的权限使用状态（例如进程退出时自动停止权限使用）时传入此参数。需要与[stopUsingPermission]{@linkprivacyManager.stopUsingPermission}传入的pid相同。<br>取值限定为整数。默认值：-1，表示不根据进程生命周期响应。 |
| usedType | PermissionUsedType | 否 | 敏感权限访问方式。<br>默认值：NORMAL_TYPE。 |
| options | PermissionUsingOptions | 否 | 权限使用可选参数，用于指定扩展身份。当需要标识调用方的扩展身份信息时传入此参数。<br>默认值：结构内每个属性的默认值请参考 [PermissionUsingOptions](arkts-ability-permissionusingoptions-i-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds256 characters, the type of the specified tokenID is not of the application type, usedType is invalid,or the enhancedIdentity in PermissionUsingOptions exceeds 48 characters. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is used repeatedly with the same input.It means the application specified by the tokenID has been using the specified permission. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let tokenID: number = rpc.IPCSkeleton.getCallingTokenId(); // 也可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
let pid: number = rpc.IPCSkeleton.getCallingPid();
let usedType: privacyManager.PermissionUsedType = privacyManager.PermissionUsedType.PICKER_TYPE;

// 不带pid和usedType参数
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// 带pid参数
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid).then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// 带usedType参数
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', -1, usedType).then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// 带pid和usedType参数
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid, usedType).then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// 带pid、usedType和enhancedIdentity
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid, usedType, {enhancedIdentity: 'test'}).then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});

```


## startUsingPermission

```TypeScript
function startUsingPermission(
    tokenID: number,
    permissionName: Permissions,
    callback: AsyncCallback<void>
  ): void
```

系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考
[on](arkts-ability-on-f-sys.md#on-1)
）。使用callback异步回调。

开始使用权限后，需要在权限使用结束时调用
[stopUsingPermission](arkts-ability-stopusingpermission-f-sys.md#stopusingpermission-1)
停止使用权限。

**起始版本：** 9

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId]{@link./bundleManager/ApplicationInfo:ApplicationInfo.accessTokenId}字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 需要使用的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当开始使用权限成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256characters, or the type of the specified tokenID is not of the application type. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | (Deprecated in 12) The specified tokenID does not exist or refer to anapplication process. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is used repeatedly with the same input.It means the application specified by the tokenID has been using the specified permission. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenID: number = 0; // 可以通过应用BundleInfo中的ApplicationInfo的accessTokenId字段获取。
// 开始使用指定权限
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', (err: BusinessError, data: void) => {
  if (err) {
    console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('startUsingPermission success');
  }
});

```

