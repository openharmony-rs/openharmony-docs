# OnFillSuccessFn

```TypeScript
type OnFillSuccessFn = (viewData: ViewData) => void
```

自动填充请求成功处理时的回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| viewData | [ViewData](arkts-ability-viewdata-i.md) | 是 | AutoFill的视图数据信息。 |
