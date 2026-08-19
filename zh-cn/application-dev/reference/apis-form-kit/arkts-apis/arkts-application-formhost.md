# @ohos.application.formHost

formHost模块提供了卡片使用方相关接口的能力，包括对使用方同一用户下安装的卡片进行删除、释放、请求更新，获取信息、状态等操作。 > **说明：** > > 从API version 9 开始废弃， > > 本模块接口均为系统接口。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [formHost](arkts-app-form-formhost.md)

<!--Device-unnamed-declare namespace formHost--><!--Device-unnamed-declare namespace formHost-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [acquireFormState](arkts-form-formhost-acquireformstate-depr-f-sys.md#acquireformstate) | 获取卡片状态。使用callback异步回调。 |
| [acquireFormState](arkts-form-formhost-acquireformstate-depr-f-sys.md#acquireformstate) | 获取卡片状态。使用Promise异步回调。 |
| [castTempForm](arkts-form-formhost-casttempform-depr-f-sys.md#casttempform) | 将指定的临时卡片转换为普通卡片。使用callback异步回调。 |
| [castTempForm](arkts-form-formhost-casttempform-depr-f-sys.md#casttempform) | 将指定的临时卡片转换为普通卡片。使用Promise异步回调。 |
| [deleteForm](arkts-form-formhost-deleteform-depr-f-sys.md#deleteform) | 删除指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务不再保留有关该卡片的信息。使用callback异步回调。 |
| [deleteForm](arkts-form-formhost-deleteform-depr-f-sys.md#deleteform) | 删除指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务不再保留有关该卡片的信息。使用Promise异步回调。 |
| [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-depr-f-sys.md#deleteinvalidforms) | 根据列表删除应用程序的无效卡片。使用callback异步回调。 |
| [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-depr-f-sys.md#deleteinvalidforms) | 根据列表删除应用程序的无效卡片。使用Promise异步回调。 |
| [disableFormsUpdate](arkts-form-formhost-disableformsupdate-depr-f-sys.md#disableformsupdate) | 向卡片框架发送通知以使指定的卡片不可以更新。该方法调用成功后，卡片刷新状态设置为去使能，卡片不可以接收来自卡片提供方的更新。使用callback异步回调。 |
| [disableFormsUpdate](arkts-form-formhost-disableformsupdate-depr-f-sys.md#disableformsupdate) | 向卡片框架发送通知以使指定的卡片不可以更新。该方法调用成功后，卡片刷新状态设置为去使能，卡片不可以接收来自卡片提供方的更新。使用Promise异步回调。 |
| [enableFormsUpdate](arkts-form-formhost-enableformsupdate-depr-f-sys.md#enableformsupdate) | 向卡片框架发送通知以使指定的卡片可以更新。该方法调用成功后，卡片刷新状态设置为使能，卡片可以接收来自卡片提供方的更新。使用callback异步回调。 |
| [enableFormsUpdate](arkts-form-formhost-enableformsupdate-depr-f-sys.md#enableformsupdate) | 向卡片框架发送通知以使指定的卡片可以更新。该方法调用成功后，卡片刷新状态设置为使能，卡片可以接收来自卡片提供方的更新。使用Promise异步回调。 |
| [getAllFormsInfo](arkts-form-formhost-getallformsinfo-depr-f-sys.md#getallformsinfo) | 获取设备上所有应用提供的卡片信息。使用callback异步回调。 |
| [getAllFormsInfo](arkts-form-formhost-getallformsinfo-depr-f-sys.md#getallformsinfo) | 获取设备上所有应用提供的卡片信息。使用Promise异步回调。 |
| [getFormsInfo](arkts-form-formhost-getformsinfo-depr-f-sys.md#getformsinfo) | 获取设备上指定应用程序提供的卡片信息。使用callback异步回调。 |
| [getFormsInfo](arkts-form-formhost-getformsinfo-depr-f-sys.md#getformsinfo) | 获取设备上指定应用程序提供的卡片信息。使用callback异步回调。 |
| [getFormsInfo](arkts-form-formhost-getformsinfo-depr-f-sys.md#getformsinfo) | 获取设备上指定应用程序提供的卡片信息。使用Promise异步回调。 |
| [isSystemReady](arkts-form-formhost-issystemready-depr-f-sys.md#issystemready) | 检查系统是否准备好。使用callback异步回调。 |
| [isSystemReady](arkts-form-formhost-issystemready-depr-f-sys.md#issystemready) | 检查系统是否准备好。使用Promise异步回调。 |
| [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-depr-f-sys.md#notifyformsenableupdate) | 通知卡片是否启用更新状态。使用callback异步回调。 |
| [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-depr-f-sys.md#notifyformsenableupdate) | 通知卡片是否启用更新状态。使用Promise异步回调。 |
| [notifyFormsVisible](arkts-form-formhost-notifyformsvisible-depr-f-sys.md#notifyformsvisible) | 通知卡片是否可见。使用callback异步回调。 |
| [notifyFormsVisible](arkts-form-formhost-notifyformsvisible-depr-f-sys.md#notifyformsvisible) | 通知卡片是否可见。使用Promise异步回调。 |
| [notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-depr-f-sys.md#notifyinvisibleforms) | 向卡片框架发送通知以使指定的卡片不可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用callback异步回调。 |
| [notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-depr-f-sys.md#notifyinvisibleforms) | 向卡片框架发送通知以使指定的卡片不可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用Promise异步回调。 |
| [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-depr-f-sys.md#notifyvisibleforms) | 向卡片框架发送通知以使指定的卡片可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用callback异步回调。 |
| [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-depr-f-sys.md#notifyvisibleforms) | 向卡片框架发送通知以使指定的卡片可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用Promise异步回调。 |
| [off_formUninstall](arkts-form-formhost-offformuninstall-depr-f-sys.md#offformuninstall) | 取消订阅卡片卸载事件。使用callback异步回调。 |
| [on_formUninstall](arkts-form-formhost-onformuninstall-depr-f-sys.md#onformuninstall) | 订阅卡片卸载事件。使用callback异步回调。 |
| [releaseForm](arkts-form-formhost-releaseform-depr-f-sys.md#releaseform) | 释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，但卡片管理器服务仍然保留有关该卡片的缓存信息和存储信息。使用callback异步回调。 |
| [releaseForm](arkts-form-formhost-releaseform-depr-f-sys.md#releaseform) | 释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务保留有关该卡片的存储信息，可以选择是否保留缓存信息。使用callback异步回调。 |
| [releaseForm](arkts-form-formhost-releaseform-depr-f-sys.md#releaseform) | 释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务保留有关该卡片的存储信息，可以选择是否保留缓存信息。使用Promise异步回调。 |
| [requestForm](arkts-form-formhost-requestform-depr-f-sys.md#requestform) | 请求卡片更新。使用callback异步回调。 |
| [requestForm](arkts-form-formhost-requestform-depr-f-sys.md#requestform) | 请求卡片更新。使用Promise异步回调。 |
<!--DelEnd-->

