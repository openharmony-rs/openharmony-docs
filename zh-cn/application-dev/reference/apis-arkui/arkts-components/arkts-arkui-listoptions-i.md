# ListOptions

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

Set initialIndex.

**类型：** number

**默认值：** 0 [since 18]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scroller

```TypeScript
scroller?: Scroller
```

Set scroller.

**类型：** Scroller

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: number | string
```

子组件主轴方向的间隔。

<br/>默认值：0
<br/>参数类型为number时单位为vp。
<br/>**说明：**
<br/>设置为负数或者大于等于List内容区长度时，按默认值显示。
<br/>space参数值小于List分割线宽度时，子组件主轴方向的间隔取分割线宽度。
<br/>List子组件的visibility属性设置为None时不显示，但该子组件上下的space还是会生效。<br/>

**类型：** number | string

**默认值：** 0 [since 18]

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spaceWidth

```TypeScript
spaceWidth?: Dimension
```

沿着主轴的列表项之间的间距。

<p><strong>注意</strong>
<br>如果设置为负数或大于或等于列表长度的值
内容区域，使用默认值。
<br>如果设置的值小于列表分割线的宽度，则列表分割线的宽度
作为间距。
<br><em>ListItemGroup</em>的子组件，其<em>可见性</em>属性设置为<em>无</em>
不显示，但它们上下的间距仍然有效。
<br>如果同时设置了spaceWidth和space，则spaceWidth优先。
</p>

**类型：** Dimension

**默认值：** 0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

