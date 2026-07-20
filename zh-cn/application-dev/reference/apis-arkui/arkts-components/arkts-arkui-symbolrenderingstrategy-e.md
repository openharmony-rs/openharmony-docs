# SymbolRenderingStrategy

渲染模式的枚举值。

**起始版本：** 11

<!--Device-unnamed-declare enum SymbolRenderingStrategy--><!--Device-unnamed-declare enum SymbolRenderingStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SINGLE

```TypeScript
SINGLE = 0
```

单色模式（默认值）。

可以设置一个或者多个颜色，默认为黑色。

当设置多个颜色时，仅生效第一个颜色。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-SymbolRenderingStrategy-SINGLE = 0--><!--Device-SymbolRenderingStrategy-SINGLE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLE_COLOR

```TypeScript
MULTIPLE_COLOR = 1
```

多色模式。

最多可以设置三个颜色。当只设置一个颜色时，修改symbol图标的第一层颜色，其他颜色保持默认颜色。

颜色设置顺序与图标分层顺序匹配，当颜色数量大于图标分层时，多余的颜色不生效。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-SymbolRenderingStrategy-MULTIPLE_COLOR = 1--><!--Device-SymbolRenderingStrategy-MULTIPLE_COLOR = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLE_OPACITY

```TypeScript
MULTIPLE_OPACITY = 2
```

分层模式。

默认为黑色，可以设置一个或者多个颜色。当设置多个颜色时，仅生效第一个颜色。

不透明度与图层相关，symbol通用图标的默认第一层透明度为100%、第二层透明度为50%、第三层透明度为20%。当设置的颜色包含透明度时，设置的透明度与每个图层的默认透明度进行叠加。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-SymbolRenderingStrategy-MULTIPLE_OPACITY = 2--><!--Device-SymbolRenderingStrategy-MULTIPLE_OPACITY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

