# ListOptions

```TypeScript
interface ListOptions
```

用于设置List组件参数。

> **说明：** 
> 
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialIndex

```TypeScript
initialIndex?: number
```

设置当前List初次加载时显示区域起始位置的item索引值。

默认值：0。当stackFromEnd为true时，默认值为总item个数-1。

**说明：** 

设置为负数或超过了当前List最后一个item的索引值时视为无效取值，无效取值按默认值显示。

从API version 14开始，如果在List组件创建完成后首次布局前（如List的[onAttach](arkts-arkui-common-comp-commonmethod-c.md#onattach)事件中），调用Scroller滚动控制器中不带动画的scrollToIndex或scrollEdge方法，会覆盖initialIndex设置的值。

设置了initialIndex后，List从initialIndex对应的子组件开始布局，在这之前的子组件未参与布局，无法计算准确大小，因此通过[currentOffset](arkts-arkui-scroll-comp-scroller-c.md#currentoffset)接口获取到的List的滚动总偏移量通过估算得出，可能会有误差。可通过设置[childrenMainSize](arkts-arkui-list-comp-attribute.md#childrenmainsize)确保List的滚动总偏移量的准确性。

**类型：** number

**默认值：** 
- API版本18+：0

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller?: Scroller
```

可滚动组件的控制器。与List绑定后，可以通过它控制List的滚动。默认不绑定滚动控制器。

**说明：** 

不允许和其他滚动类组件，如：[ArcList](arkts-arkui-arclist-comp.md#ohosarkuiarclist)、[List](arkts-arkui-list-comp.md#list)、[Grid](arkts-arkui-grid-comp.md#grid)、[Scroll](arkts-arkui-scroll-comp.md#scroll)和[WaterFlow](arkts-arkui-waterflow-comp.md#water_flow)绑定同一个滚动控制对象。

**类型：** [Scroller](arkts-arkui-scroll-comp-scroller-c.md)

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: number | string
```

子组件主轴方向的间隔。

默认值：0

参数类型为number时单位为vp。

**说明：** 

设置为负数或者大于等于List内容区长度时，按默认值显示。

space参数值小于List分割线宽度时，子组件主轴方向的间隔取分割线宽度。

List子组件的visibility属性设置为None时不显示，但该子组件上下的space还是会生效。

如果同时设置了spaceWidth和space，则spaceWidth优先生效。当spaceWidth为undefined或null时，space生效。

**类型：** number &#124; string

**默认值：** 
- API版本18+：0

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spaceWidth

```TypeScript
spaceWidth?: Dimension
```

子组件主轴方向的间隔。

默认值：0

参数类型为number时单位为vp。

**说明：** 

设置为负数或者大于等于List内容区长度时，按默认值显示。

spaceWidth参数值小于List分割线宽度时，子组件主轴方向的间隔取分割线宽度。

List子组件的visibility属性设置为None时不显示，但该子组件上下的spaceWidth间隔还是会生效。如果同时设置了spaceWidth和space，则spaceWidth优先生效。当spaceWidth为undefined或null时，space生效。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**类型：** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**默认值：** 0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
