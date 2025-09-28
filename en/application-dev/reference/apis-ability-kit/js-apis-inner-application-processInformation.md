# ProcessInformation
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module defines the process information. The information can be obtained through [getRunningProcessInformation](js-apis-app-ability-appManager.md#appmanagergetrunningprocessinformation) of appManager.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## Properties

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| pid | number | No| No| Process ID.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| uid | number | No| No| UID of the application.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| processName | string | No| No| Process name.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| bundleNames | Array&lt;string&gt; | No| No| Names of all running bundles in the process.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| state<sup>10+</sup> | [appManager.ProcessState](js-apis-app-ability-appManager.md#processstate10)| No| No| Running status of the process.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| bundleType<sup>12+</sup> | [bundleManager.BundleType](js-apis-bundleManager.md#bundletype) | No| No| Type of the bundle running in the process.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| appCloneIndex<sup>12+</sup> | number   | No  | Yes  | Index of an application clone.<br>**Atomic service API**: This API can be used in atomic services since API version 12. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';

appManager.getRunningProcessInformation((error, data) => {
  if (error) {
    console.error(`getRunningProcessInformation fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getRunningProcessInformation success, data: ${JSON.stringify(data)}`);
  }
});
```
