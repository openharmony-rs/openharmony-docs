# @ohos.privacyManager

本模块主要提供权限使用记录等隐私管理接口，支持系统应用记录、查询、监听和控制敏感权限的使用情况。权限使用记录用于描述某项敏感权限何时被使用、以何种方式被使用、当前是否处于使用中，以及这些使用记录是否允许被记录或查询。

该模块主要用于以下场景：

- 添加/查询指定应用的敏感权限访问记录。  
- 订阅权限使用状态变化事件，感知权限从未使用到前台使用、后台使用的变化，与业务逻辑进行联动。  
- 控制当前用户的权限访问记录开关。  
- 查询某个权限当前是否正在被使用。

**起始版本：** 9

<!--Device-unnamed-declare namespace privacyManager--><!--Device-unnamed-declare namespace privacyManager-End-->

**系统能力：** SystemCapability.Security.AccessToken

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord) | 受权限保护的应用在被其他服务、应用调用时，可以使用该接口增加一条权限使用记录。建议在访问敏感权限后调用此接口，以便系统记录对应的敏感权限访问事件。使用Promise异步回调。  权限使用记录包括：调用方的应用身份标识、使用的应用权限名称，以及调用方访问本应用成功和失败的次数。  权限使用记录受[setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md#setpermissionusedrecordtogglestatus-1)设置的开关状态控制。开关关闭时，调用此接口不会产生权限使用记录。 |
| [addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord-1) | 受权限保护的应用在被其他服务、应用调用时，可以使用该接口增加一条权限使用记录。建议在访问敏感权限后调用此接口，以便系统记录对应的敏感权限访问事件。使用callback异步回调。  权限使用记录包括：调用方的应用身份标识、使用的应用权限名称，以及调用方访问本应用成功和失败的次数。  权限使用记录受[setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md#setpermissionusedrecordtogglestatus-1)设置的开关状态控制。开关关闭时，调用此接口不会产生权限使用记录。 |
| [checkPermissionInUse](arkts-ability-privacymanager-checkpermissioninuse-f-sys.md#checkpermissioninuse) | 查询指定敏感权限是否正在被使用，可用于权限管理界面展示权限实时使用状态场景。判断依据为当前是否存在通过[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-1)标记开始使用且尚未通过[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1)标记停止使用的活跃调用。 |
| [getPermissionUsedRecord](arkts-ability-privacymanager-getpermissionusedrecord-f-sys.md#getpermissionusedrecord) | 获取历史权限使用记录，可用于权限审计或安全监控场景，例如检查某应用在指定时间段内对敏感权限的使用情况。使用Promise异步回调。 |
| [getPermissionUsedRecord](arkts-ability-privacymanager-getpermissionusedrecord-f-sys.md#getpermissionusedrecord-1) | 获取历史权限使用记录，可用于权限审计或安全监控场景，例如检查某应用在指定时间段内对敏感权限的使用情况。使用callback异步回调。 |
| [getPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-getpermissionusedrecordtogglestatus-f-sys.md#getpermissionusedrecordtogglestatus) | 系统应用调用此接口，可以获取当前用户的权限使用记录开关状态，例如在权限管理界面展示当前开关设置状态。使用Promise异步回调。 |
| [getPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-getpermissionusedrecordtogglestatus-f-sys.md#getpermissionusedrecordtogglestatus-1) | 系统应用调用此接口，可以获取指定子身份资料的权限使用记录开关状态，例如在权限管理界面展示当前开关设置状态。使用Promise异步回调。 |
| [getPermissionUsedTypeInfos](arkts-ability-privacymanager-getpermissionusedtypeinfos-f-sys.md#getpermissionusedtypeinfos) | 查询设备上指定应用访问敏感权限时的信息（包括敏感权限名称、敏感权限访问方式）。 |
| [off](arkts-ability-privacymanager-off-f-sys.md#off) | 取消订阅指定权限列表的权限使用状态变更事件。取消订阅成功后，将不再接收指定权限列表的状态变更通知。  取消订阅时，若不传入回调函数，则批量删除permissionList下的所有回调函数。  > **说明**  > 该接口通常与[on](privacyManager.on)配套使用，用于取消通过on创建的监听关系。 |
| [on](arkts-ability-privacymanager-on-f-sys.md#on) | 订阅指定权限列表的权限使用状态变更事件。权限使用状态变更由[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-1)和[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1)调用触发。订阅成功后，当权限使用状态变更时，回调函数会被触发，返回[ActiveChangeResponse](arkts-ability-privacymanager-activechangeresponse-i-sys.md)对象，包含权限使用状态变化的详情。使用callback异步回调。  允许相同permissionList订阅多个回调函数。  > **说明**  > 不允许使用有交集的两个permissionList分别订阅同一个回调函数。即如果两个permissionList包含相同的权限名，则不能使用同一个回调函数进行订阅。该接口通常与[off](privacyManager.off)配套使用，在不再需要监听时应调用off取消订阅。 |
| [setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md#setpermissionusedrecordtogglestatus) | 设置是否记录当前用户的权限使用情况。系统应用调用此接口，可以设置当前用户的权限使用记录开关状态。使用Promise异步回调。  status为true时，[addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord-1)接口可以正常添加使用记录；status为false时，[addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord-1)接口不产生权限使用记录，并且删除当前用户的历史记录。 |
| [setPermissionUsedRecordToggleStatus](arkts-ability-privacymanager-setpermissionusedrecordtogglestatus-f-sys.md#setpermissionusedrecordtogglestatus-1) | 设置是否记录指定子身份资料的权限使用情况。系统应用调用此接口，可以设置指定子身份资料的权限使用记录开关状态。使用Promise异步回调。  status为true时，[addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md#addpermissionusedrecord-1)接口可以正常添加使用记录；status为false时，addPermissionUsedRecord]{@link privacyManager.addPermissionUsedRecord}接口不产生权限使用记录，并且删除指定子身份资料的历史记录。 |
| [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](privacyManager.on)）。使用Promise异步回调。  开始使用权限后，需要在权限使用结束时调用[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1)停止使用权限。 |
| [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-1) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](privacyManager.on(type: 'activeStateChange', permissionList: Array<Permissions>, callback: Callback<ActiveChangeResponse>))）。使用Promise异步回调。  开始使用权限后，需要在权限使用结束时调用[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1)停止使用权限。 |
| [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-2) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](privacyManager.on(type: 'activeStateChange', permissionList: Array<Permissions>, callback:Callback<ActiveChangeResponse>))）。使用Promise异步回调。  开始使用权限后，需要在权限使用结束时调用[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1)停止使用权限。  当传入pid时，pid需要与[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1)传入的pid相同，不满足配套关系返回错误码12100004。 |
| [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-3) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考[on](privacyManager.on(type: 'activeStateChange', permissionList: Array<Permissions>, callback: Callback<ActiveChangeResponse>))）。使用callback异步回调。  开始使用权限后，需要在权限使用结束时调用[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1)停止使用权限。 |
| [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。  该接口需与[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-1)配套使用。 |
| [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用callback异步回调。  该接口需与[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-1)配套使用。 |
| [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-2) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。  pid需要与[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-1)传入的pid相同。 |
| [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-3) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。  pid需要与[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-1)传入的pid相同。 |
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
| [PermissionActiveStatus](arkts-ability-privacymanager-permissionactivestatus-e-sys.md) | 表示权限使用状态变化类型的枚举。用于描述权限使用[on)](privacyManager.on)）的回调中返回，帮助应用感知权限从未使用到前台使用、后台使用的状态切换。 |
| [PermissionUsageFlag](arkts-ability-privacymanager-permissionusageflag-e-sys.md) | 表示使用记录的查询方式的枚举。 |
| [PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md) | 表示通过何种方式使用敏感权限的枚举。  \| 名称 \| 值 \| 说明 \|  \| ----------------------- \| -- \| ---------------- \|  \| NORMAL_TYPE \| 0 \| 表示通过弹窗授权或设置授权来使用敏感权限。 \|  \| PICKER_TYPE \| 1 \| 表示通过某个PICKER服务来使用敏感权限，但此方式不会授予权限。 \|  \| SECURITY_COMPONENT_TYPE \| 2 \| 表示通过安全控件授权的方式来使用敏感权限。安全控件是系统提供的授权控件，用户点击后应用可临时获取对应权限。 \| |
<!--DelEnd-->

