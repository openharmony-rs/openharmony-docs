# ColumnSplit属性/事件

除支持通用属性外，还支持以下属性：支持通用事件。

**继承/实现关系：** ColumnSplitAttribute extends CommonMethod<ColumnSplitAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## divider

```TypeScript
divider(value: ColumnSplitDividerStyle | null)
```

设置分割线与子组件之间的距离。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ColumnSplitDividerStyle](arkts-arkui-columnsplitdividerstyle-i.md) \| null | 是 | 分割线的margin，即设置分割线与子组件的距离。对象属性包括：startMargin（子组件与上方分割线的距离）和 endMargin（子组件与下方分割线的距离）。 默认值：null。当设置为null时，分割线与子组件的距离为0vp。 非法值：按默认值处理。 |

## resizeable

```TypeScript
resizeable(value: boolean)
```

设置分割线是否可拖拽。设置为true时，用户可拖动分割线调整相邻子组件高度；设置为false时，分割线不可拖动，子组件高度固定。

> **说明：**
> 
> 初始化后，当动态修改margin、[border](arkts-arkui-commonmethod-c.md#border)、
> padding通用属性导致子组件尺寸大于相邻分割线间距时，不支持拖动分割线改变子组件的高度。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 分割线是否可拖动。设置为true时表示分割线可拖动，设置为false时表示分割线不可拖动。子组件的高度调整范围受其最大最小高度限制；当子组件尺寸大于相邻分割线间距时，不支持拖动 分割线。初始化后，当动态修改margin、border、padding通用属性导致子组件尺寸大于相邻分割线间距时，不支持拖动分割线改变子组件的高度。 默认值：false 非法值：按默认值处理。 |
