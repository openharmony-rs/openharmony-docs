# RenderingContextSettings

用来配置CanvasRenderingContext2D对象的参数，包括是否开启抗锯齿。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(antialias?: boolean)
```

构造CanvasRenderingContext2D对象，支持配置开启抗锯齿。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| antialias | boolean | 否 | 表明canvas是否开启抗锯齿。<br>异常值undefined按默认值处理。<br>false：表示不开启抗锯齿功能，true：表示开启抗锯齿。<br>默认值：false<br>**说明：**<br>绘制文本默认开启抗锯齿效果，RenderingContextSettings的antialias无法影响绘制文本的抗锯齿效果，如需修改文本抗锯齿效果，请使用[antialias&lt;sup&gt;24+&lt;/sup&gt;](#antialias24)接口。 |

## antialias

```TypeScript
antialias?: boolean
```

表明canvas是否开启抗锯齿。
<br>异常值undefined按默认值处理。
<br>false：表示不开启抗锯齿功能，true：表示开启抗锯齿。
<br>默认值：false
<br>**说明：**<br>
绘制文本默认开启抗锯齿效果，RenderingContextSettings的antialias无法影响绘制文本的抗锯齿效果，
如需修改文本抗锯齿效果，请使用[antialias<sup>24+</sup>](#antialias24)接口。

**类型：** boolean

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

