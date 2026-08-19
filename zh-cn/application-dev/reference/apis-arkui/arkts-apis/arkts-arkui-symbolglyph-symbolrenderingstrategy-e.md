# SymbolRenderingStrategy

渲染模式的枚举值。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum SymbolRenderingStrategy--><!--Device-unnamed-export declare enum SymbolRenderingStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SINGLE

```TypeScript
SINGLE = 0
```

单色渲染策略。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SymbolRenderingStrategy-SINGLE = 0--><!--Device-SymbolRenderingStrategy-SINGLE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLE_COLOR

```TypeScript
MULTIPLE_COLOR = 1
```

多色渲染策略，最多可设置三种颜色，仅设置一种颜色时更新第一层颜色，其余保持默认值。仅支持颜色值，透明度设置不生效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SymbolRenderingStrategy-MULTIPLE_COLOR = 1--><!--Device-SymbolRenderingStrategy-MULTIPLE_COLOR = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLE_OPACITY

```TypeScript
MULTIPLE_OPACITY = 2
```

分层渲染策略，默认颜色为黑色，可设置一种或多种颜色，但仅应用第一种颜色。预定义透明度：第一层100%，第二层50%，第三层20%。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SymbolRenderingStrategy-MULTIPLE_OPACITY = 2--><!--Device-SymbolRenderingStrategy-MULTIPLE_OPACITY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

