# Configuration

定义了应用运行时的环境变量，包含语言、深浅色、屏幕方向、字体等。开发者可以通过订阅环境变量，适配不同用户偏好，提升交互体验。

**起始版本：** 9

<!--Device-unnamed-export interface Configuration--><!--Device-unnamed-export interface Configuration-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## 导入模块

```TypeScript
import { Configuration } from '@kit.AbilityKit';
```

## colorMode

```TypeScript
colorMode?: ConfigurationConstant.ColorMode
```

表示应用深浅色模式，默认为浅色。

支持开发者[设置应用或组件深浅色](../../application-models/subscribe-system-environment-variable-changes.md#设置深浅色模式)。

取值范围：

- COLOR_MODE_NOT_SET：未设置  
- COLOR_MODE_LIGHT：浅色模式  
- COLOR_MODE_DARK：深色模式

**类型：** ConfigurationConstant.ColorMode

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-colorMode?: ConfigurationConstant.ColorMode--><!--Device-Configuration-colorMode?: ConfigurationConstant.ColorMode-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## direction

```TypeScript
direction?: ConfigurationConstant.Direction
```

表示应用屏幕方向。

取值范围：

- DIRECTION_NOT_SET：未设置  
- DIRECTION_HORIZONTAL：水平方向  
- DIRECTION_VERTICAL：垂直方向

该环境变量支持在[UIAbility](./js-apis-app-ability-uiAbility.md)组件和[UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md)组件中订阅，不支持在[ApplicationContext](./js-apis-inner-application-applicationContext.md)和[AbilityStage](./js-apis-app-ability-abilityStage.md)组件容器中订阅。

**类型：** ConfigurationConstant.Direction

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-direction?: ConfigurationConstant.Direction--><!--Device-Configuration-direction?: ConfigurationConstant.Direction-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## displayId

```TypeScript
displayId?: number
```

表示应用所在的物理屏幕ID。

该环境变量支持在[UIAbility](./js-apis-app-ability-uiAbility.md)组件和[UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md)组件中订阅，不支持在[ApplicationContext](./js-apis-inner-application-applicationContext.md)和[AbilityStage](./js-apis-app-ability-abilityStage.md)组件容器中订阅。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-displayId?: long--><!--Device-Configuration-displayId?: long-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## fontId

```TypeScript
fontId?: string
```

表示应用字体的唯一ID。

**类型：** string

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-fontId?: string--><!--Device-Configuration-fontId?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## fontSizeScale

```TypeScript
fontSizeScale?: number
```

表示字体大小缩放比例，取值为非负数，默认值为1。

支持开发者[设置应用字体大小](../../application-models/subscribe-system-environment-variable-changes.md#设置字体大小)。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-fontSizeScale?: double--><!--Device-Configuration-fontSizeScale?: double-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## fontWeightScale

```TypeScript
fontWeightScale?: number
```

表示字体粗细缩放比例，取值为非负数，默认值为1。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-fontWeightScale?: double--><!--Device-Configuration-fontWeightScale?: double-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## hasPointerDevice

```TypeScript
hasPointerDevice?: boolean
```

表示指针设备是否已连接，如键鼠、触控板等。true表示设备已连接，false表示设备未连接。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-hasPointerDevice?: boolean--><!--Device-Configuration-hasPointerDevice?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## language

```TypeScript
language?: string
```

表示应用当前语言，例如“zh"(中文)，“en”（英文）。

支持开发者[设置应用语言](../../application-models/subscribe-system-environment-variable-changes.md#设置应用语言)。

取值范围参考[获取系统支持的语言列表](../apis-localization-kit/js-apis-i18n.md#getsystemlanguages9)。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-language?: string--><!--Device-Configuration-language?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## locale

```TypeScript
locale?: Intl.Locale
```

表示区域设置。

应用会根据当前的区域设置自动调整其行为，以符合用户的本地化需求。该属性可以通过设置系统语言、设置系统地区和设置应用偏好语言等方式设置。

**类型：** Intl.Locale

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-locale?: Intl.Locale--><!--Device-Configuration-locale?: Intl.Locale-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## mcc

```TypeScript
mcc?: string
```

表示移动设备国家代码。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-mcc?: string--><!--Device-Configuration-mcc?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## mnc

```TypeScript
mnc?: string
```

表示移动设备网络代码。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-mnc?: string--><!--Device-Configuration-mnc?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## screenDensity

```TypeScript
screenDensity?: ConfigurationConstant.ScreenDensity
```

表示屏幕显示密度。

取值范围：

- SCREEN_DENSITY_NOT_SET：未设置  
- SCREEN_DENSITY_SDPI：120  
- SCREEN_DENSITY_MDPI：160  
- SCREEN_DENSITY_LDPI：240  
- SCREEN_DENSITY_XLDPI：320  
- SCREEN_DENSITY_XXLDPI：480  
- SCREEN_DENSITY_XXXLDPI：640

字体显示大小与屏幕像素密度呈正相关关系。通过监听屏幕像素密度变化，可以感知字体显示大小的调整。通常情况下，对于相同的物理尺寸，屏幕像素密度越高，字体显示效果越大。

该环境变量支持在[UIAbility](./js-apis-app-ability-uiAbility.md)组件和[UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md)组件中订阅，不支持在[ApplicationContext](./js-apis-inner-application-applicationContext.md)和[AbilityStage](./js-apis-app-ability-abilityStage.md)组件容器中订阅。

**类型：** ConfigurationConstant.ScreenDensity

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-screenDensity?: ConfigurationConstant.ScreenDensity--><!--Device-Configuration-screenDensity?: ConfigurationConstant.ScreenDensity-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

