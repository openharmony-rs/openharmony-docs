# @ohos.app.form.formObserver

formObserver模块提供了卡片监听方相关接口的能力，包括对同一用户下安装的卡片新增、删除、可见性变化事件的订阅和取消订阅，获取正在运行的卡片信息等。 > **说明：** > > 本模块接口均为系统接口。

**起始版本：** 23

<!--Device-unnamed-declare namespace formObserver--><!--Device-unnamed-declare namespace formObserver-End-->

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
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md) | 根据formId查询已添加的卡片信息。使用Promise异步回调。 |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md) | 根据formId查询已添加的卡片信息。使用Promise异步回调。 |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md) | 根据formId查询已添加的卡片信息。使用callback异步回调。 |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md) | 根据卡片标识formId，查询已添加的卡片信息。使用callback异步回调。 |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md) | 获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。 |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md) | 获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。 |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md) | 获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。 |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md) | 获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。 |
| [getRunningFormInfosByFilter](arkts-form-formobserver-getrunningforminfosbyfilter-f-sys.md) | 根据提供方信息查询已添加的卡片信息列表。使用Promise异步回调。 |
| [getRunningFormInfosByFilter](arkts-form-formobserver-getrunningforminfosbyfilter-f-sys.md) | 根据提供方信息查询已添加的卡片信息列表。使用callback异步回调。 |
| [offCall](arkts-form-formobserver-offcall-f-sys.md) | Unregister form call event Listening. |
| [offFormAdd](arkts-form-formobserver-offformadd-f-sys.md) | Cancels listening to the event of add form. &lt;p&gt;You can use this method to cancel listening to the event of add form.&lt;/p&gt; |
| [offFormRemove](arkts-form-formobserver-offformremove-f-sys.md) | Cancels listening to the event of remove form. &lt;p&gt;You can use this method to cancel listening to the event of remove form.&lt;/p&gt; |
| [offMessage](arkts-form-formobserver-offmessage-f-sys.md) | Unregister form message event Listening. |
| [offNotifyInvisible](arkts-form-formobserver-offnotifyinvisible-f-sys.md) | Cancels listening to the event of notifyInvisible type change. &lt;p&gt;You can use this method to cancel listening to the event of notifyInvisible type change.&lt;/p&gt; |
| [offNotifyVisible](arkts-form-formobserver-offnotifyvisible-f-sys.md) | Cancels listening to the event of notifyVisible type change. &lt;p&gt;You can use this method to cancel listening to the event of notifyVisible type change.&lt;/p&gt; |
| [offRouter](arkts-form-formobserver-offrouter-f-sys.md) | Unregister form router event Listening. |
| [off_call](arkts-form-formobserver-offcall-f-sys.md) | 取消订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
| [off_formAdd](arkts-form-formobserver-offformadd-f-sys.md) | 取消订阅卡片新增事件。使用callback异步回调。 |
| [off_formRemove](arkts-form-formobserver-offformremove-f-sys.md) | 取消订阅卡片删除事件。使用callback异步回调。 |
| [off_message](arkts-form-formobserver-offmessage-f-sys.md) | 取消订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片的信息。 |
| [off_notifyInvisible](arkts-form-formobserver-offnotifyinvisible-f-sys.md) | 取消订阅通知卡片不可见事件。使用callback异步回调。 |
| [off_notifyVisible](arkts-form-formobserver-offnotifyvisible-f-sys.md) | 取消订阅通知卡片可见的事件。使用callback异步回调。 |
| [off_router](arkts-form-formobserver-offrouter-f-sys.md) | 取消订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
| [onCall](arkts-form-formobserver-oncall-f-sys.md) | Call event listening in registered form. &lt;p&gt;This interface requires permission to receive callback.&lt;/p&gt; |
| [onCall](arkts-form-formobserver-oncall-f-sys.md) | Call event listening in registered form. &lt;p&gt;This interface requires permission to receive callback.&lt;/p&gt; |
| [onFormAdd](arkts-form-formobserver-onformadd-f-sys.md) | Listens to the event of add form. &lt;p&gt;You can use this method to listen to the event of add form.&lt;/p&gt; |
| [onFormAdd](arkts-form-formobserver-onformadd-f-sys.md) | Listens to the event of add form. &lt;p&gt;You can use this method to listen to the event of add form for a particular card host.&lt;/p&gt; |
| [onFormRemove](arkts-form-formobserver-onformremove-f-sys.md) | Listens to the event of remove form. &lt;p&gt;You can use this method to listen to the event of remove form.&lt;/p&gt; |
| [onFormRemove](arkts-form-formobserver-onformremove-f-sys.md) | Listens to the event of remove form. &lt;p&gt;You can use this method to listen to the event of remove form for a particular card host.&lt;/p&gt; |
| [onMessage](arkts-form-formobserver-onmessage-f-sys.md) | Message event listening in registered form. &lt;p&gt;This interface requires permission to receive callback.&lt;/p&gt; |
| [onMessage](arkts-form-formobserver-onmessage-f-sys.md) | Message event listening in registered form. &lt;p&gt;This interface requires permission to receive callback.&lt;/p&gt; |
| [onNotifyInvisible](arkts-form-formobserver-onnotifyinvisible-f-sys.md) | Listens to the event of notifyInvisible type change. &lt;p&gt;You can use this method to listen to the event of notifyInvisible type change.&lt;/p&gt; |
| [onNotifyInvisible](arkts-form-formobserver-onnotifyinvisible-f-sys.md) | Listens to the event of notifyInvisible type change. &lt;p&gt;You can use this method to listen to the event of notifyInvisible type change for a particular card host.&lt;/p&gt; |
| [onNotifyVisible](arkts-form-formobserver-onnotifyvisible-f-sys.md) | Listens to the event of notifyVisible type change. &lt;p&gt;You can use this method to listen to the event of notifyVisible type change.&lt;/p&gt; |
| [onNotifyVisible](arkts-form-formobserver-onnotifyvisible-f-sys.md) | Listens to the event of notifyVisible type change. &lt;p&gt;You can use this method to listen to the event of notifyVisible type change for a particular card host.&lt;/p&gt; |
| [onRouter](arkts-form-formobserver-onrouter-f-sys.md) | Router event listening in registered form. &lt;p&gt;This interface requires permission to receive callback.&lt;/p&gt; |
| [onRouter](arkts-form-formobserver-onrouter-f-sys.md) | Router event listening in registered form. &lt;p&gt;This interface requires permission to receive callback.&lt;/p&gt; |
| [on_call](arkts-form-formobserver-oncall-f-sys.md) | 订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
| [on_call](arkts-form-formobserver-oncall-f-sys.md) | 订阅指定卡片使用方的卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。 |
| [on_formAdd](arkts-form-formobserver-onformadd-f-sys.md) | 订阅卡片新增事件。使用callback异步回调，返回当前新增卡片的信息。 |
| [on_formAdd](arkts-form-formobserver-onformadd-f-sys.md) | 订阅卡片新增事件。使用callback异步回调，返回指定卡片使用方应用新增卡片的信息。 |
| [on_formRemove](arkts-form-formobserver-onformremove-f-sys.md) | 订阅卡片删除事件。使用callback异步回调，返回当前删除卡片的信息。 |
| [on_formRemove](arkts-form-formobserver-onformremove-f-sys.md) | 订阅卡片删除事件。使用callback异步回调，返回指定卡片使用方应用被删除卡片的信息。 |
| [on_message](arkts-form-formobserver-onmessage-f-sys.md) | 订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。 |
| [on_message](arkts-form-formobserver-onmessage-f-sys.md) | 订阅指定卡片使用方的卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。 |
| [on_notifyInvisible](arkts-form-formobserver-onnotifyinvisible-f-sys.md) | 订阅通知卡片不可见的事件。使用callback异步回调。 ​触发通知卡片不可见场景为：调用[notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md)接口通知对应卡片可见性变更为不可 见状态。 |
| [on_notifyInvisible](arkts-form-formobserver-onnotifyinvisible-f-sys.md) | 订阅通知卡片不可见的事件。使用callback异步回调。 ​触发通知卡片不可见场景为：调用[notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md)接口通知对应卡片可见性变更为不可 见状态。 |
| [on_notifyVisible](arkts-form-formobserver-onnotifyvisible-f-sys.md) | 订阅通知卡片可见的事件。使用callback异步回调。 ​触发通知卡片可见场景为：调用[notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)接口通知对应卡片可见性变更为可见状态。 |
| [on_notifyVisible](arkts-form-formobserver-onnotifyvisible-f-sys.md) | 订阅通知卡片可见的事件。使用callback异步回调。 ​触发通知卡片可见场景为：调用[notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)接口通知对应卡片可见性变更为可见状态。 |
| [on_router](arkts-form-formobserver-onrouter-f-sys.md) | 订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
| [on_router](arkts-form-formobserver-onrouter-f-sys.md) | 订阅指定卡片使用方的卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。 |
<!--DelEnd-->

