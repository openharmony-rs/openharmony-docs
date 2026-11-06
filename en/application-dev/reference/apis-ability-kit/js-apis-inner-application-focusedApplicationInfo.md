# FocusedApplicationInfo
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=d00cc090ab1e70fffee77bd26a6ec11e2edf8cae translatedAt=2026-11-03T13:27:57.758Z pushedAt=2026-11-04T06:24:14.906Z nl=1 -->

Defines the focused application information. After registering the focused application change listener using [onFocusedApplicationChanged](js-apis-app-ability-appManager.md#appmanageronfocusedapplicationchanged), when the focused application changes, the system reports the focused application information to the developer through the [onFocusedApplicationChanged](js-apis-inner-application-focusedApplicationObserver.md#focusedapplicationobserveronfocusedapplicationchanged) callback of [FocusedApplicationObserver](js-apis-inner-application-focusedApplicationObserver.md).

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## Properties

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| focusedBundleName | string | No | No | Bundle name of the focused application. |
| focusedUid | number | No | No | UID of the focused application. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let focusedApplicationObserver: appManager.FocusedApplicationObserver = {
  onFocusedApplicationChanged(info: appManager.FocusedApplicationInfo) {
    console.info(`[appManager] onFocusedApplicationChanged: ${JSON.stringify(info)}`);
    console.info(`info.focusedBundleName: ${info.focusedBundleName}`);
    console.info(`info.focusedUid: ${info.focusedUid}`);
  }
};

try {
  const observerId = appManager.onFocusedApplicationChanged(focusedApplicationObserver);
  console.info(`[appManager] observerId: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```
<!--no_check-->