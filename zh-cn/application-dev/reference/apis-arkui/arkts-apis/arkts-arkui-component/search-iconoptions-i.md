# IconOptions

图标样式对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface IconOptions--><!--Device-unnamed-export interface IconOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

图标颜色。 默认值：Wearable设备是'#A9FFFFFF'，浅灰色；其余设备是'#99182431'，深灰色。

**类型：** ResourceColor

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IconOptions-color?: ResourceColor--><!--Device-IconOptions-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

图标尺寸，不支持百分比。 默认值根据[searchIcon]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、[cancelButton]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_属性中的实际配置生效。

**类型：** Length

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IconOptions-size?: Length--><!--Device-IconOptions-size?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src?: ResourceStr
```

图标/图片源。 默认值：跟随主题。

**类型：** ResourceStr

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IconOptions-src?: ResourceStr--><!--Device-IconOptions-src?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

