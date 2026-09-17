# @ohos.backgroundTaskManager (Background Task Management) (System API)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=520f9a32cdb2e9a005e54fc92b1c491413781b64 translatedAt=2026-09-15T12:56:39.894Z pushedAt=2026-09-17T06:33:38.068Z -->

The **BackgroundTaskManager** module provides APIs to manage background tasks.

If there is a service that needs to continue executing or be executed later when the application or service module is running in the background (not visible to users), the application or service module can request a transient task to delay the suspension or a continuous task to avoid the suspension based on the service type.

If an application has a task that cannot be interrupted when the application is switched to the background and can be completed within a short period of time, the application can request a transient task. For example, if the user exists the application before the cleanup is completed, the application can request a transient task to complete the cleanup.

If an application has a service that can be intuitively perceived by users and needs to run in the background for a long period of time (for example, music playback in the background), the application can request a continuous task.

For privileged system applications, an independent efficiency resource request API is provided.

>  **NOTE**
>
> - This module is deprecated since API version 9. You are advised to use [@ohos.resourceschedule.backgroundTaskManager (Background Task Management)](js-apis-resourceschedule-backgroundTaskManager-sys.md).
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.backgroundTaskManager (Background Task Management)](js-apis-backgroundTaskManager.md).


## Modules to Import

```ts
import backgroundTaskManager from '@ohos.backgroundTaskManager';  
```

## BackgroundMode<sup>8+</sup>

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name                    | Value | Description                   |
| ----------------------- | ---- | --------------------- |
| WIFI_INTERACTION        | 7    | WLAN-related.<br>This is a system API.|
| VOIP                    | 8    | Audio and video calls.<br>This is a system API. |
