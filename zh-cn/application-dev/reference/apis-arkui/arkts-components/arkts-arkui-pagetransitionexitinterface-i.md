# PageTransitionExitInterface

当前页面的自定义退场动效。继承自[CommonTransition](arkts-arkui-commontransition-c.md)。

**继承/实现关系：** PageTransitionExitInterface extends [CommonTransition<PageTransitionExitInterface>](CommonTransition<PageTransitionExitInterface>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
(value: PageTransitionOptions): PageTransitionExitInterface
```

设置当前页面的自定义退场动效。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PageTransitionOptions | 是 | 配置退场动效的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PageTransitionExitInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onExit

```TypeScript
onExit(event: PageTransitionCallback): PageTransitionExitInterface
```

逐帧回调，直到出场动画结束，progress从0变化到1。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | PageTransitionCallback | 是 | 出场动画的逐帧回调直到出场动画结束，progress从0变化到1。<br>**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PageTransitionExitInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

