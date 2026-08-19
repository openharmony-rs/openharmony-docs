# Font

设置文本样式。 > **说明：** > > 可以使用[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync)注册自定义字体。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface Font--><!--Device-unnamed-export declare interface Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## family

```TypeScript
family?: string | Resource
```

字体列表。 使用多个字体时，请用逗号','分隔，字体的优先级按顺序生效。

**类型：** string \| [Resource](arkts-na-resource-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-family?: string | Resource--><!--Device-Font-family?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

设置文本尺寸，Length为number类型时，使用fp单位。不支持设置百分比字符串。 默认值：16.0

**类型：** [Length](arkts-na-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-size?: Length--><!--Device-Font-size?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: FontStyle
```

设置文本的字体样式。 默认值：FontStyle.Normal

**类型：** [FontStyle](../../apis-arkui/arkts-apis/arkts-arkui-fontstyle-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-style?: FontStyle--><!--Device-Font-style?: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## weight

```TypeScript
weight?: FontWeight | int | string
```

设置文本的字体粗细，number类型取值[100, 900]，取值间隔为100，取值越大，字体越粗。 默认值：400 | FontWeight.Normal

**类型：** [FontWeight](../../apis-arkui/arkts-apis/arkts-arkui-fontweight-e.md) \| int \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Font-weight?: FontWeight | int | string--><!--Device-Font-weight?: FontWeight | int | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

