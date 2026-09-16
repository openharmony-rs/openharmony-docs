# ScrollBar属性/事件

除支持通用属性外，还支持以下属性：

**继承/实现关系：** ScrollBarAttribute extends CommonMethod<ScrollBarAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableNestedScroll

```TypeScript
enableNestedScroll(enabled: Optional<boolean>)
```

设置滚动条是否嵌套滚动。用于多层滚动容器、嵌套列表等需要通过滚动条拖动内层可滚动组件并联动父级滚动的场景，仅当ScrollBar通过Scroller与可滚动组件绑定时生效。

> **说明：** 
> 
> 滚动条使能嵌套滚动时，滚动条的滚动偏移量会先发送给绑定的内层滚动组件，内层滚动组件再根据设置的嵌套滚动优先级依次传递给外层父滚动组件。
> 
> WaterFlow组件的布局模式为移动窗口式（[WaterFlowLayoutMode.SLIDING_WINDOW](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowlayoutmode12)）时，不支持嵌套滚动。
> 
> 设置嵌套滚动模式为[PARALLEL](../../../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10)时，父子组件同时滚动，需要开发者在[onScrollFrameBegin](../../../reference/apis-arkui/arkui-ts/ts-container-scroll.md#onscrollframebegin9)中按照所需逻辑，自行设置父子组件滚动顺序。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否执行嵌套滚动。当需要在多层滚动容器之间传递滚动事件时设置为true；不需要嵌套滚动时设置为false。<br>默认值：false |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

设置滚动条的颜色，仅滚动条不放置子组件时生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)&lt;ColorMetrics&gt; | 是 | 滚动条的颜色，仅滚动条不放置子组件时生效。<br>默认值：ColorMetrics.numeric(0x66182431) |
