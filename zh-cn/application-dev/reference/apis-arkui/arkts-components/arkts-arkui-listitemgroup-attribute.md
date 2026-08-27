# ListItemGroup属性/事件

除支持通用属性外，还支持以下属性：

**继承/实现关系：** ListItemGroupAttribute extends CommonMethod<ListItemGroupAttribute>

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## childrenMainSize

```TypeScript
childrenMainSize(value: ChildrenMainSize)
```

设置ListItemGroup组件的子组件在主轴方向的大小信息。

> **说明：**
> 
> - 当List组件的子组件包含ListItemGroup时，必须同时给List组件和每个ListItemGroup组件设置childrenMainSize属性。ListItemGroup通过该属性提供其子组件在主轴方向的大小信
> 息，用于配合List组件的childrenMainSize属性正常生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ChildrenMainSize](arkts-arkui-childrenmainsize-c.md) | 是 | 该对象用来维护子组件在主轴方向的大小信息。 |

## divider

```TypeScript
divider(
    value: ListDividerOptions | null,
  )
```

设置ListItem分割线样式，默认无分割线。strokeWidth，startMargin和endMargin不支持设置百分比。ListItem设置多态样式时，被按压的子组件上下的分割线不绘制。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ListDividerOptions](arkts-arkui-listdivideroptions-i.md) \| null | 是 | ListItem分割线样式。 |
