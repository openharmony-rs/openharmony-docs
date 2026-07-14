# TextDataDetectorConfig

该配置只支持[Text](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-text.md)组件和[RichEditor](arkts-arkui-richeditor.md)组件。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

设置文本识别成功后的实体颜色。

默认值：'#ff0a59f7'

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: DecorationStyleInterface
```

设置文本识别成功后的实体装饰线样式。

默认值：

{

 type: TextDecorationType.Underline,

 color: 与实体颜色一致,

 style: TextDecorationStyle.SOLID 

}

**类型：** DecorationStyleInterface

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enablePreviewMenu

```TypeScript
enablePreviewMenu?: boolean
```

设置是否开启文本识别长按显示预览菜单。true表示开启，false表示未开启。

默认值：false

当[copyOptions](RichEditorAttribute#copyOptions)设置为None时，若enablePreviewMenu设置为true，长按AI实体也不能显示预览菜单。

该参数在Phone、Tablet中可正常调用，在PC/2in1、TV和Wearable等其他设备类型中无效果。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDetectResultUpdate

```TypeScript
onDetectResultUpdate?: Callback<string>
```

文本识别成功后，触发onDetectResultUpdate回调。

**类型：** Callback<string>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## types

```TypeScript
types: TextDataDetectorType[]
```

设置文本识别的实体类型。设置types为null或者[]时，识别所有类型的实体，否则只识别指定类型的实体。

**类型：** TextDataDetectorType[]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

