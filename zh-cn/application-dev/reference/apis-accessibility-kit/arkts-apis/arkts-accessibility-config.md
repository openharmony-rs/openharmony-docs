# @ohos.accessibility.config

本模块提供系统辅助功能的配置，包括辅助扩展的启用与关闭、高对比度文字显示、鼠标键、无障碍字幕配置等。

**起始版本：** 9

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
| [disableAbility](arkts-accessibility-config-disableability-f-sys.md#disableability) | 关闭辅助扩展。使用Promise异步回调。 |
| [disableAbility](arkts-accessibility-config-disableability-f-sys.md#disableability-1) | 关闭辅助扩展，使用callback异步回调。 |
| [enableAbility](arkts-accessibility-config-enableability-f-sys.md#enableability) | 启用辅助扩展。使用Promise异步回调。 |
| [enableAbility](arkts-accessibility-config-enableability-f-sys.md#enableability-1) | 启用辅助扩展，使用callback异步回调。 |
| [enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md#enableabilitywithcallback) | 启用辅助扩展，并指定[ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md)作为辅助扩展应用状态变化的回调函数。使用Promise异步回调。 |
| [getSeniorModeStateForApp](arkts-accessibility-config-getseniormodestateforapp-f-sys.md#getseniormodestateforapp) | Get the senior mode state for app. |
| [off](arkts-accessibility-config-off-f-sys.md#off) | 取消启用的辅助扩展的列表变化监听，使用callback异步回调。 |
| [off](arkts-accessibility-config-off-f-sys.md#off-1) | 取消已安装的辅助扩展的列表变化监听，使用callback异步回调。 |
| [offSeniorModeStateChangeForApp](arkts-accessibility-config-offseniormodestatechangeforapp-f-sys.md#offseniormodestatechangeforapp) | Unregister the observer for application's senior mode state changes. |
| [on](arkts-accessibility-config-on-f-sys.md#on) | 添加启用的辅助扩展的列表变化监听，使用callback异步回调。 |
| [on](arkts-accessibility-config-on-f-sys.md#on-1) | 添加已安装的辅助扩展的列表变化监听，使用callback异步回调。 |
| [onSeniorModeStateChangeForApp](arkts-accessibility-config-onseniormodestatechangeforapp-f-sys.md#onseniormodestatechangeforapp) | Register an observer for anyone application's senior mode state changes. |
| [setMagnificationState](arkts-accessibility-config-setmagnificationstate-f-sys.md#setmagnificationstate) | 触发或者关闭放大手势功能的放大效果，使用前需要保证放大手势功能已开启。 |
| [setSeniorModeStateForApp](arkts-accessibility-config-setseniormodestateforapp-f-sys.md#setseniormodestateforapp) | Set the senior mode state for app. |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppSeniorModeInfo](arkts-accessibility-config-appseniormodeinfo-i-sys.md) | Indicates the senior mode information of an application. |
| [Config](arkts-accessibility-config-config-i-sys.md) | 用于属性的设置、获取与监听。 |
| [ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md) | 通过[enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md#enableabilitywithcallback-1)接口启用辅助扩展应用时提供的回调函数。辅助扩展应用连接断开时，回调函数将被调用。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ClickResponseTime](arkts-accessibility-config-clickresponsetime-t-sys.md) | 用于不同时间长短的点击重复时间。 |
| [DaltonizationColorFilter](arkts-accessibility-config-daltonizationcolorfilter-t-sys.md) | 颜色滤镜功能开启时（[daltonizationState](daltonizationState)设置为true)，颜色滤镜的配置(即设置的DaltonizationColorFilter的值)生效；颜色滤镜功能关闭时（[daltonizationState](daltonizationState)设置为false)，显示为正常类型。 |
| [OnDisconnectCallback](arkts-accessibility-config-ondisconnectcallback-t-sys.md) | 描述AccessibilityExtensionAbility断开连接的回调接口。 |
| [RepeatClickInterval](arkts-accessibility-config-repeatclickinterval-t-sys.md) | 忽略重复点击功能开启时（[ignoreRepeatClick](ignoreRepeatClick)设置为true)，忽略重复点击的配置(即设置的RepeatClickInterval的值)生效；忽略重复点击功能关闭时（[ignoreRepeatClick](ignoreRepeatClick)设置为false)，显示为正常类型。 |
<!--DelEnd-->

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [audioBalance](arkts-accessibility-config-con-sys.md#audiobalance) | 表示左右声道音量平衡的配置。取值范围为-1.0~1.0。默认值为0.0。 |
| [audioMono](arkts-accessibility-config-con-sys.md#audiomono) | 表示单声道音频的配置。true表示已启用单声道音频，false表示未启用单声道音频，默认值为false。 |
| [clickResponseTime](arkts-accessibility-config-con-sys.md#clickresponsetime) | 表示点击持续时间功能配置。 |
| [daltonizationState](arkts-accessibility-config-con-sys.md#daltonizationstate) | 表示颜色滤镜功能启动状态。配合daltonizationColorFilter使用。true表示已启用颜色滤镜功能，false表示未启用颜色滤镜功能，默认值为false。 |
| [ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick) | 表示忽略重复点击功能启用状态。配合repeatClickInterval使用。true表示已启用忽略重复点击功能，false表示未启用忽略重复点击功能，默认值为false。 |
| [repeatClickInterval](arkts-accessibility-config-con-sys.md#repeatclickinterval) | 表示忽略重复点击功能配置。 |
| [screenMagnification](arkts-accessibility-config-con-sys.md#screenmagnification) | Indicates the configuration of screen magnification. |
| [shortkeyMultiTargets](arkts-accessibility-config-con-sys.md#shortkeymultitargets) | 表示辅助扩展快捷键的列表配置。取值为辅助应用的名称，格式为：['bundleName/abilityName']。 |
<!--DelEnd-->

