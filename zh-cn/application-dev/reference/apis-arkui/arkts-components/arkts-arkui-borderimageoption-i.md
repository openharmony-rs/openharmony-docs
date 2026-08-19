# BorderImageOption

Border image option

**起始版本：** 11

<!--Device-unnamed-declare interface BorderImageOption--><!--Device-unnamed-declare interface BorderImageOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## fill

```TypeScript
fill?: boolean
```

设置边框图片是否中心填充。true表示中心填充，false表示非中心填充。 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-fill?: boolean--><!--Device-BorderImageOption-fill?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outset

```TypeScript
outset?: Length | EdgeWidths | LocalizedEdgeWidths
```

设置边框图片向外延伸距离。 默认值：0 **说明：** 设置负数时取默认值。 参数类型为Length时，统一设置四条边框的向外延伸距离。 参数类型为EdgeWidths时： - Top：设置边框图片上边框向外延伸的距离。 - Bottom：设置边框图片下边框向外延伸的距离。 - Left：设置边框图片左边框向外延伸的距离。 - Right：设置边框图片右边框向外延伸的距离。 参数类型为LocalizedEdgeWidths&lt;sup&gt;12+&lt;/sup&gt;时： - Top：设置边框图片上边框向外延伸的距离。 - Bottom：设置边框图片下边框向外延伸的距离。 - Start：设置边框图片左边框向外延伸的距离。 从右至左显示语言模式下为设置边框图片右边框向外延伸的距离。 - End：设置边框图片右边框向外延伸的距离。 从右至左显示语言模式下为设置边框图片左边框向外延伸的距离。

**类型：** Length \| EdgeWidths \| LocalizedEdgeWidths

**默认值：** 0

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-outset?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-outset?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat?: RepeatMode
```

设置被切割的图片在边框上的重复方式。 默认值：RepeatMode.Stretch

**类型：** [RepeatMode](arkts-arkui-repeatmode-e.md)

**默认值：** RepeatMode.Stretch

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-repeat?: RepeatMode--><!--Device-BorderImageOption-repeat?: RepeatMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## slice

```TypeScript
slice?: Length | EdgeWidths | LocalizedEdgeWidths
```

设置边框图片左上角、右上角、左下角以及右下角的切割宽高。 默认值：0 **说明：** 设置负数时取默认值。 参数类型为Length时，统一设置四个角的宽高。 参数类型为EdgeWidths时： - Top：设置图片上侧被切割的高。 - Bottom：设置图片下侧被切割的高。 - Left：设置图片左侧被切割的宽。 - Right：设置图片右侧被切割的宽。 参数类型为LocalizedEdgeWidths&lt;sup&gt;12+&lt;/sup&gt;时： - Top：设置图片上侧被切割的高。 - Bottom：设置图片下侧被切割的高。 - Start：设置图片左侧被切割的宽。 从右至左显示语言模式下为设置图片右侧被切割的宽。 - End：设置图片右侧被切割的宽。 从右至左显示语言模式下为设置图片左侧被切割的宽。

**类型：** Length \| EdgeWidths \| LocalizedEdgeWidths

**默认值：** 0

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-slice?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-slice?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## source

```TypeScript
source?: string | Resource | LinearGradient
```

边框图源或者渐变色设置。参数类型为string类型时，用于设置边框图源，引用方式请参考[加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。 默认值：undefined（不设置边框图源） **说明：** 边框图源仅适用于容器组件，如Row、Column、Flex，在非容器组件上使用会失效。

**类型：** string \| Resource \| [LinearGradient](arkts-arkui-lineargradient-i.md)

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-source?: string | Resource | LinearGradient--><!--Device-BorderImageOption-source?: string | Resource | LinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length | EdgeWidths | LocalizedEdgeWidths
```

设置图片边框宽度。 默认值：0 **说明：** 设置负数时取默认值。 参数类型为Length时，统一设置四条边框的宽度。 参数类型为EdgeWidths时： - Top：设置图片边框上边框的宽。 - Bottom：设置图片边框下边框的宽。 - Left：设置图片边框左边框的宽。 - Right：设置图片边框右边框的宽。 参数类型为LocalizedEdgeWidths&lt;sup&gt;12+&lt;/sup&gt;时： - Top：设置图片边框上边框的宽。 - Bottom：设置图片边框下边框的宽。 - Start：设置图片边框左边框的宽。 从右至左显示语言模式下为设置图片边框右边框宽。 - End：设置图片边框右边框宽。 从右至左显示语言模式下为设置图片边框左边框的宽。

**类型：** Length \| EdgeWidths \| LocalizedEdgeWidths

**默认值：** 0

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-width?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-width?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

