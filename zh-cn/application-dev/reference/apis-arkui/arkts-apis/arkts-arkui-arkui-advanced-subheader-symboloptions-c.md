# SymbolOptions

Declare type SymbolOptions

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export declare class SymbolOptions--><!--Device-unnamed-export declare class SymbolOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## effectStrategy

```TypeScript
effectStrategy?: SymbolEffectStrategy
```

设置SymbolGlyph动效策略。 默认值：SymbolEffectStrategy.NONE **说明：** \$r('sys.symbol.ohos_*')中引用的资源仅ohos_wifi支持层级动效模式。

**类型：** [SymbolEffectStrategy](arkts-arkui-symbolglyph-symboleffectstrategy-e.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolOptions-effectStrategy?: SymbolEffectStrategy--><!--Device-SymbolOptions-effectStrategy?: SymbolEffectStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: Array<ResourceColor>
```

设置SymbolGlyph颜色。 默认值：不同渲染策略下默认值不同。

**类型：** Array&lt;[ResourceColor](../../apis-na/arkts-apis/arkts-na-resourcecolor-t.md)&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolOptions-fontColor?: Array<ResourceColor>--><!--Device-SymbolOptions-fontColor?: Array<ResourceColor>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

设置SymbolGlyph大小。 number类型取值范围：大于等于0。 设置string类型时，支持number类型取值的字符串形式，可以附带单位，例如："10"，"10fp"。 默认值：系统默认值。

**类型：** number \| string \| [Resource](../../apis-na/arkts-apis/arkts-na-resource-t.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolOptions-fontSize?: number | string | Resource--><!--Device-SymbolOptions-fontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

设置SymbolGlyph粗细。 number类型取值[100,900]，取值间隔为100，默认为400，取值越大，字体越粗。 string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“lighter”、“regular” 、“medium”分别对应FontWeight中相应的枚举值。 默认值：FontWeight.Normal

**类型：** number \| [FontWeight](../../apis-na/arkts-apis/arkts-na-enums-fontweight-e.md) \| string

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolOptions-fontWeight?: number | FontWeight | string--><!--Device-SymbolOptions-fontWeight?: number | FontWeight | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## renderingStrategy

```TypeScript
renderingStrategy?: SymbolRenderingStrategy
```

设置SymbolGlyph渲染策略。 默认值：SymbolRenderingStrategy.SINGLE **说明：** \$r('sys.symbol.ohos_*')中引用的资源仅ohos_trash_circle、ohos_folder_badge_plus、ohos_lungs支持分层与多色模式。

**类型：** [SymbolRenderingStrategy](arkts-arkui-symbolglyph-symbolrenderingstrategy-e.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymbolOptions-renderingStrategy?: SymbolRenderingStrategy--><!--Device-SymbolOptions-renderingStrategy?: SymbolRenderingStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

