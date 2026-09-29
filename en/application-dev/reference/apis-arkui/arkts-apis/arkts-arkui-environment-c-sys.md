# Environment

```TypeScript
declare class Environment
```

Provides the capability to query device environment states. It can inject system environment variables (such as the dark/light mode, language, font scale, and layout direction) into AppStorage, enabling applications to perceive and respond to device environment changes. For details about how to use it on the UI, see [Environment: Device Environment Query](../../../ui/state-management/arkts-environment.md).

## Built-in Environment Variables

| key | Type | Description |  
| -------------------- | --------------- | ------------------------------------------------------------ |  
| accessibilityEnabled | string | Whether to enable accessibility. If there is no value of **accessibilityEnabled** in the environment variables, the default value passed through APIs such as **envProp** and **envProps** is added to AppStorage.|
| colorMode | [ColorMode](arkts-arkui-colormode-e.md) | Color mode. The options are as follows:<br> - **ColorMode.LIGHT**: light mode.<br> - **ColorMode.DARK**: dark mode. |
| fontScale | number | Font scale. |
| fontWeightScale | number | Font weight ratio. |
| layoutDirection | [LayoutDirection](arkts-arkui-layoutdirection-e.md) | Layout direction. The options are as follows:<br> - **LayoutDirection.LTR**: left to right;<br> - **LayoutDirection.RTL**: right to left;<br> - **LayoutDirection.Auto**: follows the system settings. |
| languageCode | string | Current system language, which is in lowercase letters, for example, **zh**. |

**Since:** 7

<!--Device-unnamed-declare class Environment--><!--Device-unnamed-declare class Environment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Environment-constructor()--><!--Device-Environment-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
