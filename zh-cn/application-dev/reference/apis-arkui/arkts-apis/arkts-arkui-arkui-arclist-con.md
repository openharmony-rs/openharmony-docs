# 常量

## ArcList

```TypeScript
export declare const ArcList: ArcListInterface
```

弧形列表由沿弧形排列的一系列列表项组成，适用于圆形屏幕设备。适合连续、多行呈现同类数据，例如图片和文本。 > **说明：** > > - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

### 子组件 仅支持ArcListItem子组件。 > **说明：** > > ArcList的子组件索引值计算规则： > > - 按子组件的顺序依次递增。 > > - [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)语句中，只有条件成立的分支内的子组件会参与索引值计算，条件不成立的分支内子组 > 件不计算索引值。 > > - [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)/ > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)语句中，会计算展开所有子组件索引值。 > > - [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)发生变化以后，会更新子组件索引值。 > > - ArcList子组件visibility属性设置为Hidden或None依然会计算索引值。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const ArcList: ArcListInterface--><!--Device-unnamed-export declare const ArcList: ArcListInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## ArcListInstance

```TypeScript
export declare const ArcListInstance: ArcListAttribute
```

定义ArcList组件实例。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const ArcListInstance: ArcListAttribute--><!--Device-unnamed-export declare const ArcListInstance: ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## ArcListItem

```TypeScript
export declare const ArcListItem: ArcListItemInterface
```

用于展示弧形列表的子组件，必须配合ArcList使用。 > **说明：** > > - 该组件的父组件只能是ArcList。 > > - 当ArcListItem配合[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，其子组件在 > ArcListItem创建时创建；配合[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)或 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或直接作为 > ArcList组件的子组件使用时，其子组件在ArcListItem布局时创建。 > > - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

### 子组件 可以包含单个子组件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const ArcListItem: ArcListItemInterface--><!--Device-unnamed-export declare const ArcListItem: ArcListItemInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## ArcListItemInstance

```TypeScript
export declare const ArcListItemInstance: ArcListItemAttribute
```

定义ArcListItem组件实例。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const ArcListItemInstance: ArcListItemAttribute--><!--Device-unnamed-export declare const ArcListItemInstance: ArcListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

