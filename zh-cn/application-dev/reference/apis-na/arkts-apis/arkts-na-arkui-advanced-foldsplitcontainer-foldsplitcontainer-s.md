# FoldSplitContainer

FoldSplitContainer分栏布局，实现折叠屏二分栏、三分栏在展开态、悬停态以及折叠态的区域控制。

> **说明：**

> - 窗口宽度小于等于600vp时默认使用二分栏，窗口宽度大于600vp时在上下分栏的同时可支持扩展区域，窗口宽度大于600vp且在横屏半折状态下可触发悬停态布局。悬停态布局时会增加折痕区的避让并且扩展区域不可以贯穿折痕区，悬停态可  
> 设置不展示扩展区域，详情请参考[示例](docroot://reference/apis-arkui/arkui-ts/ohos-arkui-advanced-FoldSplitContainer.md#示例)。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct FoldSplitContainer--><!--Device-unnamed-export declare struct FoldSplitContainer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animationOptions

```TypeScript
animationOptions?: AnimateParam | null
```

设置动画效果相关的参数，null表示关闭动效。

**类型：** AnimateParam \| null

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-animationOptions?: AnimateParam | null--><!--Device-FoldSplitContainer-animationOptions?: AnimateParam | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expandedLayoutOptions

```TypeScript
expandedLayoutOptions: ExpandedRegionLayoutOptions
```

展开态布局信息。

**类型：** ExpandedRegionLayoutOptions

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-expandedLayoutOptions: ExpandedRegionLayoutOptions--><!--Device-FoldSplitContainer-expandedLayoutOptions: ExpandedRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extra

```TypeScript
extra?: Callback<void>
```

扩展区域回调函数，不传入的情况，没有对应区域。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-extra?: Callback<void>--><!--Device-FoldSplitContainer-extra?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foldedLayoutOptions

```TypeScript
foldedLayoutOptions: FoldedRegionLayoutOptions
```

折叠态布局信息。

**类型：** FoldedRegionLayoutOptions

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-foldedLayoutOptions: FoldedRegionLayoutOptions--><!--Device-FoldSplitContainer-foldedLayoutOptions: FoldedRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeLayoutOptions

```TypeScript
hoverModeLayoutOptions: HoverModeRegionLayoutOptions
```

悬停态布局信息。

**类型：** HoverModeRegionLayoutOptions

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-hoverModeLayoutOptions: HoverModeRegionLayoutOptions--><!--Device-FoldSplitContainer-hoverModeLayoutOptions: HoverModeRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHoverStatusChange

```TypeScript
onHoverStatusChange?: OnHoverStatusChangeHandler
```

折叠屏进入或退出悬停模式时触发的回调函数。

**类型：** OnHoverStatusChangeHandler

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-onHoverStatusChange?: OnHoverStatusChangeHandler--><!--Device-FoldSplitContainer-onHoverStatusChange?: OnHoverStatusChangeHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary: Callback<void>
```

主要区域回调函数。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-primary: Callback<void>--><!--Device-FoldSplitContainer-primary: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondary

```TypeScript
secondary: Callback<void>
```

次要区域回调函数。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-secondary: Callback<void>--><!--Device-FoldSplitContainer-secondary: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

