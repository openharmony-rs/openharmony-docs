# @ohos.app.ability.systemConfiguration (系统环境模块)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @RuiChen_01-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

systemConfiguration模块提供系统环境变化监听回调能力，包括系统深浅色模式、系统语言、系统字体大小缩放比例等变化的回调。

例如，通过对系统深浅色模式变化的监听，应用可感知系统的深浅色模式变化，并动态调整自身应用的深浅色主题以适配系统环境。

该模块与[EnvironmentCallback](js-apis-app-ability-environmentCallback.md)模块的区别在于：
- systemConfiguration模块：用于监听系统环境变量[Configuration](js-apis-app-ability-configuration.md)的变化。
- [EnvironmentCallback](js-apis-app-ability-environmentCallback.md)模块：用于监听某个应用环境变量[Configuration](js-apis-app-ability-configuration.md)的变化。

> **说明：**
>
> 本模块首批接口从API version 24 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { systemConfiguration } from '@kit.AbilityKit';
```

## UpdatedCallback

UpdatedCallback是监听系统环境变化的回调函数，开发者可通过[ApplicationContext.onSystemConfigurationUpdated](js-apis-inner-application-applicationContext.md#applicationcontextonsystemconfigurationupdated24)方法注册自定义的UpdatedCallback，来监听系统环境变化。

### onColorModeUpdated

onColorModeUpdated(colorMode: ConfigurationConstant.ColorMode): void

在注册系统环境变化的监听后，当系统深浅色模式变化时会触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | colorMode | [ConfigurationConstant.ColorMode](js-apis-app-ability-configurationConstant.md#colormode) | 是 | 变化后的系统深浅色模式。|

**示例：**

```ts
import { UIAbility, systemConfiguration, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onColorModeUpdated(colorMode: ConfigurationConstant.ColorMode) {
        console.info(`system configuration updated colormode:` + colorMode);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

### onFontSizeScaleUpdated

onFontSizeScaleUpdated(fontSizeScale: number): void

在注册系统环境变化的监听后，当系统字体大小缩放比例变化时触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | fontSizeScale | number | 是 | 变化后的系统字体大小缩放比例。|

**示例：**

```ts
import { UIAbility, systemConfiguration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onFontSizeScaleUpdated(fontSizeScale: number) {
        console.info(`system configuration updated ability:` + fontSizeScale);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

### onFontWeightScaleUpdated

onFontWeightScaleUpdated(fontWeightScale: number): void

在注册系统环境变化的监听后，当系统字体粗细缩放比例变化时触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | fontWeightScale | number | 是 | 变化后的系统字体粗细缩放比例。|

**示例：**

```ts
import { UIAbility, systemConfiguration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onFontWeightScaleUpdated(fontWeightScale: number) {
        console.info(`system configuration updated ability:` + fontWeightScale);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

### onLanguageUpdated

onLanguageUpdated(language: string): void

在注册系统环境变化的监听后，当系统语言变化时触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | language | string | 是 | 变化后的系统语言。|

**示例：**

```ts
import { UIAbility, systemConfiguration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onLanguageUpdated(language: string) {
        console.info(`system configuration updated ability:` + language);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

### onFontIdUpdated

onFontIdUpdated(fontId: string): void

在注册系统环境变化的监听后，当系统字体ID变化时触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | fontId | string | 是 | 变化后的系统字体ID。|

**示例：**

```ts
import { UIAbility, systemConfiguration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onFontIdUpdated(fontId: string) {
        console.info(`system configuration updated ability:` + fontId);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

### onMCCUpdated

onMCCUpdated(mcc: string): void

在注册系统环境变化的监听后，当移动设备国家代码变化时触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | mcc | string | 是 | 变化后的移动设备国家代码。|

**示例：**

```ts
import { UIAbility, systemConfiguration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onMCCUpdated(mcc: string) {
        console.info(`system configuration updated ability:` + mcc);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

### onMNCUpdated

onMNCUpdated(mnc: string): void

在注册系统环境变化的监听后，当移动设备网络代码变化时触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | mnc | string | 是 | 变化后的移动设备网络代码。|

**示例：**

```ts
import { UIAbility, systemConfiguration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onMNCUpdated(mnc: string) {
        console.info(`system configuration updated ability:` + mnc);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

### onHasPointerDeviceUpdated

onHasPointerDeviceUpdated(hasPointerDevice: boolean): void

在注册系统环境变化的监听后，当指针设备连接或者断开时触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | hasPointerDevice | boolean | 是 | 指针设备是否已连接，如键鼠、触控板等。true表示设备已连接，false表示设备未连接。|

**示例：**

```ts
import { UIAbility, systemConfiguration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onHasPointerDeviceUpdated(hasPointerDevice: boolean) {
        console.info(`system configuration updated ability:` + hasPointerDevice);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

### onLocaleUpdated

onLocaleUpdated(locale: string): void

在注册系统环境变化的监听后，当系统区域设置变化时触发回调。

**原子化服务API**：从API version 24开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | locale | string | 是 | 变化后的系统区域设置，该字段具体解释可以参考[Configuration](js-apis-app-ability-configuration.md)。|

**示例：**

```ts
import { UIAbility, systemConfiguration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onLocaleUpdated(locale: string) {
        console.info(`system configuration updated ability:` + locale);
      }
    }
    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```
