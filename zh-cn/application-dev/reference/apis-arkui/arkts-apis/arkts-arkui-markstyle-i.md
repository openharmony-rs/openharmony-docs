# MarkStyle

```TypeScript
declare interface MarkStyle
```

定义checkbox标记的样式。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

内部图标大小，单位vp。默认大小与多选框组件宽度相同。

不支持百分比形式设置。设置为非法值时，按照默认值处理。

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

内部图标颜色。默认值：Color.White

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

内部图标粗细，单位vp。不支持设置百分比。设置为非法值时，按照默认值处理。默认值：2

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
