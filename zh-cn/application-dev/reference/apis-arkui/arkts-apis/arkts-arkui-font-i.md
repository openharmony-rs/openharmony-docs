# Font

设置文本样式。

> **说明：** 
> 
> 可以使用[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync)注册自定义字体。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## family

```TypeScript
family?: string | Resource
```

字体列表。默认字体'HarmonyOS Sans'。

使用多个字体时，请用逗号','分隔，字体的优先级按顺序生效。例如：'Arial,HarmonyOS Sans'。

**类型：** string &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

设置文本尺寸，Length为number类型时，使用fp单位。不支持设置百分比字符串。

默认值：16.0

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: FontStyle
```

设置文本的字体样式。

默认值：FontStyle.Normal

**类型：** [FontStyle](arkts-arkui-fontstyle-e.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## weight

```TypeScript
weight?: FontWeight | number | string
```

设置文本的字体粗细，number类型取值[100, 900]，取值间隔为100，取值越大，字体越粗。

默认值：400 | FontWeight.Normal

**类型：** [FontWeight](arkts-arkui-fontweight-e.md) &#124; number &#124; string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
