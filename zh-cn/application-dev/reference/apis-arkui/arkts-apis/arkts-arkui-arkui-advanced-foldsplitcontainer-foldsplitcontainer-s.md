# FoldSplitContainer

FoldSplitContainer分栏布局，实现折叠屏二分栏、三分栏在展开态（设备完全展开状态）、悬停态（设备半折叠状态）以及折叠态（设备完全折叠状态）的区域控制。适用于折叠屏应用的响应式布局适配场景，可帮助开发者实现多屏状态下的智 能分栏布局，提升用户体验。折叠状态详情可参考[display.FoldStatus](arkts-arkui-display-foldstatus-e.md#FoldStatus)。 > **说明：** > > - 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 窗口宽度小于等于600vp时默认使用二分栏，窗口宽度大于600vp时在上下分栏的同时可支持扩展区域，窗口宽度大于600vp且在横屏半折状态下可触发悬停态布局。悬停态布局时会增加折痕区的避让并且扩展区域不可以贯穿折痕区，悬停态可 > 设置不展示扩展区域，详情请参考[示例](../../../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-FoldSplitContainer.md#示例)。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export declare struct FoldSplitContainer--><!--Device-unnamed-export declare struct FoldSplitContainer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animationOptions

```TypeScript
@Prop
  animationOptions?: AnimateParam | null
```

设置动画效果相关的参数，null表示关闭动效。 默认值：null

**类型：** [AnimateParam](../../apis-na/arkts-apis/arkts-na-common-animateparam-i.md) \| null

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-@Prop  animationOptions?: AnimateParam | null--><!--Device-FoldSplitContainer-@Prop  animationOptions?: AnimateParam | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expandedLayoutOptions

```TypeScript
@Prop
  expandedLayoutOptions: ExpandedRegionLayoutOptions
```

展开态布局信息，用于控制折叠屏展开状态下扩展区域是否贯穿、区域比例和位置等。窗口宽度大于600vp时可支持扩展区域。

**类型：** [ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-@Prop  expandedLayoutOptions: ExpandedRegionLayoutOptions--><!--Device-FoldSplitContainer-@Prop  expandedLayoutOptions: ExpandedRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extra

```TypeScript
@BuilderParam
  extra?: Callback<void>
```

扩展区域回调函数，用于构建扩展区域的UI内容。当需要实现三分栏布局或需要显示额外内容区域时传入此参数，不需要扩展区域时可省略此参数。回调函数无参数无返回值，不传入时没有对应区域。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-@BuilderParam  extra?: Callback<void>--><!--Device-FoldSplitContainer-@BuilderParam  extra?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foldedLayoutOptions

```TypeScript
@Prop
  foldedLayoutOptions: FoldedRegionLayoutOptions
```

折叠态布局信息，用于控制折叠屏折叠状态下的主要区域与次要区域的高度比例等。当设备处于折叠状态时生效，窗口宽度小于等于600vp时默认使用二分栏。

**类型：** [FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-@Prop  foldedLayoutOptions: FoldedRegionLayoutOptions--><!--Device-FoldSplitContainer-@Prop  foldedLayoutOptions: FoldedRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hoverModeLayoutOptions

```TypeScript
@Prop
  hoverModeLayoutOptions: HoverModeRegionLayoutOptions
```

悬停态布局信息，用于控制折叠屏半折悬停状态下是否显示扩展区域、区域比例和位置等。窗口宽度大于600vp且在横屏半折状态下可触发悬停态布局。

**类型：** [HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-@Prop  hoverModeLayoutOptions: HoverModeRegionLayoutOptions--><!--Device-FoldSplitContainer-@Prop  hoverModeLayoutOptions: HoverModeRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHoverStatusChange

```TypeScript
onHoverStatusChange?: OnHoverStatusChangeHandler
```

折叠屏进入或退出悬停模式时触发的回调函数。不传入时，不回调悬停状态变化。

**类型：** [OnHoverStatusChangeHandler](arkts-arkui-onhoverstatuschangehandler-t.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-onHoverStatusChange?: OnHoverStatusChangeHandler--><!--Device-FoldSplitContainer-onHoverStatusChange?: OnHoverStatusChangeHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
@BuilderParam
  primary: Callback<void>
```

主要区域回调函数，用于构建主要区域的UI内容。回调函数无参数无返回值，在组件布局时被调用。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-@BuilderParam  primary: Callback<void>--><!--Device-FoldSplitContainer-@BuilderParam  primary: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondary

```TypeScript
@BuilderParam
  secondary: Callback<void>
```

次要区域回调函数，用于构建次要区域的UI内容。回调函数无参数无返回值，在组件布局时被调用。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldSplitContainer-@BuilderParam  secondary: Callback<void>--><!--Device-FoldSplitContainer-@BuilderParam  secondary: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

