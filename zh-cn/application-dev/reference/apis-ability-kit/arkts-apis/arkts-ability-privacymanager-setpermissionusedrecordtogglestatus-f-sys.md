# setPermissionUsedRecordToggleStatus（系统接口）

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

<a id="setpermissionusedrecordtogglestatus"></a>
## setPermissionUsedRecordToggleStatus

```TypeScript
function setPermissionUsedRecordToggleStatus(status: boolean): Promise<void>
```

设置是否记录当前用户的权限使用情况。系统应用调用此接口，可以设置当前用户的权限使用记录开关状态。使用Promise异步回调。

status为true时，[addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord-1)接口可以正常添加使用记录；status为false时，[addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord-1)接口不产生权限使用记录，并且删除当前用户的历史记录。

**起始版本：** 18

**需要权限：** ohos.permission.PERMISSION_RECORD_TOGGLE

<!--Device-privacyManager-function setPermissionUsedRecordToggleStatus(status: boolean): Promise<void>--><!--Device-privacyManager-function setPermissionUsedRecordToggleStatus(status: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | boolean | 是 | 权限使用记录开关状态。true为开，false为关。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_RECORD_TOGGLE". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | Operation not allowed. The toggle status of the specified permission has already been set by [setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md#setpermissionusedrecordtogglestatus-1).<br>**适用版本：** 26.1.0+ |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. Possible causes: 1. Database error. 2. Failed to query all applications under the user. |

**示例：**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 设置权限使用记录开关状态
privacyManager.setPermissionUsedRecordToggleStatus(true).then(() => {
  console.info('setPermissionUsedRecordToggleStatus success');
}).catch((err: BusinessError): void => {
  console.error(`setPermissionUsedRecordToggleStatus fail, code: ${err.code}, message: ${err.message}`);
});

```


<a id="setpermissionusedrecordtogglestatus-1"></a>
## setPermissionUsedRecordToggleStatus

```TypeScript
function setPermissionUsedRecordToggleStatus(status: boolean, subProfileId: number): Promise<void>
```

设置是否记录指定子身份资料的权限使用情况。系统应用调用此接口，可以设置指定子身份资料的权限使用记录开关状态。使用Promise异步回调。

status为true时，[addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord-1)接口可以正常添加使用记录；status为false时，addPermissionUsedRecord]{@link privacyManager.addPermissionUsedRecord}接口不产生权限使用记录，并且删除指定子身份资料的历史记录。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.PERMISSION_RECORD_TOGGLE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-privacyManager-function setPermissionUsedRecordToggleStatus(status: boolean, subProfileId: int): Promise<void>--><!--Device-privacyManager-function setPermissionUsedRecordToggleStatus(status: boolean, subProfileId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | boolean | 是 | 权限使用记录开关状态。true为开，false为关。 |
| subProfileId | number | 是 | 子身份资料的标识符。可以通过[OsAccountSubProfile.id](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-osaccountsubprofile-i-sys.md#id)获取。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_RECORD_TOGGLE". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The specified subProfileId does not exist for the current user. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | Operation not allowed. The toggle status of the specified permission has already been set by [setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md#setpermissionusedrecordtogglestatus-1). |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. Possible causes: 1. Database error. 2. Failed to query all applications under the user. |

