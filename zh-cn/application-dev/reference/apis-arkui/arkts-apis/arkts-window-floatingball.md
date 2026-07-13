# @ohos.window.floatingBall

该模块提供闪控球的基础功能，包括判断设备是否支持闪控球功能，以及创建闪控球控制器来启动、更新或停止闪控球。适用于跨应用的题目搜索、账单记录、商品比价、抢单、翻译场景，以及金融类应用的实时盯盘场景，以小窗模式呈现内容。闪控球以悬浮小组件
形式显示在其他应用之上，即时呈现应用的关键信息。

> **说明：**
>
> - 针对系统能力SystemCapability.Window.SessionManager，请先使用
> [canIUse()](arkts-arkui-global-caniuse-f.md#caniuse-1)接口判断当前设备是否支持此syscap及对应接口。

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkui-create-f.md#create-1) | 创建闪控球控制器，使用Promise异步回调。 |
| [isFloatingBallEnabled](arkts-arkui-isfloatingballenabled-f.md#isfloatingballenabled-1) | 判断当前设备是否支持闪控球功能。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FloatingBallConfiguration](arkts-arkui-floatingballconfiguration-i.md) | 创建闪控球控制器时需要提供的参数配置。 |
| [FloatingBallController](arkts-arkui-floatingballcontroller-i.md) | 闪控球控制器实例，用于启动、更新、停止闪控球以及注册回调等操作。下列API示例中都需先使用[floatingBall.create()](arkts-arkui-create-f.md#create-1)方法获取到闪控球控制器实例（即floatingBallController），再通过此实例调用对应方法。 |
| [FloatingBallParams](arkts-arkui-floatingballparams-i.md) | 启动和更新闪控球的配置参数。 |
| [FloatingBallWindowInfo](arkts-arkui-floatingballwindowinfo-i.md) | 闪控球窗口信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FloatingBallState](arkts-arkui-floatingballstate-e.md) | 闪控球生命周期状态的枚举。 |
| [FloatingBallTemplate](arkts-arkui-floatingballtemplate-e.md) | 闪控球模板类型的枚举。 |
| [FloatingBallTextUpdateAnimationType](arkts-arkui-floatingballtextupdateanimationtype-e.md) | 闪控球文本更新动画类型的枚举。 |

