# WaterFlowOptions

瀑布流组件参数对象。

**起始版本：** 9

<!--Device-unnamed-declare interface WaterFlowOptions--><!--Device-unnamed-declare interface WaterFlowOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: CustomBuilder
```

设置WaterFlow尾部组件，用于在瀑布流末尾显示自定义内容（如加载提示、底部标识等）。不设置时不显示尾部组件。

**类型：** CustomBuilder

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowOptions-footer?: CustomBuilder--><!--Device-WaterFlowOptions-footer?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footerContent

```TypeScript
footerContent?: ComponentContent
```

设置WaterFlow尾部组件。该参数的优先级高于参数footer，即同时设置footer和footerContent时，以footerContent设置的组件为准。

**类型：** ComponentContent

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowOptions-footerContent?: ComponentContent--><!--Device-WaterFlowOptions-footerContent?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutMode

```TypeScript
layoutMode?: WaterFlowLayoutMode
```

设置WaterFlow的布局模式，根据使用场景选择更切合的模式。

**类型：** WaterFlowLayoutMode

**默认值：** ALWAYS_TOP_DOWN

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowOptions-layoutMode?: WaterFlowLayoutMode--><!--Device-WaterFlowOptions-layoutMode?: WaterFlowLayoutMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller?: Scroller
```

可滚动组件的控制器，与可滚动组件绑定。

<p><strong>说明</strong><br>不允许和其他滚动类组件，如：ArcList、List、Grid、Scroll和WaterFlow绑定同一个滚动控制对象。</p>

**类型：** Scroller

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowOptions-scroller?: Scroller--><!--Device-WaterFlowOptions-scroller?: Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sections

```TypeScript
sections?: WaterFlowSections
```

设置FlowItem分组，实现同一个瀑布流组件内部各分组使用不同列数混合布局。适用于需要在不同区域使用不同列数布局的场景。不设置时使用统一列数布局。

<p><strong>说明</strong><br>1. 使用分组混合布局时会忽略columnsTemplate和rowsTemplate属性。<br>2. 使用分组混合布局时不支持单独设置footer，可以使用最后一个分组作为尾部组件。</p>

**类型：** WaterFlowSections

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowOptions-sections?: WaterFlowSections--><!--Device-WaterFlowOptions-sections?: WaterFlowSections-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

