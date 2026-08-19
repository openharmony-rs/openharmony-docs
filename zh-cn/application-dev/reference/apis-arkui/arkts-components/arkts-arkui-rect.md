# Rect

矩形绘制组件，用于在界面中绘制矩形图形，支持设置填充颜色、边框样式、圆角等属性。 > **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > 该组件从API version 20开始支持使用AttributeUpdater类的 > updateConstructorParams接口更新构造参数。

## 子组件 无

## Rect

```TypeScript
Rect(
    options?: RectOptions | RoundedRectOptions,
  )
```

Use new function to create Rect. Anonymous Object Rectification.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RectInterface-new (    options?: RectOptions | RoundedRectOptions,  ): RectAttribute--><!--Device-RectInterface-new (    options?: RectOptions | RoundedRectOptions,  ): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) \| [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 否 | Rect options |

## Rect

```TypeScript
Rect(
    options?: RectOptions | RoundedRectOptions,
  )
```

用于绘制矩形的构造函数。调用后创建一个Rect对象，可设置宽度、高度、圆角等属性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RectInterface-(    options?: RectOptions | RoundedRectOptions,  ): RectAttribute--><!--Device-RectInterface-(    options?: RectOptions | RoundedRectOptions,  ): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) \| [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 否 | Rect绘制属性，包含宽度、高度、圆角等配置。不传入时使用各属性默认值绘制矩形（宽高和圆角均为0）。 <br>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RectOptions](arkts-arkui-rectoptions-i.md) | 用于描述矩形绘制组件的绘制属性。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [RoundedRectOptions](arkts-arkui-roundedrectoptions-i.md) | 用于描述圆角矩形绘制组件的绘制属性。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |

