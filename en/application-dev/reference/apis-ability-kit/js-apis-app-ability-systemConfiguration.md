# @ohos.app.ability.systemConfiguration (System Configuration Module)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @RuiChen_01-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=3aa40246364e56f5b7bd8781719da2a82c6b0f3a translatedAt=2026-06-03T07:28:54.854Z pushedAt=2026-06-03T09:04:18.055Z -->

The systemConfiguration module provides the capability to listen for system configuration change callbacks, including callbacks for changes in system dark/light mode, system language, system font size scaling ratio, and more.

For example, by listening for system dark/light mode changes, an application can perceive the system's dark/light mode changes and dynamically adjust its own dark/light theme to adapt to the system configuration.

The difference between this module and the [EnvironmentCallback](js-apis-app-ability-environmentCallback.md) module is as follows:

- systemConfiguration module: Used to listen for changes in the system configuration variable [Configuration](js-apis-app-ability-configuration.md).

- [EnvironmentCallback](js-apis-app-ability-environmentCallback.md) module: Used to listen for changes in an application's environment variables [Configuration](js-apis-app-ability-configuration.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { systemConfiguration } from '@kit.AbilityKit';
```

## UpdatedCallback

UpdatedCallback is a callback function for listening to system configuration changes. Developers can register a custom UpdatedCallback through [ApplicationContext.onSystemConfigurationUpdated](js-apis-inner-application-applicationContext.md#applicationcontextonsystemconfigurationupdated24) to listen for system configuration changes.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| onColorModeUpdated | [OnColorModeUpdatedFn](#oncolormodeupdatedfn) | No | Yes | Triggered when the system color mode changes, after the listener for system configuration changes is registered. |
| onFontSizeScaleUpdated | [OnFontSizeScaleUpdatedFn](#onfontsizescaleupdatedfn) | No | Yes | Triggered when the system font size scale changes, after the listener for system configuration changes is registered. |
| onFontWeightScaleUpdated | [OnFontWeightScaleUpdatedFn](#onfontweightscaleupdatedfn) | No | Yes | Triggered when the system font weight scale changes, after the listener for system configuration changes is registered. |
| onLanguageUpdated | [OnLanguageUpdatedFn](#onlanguageupdatedfn) | No | Yes | Triggered when the system language changes, after the listener for system configuration changes is registered. |
| onFontIdUpdated | [OnFontIdUpdatedFn](#onfontidupdatedfn) | No | Yes | Triggered when the system font ID changes, after the listener for system configuration changes is registered. |
| onMCCUpdated | [OnMCCUpdatedFn](#onmccupdatedfn) | No | Yes | Triggered when the mobile country code changes, after the listener for system configuration changes is registered. |
| onMNCUpdated | [OnMNCUpdatedFn](#onmncupdatedfn) | No | Yes | Triggered when the mobile network code changes, after the listener for system configuration changes is registered. |
| onHasPointerDeviceUpdated | [OnHasPointerDeviceUpdatedFn](#onhaspointerdeviceupdatedfn) | No | Yes | Triggered when a pointer device is connected or disconnected, after the listener for system configuration changes is registered. |
| onLocaleUpdated | [OnLocaleUpdatedFn](#onlocaleupdatedfn) | No | Yes | Triggered when the system locale changes, after the listener for system configuration changes is registered. |

**Example:**

```ts
import { UIAbility, systemConfiguration, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let CallBack: systemConfiguration.UpdatedCallback = {
      onColorModeUpdated(colorMode: ConfigurationConstant.ColorMode) {
        console.info(`system configuration updated colormode:` + colorMode);
      },
      onFontSizeScaleUpdated(fontSizeScale: number) {
        console.info(`system configuration updated fontSizeScale:` + fontSizeScale);
      },
      onFontWeightScaleUpdated(fontWeightScale: number) {
        console.info(`system configuration updated fontWeightScale:` + fontWeightScale);
      },
      onLanguageUpdated(language: string) {
        console.info(`system configuration updated language:` + language);
      },
      onFontIdUpdated(fontId: string) {
        console.info(`system configuration updated fontId:` + fontId);
      },
      onMCCUpdated(mcc: string) {
        console.info(`system configuration updated mcc:` + mcc);
      },
      onMNCUpdated(mnc: string) {
        console.info(`system configuration updated mnc:` + mnc);
      },
      onHasPointerDeviceUpdated(hasPointerDevice: boolean) {
        console.info(`system configuration updated hasPointerDevice:` + hasPointerDevice);
      },
      onLocaleUpdated(locale: string) {
        console.info(`system configuration updated locale:` + locale);
      }
    }
    // 1. Obtain the applicationContext through the context attribute.
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2. Register a listener through the applicationContext.
      applicationContext.onSystemConfigurationUpdated(CallBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

## OnColorModeUpdatedFn

type OnColorModeUpdatedFn = (colorMode: ConfigurationConstant.ColorMode) => void

After registering a listener for system configuration changes, the callback is triggered when the system dark/light color mode changes.

**Model restriction**: This API can be used only in the Stage model.

**Atomic service API**: This API is supported in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | colorMode | [ConfigurationConstant.ColorMode](js-apis-app-ability-configurationConstant.md#colormode) | Yes | Changed system color mode. |

## OnFontSizeScaleUpdatedFn

type OnFontSizeScaleUpdatedFn = (fontSizeScale: number) => void

After registering a listener for system configuration changes, the callback is triggered when the system font size scale changes.

**Model restriction**: This API can be used only in the Stage model.

**Atomic service API**: This API supports use in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | fontSizeScale | number | Yes | Scale factor of the system font size after the change.|

## OnFontWeightScaleUpdatedFn

type OnFontWeightScaleUpdatedFn = (fontWeightScale: number) => void

After registering the listener for system configuration changes, the callback is triggered when the system font weight scale changes.

**Model restriction**: This API can be used only in the Stage model.

**Atomic service API**: This API supports use in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | fontWeightScale | number | Yes | Scale ratio of the system font weight after the change.|

## OnLanguageUpdatedFn

type OnLanguageUpdatedFn = (language: string) => void

Triggered when the system language changes, after registering a listener for system configuration changes.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | language | string | Yes | Changed system language.|

## OnFontIdUpdatedFn

type OnFontIdUpdatedFn = (fontId: string) => void

After registering a listener for system configuration changes, this callback is triggered when the system font ID changes.

**Model restriction**: This API can be used only in the Stage model.

**Atomic service API**: This API is supported in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | fontId | string | Yes | ID of the changed system font.|

## OnMCCUpdatedFn

type OnMCCUpdatedFn = (mcc: string) => void

After registering a listener for system configuration changes, this callback is triggered when the mobile country code changes.

**Model restriction**: This API can be used only in the Stage model.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | mcc | string | Yes | Changed mobile country code.|

## OnMNCUpdatedFn

type OnMNCUpdatedFn = (mnc: string) => void

After registering a listener for system configuration changes, this callback is triggered when the mobile device network code changes.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API supports use in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | mnc | string | Yes | Changed mobile device network code.|

## OnHasPointerDeviceUpdatedFn

type OnHasPointerDeviceUpdatedFn = (hasPointerDevice: boolean) => void

After registering the listener for system configuration changes, the callback is triggered when a pointer device is connected or disconnected.

**Model restriction**: This API can be used only in the Stage model.

**Atomic service API**: This API is supported in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | hasPointerDevice | boolean | Yes | Whether a pointer device (such as a keyboard, mouse, or touchpad) is connected. The value **true** means the device is connected, and **false** means the device is not connected.|

## OnLocaleUpdatedFn

type OnLocaleUpdatedFn = (locale: string) => void

Called when the system locale changes after the listener for system configuration changes is registered.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API is supported in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | locale | string | Yes | Changed system locale. For details about this field, see [Configuration](js-apis-app-ability-configuration.md).|