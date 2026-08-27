# Column属性/事件

除支持通用属性外，还支持以下属性：支持通用事件。

**继承/实现关系：** ColumnAttribute extends CommonMethod<ColumnAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alignItems

```TypeScript
alignItems(value: HorizontalAlign)
```

设置子组件在水平方向上的对齐格式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [HorizontalAlign](../arkts-apis/arkts-arkui-horizontalalign-e.md) | 是 | 子组件在水平方向上的对齐格式。 默认值：HorizontalAlign.Center |

## justifyContent

```TypeScript
justifyContent(value: FlexAlign)
```

设置子组件在垂直方向上的对齐格式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FlexAlign](../arkts-apis/arkts-arkui-flexalign-e.md) | 是 | 子组件在垂直方向上的对齐格式。 默认值：FlexAlign.Start    **说明：** 若子组件不设置[flexShrink](arkts-arkui-commonmethod-c.md#flexshrink)，FlexAlign.Center和FlexAlign.End可能失效，详见下方说明。设置为 FlexAlign.SpaceBetween、FlexAlign.SpaceAround、FlexAlign.SpaceEvenly时，[space](arkts-arkui-columnoptions-i.md)属性不生效。 |

## reverse

```TypeScript
reverse(isReversed: Optional<boolean>)
```

设置子组件在垂直方向上的排列是否反转。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isReversed | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 子组件在垂直方向上的排列是否反转。 默认值：true。设置true表示子组件在垂直方向上反转排列，设置false表示子组件在垂直方向上正序排列。 |
