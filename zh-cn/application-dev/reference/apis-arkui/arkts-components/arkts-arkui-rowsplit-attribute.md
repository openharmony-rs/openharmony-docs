# RowSplit属性/事件

除支持通用属性外，还支持以下属性：支持通用事件。

**继承/实现关系：** RowSplitAttribute extends CommonMethod<RowSplitAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## resizeable

```TypeScript
resizeable(value: boolean)
```

设置分割线是否可拖拽。设置为true时，用户可以拖拽分割线改变子组件宽度；设置为false时，分割线位置固定。

> **说明：**
> 
> 初始化后，动态修改margin、border、padding通用属性导致子组件宽度大于相邻分割线间距的异常情况下，不支持拖动分割线改变子组件的宽度。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 分割线是否可拖拽。设置为true时表示分割线可拖拽，设置为false时表示分割线不可拖拽。 默认值：false 非法值：按默认值处理。 |
