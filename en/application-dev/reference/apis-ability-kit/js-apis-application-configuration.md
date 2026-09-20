# @ohos.application.Configuration (Configuration)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T10:56:32.991Z pushedAt=2026-09-05T10:47:30.499Z -->

The module defines environment change information. Configuration is an interface definition and is used only for field declaration.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This module is deprecated since API version 9. You are advised to use [@ohos.app.ability.Configuration (Environment Variables)](js-apis-app-ability-configuration.md) instead.

## Modules to Import

```ts
import Configuration from '@ohos.application.Configuration';
```

## Configuration

**System capability**: SystemCapability.Ability.AbilityBase

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| language<sup>8+</sup> | string | No| Yes| Language of the application, for example, **zh**.|
| colorMode<sup>8+</sup> | [ConfigurationConstant.ColorMode](js-apis-application-configurationConstant.md#colormode) | No| Yes| Color mode, which can be **COLOR_MODE_LIGHT** or **COLOR_MODE_DARK**. The default value is **COLOR_MODE_LIGHT**.|

**Example**
```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import EnvironmentCallback from '@ohos.app.ability.EnvironmentCallback';
import Want from '@ohos.app.ability.Want';
import Window from '@ohos.window';
import { BusinessError } from '@ohos.base';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
  }

  onDestroy() {
  }

  onWindowStageCreate(windowStage: Window.WindowStage) {
    let envCallback: EnvironmentCallback = {
      onConfigurationUpdated(config) {
        console.info(`envCallback onConfigurationUpdated success: ${JSON.stringify(config)}`);
        let language = config.language;
        let colorMode = config.colorMode;
      },
      onMemoryLevel(level) {
        console.info(`onMemoryLevel level: ${JSON.stringify(level)}`);
      }
    };

    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.on('environment', envCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }

    windowStage.loadContent('pages/index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content, data: ${JSON.stringify(data)}`);
    });
  }
}
```

