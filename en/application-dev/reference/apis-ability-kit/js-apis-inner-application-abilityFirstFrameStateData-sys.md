# AbilityFirstFrameStateData (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module defines the struct reported by the callback when the first frame of an ability is rendered. After registering the first frame rendering completion event of an ability by using [on](js-apis-app-ability-appManager-sys.md#appmanageronabilityfirstframestate12), you can obtain the reported struct through the [onAbilityFirstFrameDrawn](./js-apis-inner-application-abilityFirstFrameStateObserver-sys.md#onabilityfirstframedrawn) callback of [AbilityFirstFrameStateObserver](js-apis-inner-application-abilityFirstFrameStateObserver-sys.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## Attributes

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name       | Type   | Read Only| Optional| Description            |
| ----------- | ------- | ---- | ---- | ---------------- |
| bundleName  | string  | No  | No  | Bundle name.|
| moduleName  | string  | No  | No  | Module name.|
| abilityName | string  | No  | No  | Ability name.   |
| appIndex    | number  | No  | No  | Index of the DLP sandbox. |
| isColdStart | boolean | No  | No  | Enabled status of cold start. **true** if enabled, **false** otherwise.    |
