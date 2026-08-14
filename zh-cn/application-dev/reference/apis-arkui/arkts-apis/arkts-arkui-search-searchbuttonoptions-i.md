# SearchButtonOptions

搜索按钮样式对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface SearchButtonOptions--><!--Device-unnamed-export interface SearchButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoDisable

```TypeScript
autoDisable?: boolean
```

Search无文本内容时按钮置灰且不可点击。 默认值：false true表示开启按钮置灰功能，false表示不开启。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchButtonOptions-autoDisable?: boolean--><!--Device-SearchButtonOptions-autoDisable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

文本按钮字体颜色。 默认值：Wearable设备是'#007dff'，TV设备是'#5291ff'，其他设备是'#5ea1ff'，均是蓝色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchButtonOptions-fontColor?: ResourceColor--><!--Device-SearchButtonOptions-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Length
```

文本按钮字体大小，不支持百分比。 默认值：Wearable设备15fp，其他设备14fp。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchButtonOptions-fontSize?: Length--><!--Device-SearchButtonOptions-fontSize?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

