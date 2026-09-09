# ProcessInfo

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=83eb20b2da17b66d3089c14abb21986b856a3985 translatedAt=2026-09-03T11:33:22.870Z pushedAt=2026-09-05T10:47:30.639Z -->

Process information object. Developers can use [getProcessInfo](js-apis-inner-app-context.md#contextgetprocessinfo7) to obtain the process information of the current Ability in scenarios such as debugging, performance monitoring, and multi-process management.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. The APIs of this module can be used only in the FA model. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import featureAbility from '@ohos.ability.featureAbility';
```

## Attributes

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| pid | number | No| No| Process ID.|
| processName | string | No| No| Process name.|

**Example**
<!--code_no_check_fa-->
```ts
import featureAbility from '@ohos.ability.featureAbility';

let context = featureAbility.getContext();
context.getProcessInfo((error, data) => {
    if (error && error.code !== 0) {
        console.error(`getProcessInfo fail, error: ${JSON.stringify(error)}`);
    } else {
        console.info(`getProcessInfo success, data: ${JSON.stringify(data)}`);
        let pid = data.pid;
        let processName = data.processName;
    }
});
```

