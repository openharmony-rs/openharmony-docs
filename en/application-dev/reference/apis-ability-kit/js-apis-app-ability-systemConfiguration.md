# @ohos.app.ability.systemConfiguration (System Environment Module)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @RuiChen_01-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=8bf852b2046babdde40e5fda6e0beeb685c8696d translatedAt=2026-09-03T10:34:13.827Z pushedAt=2026-09-08T08:03:50.669Z -->

The systemConfiguration module provides the capability to listen for system environment changes, including callbacks for changes in the system dark/light color mode, system language, and system font scale.

For example, by listening for changes in the system dark/light color mode, an app can sense the change and dynamically adjust its own dark/light theme to adapt to the system environment.

The difference between this module and the [EnvironmentCallback](js-apis-app-ability-environmentCallback.md) module is as follows:
- systemConfiguration module: used to listen for changes in the system environment variable [Configuration](js-apis-app-ability-configuration.md).
- [EnvironmentCallback](js-apis-app-ability-environmentCallback.md) module: used to listen for changes in the app environment variable [Configuration](js-apis-app-ability-configuration.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { systemConfiguration } from '@kit.AbilityKit';
```

## UpdatedCallback

UpdatedCallback is a callback used to listen for system environment changes. Developers can register a custom UpdatedCallback through [ApplicationContext.onSystemConfigurationUpdated](js-apis-inner-application-applicationContext.md#applicationcontextonsystemconfigurationupdated24) to listen for system environment changes.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| onColorModeUpdated | [OnColorModeUpdatedFn](#oncolormodeupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when the system color mode changes. |
| onFontSizeScaleUpdated | [OnFontSizeScaleUpdatedFn](#onfontsizescaleupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when the system font size scale changes. |
| onFontWeightScaleUpdated | [OnFontWeightScaleUpdatedFn](#onfontweightscaleupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when the system font weight scale changes. |
| onLanguageUpdated | [OnLanguageUpdatedFn](#onlanguageupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when the system language changes. |
| onFontIdUpdated | [OnFontIdUpdatedFn](#onfontidupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when the system font ID changes. |
| onMCCUpdated | [OnMCCUpdatedFn](#onmccupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when the Mobile Country Code (MCC) changes. |
| onMNCUpdated | [OnMNCUpdatedFn](#onmncupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when the Mobile Network Code (MNC) changes. |
| onHasPointerDeviceUpdated | [OnHasPointerDeviceUpdatedFn](#onhaspointerdeviceupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when a pointer device is connected or disconnected. |
| onLocaleUpdated | [OnLocaleUpdatedFn](#onlocaleupdatedfn) | No | Yes | After the listener for system environment changes is registered, the callback is triggered when the system locale changes. |

**Example**

```ts
import { UIAbility, systemConfiguration, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let callback: systemConfiguration.UpdatedCallback = {
      onColorModeUpdated: (colorMode: ConfigurationConstant.ColorMode) => {
        console.info(`system configuration updated colormode:` + colorMode);
      },
      onFontSizeScaleUpdated: (fontSizeScale: number) => {
        console.info(`system configuration updated fontSizeScale:` + fontSizeScale);
      },
      onFontWeightScaleUpdated: (fontWeightScale: number) => {
        console.info(`system configuration updated fontWeightScale:` + fontWeightScale);
      },
      onLanguageUpdated: (language: string) => {
        console.info(`system configuration updated language:` + language);
      },
      onFontIdUpdated: (fontId: string) => {
        console.info(`system configuration updated fontId:` + fontId);
      },
      onMCCUpdated: (mcc: string) => {
        console.info(`system configuration updated mcc:` + mcc);
      },
      onMNCUpdated: (mnc: string) => {
        console.info(`system configuration updated mnc:` + mnc);
      },
      onHasPointerDeviceUpdated: (hasPointerDevice: boolean) => {
        console.info(`system configuration updated hasPointerDevice:` + hasPointerDevice);
      },
      onLocaleUpdated: (locale: string) => {
        console.info(`system configuration updated locale:` + locale);
      }
    }
    // 1. Obtain the applicationContext through the context attribute.
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2. Register the listener through applicationContext.
      applicationContext.onSystemConfigurationUpdated(callback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```
## OnColorModeUpdatedFn

type OnColorModeUpdatedFn = (colorMode: ConfigurationConstant.ColorMode) => void

Called when the system color mode changes after the listener for system environment changes is registered.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | colorMode | [ConfigurationConstant.ColorMode](js-apis-app-ability-configurationConstant.md#colormode) | Yes | Color mode of the system after the change. |

## OnFontSizeScaleUpdatedFn

type OnFontSizeScaleUpdatedFn = (fontSizeScale: number) => void

Called when the system font scale changes after the listener for system environment changes is registered.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Required | Description |
  | -------- | -------- | -------- | -------- |
  | fontSizeScale | number | Yes | System font size scale after the change. |

## OnFontWeightScaleUpdatedFn

type OnFontWeightScaleUpdatedFn = (fontWeightScale: number) => void

Called when the system font weight scale changes after the listener for system environment changes is registered.


**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Required | Description |
  | -------- | -------- | -------- | -------- |
  | fontWeightScale | number | Yes | System font weight scale after the change. |

## OnLanguageUpdatedFn

type OnLanguageUpdatedFn = (language: string) => void

Called to trigger a callback when the system language changes after the listener for system environment changes is registered.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Required | Description |
  | -------- | -------- | -------- | -------- |
  | language | string | Yes | System language after the change. |

## OnFontIdUpdatedFn

type OnFontIdUpdatedFn = (fontId: string) => void

Called when the system font ID changes after the listener for system environment changes is registered.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | fontId | string | Yes | ID of the system font after the change. |

## OnMCCUpdatedFn

type OnMCCUpdatedFn = (mcc: string) => void

After the listener for system environment changes is registered, this callback is triggered when the country code of the mobile device changes.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Required | Description |
  | -------- | -------- | -------- | -------- |
  | mcc | string | Yes | Mobile Country Code (MCC) after the change. |

## OnMNCUpdatedFn

type OnMNCUpdatedFn = (mnc: string) => void

Called when the mobile device network code changes after the listener for system environment changes is registered.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | mnc | string | Yes | Mobile Network Code (MNC) after the change. |

## OnHasPointerDeviceUpdatedFn

type OnHasPointerDeviceUpdatedFn = (hasPointerDevice: boolean) => void

Called when a pointer device is connected or disconnected after the listener for system environment changes is registered.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Required | Description |
  | -------- | -------- | -------- | -------- |
  | hasPointerDevice | boolean | Yes | Whether a pointer device, such as a keyboard, mouse, or touchpad, is connected. The value true indicates that the device is connected, and false indicates the opposite. |

## OnLocaleUpdatedFn

type OnLocaleUpdatedFn = (locale: string) => void

Called when the system locale changes after the listener for system environment changes is registered.

**Model restriction:** This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | locale | string | Yes | System locale after the change. For details about this field, see [Configuration](js-apis-app-ability-configuration.md).|
