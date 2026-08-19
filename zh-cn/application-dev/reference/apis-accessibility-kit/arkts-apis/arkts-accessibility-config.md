# @ohos.accessibility.config

本模块提供系统辅助功能的配置，包括辅助扩展的启用与关闭、高对比度文字显示、鼠标键、无障碍字幕配置等。

**起始版本：** 23

<!--Device-unnamed-declare namespace config--><!--Device-unnamed-declare namespace config-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableAbility](arkts-accessibility-config-disableability-f-sys.md) | 关闭辅助扩展，需与[config.enableAbility](arkts-accessibility-config-enableability-f-sys.md)或 [config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md)配对使用。使用Promise异步回调。 |
| [disableAbility](arkts-accessibility-config-disableability-f-sys.md) | 关闭辅助扩展，需与[config.enableAbility](arkts-accessibility-config-enableability-f-sys.md)或 [config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md)配对使用。使用callback异步回调。 |
| [enableAbility](arkts-accessibility-config-enableability-f-sys.md) | 启用辅助扩展，需与[config.disableAbility](arkts-accessibility-config-disableability-f-sys.md)配对使用。使用Promise异步回调。 与[config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md)相比，本接口仅启用辅助扩展，不监听辅助扩展的连接状态变化；若需要监听辅助扩展断开 连接事件，请使用[config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md)。 |
| [enableAbility](arkts-accessibility-config-enableability-f-sys.md) | 启用辅助扩展，需与[config.disableAbility](arkts-accessibility-config-disableability-f-sys.md)配对使用。使用callback异步回调。 与[config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md)相比，本接口仅启用辅助扩展，不监听辅助扩展的连接状态变化；若需要监听辅助扩展断开 连接事件，请使用[config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md)。 |
| [enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md) | 启用辅助扩展，并指定[ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md)作为辅助扩展连接断开事件的回调函数。使用Promise异步回调。 当辅助扩展进程异常断开连接时，将触发ConnectCallback的onDisconnect回调。需与[config.disableAbility](arkts-accessibility-config-disableability-f-sys.md)配对使用。 |
| [getSeniorModeStateForApp](arkts-accessibility-config-getseniormodestateforapp-f-sys.md) | 查询应用“长辈模式”的状态。使用Promise异步回调。 |
| [offEnabledAccessibilityExtensionListChange](arkts-accessibility-config-offenabledaccessibilityextensionlistchange-f-sys.md) | Unregister listener that watches for changes in the enabled status of accessibility extensions. |
| [offInstalledAccessibilityListChange](arkts-accessibility-config-offinstalledaccessibilitylistchange-f-sys.md) | Unregister listener that watches for changes in the installed status of accessibility extensions. |
| [offSeniorModeStateChangeForApp](arkts-accessibility-config-offseniormodestatechangeforapp-f-sys.md) | 取消监听所有应用“长辈模式”的状态变化事件。使用callback异步回调。 |
| [off_enabledAccessibilityExtensionListChange](arkts-accessibility-config-offenabledaccessibilityextensionlistchange-f-sys.md) | 取消启用的辅助扩展的列表变化监听。使用callback异步回调。 |
| [off_installedAccessibilityListChange](arkts-accessibility-config-offinstalledaccessibilitylistchange-f-sys.md) | 取消已安装的辅助扩展的列表变化监听。使用callback异步回调。 |
| [onEnabledAccessibilityExtensionListChange](arkts-accessibility-config-onenabledaccessibilityextensionlistchange-f-sys.md) | Register the listener that watches for changes in the enabled status of accessibility extensions. |
| [onInstalledAccessibilityListChange](arkts-accessibility-config-oninstalledaccessibilitylistchange-f-sys.md) | Register the listener that watches for changes in the installed status of accessibility extensions. |
| [onSeniorModeStateChangeForApp](arkts-accessibility-config-onseniormodestatechangeforapp-f-sys.md) | 监听所有应用“长辈模式”的状态变化事件。使用callback异步回调。 |
| [on_enabledAccessibilityExtensionListChange](arkts-accessibility-config-onenabledaccessibilityextensionlistchange-f-sys.md) | 添加启用的辅助扩展的列表变化监听。使用callback异步回调。 需与 [config.off('enabledAccessibilityExtensionListChange')](arkts-accessibility-config-offenabledaccessibilityextensionlistchange-f-sys.md) 配对使用，在不需要监听时调用off取消注册，避免资源泄漏。 |
| [on_installedAccessibilityListChange](arkts-accessibility-config-oninstalledaccessibilitylistchange-f-sys.md) | 添加已安装的辅助扩展的列表变化监听。使用callback异步回调。 需与 [config.off('installedAccessibilityListChange')](arkts-accessibility-config-offenabledaccessibilityextensionlistchange-f-sys.md) 配对使用，在不需要监听时调用off取消注册，避免资源泄漏。 |
| [setMagnificationState](arkts-accessibility-config-setmagnificationstate-f-sys.md) | 设置放大效果的启用状态。放大效果依赖放大手势功能，仅在放大手势功能已启用的前提下，本接口的设置才会生效。 |
| [setSeniorModeStateForApp](arkts-accessibility-config-setseniormodestateforapp-f-sys.md) | 设置应用“长辈模式”的状态。使用Promise异步回调。 |
| [startBlinking](arkts-accessibility-config-startblinking-f-sys.md) | 启用闪光灯或屏幕以进行闪烁提醒。 |
| [stopBlinking](arkts-accessibility-config-stopblinking-f-sys.md) | 停止闪光灯闪烁或屏幕闪烁。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppSeniorModeInfo](arkts-accessibility-config-appseniormodeinfo-i-sys.md) | “长辈模式”在应用中的状态信息。 |
| [Config](arkts-accessibility-config-config-i-sys.md) | 用于属性的设置、获取与监听。 |
| [ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md) | 通过[config.enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md)接口启用辅助扩展应用时提供的回调函数。辅助扩展应用连接断开时，回调函数将被调 用。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BlinkResultCode](arkts-accessibility-config-blinkresultcode-e-sys.md) | 表示闪烁操作的结果码枚举。 |
| [BlinkingMode](arkts-accessibility-config-blinkingmode-e-sys.md) | 表示闪烁模式的枚举。 |
| [BlinkingScenario](arkts-accessibility-config-blinkingscenario-e-sys.md) | 表示闪烁场景的枚举。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ClickResponseTime](arkts-accessibility-config-clickresponsetime-t-sys.md) | 用于不同时间长短的点击持续时间。 |
| [DaltonizationColorFilter](arkts-accessibility-config-daltonizationcolorfilter-t-sys.md) | 色彩校正功能启用时（[daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate)设置为true）配置生效；色彩校正功能未启用时（ [daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate)设置为false）显示为正常类型。 |
| [OnDisconnectCallback](arkts-accessibility-config-ondisconnectcallback-t-sys.md) | 描述AccessibilityExtensionAbility断开连接的回调接口。 |
| [RepeatClickInterval](arkts-accessibility-config-repeatclickinterval-t-sys.md) | 忽略重复点击功能启用时（[ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick)设置为true）配置生效；忽略重复点击功能未启用时（ [ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick)设置为false）不生效。 |
<!--DelEnd-->

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [audioBalance](arkts-accessibility-config-con-sys.md#audiobalance) | 表示左右声道音量平衡的配置。-1.0表示仅左声道输出；0.0表示左右声道平衡输出；1.0表示仅右声道输出；中间值为左右声道音量的线性比例。取值范围为-1.0~1.0。默认值为0.0。 |
| [audioMono](arkts-accessibility-config-con-sys.md#audiomono) | 表示单声道音频功能启用状态。true表示已启用单声道音频功能，false表示未启用单声道音频功能，默认值为false。 |
| [clickResponseTime](arkts-accessibility-config-con-sys.md#clickresponsetime) | 表示点击持续时间功能配置。 |
| [daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate) | 表示色彩校正功能启用状态。配合daltonizationColorFilter使用。true表示已启用色彩校正功能，false表示未启用色彩校正功能，默认值为false。 |
| [ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick) | 表示忽略重复点击功能启用状态。配合repeatClickInterval使用。true表示已启用忽略重复点击功能，false表示未启用忽略重复点击功能，默认值为false。 |
| [repeatClickInterval](arkts-accessibility-config-con-sys.md#repeatclickinterval) | 表示忽略重复点击的时间间隔配置。配合ignoreRepeatClick使用，仅当ignoreRepeatClick设置为true时，此配置生效。默认值为Shortest，表示最短间隔。 |
| [screenMagnification](arkts-accessibility-config-con-sys.md#screenmagnification) | Indicates the configuration of screen magnification. |
| [shortkeyMultiTargets](arkts-accessibility-config-con-sys.md#shortkeymultitargets) | 表示辅助扩展快捷键的多目标列表配置。取值为辅助扩展应用的名称，格式为：['bundleName/abilityName']。格式不正确或名称无效时，设置不生效。 |
<!--DelEnd-->

