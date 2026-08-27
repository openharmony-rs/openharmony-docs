# AbilityCallbackFn

```TypeScript
type AbilityCallbackFn = (ability: any) => void
```

当监听到Ability时调用此回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | any | 是 | 表示注册监听的Ability。 |
