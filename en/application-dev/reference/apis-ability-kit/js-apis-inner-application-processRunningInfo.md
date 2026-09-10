# ProcessRunningInfo
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!--deprecated_code_no_check-->
<!-- md-trans-meta sourceCommit=b8128bc63f81dd586f2cdead7dfccd2fcdec2559 translatedAt=2026-09-03T12:02:44.936Z pushedAt=2026-09-05T10:47:30.860Z -->

ProcessRunningInfo defines the process running information, including the process ID, application UID, process name, and names of all running Bundles in the process. The information can be obtained through [getProcessRunningInfos](js-apis-application-appManager.md#appmanagergetprocessrunninginfosdeprecated) in appManager.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs are supported since API version 8 and deprecated since API version 9. You are advised to use [ProcessInformation<sup>9+</sup>](js-apis-inner-application-processInformation.md) instead.

## Modules to Import

```ts
import appManager from '@ohos.application.appManager';
```

## Attributes

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| pid | number | No| No| Process ID.|
| uid | number | No | No | UID of the application. |
| processName | string | No| No| Process name.|
| bundleNames | Array&lt;string&gt; | No| No| Names of all running bundles in the process.|

**Example**
```ts
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getProcessRunningInfos().then((data) => {
    console.info(`success: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
    console.error(`failed: ${JSON.stringify(error)}`);
});
```
