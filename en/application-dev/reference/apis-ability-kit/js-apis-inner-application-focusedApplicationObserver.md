# FocusedApplicationObserver
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=d00cc090ab1e70fffee77bd26a6ec11e2edf8cae translatedAt=2026-11-03T13:28:43.037Z pushedAt=2026-11-04T06:24:30.786Z nl=1 -->

The focused application observer can be passed as an input parameter to the [onFocusedApplicationChanged](js-apis-app-ability-appManager.md#appmanageronfocusedapplicationchanged) method to listen for changes in the focused application.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## FocusedApplicationObserver.onFocusedApplicationChanged

onFocusedApplicationChanged(info: FocusedApplicationInfo): void

Callback function executed when the focused application changes.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| info | [FocusedApplicationInfo](js-apis-inner-application-focusedApplicationInfo.md) | Yes | Information about the focused application. |

**Example**
```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let focusedApplicationObserver: appManager.FocusedApplicationObserver = {
  onFocusedApplicationChanged(info: appManager.FocusedApplicationInfo) {
    console.info(`[appManager] onFocusedApplicationChanged: ${JSON.stringify(info)}`);
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