# TextDataDetectorConfig

文本识别配置项。该配置只支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_组件和 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TextDataDetectorConfig--><!--Device-unnamed-export declare interface TextDataDetectorConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

设置文本识别成功后的实体颜色。 默认值：'#ff0a59f7'

**类型：** ResourceColor

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextDataDetectorConfig-color?: ResourceColor--><!--Device-TextDataDetectorConfig-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: DecorationStyleInterface
```

设置文本识别成功后的实体装饰线样式。 默认值： { type: TextDecorationType.Underline, color: 与实体颜色一致, style: TextDecorationStyle.SOLID }

**类型：** DecorationStyleInterface

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextDataDetectorConfig-decoration?: DecorationStyleInterface--><!--Device-TextDataDetectorConfig-decoration?: DecorationStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enablePreviewMenu

```TypeScript
enablePreviewMenu?: boolean
```

设置是否开启文本识别长按显示预览菜单。true表示开启，false表示未开启。 默认值：false 当\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_设置为None时，若 enablePreviewMenu设置为true，长按AI实体也不能显示预览菜单。

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextDataDetectorConfig-enablePreviewMenu?: boolean--><!--Device-TextDataDetectorConfig-enablePreviewMenu?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDetectResultUpdate

```TypeScript
onDetectResultUpdate?: Callback<string>
```

文本识别成功后，触发onDetectResultUpdate回调。

**类型：** Callback&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextDataDetectorConfig-onDetectResultUpdate?: Callback<string>--><!--Device-TextDataDetectorConfig-onDetectResultUpdate?: Callback<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## types

```TypeScript
types: TextDataDetectorType[] | undefined | null
```

设置文本识别的实体类型。设置types为null或者undefined或者[]时，识别所有类型的实体，否则只识别指定类型的实体。

**类型：** TextDataDetectorType[] \| undefined \| null

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextDataDetectorConfig-types: TextDataDetectorType[] | undefined | null--><!--Device-TextDataDetectorConfig-types: TextDataDetectorType[] | undefined | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

