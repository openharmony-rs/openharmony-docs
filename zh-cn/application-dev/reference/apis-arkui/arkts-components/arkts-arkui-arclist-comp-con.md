# 常量

## ArcListItem

```TypeScript
export declare const ArcListItem: ArcListItemInterface
```

用于展示弧形列表的子组件，必须配合[ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist)使用。

> **说明：** 
> 
> - 该组件的父组件只能是[ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist)。
> 
> - 当ArcListItem配合[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，其子组件在ArcListItem创建时创建；配合[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)或[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或直接作为[ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist)组件的子组件使用时，其子组件在ArcListItem布局时创建。
> 
> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

### 子组件

可以包含单个子组件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## ArcListItemInstance

```TypeScript
export declare const ArcListItemInstance: ArcListItemAttribute
```

定义ArcListItem组件实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle
