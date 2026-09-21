# Configuration

```TypeScript
export interface Configuration
```

The module defines environment change information. Configuration is an interface definition and is used only for field declaration.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [Configuration/Configuration](arkts-ability-app-ability-configuration-configuration-i.md)

**System capability:** SystemCapability.Ability.AbilityBase

## Modules to Import

```TypeScript
```

## colorMode

```TypeScript
colorMode?: ConfigurationConstant.ColorMode
```

Color mode, which can be **COLOR_MODE_LIGHT** or **COLOR_MODE_DARK**. The default value is **COLOR_MODE_LIGHT**.

**Type:** [ConfigurationConstant.ColorMode](arkts-ability-configurationconstant-colormode-depr-e.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [colorMode](arkts-ability-app-ability-configuration-configuration-i.md#colormode)

**System capability:** SystemCapability.Ability.AbilityBase

## language

```TypeScript
language?: string
```

Language of the application, for example, **zh**.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [language](arkts-ability-app-ability-configuration-configuration-i.md#language)

**System capability:** SystemCapability.Ability.AbilityBase

**Examples**

```TypeScript
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
