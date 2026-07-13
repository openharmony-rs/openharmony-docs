# OnTabsAnimationStartCallback

```TypeScript
declare type OnTabsAnimationStartCallback = (index: number, targetIndex: number, extraInfo: TabsAnimationEvent) => void
```

切换动画开始时触发的回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 当前显示元素的索引，索引从0开始。 |
| targetIndex | number | 是 | 当前显示元素的索引，索引从0开始。 |
| extraInfo | TabsAnimationEvent | 是 | 动画相关信息，包括主轴方向上当前显示元素和目标元素相对Tabs起始位置的位移，以及离手速度。 |

