# ScrollBar属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** ScrollBarAttribute extends [CommonMethod<ScrollBarAttribute>](CommonMethod<ScrollBarAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class ScrollBarAttribute extends CommonMethod<ScrollBarAttribute>--><!--Device-unnamed-declare class ScrollBarAttribute extends CommonMethod<ScrollBarAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableNestedScroll

```TypeScript
enableNestedScroll(enabled: Optional<boolean>)
```

设置滚动条是否嵌套滚动。

> **说明：**  
>  
> 滚动条使能嵌套滚动时，滚动条的滚动偏移量会先发送给绑定的内层滚动组件，内层滚动组件再根据设置的嵌套滚动优先级依次传递给外层父滚动组件。  
>  
> WaterFlow组件的布局模式为移动窗口式（[WaterFlowLayoutMode.SLIDING_WINDOW](../../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowlayoutmode12)）时，不支持嵌套滚动。  
>  
> 设置嵌套滚动模式为[PARALLEL](../../../../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10)时，父子组件同时滚动，需要开发者在[onScrollFrameBegin](../../../../reference/apis-arkui/arkui-ts/ts-container-scroll.md#onscrollframebegin9)中按照所需逻辑，自行设置父子组件滚动顺序。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollBarAttribute-enableNestedScroll(enabled: Optional<boolean>): ScrollBarAttribute--><!--Device-ScrollBarAttribute-enableNestedScroll(enabled: Optional<boolean>): ScrollBarAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)<boolean> | 是 | 是否执行嵌套滚动。设置为true执行嵌套滚动，设置为false不嵌套滚动。 <br/>默认值：false |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

设置滚动条滑块的颜色，仅滚动条不放置子组件时生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollBarAttribute-scrollBarColor(color: Optional<ColorMetrics>): ScrollBarAttribute--><!--Device-ScrollBarAttribute-scrollBarColor(color: Optional<ColorMetrics>): ScrollBarAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-optional-t.md)<ColorMetrics> | 是 | 滚动条的颜色。<br/>默认值：ColorMetrics.numeric(0x66182431) |

