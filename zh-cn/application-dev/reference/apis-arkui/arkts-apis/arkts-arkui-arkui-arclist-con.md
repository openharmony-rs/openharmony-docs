# 常量

## ArcList

```TypeScript
export declare const ArcList: ArcListInterface
```

弧形列表包含一系列列表项。适合连续、多行呈现同类数据，例如图片和文本。

> **说明：**

> - 该组件从API version 18开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。  
>  
> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

### 子组件

仅支持[ArcListItem](arkts-arkui-arclist.md)子组件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const ArcList: ArcListInterface--><!--Device-unnamed-export declare const ArcList: ArcListInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## ArcListInstance

```TypeScript
export declare const ArcListInstance: ArcListAttribute
```

定义ArcList组件实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const ArcListInstance: ArcListAttribute--><!--Device-unnamed-export declare const ArcListInstance: ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## ArcListItem

```TypeScript
export declare const ArcListItem: ArcListItemInterface
```

用来展示列表具体子组件，必须配合[ArcList](arkts-arkui-arclist.md)来使用。

> **说明：**

> - 该组件的父组件只能是[ArcList](arkts-arkui-arclist.md)。  
>  
> - 当ArcListItem配合[LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，ArcListItem  
> 子组件在ArcListItem创建时创建。配合[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、  
> [ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为  
> [ArcList](arkts-arkui-arclist.md)时，ArcListItem子组件在ArcListItem布局时创建。  
>  
> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

### 子组件

可以包含单个子组件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const ArcListItem: ArcListItemInterface--><!--Device-unnamed-export declare const ArcListItem: ArcListItemInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## ArcListItemInstance

```TypeScript
export declare const ArcListItemInstance: ArcListItemAttribute
```

定义ArcListItem组件实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const ArcListItemInstance: ArcListItemAttribute--><!--Device-unnamed-export declare const ArcListItemInstance: ArcListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

