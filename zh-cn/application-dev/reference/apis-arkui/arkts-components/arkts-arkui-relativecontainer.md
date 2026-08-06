# RelativeContainer

相对布局组件，用于复杂场景中元素对齐的布局。通过设置子组件的对齐规则，实现子组件相对于容器或其他子组件的对齐，适用于需要灵活布局、减少嵌套层级的复杂界面。 子组件可以通过设置[alignRules]{@link CommonMethod#alignRules(value: AlignRuleOption)}来设置自身在相对容器中的对齐规则。 > **说明：** > > * 该组件从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > * 在RelativeContainer组件中，不设置[width]{@link CommonMethod#width(value: Length)}、 > [height]{@link CommonMethod#height(value: Length)}时，对应属性布局表现与设置为100%相同。 > > * 从API version 11开始，在RelativeContainer组件中，[width]{@link CommonMethod#width(value: Length)}、 > [height]{@link CommonMethod#height(value: Length)}设置"auto"表示自适应子组件。当width设置"auto"时，如果水平方向上子组件以容器作为锚点，则"auto"不生效（即视为 > 不设置width），垂直方向上同理。 > > * 从API version 20开始，在RelativeContainer组件中，[width]{@link CommonMethod#width(widthValue: Length | LayoutPolicy)}、 > [height]{@link CommonMethod#height(heightValue: Length | LayoutPolicy)}设置LayoutPolicy.wrapContent表示自适应子组件且被祖先节点尺寸约 > 束，设置LayoutPolicy.fixAtIdealSize表示自适应子组件且不被祖先节点尺寸约束。当width设置wrapContent或fixAtIdealSize时，如果水平方向上子组件直接或间接以容器作为锚点，则容器在该 > 方向上的尺寸不自适应该组件，垂直方向上同理。 > > * RelativeContainer中子组件的[margin]{@link CommonMethod#margin}不同于通用属性margin，指子组件到该方向上锚点的距离。例如，当alignRules设置了left锚点时， > margin.left表示子组件到left锚点的距离。若alignRules未设置某个边界方向的锚点（如未设置left或right锚点），则该方向的margin不生效。

## 子组件 支持多个子组件。

## RelativeContainer

```TypeScript
RelativeContainer()
```

相对布局组件，用于复杂场景中元素对齐的布局。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RelativeContainerInterface-(): RelativeContainerAttribute--><!--Device-RelativeContainerInterface-(): RelativeContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

