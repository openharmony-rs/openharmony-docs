# @ohos.app.ability.FenceExtensionAbility (FenceExtensionAbility)
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @liu-binjun-->
<!--Designer: @liu-binjun-->
<!--Tester: @mhy123456789-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=461bfe2357ae9914a8e5bde0c12af96637a06708 translatedAt=2026-11-03T04:31:29.719Z pushedAt=2026-11-03T12:08:25.492Z nl=1 -->

The **FenceExtensionAbility** class provides geofence-related capabilities. It is inherited from the **ExtensionAbility** class.

> **NOTE**
>
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.  

## Modules to Import

```ts
import { FenceExtensionAbility } from '@kit.LocationKit';
```

## Constraints
To ensure system security and stability and prevent FenceExtensionAbility from abusing system resources, the system manages and controls its capabilities and does not support the reference of some modules. For details, see [Appendix](#appendix).

## FenceExtensionAbility

Provides geofence-related capabilities. It is inherited from the **ExtensionAbility** class.

### Attributes

**System capability**: SystemCapability.Location.Location.Geofence

**Model restriction:** This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context | [FenceExtensionContext](js-apis-app-ability-FenceExtensionContext.md) | No| No| Context of the Geofence service.|

### onFenceStatusChange

onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record&lt;string, string&gt;): void

Represents the callback triggered when a geofence status change event is received. Service processing is then performed based on the event type and data.

**System capability**: SystemCapability.Location.Location.Geofence

**Model restriction:** This API can be used only in the stage model.

**Parameters**
| Name|  Type| Mandatory | Description |
| ------------ | ------------ | ------------ | ------------ |
| transition |  [geoLocationManager.GeofenceTransition](js-apis-geoLocationManager.md#geofencetransition12) |  Yes| Geofence transition information, including the geofence ID and geofence event. |
| additions  | Record&lt;string, string&gt;  | Yes | Additional information. |

**Example**

```ts
import { FenceExtensionAbility, geoLocationManager } from '@kit.LocationKit';
import { notificationManager } from '@kit.NotificationKit';
import { Want, wantAgent } from '@kit.AbilityKit';

export class MyFenceExtensionAbility extends FenceExtensionAbility {
  onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void {
    // Receive the geofence status change event and process the service logic.
    console.info(`on geofence transition,id:${transition.geofenceId},event:${transition.transitionEvent},additions:${JSON.stringify(additions)}`);

    // Send a geofence notification.
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility',
          parameters:
          {
            'geofenceId': transition?.geofenceId,
            'transitionEvent': transition?.transitionEvent,
          }
        } as Want
      ],
      actionType: wantAgent.OperationType.START_ABILITY,
      requestCode: 100
    };
    wantAgent.getWantAgent(wantAgentInfo).then((wantAgentMy) => {
      let notificationRequest: notificationManager.NotificationRequest = {
        id: 1,
        content: {
          notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
          normal: {
            title: "Geofence Notification",
            text: `on geofence transition,id:${transition.geofenceId},event:${transition.transitionEvent},additions:${JSON.stringify(additions)}`,
          }
        },
        notificationSlotType: notificationManager.SlotType.SOCIAL_COMMUNICATION,
        wantAgent: wantAgentMy
      };
      notificationManager.publish(notificationRequest);
    });
  }
}
```
### onDestroy

onDestroy(): void

Represents the callback triggered when a **FenceExtensionAbility** destruction event is received.

**System capability**: SystemCapability.Location.Location.Geofence

**Model restriction:** This API can be used only in the stage model.

**Example**

```ts
import { FenceExtensionAbility } from '@kit.LocationKit';

class MyFenceExtensionAbility extends FenceExtensionAbility {
  onDestroy(): void {
    // Process the FenceExtensionAbility destruction event.
    console.info(`on ability destroy`);
  }
}

```

## Appendix

FenceExtensionAbility does not support references to the following modules.

| Kit | Module |
|--|--|
| Ability Kit | [@ohos.ability.featureAbility (FeatureAbility Module)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-ability-featureability) |
| Ability Kit| [@ohos.ability.particleAbility (ParticleAbility Module)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-ability-particleability) |
| Ability Kit| [@ohos.bundle.launcherBundleManager (launcherBundleManager Module)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-launcherbundlemanager) |
| Ability Kit| [@ohos.continuation.continuationManager (Continuation/Collaboration Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-continuation-continuationmanager) |
| Ability Kit| [UIAbilityContext](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-inner-application-uiabilitycontext) |
| AppGallery Kit| [privacyManager (Privacy Management Service)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/store-privacymanager) |
| ArkUI| [@ohos.window (Window)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-window) |
| Audio Kit| [@ohos.multimedia.audio (Audio Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-audio) |
| AVSession Kit| [@ohos.multimedia.avsession (Media Session Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-avsession) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager (Background Task Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-resourceschedule-backgroundtaskmanager) |
| Background Tasks Kit| [@ohos.reminderAgent (Background Agent Reminder)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-reminderagent) |
| Background Tasks Kit| [@ohos.reminderAgentManager (Background Agent Reminder)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-reminderagentmanager) |
| Basic Services Kit | [@ohos.account.appAccount (Application Account Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-appaccount) |
| Basic Services Kit | [@ohos.account.distributedAccount (Distributed Account Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-distributed-account) |
| Basic Services Kit | [@ohos.account.osAccount (System Account Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-osaccount) |
| Basic Services Kit| [@ohos.deviceInfo (Device Information)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-device-info) |
| Basic Services Kit| [@ohos.request (Upload and Download)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-request) |
| Basic Services Kit| [@ohos.wallpaper (Wallpaper)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-wallpaper) |
| Camera Kit| [@ohos.multimedia.camera (Camera Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-camera) |
| Contacts Kit| [@ohos.connectedTag (Active Tag)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-connectedtag) |
| Contacts Kit| [@ohos.contact (Contacts)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-contact) |
| Connectivity Kit| [@ohos.nfc.cardEmulation (Standard NFC Card Emulation)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-cardemulation) |
| Connectivity Kit| [@ohos.nfc.controller (Standard NFC)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-nfccontroller) |
| Connectivity Kit| [@ohos.nfc.tag (Standard NFC Tag)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-nfctag) |
| Connectivity Kit| [nfctech (Standard NFC Tag Nfc Technology)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-nfctech) |
| Connectivity Kit| [tagSession (Standard NFC Tag TagSession)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-tagsession) |
| Form Kit | [@ohos.application.formError (formError)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-application-formerror) |
| MDM Kit| [@ohos.enterprise.adminManager (admin Permission Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-enterprise-adminmanager) |
| Media Kit| [@ohos.multimedia.media (Media Service)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-media) |
| Performance Analysis Kit| [@ohos.hidebug (Debug)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-hidebug) |
| Sensor Service Kit| [@ohos.vibrator (Vibration)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-vibrator) |
| Telephony Kit| [@ohos.telephony.call (Call)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-call) |
| Telephony Kit| [@ohos.telephony.data (Cellular Data)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-telephony-data) |
| Telephony Kit| [@ohos.telephony.observer (observer)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-observer) |
| Telephony Kit| [@ohos.telephony.radio (Network Search)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-radio) |
| Telephony Kit| [@ohos.telephony.sim (SIM Card Management)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-sim) |
| Telephony Kit| [@ohos.telephony.sms (SMS Service)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-sms) |
| User Authentication Kit| [@ohos.userIAM.userAuth (User Authentication)](https://developer.huawei.com/consumer/en/doc/harmonyos-references/js-apis-useriam-userauth) |