# TabsCustomContentTransitionCallback

```TypeScript
declare type TabsCustomContentTransitionCallback = (from: number, to: number) => TabContentAnimatedTransition | undefined
```

自定义Tabs页面切换动画开始时触发的回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type TabsCustomContentTransitionCallback = (from: number, to: number) => TabContentAnimatedTransition | undefined--><!--Device-unnamed-declare type TabsCustomContentTransitionCallback = (from: number, to: number) => TabContentAnimatedTransition | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | number | 是 | 动画开始时，当前页面的index值，索引从0开始。<br/>取值范围：[0, 索引值-1]，当设置的值超过索引值或小于0时无转场动画。  |
| to | number | 是 | 动画开始时，目标页面的index值，索引从0开始。<br/>取值范围：[0, 索引值-1]，当设置的值超过索引值或小于0时无转场动画。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TabContentAnimatedTransition](arkts-arkui-tabcontentanimatedtransition-i.md) \| undefined | Information about the custom tab switching animation.  |

