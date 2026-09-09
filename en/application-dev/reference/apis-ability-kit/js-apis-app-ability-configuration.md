# @ohos.app.ability.Configuration (Environment Variables)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=3710d9e6218f1ff30d75ca1e496a60e0f8529dc7 translatedAt=2026-09-03T10:12:15.536Z pushedAt=2026-09-05T10:47:30.369Z -->

The module defines the environment variables for the application runtime, including language, dark/light color mode, screen orientation, and font size. You can subscribe to these environment variables to adapt to different user preferences and enhance the interaction experience.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { Configuration } from '@kit.AbilityKit';
```

## Configuration

**System capability**: SystemCapability.Ability.AbilityBase

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| language | string | No | Yes | Indicates the current language of the application, for example, "zh" (Chinese) and "en" (English).<br>Supports developers to [set the application language](../../application-models/subscribe-system-environment-variable-changes.md#setting-application-language).<br>The value range can be obtained through [getSystemLanguages()](../apis-localization-kit/js-apis-i18n.md#getsystemlanguages9).<br>**Atomic service API**: Since API version 11, this API is supported in atomic services. |
| colorMode | [ConfigurationConstant.ColorMode](js-apis-app-ability-configurationConstant.md#colormode) | No| Yes| Dark/Light color mode of the application. The light color mode is used by default.<br>You can [set the dark/light color mode for an application or a component](../../application-models/subscribe-system-environment-variable-changes.md#setting-darklight-color-mode).<br>The options are as follows:<br>- **COLOR_MODE_NOT_SET**: The color mode is not set.<br>- **COLOR_MODE_LIGHT**: light mode.<br>- **COLOR_MODE_DARK**: dark mode.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| direction | [ConfigurationConstant.Direction](js-apis-app-ability-configurationConstant.md#direction) | No| Yes| Screen orientation of the application.<br>The options are as follows:<br>- **DIRECTION_NOT_SET**: The screen orientation is not set.<br>- **DIRECTION_HORIZONTAL**: horizontal direction.<br>- **DIRECTION_VERTICAL**: vertical direction.<br>You can subscribe to changes to this environment variable in the [UIAbility](./js-apis-app-ability-uiAbility.md) and [UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md), but not in the [ApplicationContext](./js-apis-inner-application-applicationContext.md) or [AbilityStage](./js-apis-app-ability-abilityStage.md).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| screenDensity  | [ConfigurationConstant.ScreenDensity](js-apis-app-ability-configurationConstant.md#screendensity) | No | Yes | Indicates the screen display density. It can be used to dynamically load resources of different resolutions.<br>Value range:<br />- SCREEN_DENSITY_NOT_SET: not set<br />- SCREEN_DENSITY_SDPI: 120<br />- SCREEN_DENSITY_MDPI: 160<br />- SCREEN_DENSITY_LDPI: 240<br />- SCREEN_DENSITY_XLDPI: 320<br />- SCREEN_DENSITY_XXLDPI: 480<br />- SCREEN_DENSITY_XXXLDPI: 640 <br>The font display size is positively correlated with the screen pixel density. By listening for screen pixel density changes, you can perceive the adjustment of the font display size. Generally, for the same physical size, the higher the screen pixel density, the larger the font display effect. <br />This environment variable can be subscribed to in the [UIAbility](./js-apis-app-ability-uiAbility.md) component and the [UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md) component, but not in the [ApplicationContext](./js-apis-inner-application-applicationContext.md) and [AbilityStage](./js-apis-app-ability-abilityStage.md) component containers.<br>**Atomic service API**: Since API version 11, this API is supported in atomic services. |
| displayId  | number | No | Yes | Indicates the ID of the physical screen where the application is located. In a multi-display device scenario, it can be used to distinguish the current screen and load different layouts or resources.<br />This environment variable can be subscribed to in the [UIAbility](./js-apis-app-ability-uiAbility.md) component and the [UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md) component, but not in the [ApplicationContext](./js-apis-inner-application-applicationContext.md) and [AbilityStage](./js-apis-app-ability-abilityStage.md) component containers.<br>**Atomic service API**: Since API version 11, this API is supported in atomic services. |
| hasPointerDevice  | boolean | No| Yes| Whether a pointer device, such as a keyboard, mouse, or touchpad, is connected. **true** if connected, **false** otherwise.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| fontId<sup>14+</sup> | string | No | Yes | Indicates the unique ID of the application font. When the system font is switched, developers can clear the cached glyphs/bitmaps and refresh the pre-rendered text based on this ID.<br>**Atomic service API**: Since API version 14, this API is supported in atomic services. |
| fontSizeScale<sup>12+</sup> | number | No | Yes | Indicates the font size scale. The value is a non-negative number, and the default value is 1.<br>Supports developers to [set the application font size](../../application-models/subscribe-system-environment-variable-changes.md#setting-font-size).<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
| fontWeightScale<sup>12+</sup> | number | No | Yes | Indicates the font weight scale. The value is a non-negative number, and the default value is 1.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
| mcc<sup>12+</sup> | string | No  | Yes | Indicates the mobile country code.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
| mnc<sup>12+</sup> | string | No  | Yes | Indicates the mobile network code.<br>**Atomic service API**: Since API version 12, this API is supported in atomic services. |
| locale<sup>20+</sup> | [Intl.Locale](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Locale) | No  | Yes | Indicates the locale.<br>The application automatically adjusts its behavior based on the current locale to meet the user's localization requirements. This attribute can be set by setting the system language, system region, and application preferred language.<br>**Atomic service API**: Since API version 20, this API is supported in atomic services. |

> **NOTE**
>
> - The value **No** in the **Read-only** column of each property in the **Configuration** object indicates that developers can assign values to these properties in code. However, this only modifies the property values of the **Configuration** object instance and does not change the running environment or system settings of the application. To set environment variables such as the language, dark/light color mode, and font size of the application, use the corresponding APIs, for example, [setLanguage](js-apis-inner-application-applicationContext.md#applicationcontextsetlanguage11), [setColorMode](js-apis-inner-application-applicationContext.md#applicationcontextsetcolormode11), and [setFontSizeScale](js-apis-inner-application-applicationContext.md#applicationcontextsetfontsizescale13).

**Example**

```ts
import { UIAbility, AbilityConstant, EnvironmentCallback, Want, Configuration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let envCallback: EnvironmentCallback = {
      onConfigurationUpdated(config: Configuration): void {
        console.info(`envCallback onConfigurationUpdated success: ${JSON.stringify(config)}`);
        let language = config.language;
        let colorMode = config.colorMode;
        let direction = config.direction;
        let screenDensity = config.screenDensity;
        let displayId = config.displayId;
        let hasPointerDevice = config.hasPointerDevice;
        let fontId = config.fontId;
        let fontSizeScale = config.fontSizeScale;
        let fontWeightScale = config.fontWeightScale;
        let mcc = config.mcc;
        let mnc = config.mnc;
        let locale = config.locale;
      },
      onMemoryLevel(level) {
        console.info(`onMemoryLevel level: ${level}`);
      }
    };
    try {
      let applicationContext = this.context.getApplicationContext();
      let callbackId = applicationContext.on('environment', envCallback);
      console.info(`callbackId: ${callbackId}`);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```