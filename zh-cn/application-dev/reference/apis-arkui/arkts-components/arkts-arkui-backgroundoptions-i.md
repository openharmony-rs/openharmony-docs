# BackgroundOptions

指定背景选项

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## align

```TypeScript
align?: Alignment
```

Set the alignment of the custom background and component.

Anonymous Object Rectification.

**类型：** Alignment

**默认值：** Alignment.Center

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ignoresLayoutSafeAreaEdges

```TypeScript
ignoresLayoutSafeAreaEdges?: Array<LayoutSafeAreaEdge>
```

The set of edges for which to ignore layout safe area. To respect safe area insets on all edges, explicitly pass empty edge set.

**类型：** Array<LayoutSafeAreaEdge>

**默认值：** The default value is LayoutSafeAreaEdge.ALL when background is ResourceColor, otherwise it is an empty array [].

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

