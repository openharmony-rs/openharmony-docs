# Environment

```TypeScript
declare class Environment
```

For details about how to use environment parameters, see [Environment: Device Environment Query](../../../ui/state-management/arkts-environment.md).

## Built-in Environment Variables

| key | Type | Description |  
| -------------------- | --------------- | ------------------------------------------------------------ |  
| accessibilityEnabled | string | Whether to enable accessibility. If there is no value of **accessibilityEnabled** in the environment variables, the default value passed through APIs such as **envProp** and **envProps** is added to AppStorage.|
| colorMode | [ColorMode](arkts-arkui-colormode-e.md) | Color mode. The options are as follows:<br>- **ColorMode.LIGHT**: light mode.<br>- **ColorMode.DARK**: dark mode.|
| fontScale | number | Font scale. |
| [fontWeightScale](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md) | number | Font weight ratio. |
| [layoutDirection](arkts-arkui-securitycomponentmethod-c.md) | [LayoutDirection](arkts-arkui-layoutdirection-e.md) | Layout direction. The options are as follows:<br>- **LayoutDirection.LTR**: from left to right.<br>- **LayoutDirection.RTL**: from right to left.<br>- **Auto**: follows the system settings.|
| languageCode | string | Current system language, which is in lowercase letters, for example, **zh**.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

Constructor.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
