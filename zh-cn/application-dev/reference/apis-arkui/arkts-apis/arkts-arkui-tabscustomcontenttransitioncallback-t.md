# TabsCustomContentTransitionCallback

```TypeScript
export type TabsCustomContentTransitionCallback = (from: int, to: int) => (TabContentAnimatedTransition | undefined)
```

自定义Tabs页面切换动画开始时触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type TabsCustomContentTransitionCallback = (from: int, to: int) => (TabContentAnimatedTransition | undefined)--><!--Device-unnamed-export type TabsCustomContentTransitionCallback = (from: int, to: int) => (TabContentAnimatedTransition | undefined)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | int | 是 | 动画开始时，当前页面的index值，索引从0开始。\_\_\_HTML\_TAG\_USD\_0\_\_\_ 取值范围为全体整数 取值限定为整数。取值约束:取值范围：[0, index-1] 当设置的值超过索引值或小于0时无转场动画。  |
| to | int | 是 | 动画开始时，目标页面的index值，索引从0开始。\_\_\_HTML\_TAG\_USD\_0\_\_\_ 取值范围为全体整数 取值限定为整数。取值约束:取值范围：[0,索引值] 当设置的值超过索引值或小于0时无转场动画。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| (TabContentAnimatedTransition \| undefined) | Returns animated transition options of tab or undefined. |

