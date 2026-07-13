# Row属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**继承/实现关系：** RowAttribute extends [CommonMethod<RowAttribute>](CommonMethod<RowAttribute>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: VerticalAlign)
```

设置子组件在垂直方向上的对齐格式。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | VerticalAlign | 是 | 子组件在垂直方向上的对齐格式。<br/>默认值：VerticalAlign.Center |

## justifyContent

```TypeScript
justifyContent(value: FlexAlign)
```

设置子组件在水平方向上的对齐格式。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | FlexAlign | 是 | 子组件在水平方向上的对齐格式。<br/>默认值：FlexAlign.Start |

## reverse

```TypeScript
reverse(isReversed: Optional<boolean>)
```

设置子组件在水平方向上的排列是否反转。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isReversed | Optional&lt;boolean&gt; | 是 | 子组件在水平方向上的排列是否反转。<br/>默认值：true，设置true表示子组件在水平方向上反转排列，设置false表示子组件在水平方向上正序排列。 |

