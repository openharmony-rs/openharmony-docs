# @ohos.app.form.formObserver(卡片监听方-FormObserver)

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
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md#getrunningforminfobyid) | 根据formId查询已添加的卡片信息。使用Promise异步回调。 |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md#getrunningforminfobyid-1) | 根据formId查询已添加的卡片信息。使用Promise异步回调。 |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md#getrunningforminfobyid-2) | 根据formId查询已添加的卡片信息。使用callback异步回调。 |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md#getrunningforminfobyid-3) | 根据卡片标识formId，查询已添加的卡片信息。使用callback异步回调。 |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md#getrunningforminfos) | 获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。 |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md#getrunningforminfos-1) | 获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。 |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md#getrunningforminfos-2) | 获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。 |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md#getrunningforminfos-3) | 获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。 |
| [getRunningFormInfosByFilter](arkts-form-formobserver-getrunningforminfosbyfilter-f-sys.md#getrunningforminfosbyfilter) | 根据提供方信息查询已添加的卡片信息列表。使用Promise异步回调。 |
| [getRunningFormInfosByFilter](arkts-form-formobserver-getrunningforminfosbyfilter-f-sys.md#getrunningforminfosbyfilter-1) | 根据提供方信息查询已添加的卡片信息列表。使用callback异步回调。 |
| [off](arkts-form-formobserver-off-f-sys.md#offformadd) | 取消订阅卡片新增事件。使用callback异步回调。 |
| [off](arkts-form-formobserver-off-f-sys.md#offformremove) | 取消订阅卡片删除事件。使用callback异步回调。 |
| [off](arkts-form-formobserver-off-f-sys.md#offnotifyvisible) | 取消订阅通知卡片可见的事件。使用callback异步回调。 |
| [off](arkts-form-formobserver-off-f-sys.md#offnotifyinvisible) | 取消订阅通知卡片不可见事件。使用callback异步回调。 |
| [off](arkts-form-formobserver-off-f-sys.md#offrouter) | 取消订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
| [off](arkts-form-formobserver-off-f-sys.md#offmessage) | 取消订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片的信息。 |
| [off](arkts-form-formobserver-off-f-sys.md#offcall) | 取消订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#onformadd) | 订阅卡片新增事件。使用callback异步回调，返回当前新增卡片的信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#onformadd) | 订阅卡片新增事件。使用callback异步回调，返回指定卡片使用方应用新增卡片的信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#onformremove) | 订阅卡片删除事件。使用callback异步回调，返回当前删除卡片的信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#onformremove) | 订阅卡片删除事件。使用callback异步回调，返回指定卡片使用方应用被删除卡片的信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#onnotifyvisible) | 订阅通知卡片可见的事件。使用callback异步回调。 |
| [on](arkts-form-formobserver-on-f-sys.md#onnotifyvisible) | 订阅通知卡片可见的事件。使用callback异步回调。 |
| [on](arkts-form-formobserver-on-f-sys.md#onnotifyinvisible) | 订阅通知卡片不可见的事件。使用callback异步回调。 |
| [on](arkts-form-formobserver-on-f-sys.md#onnotifyinvisible) | 订阅通知卡片不可见的事件。使用callback异步回调。 |
| [on](arkts-form-formobserver-on-f-sys.md#onrouter) | 订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#onrouter) | 订阅指定卡片使用方的卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#onmessage) | 订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#onmessage) | 订阅指定卡片使用方的卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#oncall) | 订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
| [on](arkts-form-formobserver-on-f-sys.md#oncall) | 订阅指定卡片使用方的卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
<!--DelEnd-->
