# @ohos.app.form.formObserver(formObserver)

formObserver模块提供了卡片监听方相关接口的能力，包括对同一用户下安装的卡片新增、删除、可见性变化事件的订阅和取消订阅，获取正在运行的卡片信息等。

> **说明：**
> 
> 本模块接口均为系统接口。

**起始版本：** 10

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { formObserver } from '@kit.FormKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getRunningFormInfoById(formObserver)](arkts-form-formobserver-getrunningforminfobyid-f-sys.md) | 根据formId查询已添加的卡片信息。使用Promise异步回调。 |
| [getRunningFormInfoById(formObserver)](arkts-form-formobserver-getrunningforminfobyid-f-sys.md) | 根据formId查询已添加的卡片信息。使用Promise异步回调。 |
| [getRunningFormInfoById(formObserver)](arkts-form-formobserver-getrunningforminfobyid-f-sys.md) | 根据formId查询已添加的卡片信息。使用callback异步回调。 |
| [getRunningFormInfoById(formObserver)](arkts-form-formobserver-getrunningforminfobyid-f-sys.md) | 根据卡片标识formId，查询已添加的卡片信息。使用callback异步回调。 |
| [getRunningFormInfos(formObserver)](arkts-form-formobserver-getrunningforminfos-f-sys.md) | 获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。 |
| [getRunningFormInfos(formObserver)](arkts-form-formobserver-getrunningforminfos-f-sys.md) | 获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。 |
| [getRunningFormInfos(formObserver)](arkts-form-formobserver-getrunningforminfos-f-sys.md) | 获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。 |
| [getRunningFormInfos(formObserver)](arkts-form-formobserver-getrunningforminfos-f-sys.md) | 获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。 |
| [getRunningFormInfosByFilter(formObserver)](arkts-form-formobserver-getrunningforminfosbyfilter-f-sys.md) | 根据提供方信息查询已添加的卡片信息列表。使用Promise异步回调。 |
| [getRunningFormInfosByFilter(formObserver)](arkts-form-formobserver-getrunningforminfosbyfilter-f-sys.md) | 根据提供方信息查询已添加的卡片信息列表。使用callback异步回调。 |
| off(formObserver) | 取消订阅卡片新增事件。使用callback异步回调。 |
| off(formObserver) | 取消订阅卡片删除事件。使用callback异步回调。 |
| off(formObserver) | 取消订阅通知卡片可见的事件。使用callback异步回调。 |
| off(formObserver) | 取消订阅通知卡片不可见事件。使用callback异步回调。 |
| off(formObserver) | 取消订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
| off(formObserver) | 取消订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片的信息。 |
| off(formObserver) | 取消订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
| on(formObserver) | 订阅卡片新增事件。使用callback异步回调，返回当前新增卡片的信息。 |
| on(formObserver) | 订阅卡片新增事件。使用callback异步回调，返回指定卡片使用方应用新增卡片的信息。 |
| on(formObserver) | 订阅卡片删除事件。使用callback异步回调，返回当前删除卡片的信息。 |
| on(formObserver) | 订阅卡片删除事件。使用callback异步回调，返回指定卡片使用方应用被删除卡片的信息。 |
| on(formObserver) | 订阅通知卡片可见的事件。使用callback异步回调。​触发通知卡片可见场景为：调用[notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)接口通知对应卡片可见性变更为可见状态。 |
| on(formObserver) | 订阅通知卡片可见的事件。使用callback异步回调。​触发通知卡片可见场景为：调用[notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)接口通知对应卡片可见性变更为可见状态。 |
| on(formObserver) | 订阅通知卡片不可见的事件。使用callback异步回调。​触发通知卡片不可见场景为：调用[notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md)接口通知对应卡片可见性变更为不可 见状态。 |
| on(formObserver) | 订阅通知卡片不可见的事件。使用callback异步回调。​触发通知卡片不可见场景为：调用[notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md)接口通知对应卡片可见性变更为不可 见状态。 |
| on(formObserver) | 订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
| on(formObserver) | 订阅指定卡片使用方的卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
| on(formObserver) | 订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。 |
| on(formObserver) | 订阅指定卡片使用方的卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。 |
| on(formObserver) | 订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
| on(formObserver) | 订阅指定卡片使用方的卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
<!--DelEnd-->
