# @ohos.app.form.formObserver(formObserver)

Interface of formObserver.

@namespace formObserver

**Since:** 10

<!--Device-unnamed-declare namespace formObserver--><!--Device-unnamed-declare namespace formObserver-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { formObserver } from '@kit.FormKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md#getrunningforminfobyid1) | Obtains the RunningFormInfo object by formId. |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md#getrunningforminfobyid2) | Obtains the RunningFormInfo object by formId. |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md#getrunningforminfobyid3) | Obtains the RunningFormInfo object by formId. |
| [getRunningFormInfoById](arkts-form-formobserver-getrunningforminfobyid-f-sys.md#getrunningforminfobyid4) | Obtains the RunningFormInfo object by formId. |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md#getrunningforminfos1) | Obtains the RunningFormInfo objects provided by a specific card host application on the device. |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md#getrunningforminfos2) | Obtains the RunningFormInfo objects provided by a specific card host application on the device. |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md#getrunningforminfos3) | Obtains the RunningFormInfo objects provided by a specific card host application on the device. |
| [getRunningFormInfos](arkts-form-formobserver-getrunningforminfos-f-sys.md#getrunningforminfos4) | Obtains the RunningFormInfo objects provided by a specific card host application on the device. |
| [getRunningFormInfosByFilter](arkts-form-formobserver-getrunningforminfosbyfilter-f-sys.md#getrunningforminfosbyfilter1) | Obtains the RunningFormInfo objects by FormProviderFilter. |
| [getRunningFormInfosByFilter](arkts-form-formobserver-getrunningforminfosbyfilter-f-sys.md#getrunningforminfosbyfilter2) | Obtains the RunningFormInfo objects by FormProviderFilter. |
| [off('formAdd')](arkts-form-formobserver-off-f-sys.md#offformadd) | Cancels listening to the event of add form.<p>You can use this method to cancel listening to the event of add form.</p> |
| [off('formRemove')](arkts-form-formobserver-off-f-sys.md#offformremove) | Cancels listening to the event of remove form.<p>You can use this method to cancel listening to the event of remove form.</p> |
| [off('notifyVisible')](arkts-form-formobserver-off-f-sys.md#offnotifyvisible) | Cancels listening to the event of notifyVisible type change.<p>You can use this method to cancel listening to the event of notifyVisible type change.</p> |
| [off('notifyInvisible')](arkts-form-formobserver-off-f-sys.md#offnotifyinvisible) | Cancels listening to the event of notifyInvisible type change.<p>You can use this method to cancel listening to the event of notifyInvisible type change.</p> |
| [off('router')](arkts-form-formobserver-off-f-sys.md#offrouter) | Unregister form router event Listening. |
| [off('message')](arkts-form-formobserver-off-f-sys.md#offmessage) | Unregister form message event Listening. |
| [off('call')](arkts-form-formobserver-off-f-sys.md#offcall) | Unregister form call event Listening. |
| [on('formAdd')](arkts-form-formobserver-on-f-sys.md#onformadd) | Listens to the event of add form.<p>You can use this method to listen to the event of add form.</p> |
| [on('formAdd')](arkts-form-formobserver-on-f-sys.md#onformadd) | Listens to the event of add form.<p>You can use this method to listen to the event of add form for a particular card host.</p> |
| [on('formRemove')](arkts-form-formobserver-on-f-sys.md#onformremove) | Listens to the event of remove form.<p>You can use this method to listen to the event of remove form.</p> |
| [on('formRemove')](arkts-form-formobserver-on-f-sys.md#onformremove) | Listens to the event of remove form.<p>You can use this method to listen to the event of remove form for a particular card host.</p> |
| [on('notifyVisible')](arkts-form-formobserver-on-f-sys.md#onnotifyvisible) | Listens to the event of notifyVisible type change.<p>You can use this method to listen to the event of notifyVisible type change.</p> |
| [on('notifyVisible')](arkts-form-formobserver-on-f-sys.md#onnotifyvisible) | Listens to the event of notifyVisible type change.<p>You can use this method to listen to the event of notifyVisible type change for a particular card host.</p> |
| [on('notifyInvisible')](arkts-form-formobserver-on-f-sys.md#onnotifyinvisible) | Listens to the event of notifyInvisible type change.<p>You can use this method to listen to the event of notifyInvisible type change.</p> |
| [on('notifyInvisible')](arkts-form-formobserver-on-f-sys.md#onnotifyinvisible) | Listens to the event of notifyInvisible type change.<p>You can use this method to listen to the event of notifyInvisible type change for a particular card host.</p> |
| [on('router')](arkts-form-formobserver-on-f-sys.md#onrouter) | Router event listening in registered form.<p>This interface requires permission to receive callback.</p> |
| [on('router')](arkts-form-formobserver-on-f-sys.md#onrouter) | Router event listening in registered form.<p>This interface requires permission to receive callback.</p> |
| [on('message')](arkts-form-formobserver-on-f-sys.md#onmessage) | Message event listening in registered form.<p>This interface requires permission to receive callback.</p> |
| [on('message')](arkts-form-formobserver-on-f-sys.md#onmessage) | Message event listening in registered form.<p>This interface requires permission to receive callback.</p> |
| [on('call')](arkts-form-formobserver-on-f-sys.md#oncall) | Call event listening in registered form.<p>This interface requires permission to receive callback.</p> |
| [on('call')](arkts-form-formobserver-on-f-sys.md#oncall) | Call event listening in registered form.<p>This interface requires permission to receive callback.</p> |
<!--DelEnd-->
