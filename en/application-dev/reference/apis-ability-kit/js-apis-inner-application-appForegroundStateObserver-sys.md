# AppForegroundStateObserver (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=83eb20b2da17b66d3089c14abb21986b856a3985 translatedAt=2026-09-03T11:40:40.581Z pushedAt=2026-09-05T10:47:30.674Z -->

Defines the listener for the application startup, foreground and background, and exit states. It can be used as an input parameter of [appManager.on('appForegroundState')](js-apis-app-ability-appManager-sys.md#appmanageronappforegroundstate11) to listen for the startup, foreground and background, and exit changes of all applications.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## AppForegroundStateObserver

### onAppStateChanged

onAppStateChanged(appStateData: AppStateData): void

Called when the application startup, foreground and background, or exit state changes.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name | Type| Mandatory| Description  |
| ------ | ---- | ---- | ----- |
| appStateData   | [AppStateData](js-apis-inner-application-appStateData.md)   | Yes | Application state data.|

**Example**
```ts
import { appManager } from '@kit.AbilityKit';

let observer: appManager.AppForegroundStateObserver = {
  onAppStateChanged(appStateData: appManager.AppStateData) {
    console.info(`onAppStateChanged appStateData: ${JSON.stringify(appStateData)}`);
  },
};
appManager.on('appForegroundState', observer);
```