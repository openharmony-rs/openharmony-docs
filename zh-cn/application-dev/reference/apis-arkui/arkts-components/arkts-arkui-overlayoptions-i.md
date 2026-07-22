# OverlayOptions

浮层的定位。
> **说明：**  
>  
> 为规范匿名对象的定义，API 12版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。  
>  
> align和offset都设置时，效果重叠，浮层相对于组件方位定位后，再基于当前位置的左上角进行偏移。

**起始版本：** 12

<!--Device-unnamed-declare interface OverlayOptions--><!--Device-unnamed-declare interface OverlayOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## align

```TypeScript
align?: Alignment
```

设置浮层相对于组件的方位。

默认值：TopStart

**类型：** Alignment

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-OverlayOptions-align?: Alignment--><!--Device-OverlayOptions-align?: Alignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: OverlayOffset
```

设置浮层基于自身左上角的偏移量。浮层默认处于组件左上角。

**类型：** OverlayOffset

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-OverlayOptions-offset?: OverlayOffset--><!--Device-OverlayOptions-offset?: OverlayOffset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

