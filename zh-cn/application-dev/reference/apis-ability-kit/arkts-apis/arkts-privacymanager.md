# @ohos.privacyManager(Privacy Management)

###### Core Enum Types
 - **PermissionUsageFlag:** 权限使用记录查询方式枚举，用于指定查询汇总数据或明细数据。
 - **PermissionActiveStatus:** 权限使用状态变化类型枚举，用于表示未使用、前台使用或后台使用状态。
 - **PermissionUsedType:** 敏感权限使用类型枚举，用于表示通过普通授权、Picker或安全控件方式使用敏感权限。
 ###### Core Interface Types
 - **PermissionUsedRequest:** 权限使用记录查询请求对象，用于指定查询应用、权限、时间范围和查询方式。
 - **PermissionUsedResponse:** 权限使用记录查询响应对象，用于返回查询时间范围和应用维度记录集合。
 - **BundleUsedRecord:** 应用或设备维度的权限使用记录对象，用于返回某个应用或远端设备的权限访问记录。
 - **PermissionUsedRecord:** 单个权限的访问记录对象，用于返回访问次数、拒绝次数、最后访问时间和明细记录。
 - **UsedRecordDetail:** 单次访问记录详情对象，用于返回访问状态、时间戳、访问时长和使用类型等信息。
 - **ActiveChangeResponse:** 权限使用状态变化事件对象，用于返回权限活跃状态变化详情。
 - **PermissionUsedTypeInfo:** 权限使用类型信息对象，用于返回应用访问敏感权限时的使用类型。
 - **AddPermissionUsedRecordOptions:** 添加权限使用记录可选参数对象，用于指定敏感权限使用类型和扩展身份。
 - **PermissionUsingOptions:** 权限使用可选参数对象，用于指定扩展身份。
 ###### Core Function Types
 - **addPermissionUsedRecord:** 添加权限使用记录。
 - **getPermissionUsedRecord:** 查询权限使用记录。
 - **setPermissionUsedRecordToggleStatus:** 设置权限使用记录开关状态。
 - **getPermissionUsedRecordToggleStatus:** 查询权限使用记录开关状态。
 - **startUsingPermission:** 标记开始使用敏感权限。
 - **stopUsingPermission:** 标记停止使用敏感权限。
 - **checkPermissionInUse:** C检查指定权限当前是否正在被使用。
 - **on:** 订阅权限使用状态变化事件。
 - **off:** 取消订阅权限使用状态变化事件。
 - **getPermissionUsedTypeInfos:** 查询敏感权限访问类型信息。
 ###### Core Class
 - **privacyManager:** Provides the core class for privacy management.
 


**起始版本：** 9

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
| addPermissionUsedRecord(Privacy Management) | 受权限保护的应用在被其他服务、应用调用时，可以使用该接口增加一条权限使用记录。 建议在访问敏感权限后调用此接口，以便系统记录对应的敏感权限访问事件。使用Promise异步回调。权限使用记录包括：调用方的应用身份标识、使用的应用权限名称，以及调用方访问本应用成功和失败的次数。权限使用记录受setPermissionUsedRecordToggleStatus设置的开关状态控制。 开关关闭时，调用此接口不会产生权限使用记录。 |
| addPermissionUsedRecord(Privacy Management) | 受权限保护的应用在被其他服务、应用调用时，可以使用该接口增加一条权限使用记录。建议在访问敏感权限后调用此接口，以便系统记录对应的敏感权限访问事件。使用callback异步回调。权限使用记录包括：调用方的应用身份标识、使用的应用权限名称，以及调用方访问本应用成功和失败的次数。权限使用记录受setPermissionUsedRecordToggleStatus设置的开关状态控制。开关关 闭时，调用此接口不会产生权限使用记录。 |
| checkPermissionInUse(Privacy Management) | 查询指定敏感权限是否正在被使用，可用于权限管理界面展示权限实时使用状态场景。 判断依据为当前是否存在通过startUsingPermission 标记开始使用且尚未通过stopUsingPermission标记停止使用的活跃调用。 |
| getPermissionUsedRecord(Privacy Management) | 获取历史权限使用记录，可用于权限审计或安全监控场景，例如检查某应用在指定时间段内对敏感权限的使用情况。使用Promise异步回调。 |
| getPermissionUsedRecord(Privacy Management) | 获取历史权限使用记录，可用于权限审计或安全监控场景，例如检查某应用在指定时间段内对敏感权限的使用情况。使用callback异步回调。 |
| getPermissionUsedRecordToggleStatus(Privacy Management) | 系统应用调用此接口，可以获取当前用户的权限使用记录开关状态，例如在权限管理界面展示当前开关设置状态。使用Promise异步回调。 |
| getPermissionUsedRecordToggleStatus(Privacy Management) | 系统应用调用此接口，可以获取指定子身份资料的权限使用记录开关状态，例如在权限管理界面展示当前开关设置状态。使用Promise异步回调。 |
| getPermissionUsedTypeInfos(Privacy Management) | 查询设备上指定应用访问敏感权限时的信息（包括敏感权限名称、敏感权限访问方式）。 |
| off(Privacy Management) | 取消订阅指定权限列表的权限使用状态变更事件。取消订阅成功后，将不再接收指定权限列表的状态变更通知。取消订阅时，若不传入回调函数，则批量删除permissionList下的所有回调函数。 |
| on(Privacy Management) | 订阅指定权限列表的权限使用状态变更事件。权限使用状态变更由startUsingPermission和stopUsingPermission调用触发。订阅成功后，当权限使用状态变更时，回调函数会被触发，返回ActiveChangeResponse对象，包含权限使用状态变化的详情。使用callback异步回调。允许相同permissionList订阅多个回调函数。 |
| setPermissionUsedRecordToggleStatus(Privacy Management) | 设置是否记录当前用户的权限使用情况。系统应用调用此接口，可以设置当前用户的权限使用记录开关状态。使用Promise异步回调。status为true时，addPermissionUsedRecord接口可以正常添加使用记录；status为false时， addPermissionUsedRecord接口不产生权限使用记录，并且删除当前用户的历史记录。 |
| setPermissionUsedRecordToggleStatus(Privacy Management) | 设置是否记录指定子身份资料的权限使用情况。系统应用调用此接口，可以设置指定子身份资料的权限使用记录开关状态。使用Promise异步回调。status为true时，addPermissionUsedRecord接口可以正常添加使用记录；status为false时，addPermissionUsedRecord]addPermissionUsedRecord接口不产生权限使用记录，并且删除指定子身份资料的历史记录。 |
| startUsingPermission(Privacy Management) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考on）。使用Promise异步回调。开始使用权限后，需要在权限使用结束时调用stopUsingPermission停止使用权限。 |
| startUsingPermission(Privacy Management) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考 on）。 使用Promise异步回调。开始使用权限后，需要在权限使用结束时调用 stopUsingPermission 停止使用权限。 |
| startUsingPermission(Privacy Management) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考 on ）。使用Promise异步回调。开始使用权限后，需要在权限使用结束时调用 stopUsingPermission 停止使用权限。当传入pid时，pid需要与 stopUsingPermission 传入的pid相同，不满足配套关系返回错误码12100004。 |
| startUsingPermission(Privacy Management) | 系统应用调用此接口，能够向系统上报应用在前后台的权限使用状态。隐私服务将此状态通知所有该权限使用状态变更事件的订阅者（订阅方法参考 on ）。使用callback异步回调。开始使用权限后，需要在权限使用结束时调用 stopUsingPermission 停止使用权限。 |
| stopUsingPermission(Privacy Management) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。 适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。该接口需与startUsingPermission配套使用。 |
| stopUsingPermission(Privacy Management) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。 适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用callback异步回调。该接口需与startUsingPermission配套使用。 |
| stopUsingPermission(Privacy Management) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。 适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。pid需要与startUsingPermission传入的pid相同。 |
| stopUsingPermission(Privacy Management) | 系统应用调用此接口，标记不再使用指定权限。调用成功后，隐私服务将此状态变化通知所有该权限使用状态变更事件的订阅者。适用于应用完成敏感操作后或退出前台时，通知系统权限使用结束。使用Promise异步回调。pid需要与 startUsingPermission 传入的pid相同。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| ActiveChangeResponse(Privacy Management) | 表示某次权限使用状态变化的详情。 |
| AddPermissionUsedRecordOptions(Privacy Management) | 添加权限使用记录可选参数集。 |
| BundleUsedRecord(Privacy Management) | 某个应用或设备的访问记录。 |
| PermissionUsedRecord(Privacy Management) | 某个权限的访问记录。 |
| PermissionUsedRequest(Privacy Management) | 表示使用记录的查询请求。 |
| PermissionUsedResponse(Privacy Management) | 表示所有应用或设备的访问记录。 |
| PermissionUsedTypeInfo(Privacy Management) | 表示某次权限使用类型的详情。 |
| PermissionUsingOptions(Privacy Management) | 权限使用可选参数集。 |
| UsedRecordDetail(Privacy Management) | 单次访问记录详情。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| PermissionActiveStatus(Privacy Management) | 表示权限使用状态变化类型的枚举。用于描述权限使用on)）的回调中返回，帮助应用感知权限从未使用到前台使用、后台使用的状态切换。 |
| PermissionUsageFlag(Privacy Management) | 表示使用记录的查询方式的枚举。 |
| PermissionUsedType(Privacy Management) | 表示通过何种方式使用敏感权限的枚举。  \| 名称 \| 值 \| 说明 \| \| ----------------------- \| -- \| ---------------- \| \| NORMAL_TYPE \| 0 \| 表示通过弹窗授权或设置授权来使用敏感权限。 \| \| PICKER_TYPE \| 1 \| 表示通过某个PICKER服务来使用敏感权限，但此方式不会授予权限。 \| \| SECURITY_COMPONENT_TYPE \| 2 \| 表示通过安全控件授权的方式来使用敏感权限。安全控件是系统提供的授权控件，用户点击后应用可临时获取对应权限。 \| |
<!--DelEnd-->
