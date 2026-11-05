# DistributedExtensionAbility

```TypeScript
declare class DistributedExtensionAbility
```

The **DistributedExtensionAbility** module provides distributed extension capabilities and lifecycle callbacks for distributed ability creation, destruction, and connection.

**Since:** 20

<!--Device-unnamed-declare class DistributedExtensionAbility--><!--Device-unnamed-declare class DistributedExtensionAbility-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## ExtensionAbility Usage Restrictions

To ensure system security and stability, DistributedExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
```

## onCollaborate

```TypeScript
onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult
```

Callback invoked to return the collaboration result in multi-device collaboration scenarios.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistributedExtensionAbility-onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult--><!--Device-DistributedExtensionAbility-onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wantParam | Record&lt;string, Object&gt; | Yes | Want parameter, which supports only the key **"ohos.extra.param.key.supportCollaborateIndex"**. The key can be used to obtain the data passed by the caller andperform corresponding processing. |

**Return value:**

| Type | Description |
| --- | --- |
| [AbilityConstant.CollaborateResult](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-collaborateresult-e.md) | Collaboration result, that is, whether the target application accepts the collaboration request. |

**Examples**

```TypeScript
import { abilityConnectionManager, DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { AbilityConstant } from '@kit.AbilityKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    console.info(`DistributedExtension onCollabRequest Accept to the result of Ability collaborate`);
    let sessionId = -1;
    const collaborationValues = wantParam["CollaborationValues"] as abilityConnectionManager.CollaborationValues;
    if (collaborationValues == undefined) {
      return sessionId;
    }
    console.info(`onCollab, collaborationValues: ${JSON.stringify(collaborationValues)}`);
    return AbilityConstant.CollaborateResult.ACCEPT;
  }
}
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Callback invoked to initialize the service logic when a **DistributedExtensionAbility** instance is created.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistributedExtensionAbility-onCreate(want: Want): void--><!--Device-DistributedExtensionAbility-onCreate(want: Want): void-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to the **DistributedExtensionAbility** instance, including the ability name and bundle name. |

**Examples**

```TypeScript
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

## onDestroy

```TypeScript
onDestroy(): void
```

Callback invoked to clear resources when a **ServiceExtensionAbility** instance is destroyed.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistributedExtensionAbility-onDestroy(): void--><!--Device-DistributedExtensionAbility-onDestroy(): void-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Examples**

```TypeScript
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onDestroy() {
    console.info('DistributedExtension onDestroy ok');
  }
}
```

## context

```TypeScript
context: DistributedExtensionContext
```

Context of the **DistributedExtension**. This context inherits from **ExtensionContext**.

**Type:** [DistributedExtensionContext](arkts-distributedservice-application-distributedextensioncontext-distributedextensioncontext-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistributedExtensionAbility-context: DistributedExtensionContext--><!--Device-DistributedExtensionAbility-context: DistributedExtensionContext-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Appendix

DistributedExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Ability Kit | [@ohos.ability.featureAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-featureability.md) |
| Ability Kit | [@ohos.ability.particleAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-particleability.md) |
| Accessibility Kit | [@ohos.accessibility.config](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-accessibility-config.md) |
| Basic Services Kit | [@ohos.account.appAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-appaccount.md) |
| Basic Services Kit | [@ohos.account.distributedAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-distributedaccount.md) |
| Basic Services Kit | [@ohos.account.osAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-osaccount.md) |
| Form Kit | [@ohos.app.form.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-app-form-formbindingdata.md) |
| Form Kit | [@ohos.app.form.FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Form Kit | [@ohos.app.form.formInfo](../../apis-form-kit/arkts-apis/arkts-form-app-form-forminfo.md) |
| Form Kit | [@ohos.app.form.formProvider](../../apis-form-kit/arkts-apis/arkts-form-app-form-formprovider.md) |
| Form Kit | [@ohos.application.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-application-formbindingdata.md) |
| Form Kit | [@ohos.application.formError](../../apis-form-kit/arkts-apis/arkts-form-application-formerror.md) |
| Form Kit | [@ohos.application.formHost](../../apis-form-kit/arkts-apis/arkts-form-application-formhost.md) |
| Form Kit | [@ohos.application.formInfo](../../apis-form-kit/arkts-apis/arkts-form-application-forminfo.md) |
| Form Kit | [@ohos.application.formProvider](../../apis-form-kit/arkts-apis/arkts-form-application-formprovider.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Ability Kit | [@ohos.continuation.continuationManager](../../apis-ability-kit/arkts-apis/arkts-ability-continuation-continuationmanager.md) |
| Media Library Kit | [@ohos.file.AlbumPickerComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-albumpickercomponent.md) |
| Media Library Kit | [@ohos.file.photoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photoaccesshelper.md) |
| Media Library Kit | [@ohos.file.PhotoPickerComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photopickercomponent.md) |
| Core File Kit | [@ohos.file.picker](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-picker.md) |
| Media Library Kit | [@ohos.file.RecentPhotoComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-recentphotocomponent.md) |
| Media Library Kit | [@ohos.file.sendablePhotoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-sendablephotoaccesshelper.md) |
| IME Kit | [@ohos.inputMethod](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| Media Library Kit | [@ohos.multimedia.movingphotoview](../../apis-media-library-kit/arkts-components/arkts-medialibrary-multimedia-movingphotoview.md) |
| Input Kit | [@ohos.multimodalInput.inputMonitor](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-inputmonitor.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Connectivity Kit | [nfctech](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfctech.md) |
| Notification Kit | [@ohos.notification](../../apis-notification-kit/arkts-apis/arkts-notification-notification.md) |
| Notification Kit | [@ohos.notificationManager](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager.md) |
| Notification Kit | [@ohos.notificationSubscribe](../../apis-notification-kit/arkts-apis/arkts-notification-notificationsubscribe.md) |
| Basic Services Kit | [@ohos.power](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-power.md) |
| ArkUI | [@ohos.prompt](../../apis-arkui/arkts-apis/arkts-arkui-prompt.md) |
| ArkUI | [@ohos.promptAction](../../apis-arkui/arkts-apis/arkts-arkui-promptaction.md) |
| Background Tasks Kit | [@ohos.reminderAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagentmanager.md) |
| ArkUI | [@ohos.screen](../../apis-arkui/arkts-apis/arkts-arkui-screen.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Ability Kit | [ServiceExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-serviceextensioncontext.md) |
| Connectivity Kit | [tagSession](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-tagsession.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Telephony Kit | [telephony.voipCall](../../apis-telephony-kit/arkts-apis/arkts-telephony-voipcall.md) |
| Ability Kit | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext.md) |
| User Authentication Kit | [@ohos.userIAM.faceAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-faceauth.md) |
| User Authentication Kit | [@ohos.userIAM.userAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-userauth.md) |
| Sensor Service Kit | [@ohos.vibrator](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-vibrator.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
