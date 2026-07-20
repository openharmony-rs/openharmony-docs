# AtManager

程序访问控制管理类，提供权限校验、运行时权限弹窗申请、设置页授权引导、全局开关请求和权限状态监听等能力。通过[createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md#createatmanager-1)获取实例。

**起始版本：** 8

<!--Device-abilityAccessCtrl-interface AtManager--><!--Device-abilityAccessCtrl-interface AtManager-End-->

**系统能力：** SystemCapability.Security.AccessToken

## 导入模块

```TypeScript
import { Context, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
```

<a id="checkaccesstoken"></a>
## checkAccessToken

```TypeScript
checkAccessToken(tokenID: number, permissionName: Permissions): Promise<GrantStatus>
```

校验应用是否已被授予指定权限。调用成功后，返回当前权限的授权状态，开发者可据此决定直接执行后续业务、继续发起权限申请，或引导用户前往系统设置修改授权状态。使用Promise异步回调。

适用于应用访问相机、麦克风、位置等受保护资源前进行前置权限判断的场景。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-checkAccessToken(tokenID: int, permissionName: Permissions): Promise<GrantStatus>--><!--Device-AtManager-checkAccessToken(tokenID: int, permissionName: Permissions): Promise<GrantStatus>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 要校验的目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)；<br>若校验本应用，也可通过[bundleManager.getBundleInfoForSelfSync](arkts-ability-bundlemanager-getbundleinfoforselfsync-f.md#getbundleinfoforselfsync-1)获取。 |
| permissionName | Permissions | 是 | 需要校验的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;GrantStatus&gt; | Promise对象，返回授权状态结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2.Incorrect parameter types. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, or the permissionName exceeds 256characters. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 获取应用的bundleInfo信息
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// 获取应用的TokenID
let tokenID: number = bundleInfo.appInfo.accessTokenId;
// 设置需要校验的权限名
let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
// 校验应用是否被授予权限
atManager.checkAccessToken(tokenID, permissionName).then((data: abilityAccessCtrl.GrantStatus) => {
  console.info(`checkAccessToken success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`checkAccessToken fail, code: ${err.code}, message: ${err.message}`);
});

```

<a id="checkaccesstokensync"></a>
## checkAccessTokenSync

```TypeScript
checkAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus
```

校验应用是否已被授予指定权限，同步返回该权限的授权状态。开发者可据此决定直接执行后续业务流程，或继续发起权限申请，或引导用户前往设置页修改授权状态。

与[checkAccessToken](arkts-ability-abilityaccessctrl-atmanager-i.md#checkaccesstoken-1)相比，本接口同步返回授权状态，适用于无需异步处理的权限校验场景。

适用于应用访问相机、麦克风、位置等受保护资源前进行前置权限判断的场景。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-checkAccessTokenSync(tokenID: int, permissionName: Permissions): GrantStatus--><!--Device-AtManager-checkAccessTokenSync(tokenID: int, permissionName: Permissions): GrantStatus-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 要校验的目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)；<br>若校验本应用，也可通过[bundleManager.getBundleInfoForSelfSync](arkts-ability-bundlemanager-getbundleinfoforselfsync-f.md#getbundleinfoforselfsync-1)获取。 |
| permissionName | Permissions | 是 | 需要校验的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GrantStatus](arkts-ability-abilityaccessctrl-grantstatus-e.md) | 枚举实例，返回授权状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, or the permissionName exceeds 256characters. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 获取应用的bundleInfo信息
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// 获取应用的TokenID
let tokenID: number = bundleInfo.appInfo.accessTokenId;
// 设置需要校验的权限名
let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
// 同步校验应用是否被授予权限
let data: abilityAccessCtrl.GrantStatus = atManager.checkAccessTokenSync(tokenID, permissionName);
console.info(`Result: ${data}`);

```

<a id="getselfpermissionstatus"></a>
## getSelfPermissionStatus

```TypeScript
getSelfPermissionStatus(permissionName: Permissions): PermissionStatus
```

查询当前应用的权限状态，同步返回结果。调用成功后，返回当前权限的状态。与[checkAccessToken](arkts-ability-abilityaccessctrl-atmanager-i.md#checkaccesstoken-1)不同，本接口无需传入应用身份标识，仅用于查询当前应用自身权限状态。

适用于在判断是否需要请求权限前、权限申请后确认授权结果、或监听到权限状态变化后重新查询等场景。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-getSelfPermissionStatus(permissionName: Permissions): PermissionStatus--><!--Device-AtManager-getSelfPermissionStatus(permissionName: Permissions): PermissionStatus-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | Permissions | 是 | 需要查询状态的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PermissionStatus](arkts-ability-abilityaccessctrl-permissionstatus-e.md) | 枚举实例，返回权限状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The permissionName is empty or exceeds 256 characters. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
try {
  // 查询当前应用的权限状态
  let data: abilityAccessCtrl.PermissionStatus = atManager.getSelfPermissionStatus('ohos.permission.CAMERA');
  console.info(`getSelfPermissionStatus success, result: ${data}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`getSelfPermissionStatus fail, code: ${error.code}, message: ${error.message}`);
}

```

<a id="off"></a>
## off('selfPermissionStateChange')

```TypeScript
off(
      type: 'selfPermissionStateChange',
      permissionList: Array<Permissions>,
      callback?: Callback<PermissionStateChangeInfo>
    ): void
```

取消订阅自身指定权限列表的权限状态变更事件。取消订阅成功后，将不再接收指定权限列表的状态变化通知。

在无需继续监听权限变化、应用退出或切换页面等场景下，可调用该接口取消订阅。

> **说明**  
> 当不传入callback参数时，将批量删除与permissionList相关联的所有回调函数。  
> 该接口通常与[on](abilityAccessCtrl.AtManager.on)配套使用，用于取消通过on创建的监听关系。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-off(
      type: 'selfPermissionStateChange',
      permissionList: Array<Permissions>,
      callback?: Callback<PermissionStateChangeInfo>
    ): void--><!--Device-AtManager-off(
      type: 'selfPermissionStateChange',
      permissionList: Array<Permissions>,
      callback?: Callback<PermissionStateChangeInfo>
    ): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selfPermissionStateChange' | 是 | 取消订阅事件类型，固定为'selfPermissionStateChange'，权限状态变更事件。 |
| permissionList | Array&lt;Permissions&gt; | 是 | 取消订阅的权限名列表，为空时表示取消订阅所有的权限状态变化，必须与on订阅时的权限列表匹配（不区分顺序）。<br>最大长度为1024。取值约束：列表中的权限名需为有效权限名，权限名长度不能超过256个字符。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;PermissionStateChangeInfo&gt; | 否 | 回调函数。取消订阅指定权限名状态变更事件的回调。不传入此参数时，将批量删除与permissionList相关联的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is not used in pair with 'on'. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建权限管理实例
  let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
  // 设置需要取消订阅的权限列表
  let permissionList: Array<Permissions> = ['ohos.permission.APPROXIMATELY_LOCATION'];
  // 取消订阅权限状态变化
  atManager.off('selfPermissionStateChange', permissionList);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Code: ${error.code}, message: ${error.message}`);
}

```

<a id="on"></a>
## on('selfPermissionStateChange')

```TypeScript
on(
      type: 'selfPermissionStateChange',
      permissionList: Array<Permissions>,
      callback: Callback<PermissionStateChangeInfo>
    ): void
```

订阅本应用的指定权限列表的权限授权状态变化事件，使用callback异步回调。可在需要根据权限状态实时更新UI或业务逻辑、监听用户授权行为等场景中使用。不再需要监听时，调用[off](abilityAccessCtrl.AtManager.off)取消订阅。

- 多次调用本订阅接口时，如果订阅的权限列表相同，callback不同，允许订阅成功。  
- 多次调用本订阅接口时，如果订阅的权限列表间有相同的子集，callback相同时，订阅失败。

> **说明**  
> 权限状态由“已授权”变更为“未授权”可能存在两种场景：  
> - 用户主动撤销：系统会终止对应应用进程。  
> - 系统主动回收：应用进程不会终止。典型场景如安全控件的单次授权，在授权周期结束后由系统自动回收。  
> 该接口通常与[off](abilityAccessCtrl.AtManager.off)配套使用，当不再需要监听时应调用off取消订阅。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-on(
      type: 'selfPermissionStateChange',
      permissionList: Array<Permissions>,
      callback: Callback<PermissionStateChangeInfo>
    ): void--><!--Device-AtManager-on(
      type: 'selfPermissionStateChange',
      permissionList: Array<Permissions>,
      callback: Callback<PermissionStateChangeInfo>
    ): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selfPermissionStateChange' | 是 | 订阅事件类型，固定为'selfPermissionStateChange'，自身权限状态变更事件。 |
| permissionList | Array&lt;Permissions&gt; | 是 | 订阅的权限名列表，为空时表示订阅所有的权限状态变化。传入无效值时返回错误码12100001。<br>最大长度为1024。取值约束：列表中的权限名需为有效权限名，权限名长度不能超过256个字符。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;PermissionStateChangeInfo&gt; | 是 | 回调函数。订阅指定权限名状态变更事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. Possible causes: 1. The permissionList exceeds the size limit; 2. The permissionNames in the list are all invalid. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is used repeatedly with the same input. |
| [12100005](../errorcode-access-token.md#12100005-监听器数量超过限制) | The registration time has exceeded the limit. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建权限管理实例
  let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
  // 设置需要订阅的权限列表
  let permissionList: Array<Permissions> = ['ohos.permission.APPROXIMATELY_LOCATION'];
  // 订阅权限状态变化
  atManager.on('selfPermissionStateChange', permissionList, (data: abilityAccessCtrl.PermissionStateChangeInfo) => {
    console.info('receive permission state change');
    console.info(`data change: ${data.change}, tokenID: ${data.tokenID}, permission name: ${data.permissionName}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Code: ${error.code}, message: ${error.message}`);
}

```

<a id="openpermissiononsetting"></a>
## openPermissionOnSetting

```TypeScript
openPermissionOnSetting(context: Context, permission: Permissions): Promise<SelectedResult>
```

用于[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)/[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)拉起权限设置页面。调用成功后会打开权限设置页面，用户在页面中操作后，返回用户在设置页面中的选择结果。使用Promise异步回调。

适用于 [manual_settings](docroot://security/AccessToken/app-permission-mgmt-overview.md#manual_settings手动设置授权)类型权限无法通过普通授权弹窗申请、必须引导用户进入系统设置完成授权的场景。manual_settings类型权限是指只能由用户在系统设置中手动开启的权限，无法通过普通授权弹窗直接申请。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtManager-openPermissionOnSetting(context: Context, permission: Permissions): Promise<SelectedResult>--><!--Device-AtManager-openPermissionOnSetting(context: Context, permission: Permissions): Promise<SelectedResult>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 请求权限的UIAbility/UIExtensionAbility的Context。若传入其他应用、无效页面或非Stage模型的Context，接口可能报错或无法打开设置页面。 |
| permission | Permissions | 是 | 需要跳转设置页处理的权限名。传入无效或未在module.json中声明的权限时返回错误码12100001；仅支持授权方式为[manual_settings](docroot://security/AccessToken/app-permission-mgmt-overview.md#manual_settings手动设置授权)类型的权限，传入其他类型权限时返回错误码12100014。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SelectedResult&gt; | Promise对象，返回用户在设置页面中的选择结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. Possible causes: 1. The context is invalid because it does not belong to the application itself; 2. The permission is invalid or not declared in the module.json file. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. An error occurs when creating the pop-up window or obtaining the user operation result. |
| [12100014](../errorcode-access-token.md#12100014-非预期的权限) | Unexpected permission. The permission is not a manual_settings permission. |

**示例：**

示例中context的获取方式请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { abilityAccessCtrl, Context, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 请在组件内获取context
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 拉起跳转设置页弹窗
atManager.openPermissionOnSetting(context, 'ohos.permission.HOOK_KEY_EVENT').then((data: abilityAccessCtrl.SelectedResult) => {
  console.info(`openPermissionOnSetting success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`openPermissionOnSetting fail, code: ${err.code}, message: ${err.message}`);
});

```

<a id="requestglobalswitch"></a>
## requestGlobalSwitch

```TypeScript
requestGlobalSwitch(context: Context, type: SwitchType): Promise<boolean>
```

用于UIAbility/UIExtensionAbility拉起全局开关设置弹窗。调用成功后，若全局开关处于关闭状态，则弹出全局开关设置界面供用户操作；若全局开关已开启，则不拉起弹窗并返回true。使用Promise异步回调。

适用于依赖系统级全局开关（如相机、麦克风、定位）开启的场景。

当应用需要使用相机、麦克风或定位等需要全局开关管控的功能时，如果对应的全局开关被关闭，应用可拉起此弹窗请求用户开启对应功能。如果当前全局开关的状态为开启，则不拉起弹窗。

<!--RP5-->

![requestGlobalSwitch](docroot://reference/apis-ability-kit/figures/requestGlobalSwitch.png)

<!--RP5End-->

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-requestGlobalSwitch(context: Context, type: SwitchType): Promise<boolean>--><!--Device-AtManager-requestGlobalSwitch(context: Context, type: SwitchType): Promise<boolean>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 请求全局开关的UIAbility/UIExtensionAbility的Context。若传入其他应用、无效页面或非Stage模型的Context，接口可能报错或无法拉起弹窗。 |
| type | [SwitchType](arkts-ability-abilityaccessctrl-switchtype-e.md) | 是 | 指定需要请求开启的全局开关类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前全局开关处于开启状态；返回false表示当前全局开关仍处于关闭状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. Possible causes: 1. The context is invalid because it does not belong to the application itself; 2. The type of global switch is not supported. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. An error occurs when creating the pop-up window or obtaining user operation result. |
| [12100013](../errorcode-access-token.md#12100013-全局开关已开启) | The specific global switch is already open. |

**示例：**

示例中context的获取方式请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { abilityAccessCtrl, Context, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 请在组件内获取context
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 拉起全局开关设置弹窗
atManager.requestGlobalSwitch(context, abilityAccessCtrl.SwitchType.CAMERA).then((data: boolean) => {
  console.info(`requestGlobalSwitch success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`requestGlobalSwitch fail, code: ${err.code}, message: ${err.message}`);
});

```

<a id="requestpermissiononsetting"></a>
## requestPermissionOnSetting

```TypeScript
requestPermissionOnSetting(context: Context, permissionList: Array<Permissions>): Promise<Array<GrantStatus>>
```

用于[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)/[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)二次拉起权限设置弹窗，返回授权状态数组。使用Promise异步回调。

适用于用户在首次弹窗中已拒绝过该权限授予，需要通过设置页面继续申请权限的场景。

在调用此接口前，应用需要先调用[requestPermissionsFromUser](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissionsfromuser-1)。如果用户已在首次弹窗中授权，则调用当前接口不会拉起授权弹窗。

<!--RP4-->

![requestPermissionOnSetting](docroot://reference/apis-ability-kit/figures/requestPermissionOnSetting.png)

<!--RP4End-->

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-requestPermissionOnSetting(context: Context, permissionList: Array<Permissions>): Promise<Array<GrantStatus>>--><!--Device-AtManager-requestPermissionOnSetting(context: Context, permissionList: Array<Permissions>): Promise<Array<GrantStatus>>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 请求权限的UIAbility/UIExtensionAbility的Context。若传入其他应用、无效页面或非Stage模型的Context，接口可能报错或无法拉起弹窗。 |
| permissionList | Array&lt;Permissions&gt; | 是 | 权限名列表。该数组不能为空，仅支持传入已声明且用户已撤销授权的user_grant权限，且传入权限需属于同一[权限组](docroot://security/AccessToken/app-permission-group-list.md)。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;GrantStatus&gt;&gt; | Promise对象，返回授权状态数组，数组中每个元素对应permissionList中相应权限的授权结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. Possible causes: 1. The context is invalid because it does not belong to the application itself; 2. The permission list contains the permission that is not declared in the module.json file; 3. The permission list is invalid because the permissions in it do not belong to the same permission group; 4. The permission list contains one or more system_grant permissions. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. An error occurs when creating the pop-up window or obtaining the user operation result. |
| [12100010](../errorcode-access-token.md#12100010-存在未被处理的请求) | The request already exists.<br>**适用版本：** 12 - 20 |
| [12100011](../errorcode-access-token.md#12100011-输入的所有权限均已被授权) | All permissions in the permission list have been granted. |
| [12100012](../errorcode-access-token.md#12100012-输入的权限中存在未被用户拒绝过的权限) | The permission list contains the permission that has not been revoked by the user. |
| [12100014](../errorcode-access-token.md#12100014-非预期的权限) | Unexpected permission. You cannot request this type of permission from users via a pop-up window.<br>**适用版本：** 21+ |

**示例：**

示例中context的获取方式请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { abilityAccessCtrl, Context, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 请在组件内获取context
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 拉起权限设置弹窗
atManager.requestPermissionOnSetting(context, ['ohos.permission.CAMERA']).then((data: Array<abilityAccessCtrl.GrantStatus>) => {
  console.info(`requestPermissionOnSetting success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`requestPermissionOnSetting fail, code: ${err.code}, message: ${err.message}`);
});

```

<a id="requestpermissionsfromuser"></a>
## requestPermissionsFromUser

```TypeScript
requestPermissionsFromUser(context: Context, permissionList: Array<Permissions>, requestCallback: AsyncCallback<PermissionRequestResult>) : void
```

用于<!--RP1-->[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)<!--RP1End-->拉起弹窗请求[用户授权](docroot://security/AccessToken/request-user-authorization.md)，返回本次请求权限的授权结果。使用callback异步回调。

适用于应用首次访问受保护资源前主动向用户申请[user_grant](docroot://security/AccessToken/app-permission-mgmt-overview.md#user_grant用户授权) 权限的场景。

如果用户拒绝授权，将无法通过此接口再次拉起授权弹窗。开发者可引导用户前往系统设置界面手动授权，或调用[requestPermissionOnSetting](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissiononsetting-1)拉起权限设置弹窗，引导用户完成授权。

<!--RP3-->

![requestPermissionsFromUser](docroot://reference/apis-ability-kit/figures/requestPermissionsFromUser.png)

<!--RP3End-->

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-requestPermissionsFromUser(context: Context, permissionList: Array<Permissions>, requestCallback: AsyncCallback<PermissionRequestResult>) : void--><!--Device-AtManager-requestPermissionsFromUser(context: Context, permissionList: Array<Permissions>, requestCallback: AsyncCallback<PermissionRequestResult>) : void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 请求权限的<!--RP1-->UIAbility<!--RP1End-->的Context。<br>若传入其他应用、无效页面或非Stage模型的Context，接口可能报错或无法拉起弹窗。 |
| permissionList | Array&lt;Permissions&gt; | 是 | 权限名列表。建议仅传入当前业务场景必要的敏感权限，避免一次申请过多权限。<br>最小长度为1。取值约束：权限名长度不能超过256个字符。 |
| requestCallback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PermissionRequestResult&gt; | 是 | 回调函数。调用完成后通过err返回错误信息，通过data返回权限请求结果对象。开发者可根据权限请求结果判断用户是否授权、是否展示过弹窗以及失败原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | (Deprecated in 12) Invalid parameter. The context is invalid when it does not belong to the application itself. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. An error occurs when creating the pop-up window or obtaining user operation results. |

**示例：**

关于向用户申请授权的完整流程及示例，请参见[向用户申请授权](../../security/AccessToken/request-user-authorization.md)。

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 请在组件内获取context
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 请求用户授权
atManager.requestPermissionsFromUser(context, ['ohos.permission.CAMERA'], (err: BusinessError, data: PermissionRequestResult) => {
  if (err) {
    console.error(`requestPermissionsFromUser fail, code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`requestPermissionsFromUser success, result: ${data}`);
    console.info('requestPermissionsFromUser data permissions:' + data.permissions);
    console.info('requestPermissionsFromUser data authResults:' + data.authResults);
    console.info('requestPermissionsFromUser data dialogShownResults:' + data.dialogShownResults);
    console.info('requestPermissionsFromUser data errorReasons:' + data.errorReasons);
  }
});

```

<a id="requestpermissionsfromuser-1"></a>
## requestPermissionsFromUser

```TypeScript
requestPermissionsFromUser(context: Context, permissionList: Array<Permissions>) : Promise<PermissionRequestResult>
```

用于<!--RP1-->[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)<!--RP1End-->拉起弹窗请求[用户授权](docroot://security/AccessToken/request-user-authorization.md)，返回本次请求权限的授权结果。使用Promise异步回调。

适用于应用首次访问受保护资源前主动向用户申请user_grant权限的场景。

> **说明**  
> 如果用户拒绝授权，将无法通过此接口再次拉起授权弹窗。开发者可引导用户前往系统设置界面手动授权，或调用  
> [requestPermissionOnSetting](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissiononsetting-1)拉起权限设置弹窗，引导用户完成授权。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AtManager-requestPermissionsFromUser(context: Context, permissionList: Array<Permissions>) : Promise<PermissionRequestResult>--><!--Device-AtManager-requestPermissionsFromUser(context: Context, permissionList: Array<Permissions>) : Promise<PermissionRequestResult>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 请求权限的<!--RP1-->UIAbility<!--RP1End-->的Context。若传入其他应用、无效页面或非Stage模型的Context，接口可能报错或无法拉起弹窗。 |
| permissionList | Array&lt;Permissions&gt; | 是 | 权限名列表。建议仅传入当前业务场景必要的敏感权限，避免一次申请过多权限。<br>最小长度为1。取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PermissionRequestResult&gt; | Promise对象，返回权限请求结果对象，包含权限数组、每个权限的授权结果、是否展示弹窗以及失败原因等信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | (Deprecated in 12) Invalid parameter. The context is invalid when it does not belong to the application itself. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. An error occurs when creating the pop-up window or obtaining the user operation result.<br>**适用版本：** 11+ |

**示例：**

关于向用户申请授权的完整流程及示例，请参见[向用户申请授权](../../security/AccessToken/request-user-authorization.md)。

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 请在组件内获取context
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 请求用户授权
atManager.requestPermissionsFromUser(context, ['ohos.permission.CAMERA']).then((data: PermissionRequestResult) => {
  console.info(`requestPermissionsFromUser success, result: ${data}`);
  console.info('requestPermissionsFromUser data permissions:' + data.permissions);
  console.info('requestPermissionsFromUser data authResults:' + data.authResults);
  console.info('requestPermissionsFromUser data dialogShownResults:' + data.dialogShownResults);
  console.info('requestPermissionsFromUser data errorReasons:' + data.errorReasons);
}).catch((err: BusinessError): void => {
  console.error(`requestPermissionsFromUser fail, code: ${err.code}, message: ${err.message}`);
});

```

<a id="verifyaccesstoken"></a>
## verifyAccessToken

```TypeScript
verifyAccessToken(tokenID: number, permissionName: Permissions): Promise<GrantStatus>
```

校验应用是否已被授予指定权限，调用成功后，返回当前权限的授权状态，开发者可据此决定直接执行后续业务、继续发起权限申请，或引导用户前往系统设置修改授权状态。使用Promise异步回调。

适用于应用访问受保护资源前进行前置权限判断的场景。

> **说明**  
> 建议使用[checkAccessToken](#checkaccesstoken9)替代。

**起始版本：** 9

<!--Device-AtManager-verifyAccessToken(tokenID: int, permissionName: Permissions): Promise<GrantStatus>--><!--Device-AtManager-verifyAccessToken(tokenID: int, permissionName: Permissions): Promise<GrantStatus>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 要校验的目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)；<br>若校验本应用，也可通过[bundleManager.getBundleInfoForSelfSync](arkts-ability-bundlemanager-getbundleinfoforselfsync-f.md#getbundleinfoforselfsync-1)获取。 |
| permissionName | Permissions | 是 | 需要校验的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;GrantStatus&gt; | Promise对象，返回授权状态结果。 |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 获取应用的bundleInfo信息
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// 获取应用的TokenID
let tokenID: number = bundleInfo.appInfo.accessTokenId;
// 设置需要校验的权限名
let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
// 校验应用是否被授予权限
atManager.verifyAccessToken(tokenID, permissionName).then((data: abilityAccessCtrl.GrantStatus) => {
  console.info(`verifyAccessToken success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`verifyAccessToken fail, code: ${err.code}, message: ${err.message}`);
});

```

<a id="verifyaccesstoken-1"></a>
## verifyAccessToken

```TypeScript
verifyAccessToken(tokenID: number, permissionName: string): Promise<GrantStatus>
```

校验应用是否已被授予指定权限。调用成功后，返回当前权限的授权状态，开发者可据此决定后续操作。使用Promise异步回调。

> **说明**  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[checkAccessToken](#checkaccesstoken9)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** checkAccessToken

<!--Device-AtManager-verifyAccessToken(tokenID: number, permissionName: string): Promise<GrantStatus>--><!--Device-AtManager-verifyAccessToken(tokenID: number, permissionName: string): Promise<GrantStatus>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 要校验的目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)；<br>若校验本应用，也可通过[bundleManager.getBundleInfoForSelfSync](arkts-ability-bundlemanager-getbundleinfoforselfsync-f.md#getbundleinfoforselfsync-1)获取。 |
| permissionName | string | 是 | 需要校验的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;GrantStatus&gt; | Promise对象，返回授权状态结果。 |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 获取应用的bundleInfo信息
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// 获取应用的TokenID
let tokenID: number = bundleInfo.appInfo.accessTokenId;
// 设置需要校验的权限名
let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
// 校验应用是否被授予权限
atManager.verifyAccessToken(tokenID, permissionName).then((data: abilityAccessCtrl.GrantStatus) => {
  console.info(`verifyAccessToken success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`verifyAccessToken fail, code: ${err.code}, message: ${err.message}`);
});

```

<a id="verifyaccesstokensync"></a>
## verifyAccessTokenSync

```TypeScript
verifyAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus
```

校验应用是否已被授予指定权限，同步返回该权限的授权状态。开发者可据此决定直接执行后续业务流程，或继续发起权限申请，或引导用户前往系统设置修改授权状态。

适用于应用访问相机、麦克风、位置等受保护资源前进行前置权限判断的场景。

建议使用[checkAccessTokenSync](arkts-ability-abilityaccessctrl-atmanager-i.md#checkaccesstokensync-1)替代。

**起始版本：** 9

<!--Device-AtManager-verifyAccessTokenSync(tokenID: int, permissionName: Permissions): GrantStatus--><!--Device-AtManager-verifyAccessTokenSync(tokenID: int, permissionName: Permissions): GrantStatus-End-->

**系统能力：** SystemCapability.Security.AccessToken

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 要校验的目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。该参数必须为大于0的整数，传入0时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)；<br>若校验本应用，也可通过[bundleManager.getBundleInfoForSelfSync](arkts-ability-bundlemanager-getbundleinfoforselfsync-f.md#getbundleinfoforselfsync-1)获取。 |
| permissionName | Permissions | 是 | 需要校验的权限名称。权限名长度不能超过256个字符，传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GrantStatus](arkts-ability-abilityaccessctrl-grantstatus-e.md) | 枚举实例，返回授权状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, or the permissionName exceeds 256characters. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建权限管理器实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 获取应用的bundleInfo信息
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// 获取应用的TokenID
let tokenID: number = bundleInfo.appInfo.accessTokenId;
try {
  // 设置需要校验的权限名
  let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
  // 同步校验应用是否被授予权限
  let data: abilityAccessCtrl.GrantStatus = atManager.verifyAccessTokenSync(tokenID, permissionName);
  console.info(`verifyAccessTokenSync success, result: ${data}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`verifyAccessTokenSync fail, code: ${error.code}, message: ${error.message}`);
}

```

