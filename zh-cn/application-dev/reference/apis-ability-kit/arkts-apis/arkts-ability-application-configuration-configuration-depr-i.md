# Configuration

定义环境变化信息。Configuration是接口定义，仅做字段声明。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Configuration/Configuration](arkts-ability-app-ability-configuration-configuration-i.md)

**系统能力：** SystemCapability.Ability.AbilityBase

## 导入模块

```TypeScript
```

## colorMode

```TypeScript
colorMode?: ConfigurationConstant.ColorMode
```

表示深浅色模式，取值范围：浅色模式（COLOR_MODE_LIGHT），深色模式（COLOR_MODE_DARK）。默认为浅色。

**类型：** ConfigurationConstant.ColorMode

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [colorMode](arkts-ability-app-ability-configuration-configuration-i.md#colormode)

**系统能力：** SystemCapability.Ability.AbilityBase

## language

```TypeScript
language?: string
```

表示应用程序的当前语言。例如：zh。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [language](arkts-ability-app-ability-configuration-configuration-i.md#language)

**系统能力：** SystemCapability.Ability.AbilityBase

**示例**

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
