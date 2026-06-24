# @ohos.window.floatView

标准悬浮窗是悬浮在桌面/应用界面上的小型窗口，提供灵活的窗口管理能力。

本模块提供标准悬浮窗能力，包括判断设备是否支持标准悬浮窗功能、创建标准悬浮窗控制器以启动、更新或停止标准悬浮窗等。

**适用场景：**

标准悬浮窗适用于需要在独立小窗口中持续展示应用内容或提供快捷操作的场景。例如：

- 股市盯盘应用：用户在浏览其他应用时，通过标准悬浮窗实时查看股票行情变化，无需频繁切换应用。
- 手机直播应用：主播在直播过程中使用标准悬浮窗展示自定义的互动面板或控制界面，方便实时操作和互动。

**与闪控球联动：**

本模块可与[@ohos.window.floatingBall](arkts-window-floatingball.md#floatingBall)（闪控球）联合使用。通过
[floatView.bind](arkts-arkui-floatview-bind-f.md#bind-1)接口将标准悬浮窗控制器与闪控球控制器绑定后，用户点击闪控球可展开为标准悬浮窗，点击标准悬浮窗左上角的缩小按钮可收起为闪控球，实现两种窗口形态的相互切换。

**全局悬浮窗和标准悬浮窗对比**

- 共同点：全局悬浮窗和标准悬浮窗均为一种特殊的应用辅助窗口，具备在应用主窗口和对应Ability退至后台后仍然可以在前台显示的能力。可以用于应用退至后台后，使用其继续显示UI。
- 区别：
- 全局悬浮窗由开发者管理并实现UI绘制，无统一UI及动效。
- 标准悬浮窗由系统管理并统一绘制UI，动效更为高端精致。
- 标准悬浮窗支持与[闪控球](arkts-window-floatingball.md#floatingBall)互相绑定联合使用，实现更复杂场景。

**起始版本：** 26.0.0

> **说明：**
>
> - 针对系统能力SystemCapability.Window.SessionManager，请先使用
> [canIUse()](../../../../reference/common/js-apis-syscap.md#caniuse)接口判断当前设备是否支持此syscap及对应接口。
>
> - 本模块接口仅可在Stage模型下使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bind](arkts-arkui-floatview-bind-f.md#bind-1) | 绑定标准悬浮窗和闪控球。需要先创建[标准悬浮窗控制器](arkts-arkui-floatview-floatviewcontroller-i.md#FloatViewController)和<br/>[闪控球控制器](arkts-arkui-floatingball-floatingballcontroller-i.md#FloatingBallController)，且均未启动。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 绑定成功后，调用[start()](arkts-arkui-floatview-floatviewcontroller-i.md#start-1)或<br/>&gt; [startFloatingBall()](arkts-arkui-floatingball-floatingballcontroller-i.md#startFloatingBall-1)均会同时创<br/>&gt; 建标准悬浮窗窗口和闪控球窗口，并触发对应窗口已注册的状态回调。但同一时刻仅展示其中一个窗口，展示顺序取决于先调用哪个控制器的启动接口。<br/>&gt;<br/>&gt; - 绑定成功后，用户可通过点击操作在标准悬浮窗窗口与闪控球之间进行切换。<br/>&gt;<br/>&gt; - 绑定成功后，调用任一控制器的停止接口（[stop()](arkts-arkui-floatview-floatviewcontroller-i.md#stop-1)或<br/>&gt; [stopFloatingBall()](arkts-arkui-floatingball-floatingballcontroller-i.md#stopFloatingBall-1)）会同时销毁标<br/>&gt; 准悬浮窗窗口和闪控球窗口，并触发对应窗口已注册的状态回调。<br/> |
| [create](arkts-arkui-floatview-create-f.md#create-1) | 创建标准悬浮窗控制器。使用Promise异步回调。<br/> |
| [getFloatViewLimits](arkts-arkui-floatview-getfloatviewlimits-f.md#getFloatViewLimits-1) | 根据传入的模板类型获取对应标准悬浮窗窗口的限制，单位为px。<br/> |
| [isFloatViewEnabled](arkts-arkui-floatview-isfloatviewenabled-f.md#isFloatViewEnabled-1) | 判断当前设备是否支持标准悬浮窗功能。<br/> |
| [unbind](arkts-arkui-floatview-unbind-f.md#unbind-1) | 解绑标准悬浮窗和闪控球。需要在[标准悬浮窗控制器](arkts-arkui-floatview-floatviewcontroller-i.md#FloatViewController)和<br/>[闪控球控制器](arkts-arkui-floatingball-floatingballcontroller-i.md#FloatingBallController)均停止后才可解绑。使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FloatViewConfiguration](arkts-arkui-floatview-floatviewconfiguration-i.md) | 创建标准悬浮窗控制器时需要提供的参数配置。<br/> |
| [FloatViewController](arkts-arkui-floatview-floatviewcontroller-i.md) | 标准悬浮窗控制器实例。用于启动、停止标准悬浮窗以及注册回调等操作。<br/><br/>下列API示例中都需先使用[floatView.create()](arkts-arkui-floatview-create-f.md#create-1)方法获取到标准悬浮窗控制器实例（即floatViewController），再通过此实例调用对应方法。<br/> |
| [FloatViewLimits](arkts-arkui-floatview-floatviewlimits-i.md) | 标准悬浮窗窗口的限制。<br/> |
| [FloatViewProperties](arkts-arkui-floatview-floatviewproperties-i.md) | 标准悬浮窗窗口的属性。<br/> |
| [FloatViewRectChangeInfo](arkts-arkui-floatview-floatviewrectchangeinfo-i.md) | 标准悬浮窗矩形区域变化信息。<br/> |
| [FloatViewStateChangeInfo](arkts-arkui-floatview-floatviewstatechangeinfo-i.md) | 标准悬浮窗状态变化信息。<br/> |
| [RatioLimit](arkts-arkui-floatview-ratiolimit-i.md) | 标准悬浮窗的宽高比限制范围。宽高比比值由窗口矩形区域的宽除以高获得。<br/> |
| [TemplateProperty](arkts-arkui-floatview-templateproperty-i.md) | 切换悬浮窗模板并修改窗口尺寸时需要提供的参数配置。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FloatViewState](arkts-arkui-floatview-floatviewstate-e.md) | 标准悬浮窗状态的枚举。<br/> |
| [FloatViewTemplateType](arkts-arkui-floatview-floatviewtemplatetype-e.md) | 标准悬浮窗模板类型的枚举。<br/> |

