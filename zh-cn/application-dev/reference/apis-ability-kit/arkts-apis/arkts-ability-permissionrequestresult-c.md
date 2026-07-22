# PermissionRequestResult

PermissionRequestResult是权限申请的结果对象。开发者需先创建atManager实例，再调用requestPermissionsFromUser方法申请权限，该方法返回PermissionRequestResult对象，开发者可通过该对象的属性判断权限申请结果。权限申请整体流程及atManager的详细说明请参见[@ohos.abilityAccessCtrl (程序访问控制管理)](arkts-abilityaccessctrl.md)。

**起始版本：** 9

<!--Device-unnamed-declare class PermissionRequestResult--><!--Device-unnamed-declare class PermissionRequestResult-End-->

**系统能力：** SystemCapability.Security.AccessToken

## authResults

```TypeScript
authResults: Array<number>
```

每个请求权限对应的授权结果。

- -1：未授权。从API version 12开始，可结合dialogShownResults进一步判断原因：若dialogShownResults为true，表示用户在本次申请中明确拒绝；若为false，表示当前状态无需再弹窗，通常需要用户前往系统设置修改。  
- 0：已授权，应用可以继续访问与该权限关联的受保护资源。  
- 2：请求无效，通常表示权限未声明、权限名非法，或未满足该权限的特殊申请条件。开发者应检查权限名、module.json中的权限声明以及对应权限的申请条件。

**类型：** Array&lt;number&gt;

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequestResult-authResults: Array<int>--><!--Device-PermissionRequestResult-authResults: Array<int>-End-->

**系统能力：** SystemCapability.Security.AccessToken

## dialogShownResults

```TypeScript
dialogShownResults?: Array<boolean>
```

表示每个权限在本次申请过程中是否真正展示过授权弹窗。

- true：系统已展示授权弹窗。  
- false：系统未展示弹窗，通常是因为权限当前状态、权限类型或系统策略不允许继续走弹窗授权链路。

当authResults为-1时，结合本字段可进一步区分“本次被用户拒绝”与“当前已不再弹窗”。未返回该字段时，表示本次结果不包含授权弹窗展示状态。

**类型：** Array&lt;boolean&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequestResult-dialogShownResults?: Array<boolean>--><!--Device-PermissionRequestResult-dialogShownResults?: Array<boolean>-End-->

**系统能力：** SystemCapability.Security.AccessToken

## errorReasons

```TypeScript
errorReasons?: Array<number>
```

每个权限申请对应的原因码。主要用于解释授权失败、请求无效或无法展示弹窗的具体原因。未返回该字段时，表示本次结果不包含原因码。

- 0：本次申请合法。  
- 1：权限名非法，请检查权限名格式和取值。  
- 2：权限未声明，请在module.json中声明该权限。  
- 3：不满足对应权限的申请条件，例如部分位置权限需要满足额外前提。当前仅位置权限涉及，包括[ohos.permission.LOCATION](../../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation)与[ohos.permission.APPROXIMATELY_LOCATION](../../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location)。  
- 4：用户未同意隐私声明，请引导用户同意隐私声明后再申请权限。  
- 5：该权限不支持通过权限弹窗进行申请，可能是申请方式受限或被系统策略管控。请改用该权限支持的授权方式。  
- 6：该权限为[manual_settings](../../../security/AccessToken/app-permission-mgmt-overview.md#manual_settings手动设置授权)类型，只能通过设置页授权。从API version 21开始支持该原因码。  
- 12：服务异常，请稍后重试。

**类型：** Array&lt;number&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequestResult-errorReasons?: Array<int>--><!--Device-PermissionRequestResult-errorReasons?: Array<int>-End-->

**系统能力：** SystemCapability.Security.AccessToken

## permissions

```TypeScript
permissions: Array<string>
```

本次待申请的权限数组。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequestResult-permissions: Array<string>--><!--Device-PermissionRequestResult-permissions: Array<string>-End-->

**系统能力：** SystemCapability.Security.AccessToken

