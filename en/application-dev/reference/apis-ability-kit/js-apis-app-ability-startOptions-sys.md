# @ohos.app.ability.StartOptions (StartOptions) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @dsz2025; @yangxuguang-huawei; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2c3267fc728379ed661f6395560cc18d085c54a translatedAt=2026-09-03T10:32:42.041Z pushedAt=2026-09-05T10:47:30.433Z -->

StartOptions can be used as an input parameter for APIs used to launch a UIAbility (for example, [startAbility()](js-apis-inner-application-uiAbilityContext.md#startability-1)). It specifies the options for starting the target UIAbility, including but not limited to the window mode and the display where the target UIAbility is started.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> This topic describes only the system APIs provided by this module. For details about the public APIs, see [@ohos.app.ability.StartOptions](js-apis-app-ability-startOptions.md).

## Modules to Import

```ts
import { StartOptions } from '@kit.AbilityKit';
```

## StartOptions

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| windowFocused<sup>12+</sup> | boolean | No | Yes | Whether the window is focused. The default value is **true**, indicating that the window is focused; **false** indicates that the window is not focused.<br>**Constraints**<br>1. This feature takes effect only on 2-in-1 and tablet devices.<br>2. It takes effect only in [UIAbilityContext.startAbility](js-apis-inner-application-uiAbilityContext.md#startability-1). |

**Example**

  ```ts
  import { UIAbility, Want, StartOptions } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  export default class EntryAbility extends UIAbility {

    onForeground() {
      let want: Want = {
        deviceId: '',
        bundleName: 'com.example.myapplication',
        abilityName: 'EntryAbility'
      };
      let options: StartOptions = {
        displayId: 0
      };

      try {
        // Start the specified ability, passing in the Want and StartOptions parameters.
        this.context.startAbility(want, options, (err: BusinessError) => {
          if (err.code) {
            // Process service logic errors.
            console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
            return;
          }
          // Carry out normal service processing.
          console.info('startAbility succeed');
        });
      } catch (err) {
        // Process input parameter errors.
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`startAbility failed, code is ${code}, message is ${message}`);
      }
    }
  }
  ```
