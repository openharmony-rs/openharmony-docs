# PageTransitionEnter

Defines PageTransitionEnter Component.

## PageTransitionEnter

```TypeScript
PageTransitionEnter(value: PageTransitionOptions)
```

设置当前页面的自定义入场动效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PageTransitionEnterInterface-(value: PageTransitionOptions): PageTransitionEnterInterface--><!--Device-PageTransitionEnterInterface-(value: PageTransitionOptions): PageTransitionEnterInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PageTransitionOptions](arkts-arkui-pagetransitionoptions-i.md) | 是 | 配置入场动效的参数。 |

## PageTransitionEnter

```TypeScript
PageTransitionEnter(event: PageTransitionCallback)
```

逐帧回调，直到入场动画结束，progress从0变化到1。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PageTransitionEnterInterface-onEnter(event: PageTransitionCallback): PageTransitionEnterInterface--><!--Device-PageTransitionEnterInterface-onEnter(event: PageTransitionCallback): PageTransitionEnterInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [PageTransitionCallback](arkts-arkui-pagetransitioncallback-t.md) | 是 | 入场动画的逐帧回调直到入场动画结束，progress从0变化到1。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PageTransitionOptions](arkts-arkui-pagetransitionoptions-i.md) | 退场/进场动效的参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [PageTransitionCallback](arkts-arkui-pagetransitioncallback-t.md) | 页面转场事件回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RouteType](arkts-arkui-routetype-e.md) | 页面转场类型。 |
| [SlideEffect](arkts-arkui-slideeffect-e.md) | 页面转场时的滑入滑出效果。 |

