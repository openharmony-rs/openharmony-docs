# Rect

矩形绘制组件。

> **说明：**

> 该组件从API version 20开始支持使用[AttributeUpdater]{@link AttributeUpdater}类的
> [updateConstructorParams](docroot://reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。

## 子组件

无

## Rect

```TypeScript
Rect(
      options?: RectOptions | RoundedRectOptions,
    )
```

Use new function to create Rect.Anonymous Object Rectification.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RectInterface-new (
      options?: RectOptions | RoundedRectOptions,
    ): RectAttribute--><!--Device-RectInterface-new (
      options?: RectOptions | RoundedRectOptions,
    ): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) \| RoundedRectOptions | 否 | Rect options |

## Rect

```TypeScript
Rect(
      options?: RectOptions | RoundedRectOptions,
    )
```

用于绘制矩形的构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RectInterface-(
      options?: RectOptions | RoundedRectOptions,
    ): RectAttribute--><!--Device-RectInterface-(
      options?: RectOptions | RoundedRectOptions,
    ): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rectoptions-i.md) \| RoundedRectOptions | 否 | Rect绘制属性。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

- [RectOptions](arkts-arkui-rect-rectoptions-i.md)
- [RoundedRectOptions](arkts-arkui-rect-roundedrectoptions-i.md)
