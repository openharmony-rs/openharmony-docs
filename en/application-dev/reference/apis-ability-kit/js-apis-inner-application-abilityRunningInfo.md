# AbilityRunningInfo
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1e2bfcc9b4f85d9126c23f626a7a73b4bb891227 translatedAt=2026-09-03T11:37:06.375Z pushedAt=2026-09-05T10:47:30.656Z -->

AbilityRunningInfo is a data structure that records the running information and state of an ability, including the ability's identification information, process information, startup time, and current state. It is obtained through the [getAbilityRunningInfos](js-apis-app-ability-abilityManager.md#abilitymanagergetabilityrunninginfos14) method.
> **NOTE**
> 
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { abilityManager } from '@kit.AbilityKit';
```

## AbilityRunningInfo

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ability | [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md) | No| No| Element name of the ability.|
| pid | number | No| No| Process ID.|
| uid | number | No| No| UID of the application. |
| processName | string | No| No| Process name. |
| startTime | number | No | No | Start time of the ability, in ms. |
| abilityState | [abilityManager.AbilityState](js-apis-app-ability-abilityManager.md#abilitystate14) | No| No| Ability state. |

**Example**

```ts
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Obtain the ability running information.
  abilityManager.getAbilityRunningInfos()
    .then((data: abilityManager.AbilityRunningInfo[]) => {
      for (let i = 0; i < data.length; i++) {
        let abilityInfo = data[i];
        console.info(`getAbilityRunningInfos success, data: ${JSON.stringify(abilityInfo)}`);
      }
    })
    .catch((error: BusinessError) => {
      // Handle the case where obtaining the ability running information fails.
      console.error(`getAbilityRunningInfos fail, error code: ${JSON.stringify(error.code)}, error msg: ${JSON.stringify(error.message)}`);
    });
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`getAbilityRunningInfos fail, error code: ${JSON.stringify(code)}, error msg: ${JSON.stringify(msg)}`);
}
```