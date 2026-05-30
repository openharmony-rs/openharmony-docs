# AbilityRunningInfo
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->
AbilityRunningInfo is a struct that records the running information and state of an ability. It is obtained through [getAbilityRunningInfos](js-apis-app-ability-abilityManager.md#abilitymanagergetabilityrunninginfos14).
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
| startTime | number | No| No|Ability start time.|
| abilityState | [abilityManager.AbilityState](js-apis-app-ability-abilityManager.md#abilitystate14) | No| No| Ability state. |

**Example**

```ts
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  abilityManager.getAbilityRunningInfos()
    .then((data: abilityManager.AbilityRunningInfo[]) => {
      for (let i = 0; i < data.length; i++) {
        let abilityInfo = data[i];
        console.info(`getAbilityRunningInfos success, data: ${JSON.stringify(abilityInfo)}`);
      }
    })
    .catch((error: BusinessError) => {
      console.error(`getAbilityRunningInfos fail, error code: ${JSON.stringify(error.code)}, error msg: ${JSON.stringify(error.message)}`);
    })
} catch (e) {
  let code = (e as BusinessError).code;
  let msg = (e as BusinessError).message;
  console.error(`getAbilityRunningInfos fail, error code: ${JSON.stringify(code)}, error msg: ${JSON.stringify(msg)}`);
}
```
