# TextDataDetectorConfig

该配置只支持Text组件和RichEditor组件。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-declare interface TextDataDetectorConfig--><!--Device-unnamed-declare interface TextDataDetectorConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

设置文本识别成功后的实体颜色。 默认值：'#ff0a59f7'，表示蓝色（不透明度为100%）

**类型：** ResourceColor

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDataDetectorConfig-color?: ResourceColor--><!--Device-TextDataDetectorConfig-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: DecorationStyleInterface
```

设置文本识别成功后的实体装饰线样式。 默认值： { type: TextDecorationType.Underline, color: 与实体颜色一致, style: TextDecorationStyle.SOLID }

**类型：** DecorationStyleInterface

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDataDetectorConfig-decoration?: DecorationStyleInterface--><!--Device-TextDataDetectorConfig-decoration?: DecorationStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enablePreviewMenu

```TypeScript
enablePreviewMenu?: boolean
```

设置是否开启文本识别长按显示预览菜单。true表示开启，false表示未开启。 默认值：false 当copyOptions设置为None时，若enablePreviewMenu设置为true，长按AI实体也不能显示预览菜单。 本接口实际支持的设备类型范围（Phone、Tablet）小于其所属系统能力支持的设备类型范围（Phone、PC/2in1、Tablet、TV、Car、Wearable）。因硬件形态限制，该接口在PC/2in1、TV、Car、 Wearable设备中调用功能不生效。

**类型：** boolean

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextDataDetectorConfig-enablePreviewMenu?: boolean--><!--Device-TextDataDetectorConfig-enablePreviewMenu?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDetectResultUpdate

```TypeScript
onDetectResultUpdate?: Callback<string>
```

文本识别成功后，触发onDetectResultUpdate回调。 默认值：undefined，不触发回调。

**类型：** Callback&lt;string&gt;

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDataDetectorConfig-onDetectResultUpdate?: Callback<string>--><!--Device-TextDataDetectorConfig-onDetectResultUpdate?: Callback<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## types

```TypeScript
types: TextDataDetectorType[]
```

设置文本识别的实体类型。设置types为null或者[]时，识别所有类型的实体，否则只识别指定类型的实体。

**类型：** [TextDataDetectorType](arkts-arkui-textdatadetectortype-e.md)[]

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextDataDetectorConfig-types: TextDataDetectorType[]--><!--Device-TextDataDetectorConfig-types: TextDataDetectorType[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

