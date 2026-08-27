# Row属性/事件

除支持通用属性外，还支持以下属性：支持通用事件。

**继承/实现关系：** RowAttribute extends CommonMethod<RowAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alignItems

```TypeScript
alignItems(value: VerticalAlign)
```

设置子组件在垂直方向上的对齐格式。调用后，子组件将按照指定方式在垂直方向对齐，默认为垂直居中对齐。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [VerticalAlign](../arkts-apis/arkts-arkui-verticalalign-e.md) | 是 | 子组件在垂直方向上的对齐格式。 默认值：VerticalAlign.Center |

## justifyContent

```TypeScript
justifyContent(value: FlexAlign)
```

设置子组件在水平方向上的对齐格式。调用后，子组件将按照指定方式在水平方向对齐，默认为起始端对齐。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md) | 是 | 子组件在水平方向上的对齐格式。 默认值：FlexAlign.Start    **说明：** 从API version 9开始，space为负数或者justifyContent设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、 FlexAlign.SpaceEvenly时，space参数不生效。 |

## reverse

```TypeScript
reverse(isReversed: Optional<boolean>)
```

设置子组件在水平方向上的排列顺序是否反转。设置为true时，子组件按照从右到左的顺序排列；设置为false时，子组件按照从左到右的顺序排列。适用于需要动态调整子组件显示顺序的场景，如国际化布局适配。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isReversed | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 子组件在水平方向上的排列顺序是否反转。 设置true表示子组件在水平方向上反转排列（从右到左），设置false表示子组件在水平方向上正序排列（从左到右）。参数值为undefined时视为true，主轴方向反转。 |
