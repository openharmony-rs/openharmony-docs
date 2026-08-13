# @ohos.accessibility.config

本模块提供系统辅助功能的配置，包括辅助扩展的启用与关闭、高对比度文字显示、鼠标键、无障碍字幕配置等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace config--><!--Device-unnamed-declare namespace config-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableAbility](arkts-accessibility-config-disableability-f-sys.md#disableAbility) | 关闭辅助扩展。使用Promise异步回调。 |
| [disableAbility](arkts-accessibility-config-disableability-f-sys.md#disableAbility（系统接口）) | 关闭辅助扩展，使用callback异步回调。 |
| [enableAbility](arkts-accessibility-config-enableability-f-sys.md#enableAbility) | 启用辅助扩展。使用Promise异步回调。 |
| [enableAbility](arkts-accessibility-config-enableability-f-sys.md#enableAbility（系统接口）) | 启用辅助扩展，使用callback异步回调。 |
| [enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md#enableAbilityWithCallback) | 启用辅助扩展，并指定[ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md#ConnectCallback（系统接口）)作为辅助扩展应用状态变化的回调函数。使用Promise异步回调。 |
| [getSeniorModeStateForApp](arkts-accessibility-config-getseniormodestateforapp-f-sys.md#getSeniorModeStateForApp) | Get the senior mode state for app. |
| [offEnabledAccessibilityExtensionListChange](arkts-accessibility-config-offenabledaccessibilityextensionlistchange-f-sys.md#offEnabledAccessibilityExtensionListChange) | Unregister listener that watches for changes in the enabled status of accessibility extensions. |
| [offInstalledAccessibilityListChange](arkts-accessibility-config-offinstalledaccessibilitylistchange-f-sys.md#offInstalledAccessibilityListChange) | Unregister listener that watches for changes in the installed status of accessibility extensions. |
| [offSeniorModeStateChangeForApp](arkts-accessibility-config-offseniormodestatechangeforapp-f-sys.md#offSeniorModeStateChangeForApp) | Unregister the observer for application's senior mode state changes. |
| off_enabledAccessibilityExtensionListChange | 取消启用的辅助扩展的列表变化监听，使用callback异步回调。 |
| off_installedAccessibilityListChange | 取消已安装的辅助扩展的列表变化监听，使用callback异步回调。 |
| [onEnabledAccessibilityExtensionListChange](arkts-accessibility-config-onenabledaccessibilityextensionlistchange-f-sys.md#onEnabledAccessibilityExtensionListChange) | Register the listener that watches for changes in the enabled status of accessibility extensions. |
| [onInstalledAccessibilityListChange](arkts-accessibility-config-oninstalledaccessibilitylistchange-f-sys.md#onInstalledAccessibilityListChange) | Register the listener that watches for changes in the installed status of accessibility extensions. |
| [onSeniorModeStateChangeForApp](arkts-accessibility-config-onseniormodestatechangeforapp-f-sys.md#onSeniorModeStateChangeForApp) | Register an observer for anyone application's senior mode state changes. |
| on_enabledAccessibilityExtensionListChange | 添加启用的辅助扩展的列表变化监听，使用callback异步回调。 |
| on_installedAccessibilityListChange | 添加已安装的辅助扩展的列表变化监听，使用callback异步回调。 |
| [setMagnificationState](arkts-accessibility-config-setmagnificationstate-f-sys.md#setMagnificationState) | 触发或者关闭放大手势功能的放大效果，使用前需要保证放大手势功能已开启。 |
| [setSeniorModeStateForApp](arkts-accessibility-config-setseniormodestateforapp-f-sys.md#setSeniorModeStateForApp) | Set the senior mode state for app. |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppSeniorModeInfo](arkts-accessibility-config-appseniormodeinfo-i-sys.md) | Indicates the senior mode information of an application. |
| [Config](arkts-accessibility-config-config-i-sys.md) | 用于属性的设置、获取与监听。 |
| [ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md) | 通过[enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md#enableAbilityWithCallback（系统接口）)接口启用辅助扩展应用时提供的回调函数。辅助扩展应用连接断开时，回调函数将被调用。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ClickResponseTime](arkts-accessibility-config-clickresponsetime-t-sys.md) | 用于不同时间长短的点击重复时间。 |
| [DaltonizationColorFilter](arkts-accessibility-config-daltonizationcolorfilter-t-sys.md) | 颜色滤镜功能开启时（[daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationState)设置为true)，颜色滤镜的配置(即设置的DaltonizationColorFilter的值)生效；颜色滤镜功能关闭 时（[daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationState)设置为false)，显示为正常类型。 |
| [OnDisconnectCallback](arkts-accessibility-config-ondisconnectcallback-t-sys.md) | 描述AccessibilityExtensionAbility断开连接的回调接口。 |
| [RepeatClickInterval](arkts-accessibility-config-repeatclickinterval-t-sys.md) | 忽略重复点击功能开启时（[ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignoreRepeatClick)设置为true)，忽略重复点击的配置(即设置的RepeatClickInterval的值)生效；忽略重复点击功能关闭时 （[ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignoreRepeatClick)设置为false)，显示为正常类型。 |
<!--DelEnd-->

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [audioBalance](arkts-accessibility-config-con-sys.md#audioBalance) | 表示左右声道音量平衡的配置。取值范围为-1.0~1.0。默认值为0.0。 |
| [audioMono](arkts-accessibility-config-con-sys.md#audioMono) | 表示单声道音频的配置。true表示已启用单声道音频，false表示未启用单声道音频，默认值为false。 |
| [clickResponseTime](arkts-accessibility-config-con-sys.md#clickResponseTime) | 表示点击持续时间功能配置。 |
| [daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationState) | 表示颜色滤镜功能启动状态。配合daltonizationColorFilter使用。true表示已启用颜色滤镜功能，false表示未启用颜色滤镜功能，默认值为false。 |
| [ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignoreRepeatClick) | 表示忽略重复点击功能启用状态。配合repeatClickInterval使用。true表示已启用忽略重复点击功能，false表示未启用忽略重复点击功能，默认值为false。 |
| [repeatClickInterval](arkts-accessibility-config-con-sys.md#repeatClickInterval) | 表示忽略重复点击功能配置。 |
| [screenMagnification](arkts-accessibility-config-con-sys.md#screenMagnification) | Indicates the configuration of screen magnification. |
| [shortkeyMultiTargets](arkts-accessibility-config-con-sys.md#shortkeyMultiTargets) | 表示辅助扩展快捷键的列表配置。取值为辅助应用的名称，格式为：['bundleName/abilityName']。 |
<!--DelEnd-->

