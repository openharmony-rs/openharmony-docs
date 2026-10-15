# GeometryInfo

```TypeScript
declare interface GeometryInfo extends SizeResult
```

父组件（自定义组件）布局信息。在onMeasureSize和onPlaceChildren方法中，可通过selfLayoutInfo参数获取GeometryInfo对象，其中包含父组件的边框宽度、外边距和内边距信息，开发者在计算子组件布局时需要考虑这些信息。

**继承/实现关系：** GeometryInfo extends [SizeResult](arkts-arkui-common-comp-sizeresult-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface GeometryInfo extends SizeResult--><!--Device-unnamed-declare interface GeometryInfo extends SizeResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth: EdgeWidth
```

父组件（自定义组件）边框宽度。单位为： vp。

**类型：** [EdgeWidth](../arkts-apis/arkts-arkui-edgewidth-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-GeometryInfo-borderWidth: EdgeWidth--><!--Device-GeometryInfo-borderWidth: EdgeWidth-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin: Margin
```

父组件（自定义组件）margin信息。单位为： vp。

**类型：** [Margin](../arkts-apis/arkts-arkui-margin-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-GeometryInfo-margin: Margin--><!--Device-GeometryInfo-margin: Margin-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding: Padding
```

父组件（自定义组件）padding信息。单位为： vp。

**类型：** Padding

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-GeometryInfo-padding: Padding--><!--Device-GeometryInfo-padding: Padding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
