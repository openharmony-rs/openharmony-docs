# @ohos.application.DistributedExtensionAbility (Distributed Extension)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->

The **DistributedExtensionAbility** module provides the base class for extension capabilities in multi-device collaboration scenarios (for example, dedicated communication services between wearables and mobile phones).

As the base class for extending capabilities in multi-device collaboration scenarios, this module provides the following capabilities:

- **Lifecycle management**: provides lifecycle callbacks **onCreate**, **onCollaborate**, and **onDestroy**, covering the complete lifecycle of a collaborative ExtensionAbility from creation to destruction. This allows your app to execute service logic such as initialization, collaborative decision-making, and resource cleanup at different stages.

- **Collaborative decision-making**: provides the **onCollaborate** callback to help an app determine whether to accept (**ACCEPT**/**REJECT**) a collaboration request based on the collaboration parameters transmitted by the caller during cross-device startup. This allows the app to flexibly control whether to continue the collaboration process.

- **Context**: provides the **distributedExtensionContext**, which allows you to connect to and disconnect from a remote **ServiceExtensionAbility** to implement cross-device service calling and data exchange.

The following figure shows the core class structure of the collaboration extension and its relationship with the context and custom subclass.

 

As shown in the preceding figure:
- **Inheritance relationship**:** DistributedExtensionContext** inherits from **ExtensionContext**, and the custom subclass is inherited from **DistributedExtensionAbility**.
- **Composition relationship**: **DistributedExtensionAbility** has the **context** attribute of the **DistributedExtensionContext** type and provides collaboration capabilities such as connecting to and disconnecting from the remote **ServiceExtensionAbility**.

You can obtain the capabilities for multi-device collaboration by inheriting **DistributedExtensionAbility** and implementing the **onCreate**, **onCollaborate**, and **onDestroy** lifecycle callbacks.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
```

## DistributedExtensionAbility

### Attributes

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services, it does not work.

| Name   | Type                         | Read-Only| Optional| Description                                                      |
| ------- | ----------------------------- | ---- | ---- | ---------------------------------------------------------- |
| context | DistributedExtensionContext | No  | No  | Context of the **DistributedExtension**. This context inherits from **ExtensionContext**.|

### onCreate

onCreate(want: Want): void

Callback invoked to initialize the service logic when a **DistributedExtensionAbility** instance is created.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services, it does not work.

**Parameters**

| Name    | Type| Mandatory                                                            | Description|
| ----------| ---- | ---------------------------------------------------------------- | ---- |
| want      | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | Want information related to the current extension, which is used to carry the initialization configuration required for creating the extension.|

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCreate(want: Want) {
    console.info(`DistributedExtension Create ok`);
    console.info(`DistributedExtension on Create want: ${JSON.stringify(want)}`);
    console.info(`DistributedExtension Create end`);
  }
}
```

### onCollaborate

onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult

Defines an extension lifecycle callback, which is invoked to return the collaboration result in multi-device collaboration scenarios. The returned result determines whether to continue the collaboration process.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services, it does not work.

**Parameters**

| Name   | Type  | Mandatory| Description                                                                                                                                  |
| --------- | ------ | ---- | -------------------------------------------------------------------------------------------------------------------------------------- |
| wantParam | Record<string, Object> | Yes  | Collaboration callback parameter, which is a key-value pair object carrying collaboration-related data transmitted by the caller. You can obtain these data through key values such as **ohos.extra.param.key.supportCollaborateIndex** and **CollaborationValues** to determine whether to accept the collaboration request and process the collaboration logic, which affects whether the collaboration process continues.|

**Return value**

| Type| Description|
| ---------- | ---- |
| [AbilityConstant.CollaborateResult](../apis-ability-kit/js-apis-app-ability-abilityConstant.md#collaborateresult18) | Whether the coordinator app accepts the collaboration result. The value **ACCEPT** indicates that the collaboration is accepted and the collaboration process continues. The value **REJECT** indicates that the collaboration is rejected and the collaboration process ends.|

**Example**

```ts
import { abilityConnectionManager, DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { AbilityConstant } from '@kit.AbilityKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    console.info(`DistributedExtension onCollabRequest Accept to the result of Ability collaborate`);
    let sessionId = -1;
    const collaborationValues = wantParam["CollaborationValues"] as abilityConnectionManager.CollaborationValues;
    if (!collaborationValues) {
      console.error('Failed to get collaborationValues.');
      return sessionId;
    }
    console.info(`onCollab, collaborationValues: ${JSON.stringify(collaborationValues)}`);
    return AbilityConstant.CollaborateResult.ACCEPT;
  }
}
```

### onDestroy

onDestroy(): void

Callback invoked to clear resources when a **ServiceExtensionAbility** instance is destroyed.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services, it does not work.

**Example**

```ts
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onDestroy() {
    console.info('DistributedExtension onDestroy ok');
  }
}
```

## Appendix

**DistributedExtensionAbility** does not support referencing the following modules.
| Kit | Module|
| -------- | -------- | 
| Ability Kit| [@ohos.ability.featureAbility (FeatureAbility)](../apis-ability-kit/js-apis-ability-featureAbility.md) |
| Ability Kit| [@ohos.ability.particleAbility (ParticleAbility)](../apis-ability-kit/js-apis-ability-particleAbility.md) |
|<!--DelRow-->Ability Kit| [ServiceExtensionContext (System API)](../apis-ability-kit/js-apis-inner-application-serviceExtensionContext-sys.md)  |
|<!--DelRow-->Ability Kit| [UIAbilityContext (System API)](../apis-ability-kit/js-apis-inner-application-uiAbilityContext-sys.md)  |
| Ability Kit| [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md)  |
| Ability Kit| [@ohos.continuation.continuationManager (Continuation/Collaboration Management)](../apis-ability-kit/js-apis-continuation-continuationManager.md) |
|<!--DelRow-->Accessibility Kit| [@ohos.accessibility.config (System Accessibility Configuration) (System API)](../apis-accessibility-kit/js-apis-accessibility-config-sys.md)|
| ArkUI | [@ohos.prompt (Prompt)](../apis-arkui/js-apis-prompt.md)  |
|<!--DelRow-->ArkUI| [@ohos.promptAction (Prompt) (System API)](../apis-arkui/js-apis-promptAction-sys.md)  |
| ArkUI | [@ohos.promptAction (Prompt)](../apis-arkui/js-apis-promptAction.md)  |
|<!--DelRow-->ArkUI| [@ohos.screen (Screen) (System API)](../apis-arkui/js-apis-screen-sys.md)  |
| ArkUI | [@ohos.screenshot (Screenshot)](../apis-arkui/js-apis-screenshot.md)  |
|<!--DelRow-->ArkUI | [@ohos.window (Window) (System API)](../apis-arkui/js-apis-window-sys.md)  |
|<!--DelRow-->Audio Kit| [@ohos.multimedia.audio (Audio Management) (System API)](../apis-audio-kit/js-apis-audio-sys.md) |
|<!--DelRow-->AVSession Kit| [@ohos.multimedia.avsession (AVSession Management) (System API)](../apis-avsession-kit/js-apis-avsession-sys.md)  |
| Background Tasks Kit| [@ohos.reminderAgent (Agent-powered Reminder)](..//apis-backgroundtasks-kit/js-apis-reminderAgent.md) |
| Background Tasks Kit| [@ohos.reminderAgentManager (Agent-Powered Reminders)](../apis-backgroundtasks-kit/js-apis-reminderAgentManager.md) |
| Basic Services Kit| [@ohos.account.appAccount (App Account Management)](../apis-basic-services-kit/js-apis-appAccount.md) |
| Basic Services Kit | [@ohos.account.distributedAccount (Distributed Account Management)](../apis-basic-services-kit/js-apis-distributed-account.md) |
| Basic Services Kit | [@ohos.account.osAccount (System Account Management)](../apis-basic-services-kit/js-apis-osAccount.md) |
| Basic Services Kit | [@ohos.power (System Power Management)](../apis-basic-services-kit/js-apis-power.md) |
| Basic Services Kit | [@ohos.wallpaper (Wallpaper)](../apis-basic-services-kit/js-apis-wallpaper.md) |
|<!--DelRow-->Camera Kit| [@ohos.multimedia.camera (Camera Management) (System API)](../apis-camera-kit/js-apis-camera-sys.md)  |
| Camera Kit| [@ohos.multimedia.cameraPicker (Camera Picker)](../apis-camera-kit/js-apis-cameraPicker.md) |
| Connectivity Kit| [@ohos.connectedTag (Active Tags)](../apis-connectivity-kit/js-apis-connectedTag.md) |
| Connectivity Kit| [nfctech (Standard NFC Technologies)](../apis-connectivity-kit/js-apis-nfctech.md) |
| Connectivity Kit| [@ohos.nfc.cardEmulation (Standard NFC Card Emulation)](../apis-connectivity-kit/js-apis-cardEmulation.md) |
| Connectivity Kit| [@ohos.nfc.controller (Standard NFC)](../apis-connectivity-kit/js-apis-nfcController.md) |
| Connectivity Kit| [@ohos.nfc.tag (Standard NFC Tags)](../apis-connectivity-kit/js-apis-nfcTag.md) |
| Connectivity Kit| [tagSession (Standard NFC Tag Session)](../apis-connectivity-kit/js-apis-tagSession.md) |
| Contacts Kit| [@ohos.contact (Contacts)](../apis-contacts-kit/js-apis-contact.md) |
|<!--DelRow-->Core File Kit| [@ohos.file.picker (Picker) (System API)](../apis-core-file-kit/js-apis-file-picker-sys.md)  |
| Core File Kit| [@ohos.file.picker (Picker)](../apis-core-file-kit/js-apis-file-picker.md)  |
| Form Kit| [@ohos.app.form.formBindingData (formBindingData)](../apis-form-kit/js-apis-app-form-formBindingData.md)  |
|<!--DelRow-->Form Kit| [@ohos.app.form.FormExtensionAbility (FormExtensionAbility) (System API)](../apis-form-kit/js-apis-app-form-formExtensionAbility-sys.md)  |
| Form Kit| [@ohos.app.form.FormExtensionAbility (FormExtensionAbility)](../apis-form-kit/js-apis-app-form-formExtensionAbility.md)  |
|<!--DelRow-->Form Kit| [@ohos.app.form.formHost (formHost) (System API)](../apis-form-kit/js-apis-app-form-formHost-sys.md) |
|<!--DelRow-->Form Kit| [@ohos.app.form.formInfo (formInfo) (System API)](../apis-form-kit/js-apis-app-form-formInfo-sys.md)  |
| Form Kit| [@ohos.app.form.formInfo (formInfo)](../apis-form-kit/js-apis-app-form-formInfo.md)  |
|<!--DelRow-->Form Kit| [@ohos.app.form.formProvider (formProvider) (System API)](../apis-form-kit/js-apis-app-form-formProvider-sys.md)  |
| Form Kit| [@ohos.app.form.formProvider (formProvider)](../apis-form-kit/js-apis-app-form-formProvider.md)  |
|<!--DelRow-->Form Kit| [@ohos.application.formBindingData (formBindingData)](../apis-form-kit/js-apis-application-formBindingData.md)  |
|<!--DelRow-->Form Kit| [@ohos.application.formError (formError) (System API)](../apis-form-kit/js-apis-application-formError-sys.md)  |
| Form Kit| [@ohos.application.formError (formError)](../apis-form-kit/js-apis-application-formError.md)  |
|<!--DelRow-->Form Kit| [@ohos.application.formHost (formHost) (System API)](../apis-form-kit/js-apis-application-formHost-sys.md) |
|<!--DelRow-->Form Kit| [@ohos.application.formInfo (formInfo) (System API)](../apis-form-kit/js-apis-application-formInfo-sys.md)  |
| Form Kit| [@ohos.application.formInfo (formInfo)](../apis-form-kit/js-apis-application-formInfo.md)  |
| Form Kit| [@ohos.application.formProvider (formProvider)](../apis-form-kit/js-apis-application-formProvider.md)  |
| IME Kit| [@ohos.inputMethod (Input Method Framework)](../apis-ime-kit/js-apis-inputmethod.md) |
|<!--DelRow-->Input Kit| [@ohos.multimodalInput.inputMonitor (Input Monitor) (System API)](reference/apis-input-kit/js-apis-inputmonitor-sys.md) |
|<!--DelRow-->Media Kit| [@ohos.multimedia.media (Media) (System API)](../apis-media-kit/js-apis-media-sys.md)  |
| MultimediaKit | @ohos.multimedia.mediaLibrary (Media Library Management)|
|<!--DelRow-->Media Library Kit| [@ohos.file.photoAccessHelper (Album Management) (System API)](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md) |
|<!--DelRow-->Media Library Kit| [@ohos.file.sendablePhotoAccessHelper (Album Management) (System API)](../apis-media-library-kit/js-apis-sendablePhotoAccessHelper-sys.md) |
| Media Library Kit| [@ohos.file.sendablePhotoAccessHelper (Album Management Based on a Sendable Object)](../apis-media-library-kit/js-apis-sendablePhotoAccessHelper.md)|
| Media Library Kit| [@ohos.file.AlbumPickerComponent (AlbumPickerComponent)](../apis-media-library-kit/ohos-file-AlbumPickerComponent.md)|
| Media Library Kit| [@ohos.file.PhotoPickerComponent (PhotoPicker Component)](../apis-media-library-kit/ohos-file-PhotoPickerComponent.md)|
| Media Library Kit| [@ohos.file.RecentPhotoComponent (RecentPhotoComponent)](../apis-media-library-kit/ohos-file-RecentPhotoComponent.md)|
|<!--DelRow-->Media Library Kit| [@ohos.multimedia.movingphotoview (MovingPhotoView) (System API)](../apis-media-library-kit/ohos-multimedia-movingphotoview-sys.md) |
| Media Library Kit| [@ohos.multimedia.movingphotoview (MovingPhotoView)](../apis-media-library-kit/ohos-multimedia-movingphotoview.md)|
| Notification Kit| [@ohos.notification (Notification)](../apis-notification-kit/js-apis-notification.md) |
| Notification Kit| [@ohos.notificationManager (NotificationManager)](../apis-notification-kit/js-apis-notificationManager.md) |
|<!--DelRow-->Notification Kit| [@ohos.notificationSubscribe (NotificationSubscribe) (System API)](../apis-notification-kit/js-apis-notificationSubscribe-sys.md) |
| Sensor Service Kit| [@ohos.vibrator (Vibrator)](../apis-sensor-service-kit/js-apis-vibrator.md) |
| Telephony Kit| [@ohos.telephony.call (Call)](../apis-telephony-kit/js-apis-call.md) |
| Telephony Kit| [@ohos.telephony.sim (SIM Management)](../apis-telephony-kit/js-apis-sim.md) |
| Telephony Kit| [@ohos.telephony.sms (SMS)](../apis-telephony-kit/js-apis-sms.md) |
|<!--DelRow-->User Authentication Kit| [@ohos.userIAM.faceAuth (Facial Authentication) (System API)](../apis-user-authentication-kit/js-apis-useriam-faceauth-sys.md) |
|<!--DelRow-->User Authentication Kit| [@ohos.userIAM.userAuth (User Authentication) (System API)](../apis-user-authentication-kit/js-apis-useriam-userauth-sys.md)  |
| User Authentication Service| [@ohos.userIAM.userAuth (User Authentication)](../apis-user-authentication-kit/js-apis-useriam-userauth.md) |
<!--RP1--><!--RP1End-->
