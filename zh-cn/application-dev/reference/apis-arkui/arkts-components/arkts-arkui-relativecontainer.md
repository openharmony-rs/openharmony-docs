# RelativeContainer

相对布局组件，用于复杂场景中元素对齐的布局。

子组件可以通过设置[alignRules]{@link CommonMethod#alignRules(value: AlignRuleOption)}来设置自身在相对容器中的对齐规则。

> **说明：**
>
> *
>
> * 在RelativeContainer组件中，不设置[width]{@link CommonMethod#width(value: Length)}、
> [height]{@link CommonMethod#height(value: Length)}时，对应属性布局表现与设置为100%相同。
>
> * 从API version 11开始，在RelativeContainer组件中，[width]{@link CommonMethod#width(value: Length)}、
> [height]{@link CommonMethod#height(value: Length)}设置"auto"表示自适应子组件。当width设置"auto"时，如果水平方向上子组件以容器作为锚点，则"auto"不生效（即视为
> 不设置width），垂直方向上同理。
>
> * 从API version 20开始，在RelativeContainer组件中，[width]{@link CommonMethod#width(widthValue: Length | LayoutPolicy)}、
> [height]{@link CommonMethod#height(heightValue: Length | LayoutPolicy)}设置LayoutPolicy.wrapContent表示自适应子组件且被祖先节点尺寸约
> 束，设置LayoutPolicy.fixAtIdealSize表示自适应子组件且不被祖先节点尺寸约束。当width设置wrapContent或fixAtIdealSize时，如果水平方向上子组件直接或间接以容器作为锚点，则容器在该
> 方向上的尺寸不自适应该组件，垂直方向上同理。
>
> * 相对布局容器内的子组件的[margin]{@link CommonMethod#margin}含义不同于通用属性的margin，其含义为到该方向上的锚点的距离。若该方向上没有锚点，则该方向的margin不生效。


## RelativeContainer

```TypeScript
RelativeContainer()
```

相对布局组件，用于复杂场景中元素对齐的布局。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

- [BarrierStyle](arkts-arkui-relativecontainer-barrierstyle-i.md)
- [GuideLinePosition](arkts-arkui-relativecontainer-guidelineposition-i.md)
- [GuideLineStyle](arkts-arkui-relativecontainer-guidelinestyle-i.md)
- [LocalizedBarrierStyle](arkts-arkui-relativecontainer-localizedbarrierstyle-i.md)
- [BarrierDirection](arkts-arkui-relativecontainer-barrierdirection-e.md)
- [LocalizedBarrierDirection](arkts-arkui-relativecontainer-localizedbarrierdirection-e.md)
