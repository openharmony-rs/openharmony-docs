# @ohos.bundle.appControl

本模块提供应用拦截能力。对应用设置处置状态后，应用会被禁止运行；用户点击桌面图标时，会根据应用的处置状态，跳转到对应的页面。本模块支持对应用的处置状态进行设置、获取、删除。

> **说明：**
>
> 本模块为系统接口。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [deleteDisposedStatus](arkts-ability-deletedisposedstatus-f-sys.md#deletedisposedstatus-1) | 删除应用的处置状态。使用callback异步回调，成功返回null，失败返回对应错误信息。 |
| [deleteDisposedStatus](arkts-ability-deletedisposedstatus-f-sys.md#deletedisposedstatus-2) | 删除应用的处置状态。使用promise异步回调，成功返回null，失败返回对应错误信息。 |
| [deleteDisposedStatusSync](arkts-ability-deletedisposedstatussync-f-sys.md#deletedisposedstatussync-1) | 以同步方法删除指定应用或分身应用的处置状态。成功返回null，失败抛出对应异常。 |
| [deleteUninstallDisposedRule](arkts-ability-deleteuninstalldisposedrule-f-sys.md#deleteuninstalldisposedrule-1) | 删除指定应用或分身应用的卸载处置规则。 |
| [getAllDisposedRules](arkts-ability-getalldisposedrules-f-sys.md#getalldisposedrules-1) | 获取当前用户下已设置的所有拦截规则。 |
| [getDisposedRule](arkts-ability-getdisposedrule-f-sys.md#getdisposedrule-1) | 获取指定应用或分身应用已设置的拦截规则。 |
| [getDisposedRulesByBundle](arkts-ability-getdisposedrulesbybundle-f-sys.md#getdisposedrulesbybundle-1) | 获取指定应用程序包设置的所有拦截规则。 |
| [getDisposedStatus](arkts-ability-getdisposedstatus-f-sys.md#getdisposedstatus-1) | 获取指定应用的处置状态。使用callback异步回调，成功返回应用的处置状态，失败返回对应错误信息。 |
| [getDisposedStatus](arkts-ability-getdisposedstatus-f-sys.md#getdisposedstatus-2) | 获取指定应用已设置的处置状态。使用Promise异步回调，成功返回应用的处置状态，失败返回对应错误信息。 |
| [getDisposedStatusSync](arkts-ability-getdisposedstatussync-f-sys.md#getdisposedstatussync-1) | 以同步方法获取指定应用已设置的处置状态。成功返回应用的处置状态，失败抛出对应异常。 |
| [getUninstallDisposedRule](arkts-ability-getuninstalldisposedrule-f-sys.md#getuninstalldisposedrule-1) | 获取指定应用或分身应用已设置的优先级最高的卸载处置规则。 |
| [setDisposedRule](arkts-ability-setdisposedrule-f-sys.md#setdisposedrule-1) | 设置指定应用或分身应用的拦截规则。 |
| [setDisposedRules](arkts-ability-setdisposedrules-f-sys.md#setdisposedrules-1) | 批量设置指定应用或分身应用的拦截规则。 |
| [setDisposedStatus](arkts-ability-setdisposedstatus-f-sys.md#setdisposedstatus-1) | 设置应用的处置状态。使用callback异步回调。成功返回null，失败返回对应错误信息。 |
| [setDisposedStatus](arkts-ability-setdisposedstatus-f-sys.md#setdisposedstatus-2) | 设置应用的处置状态。使用Promise异步回调。成功返回null，失败返回对应错误信息。 |
| [setDisposedStatusSync](arkts-ability-setdisposedstatussync-f-sys.md#setdisposedstatussync-1) | 以同步方法设置应用的处置状态。成功返回null，失败抛出对应异常。 |
| [setUninstallDisposedRule](arkts-ability-setuninstalldisposedrule-f-sys.md#setuninstalldisposedrule-1) | 设置指定应用或分身应用的卸载处置规则。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DisposedRule](arkts-ability-disposedrule-i-sys.md) | 标识拦截规则。 |
| [DisposedRuleConfiguration](arkts-ability-disposedruleconfiguration-i-sys.md) | 标识批量设置拦截规则的配置。 |
| [UninstallDisposedRule](arkts-ability-uninstalldisposedrule-i-sys.md) | 标识卸载处置规则。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ComponentType](arkts-ability-componenttype-e-sys.md) | 标识功能组件类型。 |
| [ControlType](arkts-ability-controltype-e-sys.md) | 标识拦截指定应用程序的不同策略。 |
| [DisposedType](arkts-ability-disposedtype-e-sys.md) | 标识拦截应用程序的方式，例如禁用应用的全部能力、禁用应用的指定能力、或者不禁用。 |
| [UninstallComponentType](arkts-ability-uninstallcomponenttype-e-sys.md) | 标识卸载时功能组件类型。 |
<!--DelEnd-->

