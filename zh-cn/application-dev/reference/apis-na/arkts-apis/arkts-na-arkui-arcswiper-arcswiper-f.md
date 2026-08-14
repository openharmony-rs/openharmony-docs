# ArcSwiper

## ArcSwiper

```TypeScript
@ComponentBuilder
export declare function ArcSwiper(
    controller?: ArcSwiperController, 
    content_?: CustomBuilder
): ArcSwiperAttribute
```

创建弧形滑块视图容器。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ArcSwiper(    controller?: ArcSwiperController,     content_?: CustomBuilder): ArcSwiperAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ArcSwiper(    controller?: ArcSwiperController,     content_?: CustomBuilder): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [ArcSwiperController](arkts-na-arkui-arcswiper-arcswipercontroller-c.md) | 否 | 给组件绑定一个控制器，用来控制组件翻页。 |
| content_ | CustomBuilder | 否 | 可以包含子组件。&lt;br/&gt;**说明：** &lt;br/&gt;1. 子组件类型：系统组件和自定义组件，支持渲染控制类型（ [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。&lt;br/&gt;2. 不建议在执行翻页动画过程中增加或减少子 组件，会导致未进行动画的子组件提前进入视窗，引起显示异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-na-arkui-arcswiper-arcswiperattribute-i.md) |  |


## ArcSwiper

```TypeScript
@Builder
export declare function ArcSwiper(
 style_: CustomBuilderT<ArcSwiperAttribute>,
 content_?: CustomBuilder,
): ArcSwiperAttribute
```

定义ArcSwiper组件

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ArcSwiper( style_: CustomBuilderT<ArcSwiperAttribute>, content_?: CustomBuilder,): ArcSwiperAttribute--><!--Device-unnamed-@Builderexport declare function ArcSwiper( style_: CustomBuilderT<ArcSwiperAttribute>, content_?: CustomBuilder,): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[ArcSwiperAttribute](arkts-na-arkui-arcswiper-arcswiperattribute-i.md)&gt; | 是 | arcSwiper属性实例 |
| content_ | CustomBuilder | 否 | 内容区 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-na-arkui-arcswiper-arcswiperattribute-i.md) |  |

