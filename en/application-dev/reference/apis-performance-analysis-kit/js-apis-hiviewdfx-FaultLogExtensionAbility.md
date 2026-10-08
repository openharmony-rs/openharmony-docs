# @ohos.hiviewdfx.FaultLogExtensionAbility (Delayed Fault Notification)
<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @chenshi51-->
<!--Designer: @StevenLai1994-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=35e244b8d12e8a1c9056429054822612a5b198be translatedAt=2026-09-21T02:58:47.271Z pushedAt=2026-09-22T01:29:30.420Z -->

This module implements the delayed fault notification feature.

When the crash and freeze events are subscribed by [HiAppEvent](js-apis-hiviewdfx-hiappevent.md), the previous event can be received only after the application restarts. If the application fails to start or remains unresponsive for a long time, the fault may not be reported in time.

This module provides APIs for solving this issue. After the application implements FaultLogExtensionAbility, the system service is expected to start FaultLogExtensionAbility 30 minutes later after the application crashes or freezes.

You can subscribe to and process fault events through [onFaultReportReady](#onfaultreportready).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.

## Constraints
To ensure system security and stability and prevent **FaultLogExtensionAbility** from abusing system resources, the system manages and controls its capabilities. Some modules are not supported for reference. For details, see [Appendix](#appendix).

## Modules to Import

```ts
import { FaultLogExtensionAbility } from '@kit.PerformanceAnalysisKit';
```

## FaultLogExtensionAbility

Implements the delayed fault notification. You can subscribe to and process fault events through [onFaultReportReady](#onfaultreportready).

> **NOTE**
>
> - After **FaultLogExtensionAbility** is pulled up, there is only a short period of time to complete fault handling. It is recommended that the handling time not exceed 10 seconds. If the handling is not completed within the timeout period, you can save the state in [onDisconnect](#ondisconnect).
> - The timing starts when the app triggers a crash or freeze for the first time after the device is powered on or after **FaultLogExtensionAbility** was last pulled up. Repeatedly triggering crash or freeze events before **FaultLogExtensionAbility** is pulled up does not restart the timing.
> - If **FaultLogExtensionAbility** itself crashes, it will not be pulled up again by the system service.

### Properties

**System capability**: SystemCapability.HiviewDFX.Hiview.FaultLogger

| Name| Type| Read-Only| Optional| Description|
| --- | --- | --- | --- | --- |
| context | [FaultLogExtensionContext](js-apis-hiviewdfx-FaultLogExtensionContext.md) | No| No| Context of the FaultLogExtensionAbility. This context is inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).|

### onConnect

onConnect(): void

Called to perform the initialization operation when the system service completes the connection. This API can be overridden selectively.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.HiviewDFX.Hiview.FaultLogger

**Example**
```ts
export default class MyFaultLogExtension extends FaultLogExtensionAbility {
    onConnect() {
      console.info('onConnect');
    }
}
```

### onDisconnect

onDisconnect(): void

Called to release resources and clear the running status when the system service completes the disconnection. This API can be overridden selectively.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.HiviewDFX.Hiview.FaultLogger

**Example**
```ts
export default class MyFaultLogExtension extends FaultLogExtensionAbility {
    onDisconnect() {
      console.info('onDisconnect');
    }
}
```

### onFaultReportReady

onFaultReportReady(): void

Called to subscribe to and process fault events when the system service notifies the FaultLogExtensionAbility to process faults.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.HiviewDFX.Hiview.FaultLogger

**Example**
  ```ts
  import { hiAppEvent } from '@kit.PerformanceAnalysisKit';

  export default class MyFaultLogExtension extends FaultLogExtensionAbility {
      onFaultReportReady() {
          hiAppEvent.addWatcher({
              name: "watcher",
              appEventFilters: [
                  {
                      domain: hiAppEvent.domain.OS,
                      names: [hiAppEvent.event.APP_CRASH, hiAppEvent.event.APP_FREEZE]
                  }
              ],
              onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
                  // Process the fault event.
              }
          });
      }
  }
  ```

## Appendix
**FaultLogExtensionAbility** does not support the reference to the following modules.
| Kit| Module|
| ------- | ------- |
| AVSession Kit | [@ohos.multimedia.avsession (AVSession Management)](../apis-avsession-kit/arkts-apis-avsession.md) |
| Ability Kit | [@ohos.UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) |
| ArkUI | [@ohos.window (Window)](../apis-arkui/arkts-apis-window.md)|
| Audio Kit | [@ohos.multimedia.audio (Audio Management)](../apis-audio-kit/arkts-apis-audio.md) |
| Background Tasks Kit | [@ohos.backgroundTaskManager (Background Task Management)](../apis-backgroundtasks-kit/js-apis-backgroundTaskManager.md) |
| Background Tasks Kit | [@ohos.reminderAgent (reminderAgent)](..//apis-backgroundtasks-kit/js-apis-reminderAgent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager (Agent-Powered Reminders)](../apis-backgroundtasks-kit/js-apis-reminderAgentManager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager (Background Task Management)](../apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md) |
| Basic Services Kit | [@ohos.power (System Power Management)](../apis-basic-services-kit/js-apis-power.md) |
| Basic Services Kit | [@ohos.wallpaper (Wallpaper)](../apis-basic-services-kit/js-apis-wallpaper.md) |
| Camera Kit | [@ohos.multimedia.camera (Camera Management)](../apis-camera-kit/arkts-apis-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker (Camera Picker)](../apis-camera-kit/js-apis-cameraPicker.md) |
| Connectivity Kit | [@ohos.wifiManager (WLAN)](../apis-connectivity-kit/js-apis-wifiManager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt (WLAN Extension)](../apis-connectivity-kit/js-apis-wifiManagerExt.md) |
| Connectivity Kit | [@ohos.wifiext (WLAN Extension)](../apis-connectivity-kit/js-apis-wifiext.md) |
| IME Kit | [@ohos.inputMethod (Input Method Framework)](../apis-ime-kit/js-apis-inputmethod.md) |
| Media Library Kit | [@ohos.multimedia.movingphotoview (MovingPhotoView)](../apis-media-library-kit/ohos-multimedia-movingphotoview.md) |
| Notification Kit | [@ohos.notification (Notification)](../apis-notification-kit/js-apis-notification.md) |
| Notification Kit | [@ohos.notificationManager (NotificationManager)](../apis-notification-kit/js-apis-notificationManager.md) |
| <!--DelRow--> Notification Kit | [@ohos.notificationSubscribe (NotificationSubscribe)](../apis-notification-kit/js-apis-notificationSubscribe-sys.md) |
| Sensor Service Kit | [@ohos.vibrator (Vibrator)](../apis-sensor-service-kit/js-apis-vibrator.md) |
| Telephony Kit | [@ohos.telephony.call (Call)](../apis-telephony-kit/js-apis-call.md) |
| Telephony Kit | [@ohos.telephony.sim (SIM Management)](../apis-telephony-kit/js-apis-sim.md) |
| Telephony Kit | [@ohos.telephony.sms (SMS)](../apis-telephony-kit/js-apis-sms.md) |
| <!--DelRow--> User Authentication Kit | [@ohos.userIAM.faceAuth (Facial Authentication)](../apis-user-authentication-kit/js-apis-useriam-faceauth-sys.md) |
| User Authentication Kit | [@ohos.userIAM.userAuth (User Authentication)](../apis-user-authentication-kit/js-apis-useriam-userauth.md) |
