# ProcessInformation
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=8dfc858934e48c4ddfd1c710a23e129e9c1548cf translatedAt=2026-09-03T12:02:24.353Z pushedAt=2026-09-05T10:47:30.858Z -->

This module represents the running process information. Developers can obtain the running process information through [getRunningProcessInformation](js-apis-app-ability-appManager.md#appmanagergetrunningprocessinformation) of appManager.

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
| uid | number | No | No | UID of the application.<br>**Atomic service API**: This API is supported in atomic services since API version 11. |
| processName | string | No| No| Process name.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| bundleNames | Array&lt;string&gt; | No| No| Names of all running bundles in the process.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| state<sup>10+</sup> | [appManager.ProcessState](js-apis-app-ability-appManager.md#processstate10)| No| No| Running status of the process.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| bundleType<sup>12+</sup> | [bundleManager.BundleType](js-apis-bundleManager.md#bundletype) | No | No | Type of the bundle running in the current process.<br>**Atomic service API**: This API is supported in atomic services since API version 12. |
| appCloneIndex<sup>12+</sup> | number   | No | Yes | App clone index, which is used to identify different cloned app instances. The value **0** indicates the main app, and a positive integer indicates the index of the corresponding cloned instance.<br>**Atomic service API**: This API is supported in atomic services since API version 12.  |
| isPreload<sup>26+</sup> | boolean   | No | Yes | Whether the process is preloaded. The value is **true** if the process is preloaded and has not been used by any component startup request; otherwise, the value is **false**.<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API**: This API is supported in atomic services since API version 26.0.0.<br>**Since:** 26.0.0  |

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
