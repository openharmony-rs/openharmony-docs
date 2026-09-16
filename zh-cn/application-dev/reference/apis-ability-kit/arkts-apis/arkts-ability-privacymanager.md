# @ohos.privacyManager(Privacy Management)

**起始版本：** 9

**系统能力：** SystemCapability.Security.AccessToken

## Core Enum Types

- **[PermissionUsageFlag](arkts-ability-privacymanager-permissionusageflag-e-sys.md):** 权限使用记录查询方式枚举，用于指定查询汇总数据或明细数据。  
 - **[PermissionActiveStatus](arkts-ability-privacymanager-permissionactivestatus-e-sys.md):** 权限使用状态变化类型枚举，用于表示未使用、前台使用或后台使用状态。  
 - **[PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md):** 敏感权限使用类型枚举，用于表示通过普通授权、Picker或安全控件方式使用敏感权限。

## Core Interface Types

- **[PermissionUsedRequest](arkts-ability-privacymanager-permissionusedrequest-i-sys.md):** 权限使用记录查询请求对象，用于指定查询应用、权限、时间范围和查询方式。  
 - **[PermissionUsedResponse](arkts-ability-privacymanager-permissionusedresponse-i-sys.md):** 权限使用记录查询响应对象，用于返回查询时间范围和应用维度记录集合。  
 - **[BundleUsedRecord](arkts-ability-privacymanager-bundleusedrecord-i-sys.md):** 应用或设备维度的权限使用记录对象，用于返回某个应用或远端设备的权限访问记录。  
 - **[PermissionUsedRecord](arkts-ability-privacymanager-permissionusedrecord-i-sys.md):** 单个权限的访问记录对象，用于返回访问次数、拒绝次数、最后访问时间和明细记录。  
 - **[UsedRecordDetail](arkts-ability-privacymanager-usedrecorddetail-i-sys.md):** 单次访问记录详情对象，用于返回访问状态、时间戳、访问时长和使用类型等信息。  
 - **[ActiveChangeResponse](arkts-ability-privacymanager-activechangeresponse-i-sys.md):** 权限使用状态变化事件对象，用于返回权限活跃状态变化详情。  
 - **[PermissionUsedTypeInfo](arkts-ability-privacymanager-permissionusedtypeinfo-i-sys.md):** 权限使用类型信息对象，用于返回应用访问敏感权限时的使用类型。  
 - **[AddPermissionUsedRecordOptions](arkts-ability-privacymanager-addpermissionusedrecordoptions-i-sys.md):** 添加权限使用记录可选参数对象，用于指定敏感权限使用类型和扩展身份。  
 - **[PermissionUsingOptions](arkts-ability-privacymanager-permissionusingoptions-i-sys.md):** 权限使用可选参数对象，用于指定扩展身份。

## Core Function Types

- **[addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md):** 添加权限使用记录。  
 - **[getPermissionUsedRecord](arkts-ability-privacymanager-getpermissionusedrecord-f-sys.md):** 查询权限使用记录。  
 - **[setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md):** 设置权限使用记录开关状态。  
 - **[getPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-getpermissionusedrecordtogglestatus-f-sys.md):** 查询权限使用记录开关状态。  
 - **[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md):** 标记开始使用敏感权限。  
 - **[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md):** 标记停止使用敏感权限。  
 - **[checkPermissionInUse](arkts-ability-privacymanager-checkpermissioninuse-f-sys.md):** C检查指定权限当前是否正在被使用。  
 - **[on](arkts-ability-privacymanager-on-f-sys.md):** 订阅权限使用状态变化事件。  
 - **[off](arkts-ability-privacymanager-off-f-sys.md):** 取消订阅权限使用状态变化事件。  
 - **[getPermissionUsedTypeInfos](arkts-ability-privacymanager-getpermissionusedtypeinfos-f-sys.md):** 查询敏感权限访问类型信息。

## Core Class

- **privacyManager:** Provides the core class for privacy management.

![image_privacyManager](../../../reference/apis-ability-kit/figures/privacyManager.png)

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md) | 受权限保护的应用在被其他服务、应用调用时，可以使用该接口增加一条权限使用记录。建议在访问敏感权限后调用此接口，以便系统记录对应的敏感权限访问事件。使用Promise异步回调。 |
| [addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md) | 受权限保护的应用在被其他服务、应用调用时，可以使用该接口增加一条权限使用记录。建议在访问敏感权限后调用此接口，以便系统记录对应的敏感权限访问事件。使用callback异步回调。 |
| [checkPermissionInUse](arkts-ability-privacymanager-checkpermissioninuse-f-sys.md) | 查询指定敏感权限是否正在被使用，可用于权限管理界面展示权限实时使用状态场景。判断依据为当前是否存在通过[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md)标记开始使用且尚未通过[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md)标记停止使用的活跃调用。 |
| [getPermissionUsedRecord](arkts-ability-privacymanager-getpermissionusedrecord-f-sys.md) | 获取历史权限使用记录，可用于权限审计或安全监控场景，例如检查某应用在指定时间段内对敏感权限的使用情况。使用Promise异步回调。 |
| [getPermissionUsedRecord](arkts-ability-privacymanager-getpermissionusedrecord-f-sys.md) | 获取历史权限使用记录，可用于权限审计或安全监控场景，例如检查某应用在指定时间段内对敏感权限的使用情况。使用callback异步回调。 |
| [getPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-getpermissionusedrecordtogglestatus-f-sys.md) | 系统应用调用此接口，可以获取当前用户的权限使用记录开关状态，例如在权限管理界面展示当前开关设置状态。使用Promise异步回调。 |
| [getPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-getpermissionusedrecordtogglestatus-f-sys.md) | 系统应用调用此接口，可以获取指定子身份资料的权限使用记录开关状态，例如在权限管理界面展示当前开关设置状态。使用Promise异步回调。 |
| [getPermissionUsedTypeInfos](arkts-ability-privacymanager-getpermissionusedtypeinfos-f-sys.md) | 查询设备上指定应用访问敏感权限时的信息（包括敏感权限名称、敏感权限访问方式）。 |
| [off](arkts-ability-privacymanager-off-f-sys.md#offactivestatechange) | 取消订阅指定权限列表的权限使用状态变更事件。取消订阅成功后，将不再接收指定权限列表的状态变更通知。 |
| [on](arkts-ability-privacymanager-on-f-sys.md#onactivestatechange) | 订阅指定权限列表的权限使用状态变更事件。权限使用状态变更由[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md)和[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md)调用触发。订阅成功后，当权限使用状态变更时，回调函数会被触发，返回[ActiveChangeResponse](arkts-ability-privacymanager-activechangeresponse-i-sys.md)对象，包含权限使用状态变化的详情。使用callback异步回调。 |
| [setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md) | 设置是否记录当前用户的权限使用情况。系统应用调用此接口，可以设置当前用户的权限使用记录开关状态。使用Promise异步回调。 |
| [setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md) | 设置是否记录指定子身份资料的权限使用情况。系统应用调用此接口，可以设置指定子身份资料的权限使用记录开关状态。使用Promise异步回调。 |
| [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](arkts-ability-privacymanager-on-f-sys.md)）。使用Promise异步回调。 |
| [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](arkts-ability-privacymanager-on-f-sys.md#onactivestatechange)）。使用Promise异步回调。 |
| [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](arkts-ability-privacymanager-on-f-sys.md#onactivestatechange)）。使用Promise异步回调。 |
| [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](arkts-ability-privacymanager-on-f-sys.md#onactivestatechange)）。使用callback异步回调。 |
| [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。 |
| [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用callback异步回调。 |
| [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。 |
| [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActiveChangeResponse](arkts-ability-privacymanager-activechangeresponse-i-sys.md) | 表示某次权限使用状态变化的详情。 |
| [AddPermissionUsedRecordOptions](arkts-ability-privacymanager-addpermissionusedrecordoptions-i-sys.md) | 添加权限使用记录可选参数集。 |
| [BundleUsedRecord](arkts-ability-privacymanager-bundleusedrecord-i-sys.md) | 某个应用或设备的访问记录。 |
| [PermissionUsedRecord](arkts-ability-privacymanager-permissionusedrecord-i-sys.md) | 某个权限的访问记录。 |
| [PermissionUsedRequest](arkts-ability-privacymanager-permissionusedrequest-i-sys.md) | 表示使用记录的查询请求。 |
| [PermissionUsedResponse](arkts-ability-privacymanager-permissionusedresponse-i-sys.md) | 表示所有应用或设备的访问记录。 |
| [PermissionUsedTypeInfo](arkts-ability-privacymanager-permissionusedtypeinfo-i-sys.md) | 表示某次权限使用类型的详情。 |
| [PermissionUsingOptions](arkts-ability-privacymanager-permissionusingoptions-i-sys.md) | 权限使用可选参数集。 |
| [UsedRecordDetail](arkts-ability-privacymanager-usedrecorddetail-i-sys.md) | 单次访问记录详情。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PermissionActiveStatus](arkts-ability-privacymanager-permissionactivestatus-e-sys.md) | 表示权限使用状态变化类型的枚举。用于描述权限使用[on)](arkts-ability-privacymanager-on-f-sys.md)）的回调中返回，帮助应用感知权限从未使用到前台使用、后台使用的状态切换。 |
| [PermissionUsageFlag](arkts-ability-privacymanager-permissionusageflag-e-sys.md) | 表示使用记录的查询方式的枚举。 |
| [PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md) | 表示通过何种方式使用敏感权限的枚举。 |
<!--DelEnd-->
