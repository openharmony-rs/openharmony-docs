# FoldSplitContainer

```TypeScript
export declare struct FoldSplitContainer
```

实现折叠屏二分栏（主要区域+次要区域）、三分栏（主要区域+次要区域+扩展区域）在展开态、悬停态以及折叠态的区域控制。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct FoldSplitContainer--><!--Device-unnamed-export declare struct FoldSplitContainer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## onHoverStatusChange

```TypeScript
onHoverStatusChange?: OnHoverStatusChangeHandler
```

折叠屏进入或退出悬停模式时触发的回调函数。不传入时，不回调悬停状态变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-FoldSplitContainer-onHoverStatusChange?: OnHoverStatusChangeHandler--><!--Device-FoldSplitContainer-onHoverStatusChange?: OnHoverStatusChangeHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animationOptions

```TypeScript
animationOptions?: AnimateParam | null
```

设置动画效果相关的参数，null表示关闭动效。

默认值：null

**类型：** [AnimateParam](../arkts-components/arkts-arkui-common-comp-animateparam-i.md) &#124; null

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-FoldSplitContainer-animationOptions?: AnimateParam | null--><!--Device-FoldSplitContainer-animationOptions?: AnimateParam | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expandedLayoutOptions

```TypeScript
expandedLayoutOptions: ExpandedRegionLayoutOptions
```

展开态布局信息，用于控制折叠屏展开状态下扩展区域是否贯穿、区域比例和位置等。窗口宽度大于600vp时可支持扩展区域。

**类型：** [ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md)

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-FoldSplitContainer-expandedLayoutOptions: ExpandedRegionLayoutOptions--><!--Device-FoldSplitContainer-expandedLayoutOptions: ExpandedRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extra

```TypeScript
extra?: Callback<void>
```

扩展区域回调函数，用于构建扩展区域的UI内容。当需要实现三分栏布局或需要显示额外内容区域时传入此参数，不需要扩展区域时可省略此参数。回调函数无参数无返回值，不传入时没有对应区域。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**起始版本：** 12

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-FoldSplitContainer-extra?: Callback<void>--><!--Device-FoldSplitContainer-extra?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foldedLayoutOptions

```TypeScript
foldedLayoutOptions: FoldedRegionLayoutOptions
```

折叠态布局信息，用于控制折叠屏折叠状态下的主要区域与次要区域的高度比例等。当设备处于折叠状态时生效，窗口宽度小于等于600vp时默认使用二分栏。

**类型：** [FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md)

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-FoldSplitContainer-foldedLayoutOptions: FoldedRegionLayoutOptions--><!--Device-FoldSplitContainer-foldedLayoutOptions: FoldedRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeLayoutOptions

```TypeScript
hoverModeLayoutOptions: HoverModeRegionLayoutOptions
```

悬停态布局信息，用于控制折叠屏半折悬停状态下是否显示扩展区域、区域比例和位置等。窗口宽度大于600vp且在横屏半折状态下可触发悬停态布局。

**类型：** [HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md)

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-FoldSplitContainer-hoverModeLayoutOptions: HoverModeRegionLayoutOptions--><!--Device-FoldSplitContainer-hoverModeLayoutOptions: HoverModeRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary: Callback<void>
```

主要区域回调函数，用于构建主要区域的UI内容。回调函数无参数无返回值，在组件布局时被调用。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**起始版本：** 12

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-FoldSplitContainer-primary: Callback<void>--><!--Device-FoldSplitContainer-primary: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondary

```TypeScript
secondary: Callback<void>
```

次要区域回调函数，用于构建次要区域的UI内容。回调函数无参数无返回值，在组件布局时被调用。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**起始版本：** 12

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-FoldSplitContainer-secondary: Callback<void>--><!--Device-FoldSplitContainer-secondary: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
