# NavigationTitleMode

标题栏显示模式。

**起始版本：** 8

<!--Device-unnamed-declare enum NavigationTitleMode--><!--Device-unnamed-declare enum NavigationTitleMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Free

```TypeScript
Free = 0
```

当内容为满一屏的可滚动组件时，标题随着内容向上滚动而缩小（子标题的大小不变、淡出）。向下滚动内容到顶时则恢复原样。

**说明：**

标题随着内容滚动大小联动的动效在title设置为ResourceStr和NavigationCommonTitle时生效，设置成其余自定义节点类型时字体样式无法变化，下拉时只影响标题栏偏移。

可滚动组件不满一屏时，如果想使用联动效果，就要使用滚动组件提供的[edgeEffect](ListAttribute#edgeEffect)接口将options参数设置为true。未滚动状态，标题栏高度与Full模式一致；滚动时，标题栏的最小高度与Mini模式一致。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleMode-Free = 0--><!--Device-NavigationTitleMode-Free = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Full

```TypeScript
Full
```

固定为大标题模式。

默认值：只有主标题时，标题栏高度为112vp；同时有主标题和副标题时，标题栏高度为138vp。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleMode-Full--><!--Device-NavigationTitleMode-Full-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Mini

```TypeScript
Mini
```

固定为小标题模式。

默认值：API version 12之前，只有主标题时，标题栏高度为56vp；同时有主标题和副标题时，标题栏高度为82vp。从API version 12开始，该模式下标题栏高度为56vp。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationTitleMode-Mini--><!--Device-NavigationTitleMode-Mini-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

