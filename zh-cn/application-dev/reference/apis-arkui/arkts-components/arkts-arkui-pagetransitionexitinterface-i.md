# PageTransitionExitInterface

当前页面的自定义退场动效。

@extends CommonTransition&lt;PageTransitionExitInterface&gt; @interface PageTransitionExitInterface

**继承/实现关系：** PageTransitionExitInterface extends CommonTransition<PageTransitionExitInterface>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(value: PageTransitionOptions): PageTransitionExitInterface
```

设置当前页面的自定义退场动效，需在pageTransition()函数中配置，继承自[CommonTransition](arkts-arkui-commontransition-c.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PageTransitionOptions](arkts-arkui-pagetransitionoptions-i.md) | 是 | 配置退场动效的参数，包含页面转场效果的路由类型(type)、动画时长(duration)、动画曲线(curve)、动画延迟时长(delay)配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PageTransitionExitInterface](arkts-arkui-pagetransitionexitinterface-i.md) |  |

## onExit

```TypeScript
onExit(event: PageTransitionCallback): PageTransitionExitInterface
```

逐帧回调，直到退场动画结束，progress从0变化到1。与slide、translate、scale、opacity等预设动效方法配合使用时，onExit在预设动效基础上提供逐帧自定义逻辑；也可单独使用onExit实现完全自定义的退场动画效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [PageTransitionCallback](arkts-arkui-pagetransitioncallback-t.md) | 是 | 退场动画的逐帧回调，直到动画结束，progress从0变化到1。该回调仅在配置的type与实际路由类型匹配时触发。<br>**适用版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PageTransitionExitInterface](arkts-arkui-pagetransitionexitinterface-i.md) |  |
