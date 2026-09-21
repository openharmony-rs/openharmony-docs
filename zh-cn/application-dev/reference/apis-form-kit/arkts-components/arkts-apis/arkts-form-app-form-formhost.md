# @ohos.app.form.formHost(卡片使用方-FormHost)

formHost模块提供了卡片使用方相关接口的能力，包括对使用方同一用户下安装的卡片进行删除、释放、请求更新、获取卡片信息、状态等操作。

> **说明：** 
> 
> 本模块接口均为系统接口。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [acquireFormData](arkts-form-formhost-acquireformdata-f-sys.md#acquireformdata) | 请求卡片提供方数据。使用callback异步回调。 |
| [acquireFormData](arkts-form-formhost-acquireformdata-f-sys.md#acquireformdata-1) | 请求卡片提供方数据。使用Promise异步回调。 |
| [acquireFormState](arkts-form-formhost-acquireformstate-f-sys.md#acquireformstate) | 获取卡片状态。使用callback异步回调。 |
| [acquireFormState](arkts-form-formhost-acquireformstate-f-sys.md#acquireformstate-1) | 获取卡片状态。使用Promise异步回调。 |
| [addForm](arkts-form-formhost-addform-f-sys.md) | Add a form. |
| [castToNormalForm](arkts-form-formhost-casttonormalform-f-sys.md#casttonormalform) | 将指定的临时卡片转换为普通卡片。使用callback异步回调。 |
| [castToNormalForm](arkts-form-formhost-casttonormalform-f-sys.md#casttonormalform-1) | 将指定的临时卡片转换为普通卡片。使用Promise异步回调。 |
| [clearRouterProxy](arkts-form-formhost-clearrouterproxy-f-sys.md#clearrouterproxy) | 清除卡片跳转代理。使用callback异步回调。 |
| [clearRouterProxy](arkts-form-formhost-clearrouterproxy-f-sys.md#clearrouterproxy-1) | 清除卡片跳转代理。使用Promise异步回调。 |
| [deleteForm](arkts-form-formhost-deleteform-f-sys.md#deleteform) | 删除指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务不再保留有关该卡片的信息。使用callback异步回调。 |
| [deleteForm](arkts-form-formhost-deleteform-f-sys.md#deleteform-1) | 删除指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务不再保留有关该卡片的信息。使用Promise异步回调。 |
| [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md#deleteinvalidforms) | 根据有效的卡片列表，删除应用程序不在有效列表中的卡片。使用callback异步回调。 |
| [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md#deleteinvalidforms-1) | 根据列表删除应用程序的无效卡片。使用Promise异步回调。 |
| [disableFormsUpdate](arkts-form-formhost-disableformsupdate-f-sys.md#disableformsupdate) | 向卡片框架发送通知以使指定的卡片不可以更新。该方法调用成功后，卡片刷新状态设置为去使能，卡片不可以接收来自卡片提供方的更新。使用callback异步回调。 |
| [disableFormsUpdate](arkts-form-formhost-disableformsupdate-f-sys.md#disableformsupdate-1) | 向卡片框架发送通知以使指定的卡片不可以更新。该方法调用成功后，卡片刷新状态设置为去使能，卡片不可以接收来自卡片提供方的更新。使用Promise异步回调。 |
| [enableFormsUpdate](arkts-form-formhost-enableformsupdate-f-sys.md#enableformsupdate) | 向卡片框架发送通知以使指定的卡片可以更新。该方法调用成功后，卡片刷新状态设置为使能，卡片可以接收来自卡片提供方的更新。使用callback异步回调。 |
| [enableFormsUpdate](arkts-form-formhost-enableformsupdate-f-sys.md#enableformsupdate-1) | 向卡片框架发送通知以使指定的卡片可以更新。该方法调用成功后，卡片刷新状态设置为使能，卡片可以接收来自卡片提供方的更新。使用Promise异步回调。 |
| [getAllFormsInfo](arkts-form-formhost-getallformsinfo-f-sys.md#getallformsinfo) | 获取设备上所有应用提供的卡片信息（不包含模板卡片）。使用callback异步回调。 |
| [getAllFormsInfo](arkts-form-formhost-getallformsinfo-f-sys.md#getallformsinfo-1) | 获取设备上所有应用提供的卡片信息（不包含模板卡片）。使用Promise异步回调。 |
| [getAllTemplateFormsInfo](arkts-form-formhost-getalltemplateformsinfo-f-sys.md) | 获取设备上所有应用提供的模板卡片信息。使用Promise异步回调。 |
| [getFormIdsByFormLocation](arkts-form-formhost-getformidsbyformlocation-f-sys.md) | 获取设备上指定卡片位置的卡片标识列表。使用Promise异步回调。 |
| [getFormsInfo](arkts-form-formhost-getformsinfo-f-sys.md#getformsinfo) | 获取设备上指定应用程序提供的卡片信息（不包含模板卡片）。使用callback异步回调。 |
| [getFormsInfo](arkts-form-formhost-getformsinfo-f-sys.md#getformsinfo-1) | 获取设备上指定应用程序提供的卡片信息（不包含模板卡片）。使用callback异步回调。 |
| [getFormsInfo](arkts-form-formhost-getformsinfo-f-sys.md#getformsinfo-2) | 获取设备上指定应用程序提供的卡片信息（不包含模板卡片）。使用Promise异步回调。 |
| [getFormsInfo](arkts-form-formhost-getformsinfo-f-sys.md#getformsinfo-3) | 获取设备上指定应用程序提供的卡片信息（不包含模板卡片）。使用Promise异步回调。 |
| [getTemplateFormsInfo](arkts-form-formhost-gettemplateformsinfo-f-sys.md) | 获取设备上指定应用程序提供的模板卡片信息。使用Promise异步回调。 |
| [isSystemReady](arkts-form-formhost-issystemready-f-sys.md#issystemready) | 检查系统是否准备好。使用callback异步回调。 |
| [isSystemReady](arkts-form-formhost-issystemready-f-sys.md#issystemready-1) | 检查系统是否准备好。使用Promise异步回调。 |
| [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-f-sys.md#notifyformsenableupdate) | 通知卡片是否启用更新状态。使用callback异步回调。 |
| [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-f-sys.md#notifyformsenableupdate-1) | 通知卡片是否启用更新状态。使用Promise异步回调。 |
| [notifyFormsPrivacyProtected](arkts-form-formhost-notifyformsprivacyprotected-f-sys.md#notifyformsprivacyprotected) | 通知指定卡片隐私保护状态改变。使用callback异步回调。 |
| [notifyFormsPrivacyProtected](arkts-form-formhost-notifyformsprivacyprotected-f-sys.md#notifyformsprivacyprotected-1) | 通知指定卡片隐私保护状态改变。使用Promise异步回调。 |
| [notifyFormsVisible](arkts-form-formhost-notifyformsvisible-f-sys.md#notifyformsvisible) | 通知卡片是否可见。使用callback异步回调。 |
| [notifyFormsVisible](arkts-form-formhost-notifyformsvisible-f-sys.md#notifyformsvisible-1) | 通知卡片是否可见。使用Promise异步回调。 |
| [notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md#notifyinvisibleforms) | 向卡片框架发送通知以使指定的卡片不可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用callback异步回调。 |
| [notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md#notifyinvisibleforms-1) | 向卡片框架发送通知以使指定的卡片不可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用Promise异步回调。 |
| [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md#notifyvisibleforms) | 向卡片框架发送通知以使指定的卡片可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用callback异步回调。 |
| [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md#notifyvisibleforms-1) | 向卡片框架发送通知以使指定的卡片可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用Promise异步回调。 |
| [off](arkts-form-formhost-off-f-sys.md#offformuninstall) | 取消订阅卡片卸载事件。使用callback异步回调。 |
| [off](arkts-form-formhost-off-f-sys.md#offformoverflow) | 取消订阅互动卡片动效请求事件。使用callback异步回调。 |
| [off](arkts-form-formhost-off-f-sys.md#offchangesceneanimationstate) | 取消订阅互动卡片状态切换请求事件。互动卡片状态分为激活态和非激活态，非激活态下，互动卡片同普通卡片一致；激活态下，互动卡片支持拉起卡片提供方所开发的LiveFormExtensionAbility进程，实现互动卡片动效。使用callback异步回调。 |
| [off](arkts-form-formhost-off-f-sys.md#offgetformrect) | 取消订阅卡片位置尺寸查询请求事件。使用callback异步回调。 |
| [off](arkts-form-formhost-off-f-sys.md#offgetliveformstatus) | Cancels Listening to the event of get live form status. |
| [offDeleteFormsCallback](arkts-form-formhost-offdeleteformscallback-f-sys.md) | 取消订阅删除卡片事件。使用callback异步回调。 |
| [offGetWantParamsCallback](arkts-form-formhost-offgetwantparamscallback-f-sys.md) | 取消订阅获取卡片参数事件。使用callback异步回调。 |
| [offTemplateFormDetailInfoChange](arkts-form-formhost-offtemplateformdetailinfochange-f-sys.md) | 取消订阅模板卡片静态配置信息变化。使用callback异步回调。 |
| [offUpdateFormsConfigCallback](arkts-form-formhost-offupdateformsconfigcallback-f-sys.md) | 取消订阅更新卡片配置事件。使用callback异步回调。 |
| [on](arkts-form-formhost-on-f-sys.md#onformuninstall) | 订阅卡片卸载事件。使用callback异步回调。 |
| [on](arkts-form-formhost-on-f-sys.md#onformoverflow) | 订阅互动卡片动效请求事件。使用callback异步回调。 |
| [on](arkts-form-formhost-on-f-sys.md#onchangesceneanimationstate) | 订阅互动卡片状态切换请求事件。互动卡片状态分为激活态和非激活态，非激活态下，互动卡片同普通卡片一致；激活态下，互动卡片支持拉起卡片提供方所开发的LiveFormExtensionAbility进程，实现互动卡片动效。使用callback异步回调。 |
| [on](arkts-form-formhost-on-f-sys.md#ongetformrect) | 订阅卡片位置尺寸查询请求事件。使用callback异步回调。 |
| [on](arkts-form-formhost-on-f-sys.md#ongetliveformstatus) | Listens to the event of get live form status. |
| [onDeleteFormsCallback](arkts-form-formhost-ondeleteformscallback-f-sys.md) | 订阅删除卡片事件。使用callback异步回调。 |
| [onGetWantParamsCallback](arkts-form-formhost-ongetwantparamscallback-f-sys.md) | 订阅获取卡片参数事件。使用callback异步回调。 |
| [onTemplateFormDetailInfoChange](arkts-form-formhost-ontemplateformdetailinfochange-f-sys.md) | 订阅模板卡片静态配置信息变化。使用callback异步回调。 |
| [onUpdateFormsConfigCallback](arkts-form-formhost-onupdateformsconfigcallback-f-sys.md) | 订阅更新卡片配置事件。使用callback异步回调。 |
| [recoverForms](arkts-form-formhost-recoverforms-f-sys.md#recoverforms) | 恢复被回收的卡片，并将它的状态更新为不可回收，如果卡片未被回收则只更新状态为不可回收。使用Promise异步回调。 |
| [recoverForms](arkts-form-formhost-recoverforms-f-sys.md#recoverforms-1) | 恢复被回收的卡片，并将它的状态更新为不可回收。如果卡片未被回收，则只更新状态为不可回收。使用callback异步回调。 |
| [recycleForms](arkts-form-formhost-recycleforms-f-sys.md) | 立即回收卡片内存。使用Promise异步回调。 |
| [releaseForm](arkts-form-formhost-releaseform-f-sys.md#releaseform) | 释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，但卡片管理器服务仍然保留有关该卡片的缓存信息和存储信息。使用callback异步回调。 |
| [releaseForm](arkts-form-formhost-releaseform-f-sys.md#releaseform-1) | 释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务保留有关该卡片的存储信息，可以选择是否保留缓存信息。使用callback异步回调。 |
| [releaseForm](arkts-form-formhost-releaseform-f-sys.md#releaseform-2) | 释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务保留有关该卡片的存储信息，可以选择是否保留缓存信息。使用Promise异步回调。 |
| [requestForm](arkts-form-formhost-requestform-f-sys.md#requestform) | 请求卡片更新。使用callback异步回调。 |
| [requestForm](arkts-form-formhost-requestform-f-sys.md#requestform-1) | 请求卡片更新。使用Promise异步回调。 |
| [requestFormWithParams](arkts-form-formhost-requestformwithparams-f-sys.md) | 携带参数请求卡片更新。使用Promise异步回调。 |
| [setFormsRecyclable](arkts-form-formhost-setformsrecyclable-f-sys.md#setformsrecyclable) | 设置卡片可回收。使用Promise异步回调。 |
| [setFormsRecyclable](arkts-form-formhost-setformsrecyclable-f-sys.md#setformsrecyclable-1) | 设置卡片可回收。使用callback异步回调。 |
| [setPublishFormResult](arkts-form-formhost-setpublishformresult-f-sys.md) | 设置卡片加桌结果。 |
| [setRouterProxy](arkts-form-formhost-setrouterproxy-f-sys.md#setrouterproxy) | 设置卡片跳转代理。使用callback异步回调，返回卡片跳转所需要Want信息。 |
| [setRouterProxy](arkts-form-formhost-setrouterproxy-f-sys.md#setrouterproxy-1) | 设置卡片跳转代理。使用Promise异步回调，返回卡片跳转所需要Want信息。 |
| [shareForm](arkts-form-formhost-shareform-f-sys.md#shareform) | 指定formId和远程设备Id进行卡片分享。使用callback异步回调。 |
| [shareForm](arkts-form-formhost-shareform-f-sys.md#shareform-1) | 指定formId和远程设备Id进行卡片分享。使用Promise异步回调。 |
| [updateFormLocation](arkts-form-formhost-updateformlocation-f-sys.md) | 更新卡片位置。 |
| [updateFormLockedState](arkts-form-formhost-updateformlockedstate-f-sys.md) | 通知卡片管控状态更新。使用Promise异步回调。 |
| [updateFormSize](arkts-form-formhost-updateformsize-f-sys.md) | 调整卡片尺寸。 |
<!--DelEnd-->
