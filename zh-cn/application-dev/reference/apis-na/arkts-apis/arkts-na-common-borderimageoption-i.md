# BorderImageOption

Border image option

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface BorderImageOption--><!--Device-unnamed-export declare interface BorderImageOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill?: boolean
```

Whether to fill the center of the border image. true: Fill the center of the border image. false: Do not fill the center of the border image.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BorderImageOption-fill?: boolean--><!--Device-BorderImageOption-fill?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outset

```TypeScript
outset?: Length | EdgeWidths | LocalizedEdgeWidths
```

Amount by which the border image is extended beyond the border box.

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| [EdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-edgewidths-t.md) \| [LocalizedEdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-localizededgewidths-i.md)

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BorderImageOption-outset?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-outset?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat?: RepeatMode
```

Repeat mode of the source image's slices on the border.

**类型：** [RepeatMode](arkts-na-common-repeatmode-e.md)

**默认值：** RepeatMode.Stretch

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BorderImageOption-repeat?: RepeatMode--><!--Device-BorderImageOption-repeat?: RepeatMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## slice

```TypeScript
slice?: Length | EdgeWidths | LocalizedEdgeWidths
```

Slice width of the upper left corner, upper right corner, lower left corner, and lower right corner of the border image.

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| [EdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-edgewidths-t.md) \| [LocalizedEdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-localizededgewidths-i.md)

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BorderImageOption-slice?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-slice?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## source

```TypeScript
source?: string | Resource | LinearGradientOptions
```

Border image source

**类型：** string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| [LinearGradientOptions](arkts-na-common-lineargradientoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BorderImageOption-source?: string | Resource | LinearGradientOptions--><!--Device-BorderImageOption-source?: string | Resource | LinearGradientOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length | EdgeWidths | LocalizedEdgeWidths
```

Width of the border image.

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| [EdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-edgewidths-t.md) \| [LocalizedEdgeWidths](../../apis-arkui/arkts-apis/arkts-arkui-localizededgewidths-i.md)

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BorderImageOption-width?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-width?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

