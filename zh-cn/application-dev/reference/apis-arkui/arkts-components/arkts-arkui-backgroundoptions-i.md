# BackgroundOptions

指定背景选项

**起始版本：** 20

<!--Device-unnamed-declare interface BackgroundOptions--><!--Device-unnamed-declare interface BackgroundOptions-End-->

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

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundOptions-align?: Alignment--><!--Device-BackgroundOptions-align?: Alignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ignoresLayoutSafeAreaEdges

```TypeScript
ignoresLayoutSafeAreaEdges?: Array<LayoutSafeAreaEdge>
```

The set of edges for which to ignore layout safe area. To respect safe area insets on all edges, explicitly pass empty edge set.

**类型：** Array&lt;LayoutSafeAreaEdge&gt;

**默认值：** The default value is LayoutSafeAreaEdge.ALL when background is ResourceColor, otherwise it is an empty array [].

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundOptions-ignoresLayoutSafeAreaEdges?: Array<LayoutSafeAreaEdge>--><!--Device-BackgroundOptions-ignoresLayoutSafeAreaEdges?: Array<LayoutSafeAreaEdge>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

