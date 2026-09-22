# @ohos.accessibility.config(System Accessibility Configuration)

The **accessibility.config** module provides APIs for configuring system accessibility features, including accessibility extension, high-contrast text, mouse buttons, and captions.

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [disableAbility](arkts-accessibility-config-disableability-f-sys.md#disableability) | Disables an accessibility extension. This API must be used together with [config.enableAbility](arkts-accessibility-config-enableability-f-sys.md) or [config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md). This API uses a promise to return the result. |
| [disableAbility](arkts-accessibility-config-disableability-f-sys.md#disableability-1) | Disables an accessibility extension. This API must be used together with [config.enableAbility](arkts-accessibility-config-enableability-f-sys.md) or [config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md). This API uses an asynchronous callback to return the result. |
| [enableAbility](arkts-accessibility-config-enableability-f-sys.md#enableability) | Enables an accessibility extension. This API must be used together with [config.disableAbility](arkts-accessibility-config-disableability-f-sys.md). This API uses a promise to return the result. |
| [enableAbility](arkts-accessibility-config-enableability-f-sys.md#enableability-1) | Enables an accessibility extension. This API must be used together with [config.disableAbility](arkts-accessibility-config-disableability-f-sys.md). This API uses an asynchronous callback to return the result. |
| [enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md) | Enables an accessibility extension and specifies [ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md) as the callback for disconnection events of the accessibility extension. This API uses a promise to return the result. |
| [getSeniorModeStateForApp](arkts-accessibility-config-getseniormodestateforapp-f-sys.md) | Queries the senior mode state of an app. This API uses a promise to return the result. |
| [off](arkts-accessibility-config-off-f-sys.md#offenabledaccessibilityextensionlistchange) | Cancels the listener for changes in the list of enabled accessibility extensions. This API uses an asynchronous callback to return the result. |
| [off](arkts-accessibility-config-off-f-sys.md#offinstalledaccessibilitylistchange) | Cancels the listener for changes in the list of installed accessibility extensions. This API uses an asynchronous callback to return the result. |
| [offSeniorModeStateChangeForApp](arkts-accessibility-config-offseniormodestatechangeforapp-f-sys.md) | Cancels the listener for senior mode state change events of all apps. This API uses an asynchronous callback to return the result. |
| [on](arkts-accessibility-config-on-f-sys.md#onenabledaccessibilityextensionlistchange) | Adds a listener for changes in the list of enabled accessibility extensions. This API uses an asynchronous callback to return the result. |
| [on](arkts-accessibility-config-on-f-sys.md#oninstalledaccessibilitylistchange) | Adds a listener for changes in the list of installed accessibility extensions. This API uses an asynchronous callback to return the result. |
| [onSeniorModeStateChangeForApp](arkts-accessibility-config-onseniormodestatechangeforapp-f-sys.md) | Listens for senior mode state change events of all apps. This API uses an asynchronous callback to return the result. |
| [setMagnificationState](arkts-accessibility-config-setmagnificationstate-f-sys.md) | Sets the enabled state of the magnification effect. The magnification effect depends on the magnification gesture feature. This API takes effect only when the magnification gesture feature is enabled. |
| [setSeniorModeStateForApp](arkts-accessibility-config-setseniormodestateforapp-f-sys.md) | Sets the senior mode state for an app. This API uses a promise to return the result. |
| [startBlinking](arkts-accessibility-config-startblinking-f-sys.md) | Enables the flash or screen for blinking reminders. |
| [stopBlinking](arkts-accessibility-config-stopblinking-f-sys.md) | Stops flash blinking or screen blinking. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AppSeniorModeInfo](arkts-accessibility-config-appseniormodeinfo-i-sys.md) | Senior mode state information of an app. |
| [Config](arkts-accessibility-config-config-i-sys.md) | Implements configuration, acquisition, and listening for properties. |
| [ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md) | Callback provided when enabling an accessibility extension app through the [config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md) API. The callback is invoked when the connection to the accessibility extension app is disconnected. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [BlinkingMode](arkts-accessibility-config-blinkingmode-e-sys.md) | Enumerates the blinking modes. |
| [BlinkingScenario](arkts-accessibility-config-blinkingscenario-e-sys.md) | Enumerates the blinking scenarios. |
| [BlinkResultCode](arkts-accessibility-config-blinkresultcode-e-sys.md) | Enumerates the result codes of blinking operations. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ClickResponseTime](arkts-accessibility-config-clickresponsetime-t-sys.md) | Click duration of different lengths. |
| [DaltonizationColorFilter](arkts-accessibility-config-daltonizationcolorfilter-t-sys.md) | Color correction filters for different types of color vision deficiency. |
| [OnDisconnectCallback](arkts-accessibility-config-ondisconnectcallback-t-sys.md) | Describes the callback to be invoked when the connection to **AccessibilityExtensionAbility** is disconnected. |
| [RepeatClickInterval](arkts-accessibility-config-repeatclickinterval-t-sys.md) | Ignore repeated clicks at different time intervals. |
<!--DelEnd-->

<!--Del-->
### Properties(System API)

| Name | Description |
| --- | --- |
| [animationOff](arkts-accessibility-config-p-sys.md) | Whether to disable animation. The value **true** indicates that animation is disabled, and **false** indicates the opposite. |
| [brightnessDiscount](arkts-accessibility-config-p-sys.md) | Indicates the brightness discount configuration, which is used to proportionally adjust the screen display brightness. The value ranges from 0 to 1.0, where **0** indicates no brightness discount (original brightness) and **1.0** indicates the maximum brightness discount. The default value is **0.0**. |
| [captions](arkts-accessibility-config-p-sys.md) | Whether to enable captions. The value **true** indicates that caption is enabled, and **false** indicates the opposite. |
| [captionsStyle](arkts-accessibility-config-p-sys.md) | Indicates the configuration of the caption style. |
| [contentTimeout](arkts-accessibility-config-p-sys.md) | Indicates the content display suggested duration configuration, which is used to set the duration for which accessibility prompts and other content remain displayed on the screen. The value ranges from 0 to 5000, in milliseconds. The default value is **0**. |
| [daltonizationColorFilter](arkts-accessibility-config-p-sys.md) | Indicates the color correction filter configuration. Used together with daltonizationState. This configuration takes effect only when daltonizationState is set to **true**. The default value is Normal, indicating the standard type. |
| [highContrastText](arkts-accessibility-config-p-sys.md) | Whether to enable high-contrast text. The value **true** indicates that high-contrast text is enabled, and **false** indicates the opposite. |
| [invertColor](arkts-accessibility-config-p-sys.md) | Whether to enable color inversion. The value **true** indicates that color inversion is enabled, and **false** indicates the opposite. |
| [mouseAutoClick](arkts-accessibility-config-p-sys.md) | Indicates the configuration for the mouse auto-click operation. The value ranges from 0 to 5000, in milliseconds. **0** indicates that the feature is disabled, and other values indicate the duration of mouse hovering that triggers the auto-click operation. The default value is **0**. |
| [mouseKey](arkts-accessibility-config-p-sys.md) | Whether to enable the mouse button. The value **true** indicates that the mouse button is enabled, and **false** indicates the opposite. |
| [shortkey](arkts-accessibility-config-p-sys.md) | Indicates the accessibility extension shortcut key feature status. Used together with shortkeyTarget. The value **true** indicates that the accessibility extension shortcut key feature is enabled, and **false** indicates that it is disabled. The default value is **false**. |
| [shortkeyTarget](arkts-accessibility-config-p-sys.md) | Indicates the target configuration of the accessibility extension shortcut key. The value is the name of the accessibility extension app, in the format 'bundleName/abilityName'. If the format is incorrect or the name is invalid, the setting does not take effect. |
<!--DelEnd-->

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [audioBalance](arkts-accessibility-config-con-sys.md#audiobalance) | Indicates the configuration for left and right channel volume balance. **-1.0** indicates output from the left channel only; **0.0** indicates balanced output from both channels; **1.0** indicates output from the right channel only. Intermediate values represent a linear ratio of the left and right channel volumes. The value ranges from -1.0 to 1.0. The default value is **0.0**. |
| [audioMono](arkts-accessibility-config-con-sys.md#audiomono) | Indicates the mono audio feature status. The value **true** indicates that the mono audio feature is enabled, and **false** indicates that it is disabled. The default value is **false**. |
| [clickResponseTime](arkts-accessibility-config-con-sys.md#clickresponsetime) | Length of time required for a click. |
| [daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate) | Indicates the color correction feature status. Used together with daltonizationColorFilter. The value **true** indicates that color correction is enabled, and **false** indicates that it is disabled. The default value is **false**. |
| [ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick) | Whether to ignore repeated clicks. This parameter must be used together with **repeatClickInterval**. The value **true** indicates that the feature of ignoring repeated clicks is enabled, and **false** indicates the opposite. |
| [repeatClickInterval](arkts-accessibility-config-con-sys.md#repeatclickinterval) | Indicates the configuration for the interval of ignoring repeated clicks. Used together with ignoreRepeatClick. This configuration takes effect only when ignoreRepeatClick is set to **true**. The default value is Shortest, indicating the shortest interval. |
| [screenMagnification](arkts-accessibility-config-con-sys.md#screenmagnification) | Indicates the configuration of screen magnification. |
| [shortkeyMultiTargets](arkts-accessibility-config-con-sys.md#shortkeymultitargets) | Indicates the multi-target list configuration of the accessibility extension shortcut key. The value is the name of the accessibility extension app, in the format ['bundleName/abilityName']. If the format is incorrect or the name is invalid, the setting does not take effect. |
<!--DelEnd-->
