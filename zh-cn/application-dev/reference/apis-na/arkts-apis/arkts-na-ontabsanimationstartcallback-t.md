# OnTabsAnimationStartCallback

```TypeScript
export type OnTabsAnimationStartCallback = (index: int, targetIndex: int, extraInfo: TabsAnimationEvent) => void
```

切换动画开始时触发的回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnTabsAnimationStartCallback = (index: int, targetIndex: int, extraInfo: TabsAnimationEvent) => void--><!--Device-unnamed-export type OnTabsAnimationStartCallback = (index: int, targetIndex: int, extraInfo: TabsAnimationEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 当前显示元素的索引，索引从0开始。 取值范围为全体整数 取值限定为整数。 |
| targetIndex | int | 是 | 当前显示元素的索引，索引从0开始。 取值范围为全体整数 取值限定为整数。 |
| extraInfo | [TabsAnimationEvent](arkts-na-tabs-tabsanimationevent-i.md) | 是 | 动画相关信息，包括主轴方向上当前显示元素和目标元素相对Tabs起始位置的位移，以及离手速度。 |

