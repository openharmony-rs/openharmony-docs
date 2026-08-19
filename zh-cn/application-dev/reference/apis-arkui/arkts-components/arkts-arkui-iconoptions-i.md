# IconOptions

定义图标选项。

**起始版本：** 10

<!--Device-unnamed-interface IconOptions--><!--Device-unnamed-interface IconOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## color

```TypeScript
color?: ResourceColor
```

图标颜色。不传入时使用默认颜色（浅色模式为'#99182431'，表示深灰色，60%不透明度，深色模式为'#99ffffff'，表示白色，60%不透明度）。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-IconOptions-color?: ResourceColor--><!--Device-IconOptions-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

图标尺寸，不传入单位时默认单位为vp，不支持百分比。传入百分比时，不生效。

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-IconOptions-size?: Length--><!--Device-IconOptions-size?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src?: ResourceStr
```

图标/图片源。不传入时使用系统默认图标。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-IconOptions-src?: ResourceStr--><!--Device-IconOptions-src?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

