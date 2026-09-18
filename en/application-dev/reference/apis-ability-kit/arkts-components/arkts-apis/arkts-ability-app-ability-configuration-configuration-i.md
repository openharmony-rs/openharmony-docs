# Configuration

The module defines the environment variables for the application runtime, including language, dark/light color mode, screen orientation, and font size. You can subscribe to these environment variables to adapt to different user preferences and enhance the interaction experience.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## Modules to Import

```TypeScript
import { Configuration } from '@kit.AbilityKit';
```

## colorMode

```TypeScript
colorMode?: ConfigurationConstant.ColorMode
```

Dark/Light color mode of the application. The light color mode is used by default.

You can [set the dark/light color mode for an application or a component](../../../application-models/subscribe-system-environment-variable-changes.md#setting-darklight-color-mode).

The options are as follows:

- **COLOR_MODE_NOT_SET**: The color mode is not set.  
- **COLOR_MODE_LIGHT**: light mode.  
- **COLOR_MODE_DARK**: dark mode.

**Type:** [ConfigurationConstant.ColorMode](arkts-ability-configurationconstant-colormode-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## direction

```TypeScript
direction?: ConfigurationConstant.Direction
```

Screen orientation of the application.

The options are as follows:

- **DIRECTION_NOT_SET**: The screen orientation is not set.  
- **DIRECTION_HORIZONTAL**: horizontal direction.  
- **DIRECTION_VERTICAL**: vertical direction.

You can subscribe to changes to this environment variable in the [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) and [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md), but not in the [ApplicationContext](arkts-ability-applicationcontext-c.md) or [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md).

**Type:** [ConfigurationConstant.Direction](arkts-ability-configurationconstant-direction-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## displayId

```TypeScript
displayId?: number
```

ID of the display where the application is located.

You can subscribe to changes to this environment variable in the [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) and [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md), but not in the [ApplicationContext](arkts-ability-applicationcontext-c.md) or [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md).

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## fontId

```TypeScript
fontId?: string
```

Unique ID of the font.

**Type:** string

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Ability.AbilityBase

## fontSizeScale

```TypeScript
fontSizeScale?: number
```

Font size scale ratio. The value is a non-negative number. The default value is **1**.

You can [set the font size for an application](../../../application-models/subscribe-system-environment-variable-changes.md#setting-font-size).

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## fontWeightScale

```TypeScript
fontWeightScale?: number
```

Font weight scale ratio. The value is a non-negative number. The default value is **1**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## hasPointerDevice

```TypeScript
hasPointerDevice?: boolean
```

Whether a pointer device, such as a keyboard, mouse, or touchpad, is connected. **true** if connected, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## language

```TypeScript
language?: string
```

Current language of the application, for example, **zh** (Chinese) or **en** (English).

You can [set the application language](../../../application-models/subscribe-system-environment-variable-changes.md#setting-application-language).

For details about the value range, see [getSystemLanguages](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-system-c.md#getsystemlanguages).

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## locale

```TypeScript
locale?: Intl.Locale
```

Locale.

The application automatically adjusts its behavior based on the current locale to meet the localization requirements of users. This property can be set by configuring the system language, system region, and application preferred language.

**Type:** Intl.Locale

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityBase

## mcc

```TypeScript
mcc?: string
```

Mobile country code.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## mnc

```TypeScript
mnc?: string
```

Mobile network code.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityBase

## screenDensity

```TypeScript
screenDensity?: ConfigurationConstant.ScreenDensity
```

Screen density.

The options are as follows:

- **SCREEN_DENSITY_NOT_SET**: The pixel density is not set.  
- **SCREEN_DENSITY_SDPI**: 120.  
- **SCREEN_DENSITY_MDPI**: 160.  
- **SCREEN_DENSITY_LDPI**: 240.  
- **SCREEN_DENSITY_XLDPI**: 320.  
- **SCREEN_DENSITY_XXLDPI**: 480.  
- **SCREEN_DENSITY_XXXLDPI**: 640.

The font size is positively correlated with the screen pixel density. By monitoring changes in the screen pixel density, you can detect adjustments in the font size. Typically, for the same physical size, the higher the screen pixel density, the larger the font display effect.

You can subscribe to changes to this environment variable in the [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) and [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md), but not in the [ApplicationContext](arkts-ability-applicationcontext-c.md) or [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md).

**Type:** [ConfigurationConstant.ScreenDensity](arkts-ability-configurationconstant-screendensity-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase
