# AutoStartupInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @dsz2025-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2c3267fc728379ed661f6395560cc18d085c54a translatedAt=2026-09-03T11:52:21.355Z pushedAt=2026-09-05T10:47:30.709Z -->

The module defines information about the application component that automatically starts upon system boot.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
> The APIs provided by this module are system APIs.

## Properties

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                       | Type   | Read-Only| Optional| Description                                          |
| --------------------------- | ------- | ---- | ---- | ---------------------------------------------- |
| bundleName                  | string  | No   | No   | Bundle name of the application, which uniquely identifies the application.       |
| moduleName                  | string  | No  | Yes  | Module name.                        |
| abilityName                 | string  | No   | No   | Ability name of the application, which identifies the specific Ability component to start.  |
| abilityTypeName             | string  | No  | Yes  | Ability type.                       |
| appCloneIndex<sup>12+</sup> | number  | No   | Yes   | Index of the app clone. The default value is 0, indicating the main application.            |
| userId<sup>20+</sup>        | number  | Yes  | Yes  | User ID associated with the application, used to differentiate applications belonging to different user accounts on the same device.     |
| setterUserId<sup>20+</sup>  | number  | Yes  | Yes  | User ID of the person who set the application to automatically start upon system boot.        |
| canUserModify<sup>20+</sup> | boolean | Yes   | Yes   | Whether developers are allowed to modify the auto-start status of this application. The value true means allowed, and false means not allowed. The default value is false. |

**Example**

```ts
import { autoStartupManager, common } from '@kit.AbilityKit';

// Set the application to auto-start on boot.
autoStartupManager.setApplicationAutoStartup({
  bundleName: 'com.example.autostartupapp',
  moduleName: 'entry',
  abilityName: 'EntryAbility',
  abilityTypeName: 'ServiceExtension'
} as common.AutoStartupInfo, (err) => {
  if (err) {
    console.error(`setApplicationAutoStartup failed, err code: ${err.code}, err msg: ${err.message}.`);
    return;
  }
  console.info(`setApplicationAutoStartup success.`);
});
```
