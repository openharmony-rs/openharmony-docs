# FenceExtensionAbility

```TypeScript
export default class FenceExtensionAbility
```

Class of fence extension ability.

**Since:** 14

<!--Device-unnamed-export default class FenceExtensionAbility--><!--Device-unnamed-export default class FenceExtensionAbility-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## ExtensionAbility Usage Restrictions

To ensure system security and stability, FenceExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { FenceExtensionAbility } from '@kit.LocationKit';
```

## onDestroy

```TypeScript
onDestroy(): void
```

Called back before a fence extension is destroyed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-FenceExtensionAbility-onDestroy(): void--><!--Device-FenceExtensionAbility-onDestroy(): void-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**Examples**

```TypeScript
import { FenceExtensionAbility } from '@kit.LocationKit';

class MyFenceExtensionAbility extends FenceExtensionAbility {
  onDestroy(): void {
    // Process the FenceExtensionAbility destruction event.
    console.info(`on ability destroy`);
  }
}
```

## onFenceStatusChange

```TypeScript
onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void
```

Called back when geofence status is change.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-FenceExtensionAbility-onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void--><!--Device-FenceExtensionAbility-onFenceStatusChange(transition: geoLocationManager.GeofenceTransition, additions: Record<string, string>): void-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transition | [geoLocationManager.GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md) | Yes | Geofence transition status |
| additions | Record&lt;string, string&gt; | Yes | Indicates additional information |

**Examples**

```TypeScript
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
            "geofenceId": transition?.geofenceId,
            "transitionEvent": transition?.transitionEvent,
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

## context

```TypeScript
context: FenceExtensionContext
```

Indicates the fence extension context.

**Type:** [FenceExtensionContext](arkts-location-app-ability-fenceextensioncontext-fenceextensioncontext-c-sys.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-FenceExtensionAbility-context: FenceExtensionContext--><!--Device-FenceExtensionAbility-context: FenceExtensionContext-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## Appendix

FenceExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Ability Kit | [@ohos.ability.featureAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-featureability.md) |
| Ability Kit | [@ohos.ability.particleAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-particleability.md) |
| Accessibility Kit | [@ohos.accessibility.config](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-accessibility-config.md) |
| Basic Services Kit | [@ohos.account.appAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-appaccount.md) |
| Basic Services Kit | [@ohos.account.distributedAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-distributedaccount.md) |
| Basic Services Kit | [@ohos.account.osAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-osaccount.md) |
| Ability Kit | [@ohos.app.ability.quickFixManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-quickfixmanager.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Form Kit | [@ohos.application.formError](../../apis-form-kit/arkts-apis/arkts-form-application-formerror.md) |
| Form Kit | [@ohos.application.formHost](../../apis-form-kit/arkts-apis/arkts-form-application-formhost.md) |
| Background Tasks Kit | [@ohos.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager.md) |
| Ability Kit | [@ohos.bundle.bundleMonitor](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-bundlemonitor.md) |
| Ability Kit | [@ohos.bundle.distributedBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-distributedbundlemanager.md) |
| Ability Kit | [@ohos.bundle.freeInstall](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-freeinstall.md) |
| Ability Kit | [@ohos.bundle.innerBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-innerbundlemanager.md) |
| Ability Kit | [@ohos.bundle.installer](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-installer.md) |
| Ability Kit | [@ohos.bundle.launcherBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-launcherbundlemanager.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Ability Kit | [@ohos.continuation.continuationManager](../../apis-ability-kit/arkts-apis/arkts-ability-continuation-continuationmanager.md) |
| Ability Kit | [@ohos.distributedBundle](../../apis-ability-kit/arkts-apis/arkts-ability-distributedbundle.md) |
| Ability Kit | [@ohos.distributedMissionManager](../../apis-ability-kit/arkts-apis/arkts-ability-distributedmissionmanager.md) |
| MDM Kit | [@ohos.enterprise.adminManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-adminmanager.md) |
| Mdm Kit | [enterprise.dataTimeManager](../../apis-mdm-kit/arkts-apis/arkts-enterprise-datatimemanager.md) |
| MDM Kit | [@ohos.enterprise.deviceInfo](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-deviceinfo.md) |
| Core File Kit | [@ohos.filemanagement.userFileManager](../../apis-core-file-kit/arkts-apis/arkts-corefile-filemanagement-userfilemanager.md) |
| Performance Analysis Kit | [@ohos.hidebug](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-hidebug.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Ability Kit | [@ohos.privacyManager](../../apis-ability-kit/arkts-apis/arkts-ability-privacymanager.md) |
| Background Tasks Kit | [@ohos.reminderAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagentmanager.md) |
| Basic Services Kit | [@ohos.request](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-request.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.usageStatistics](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-usagestatistics.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.data](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-data.md) |
| Telephony Kit | [@ohos.telephony.observer](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-observer.md) |
| Telephony Kit | [@ohos.telephony.radio](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-radio.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Basic Services Kit | [@ohos.update](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-update.md) |
| User Authentication Kit | [@ohos.userIAM.faceAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-faceauth.md) |
| User Authentication Kit | [@ohos.userIAM.userAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-userauth.md) |
| Sensor Service Kit | [@ohos.vibrator](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-vibrator.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
| Ability Kit | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md) |
| Ability Kit | [ServiceExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-serviceextensioncontext.md) |
| Ability Kit | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext.md) |
| Connectivity Kit | [nfctech](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfctech.md) |
| Connectivity Kit | [tagSession](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-tagsession.md) |
