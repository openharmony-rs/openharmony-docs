# WaterFlowOptions

提供瀑布流组件的参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface WaterFlowOptions--><!--Device-unnamed-export declare interface WaterFlowOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: CustomBuilder
```

瀑布流组件的尾部组件。

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowOptions-footer?: CustomBuilder--><!--Device-WaterFlowOptions-footer?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footerContent

```TypeScript
footerContent?: ComponentContentBase
```

瀑布流组件的尾部组件。

**类型：** ComponentContentBase

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowOptions-footerContent?: ComponentContentBase--><!--Device-WaterFlowOptions-footerContent?: ComponentContentBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutMode

```TypeScript
layoutMode?: WaterFlowLayoutMode
```

瀑布流组件的布局模式。

**类型：** WaterFlowLayoutMode

**默认值：** ALWAYS_TOP_DOWN

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowOptions-layoutMode?: WaterFlowLayoutMode--><!--Device-WaterFlowOptions-layoutMode?: WaterFlowLayoutMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller?: Scroller
```

可滚动组件的控制器，与可滚动组件绑定。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_不允许和其他滚动类组件，如ArcList、List、Grid、Scroll绑定同一个滚动控制对象。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_

**类型：** Scroller

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowOptions-scroller?: Scroller--><!--Device-WaterFlowOptions-scroller?: Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sections

```TypeScript
sections?: WaterFlowSections
```

瀑布流项分组，不同分组可以设置不同的列数。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_1. 使用分组时，columnsTemplate和rowsTemplate属性将被忽略。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_2. 使用分组时不支持单独设置footer，可以使用最后一个分组作为尾部组件。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_

**类型：** WaterFlowSections

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowOptions-sections?: WaterFlowSections--><!--Device-WaterFlowOptions-sections?: WaterFlowSections-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

