# IconOptions

图标样式对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface IconOptions--><!--Device-unnamed-export interface IconOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

图标颜色。 默认值：Wearable设备是'#A9FFFFFF'，浅灰色；其余设备是'#99182431'，深灰色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IconOptions-color?: ResourceColor--><!--Device-IconOptions-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

图标尺寸，不支持百分比。 默认值根据searchIcon、cancelButton属性中的实际配置生效。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IconOptions-size?: Length--><!--Device-IconOptions-size?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src?: ResourceStr
```

图标/图片源。 默认值：跟随主题。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IconOptions-src?: ResourceStr--><!--Device-IconOptions-src?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

