# OnContinueDoneCallback（系统接口）

```TypeScript
type OnContinueDoneCallback = (result: number) => void
```

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | number | 是 | 迁移任务的结果，0表示迁移成功，非0值表示迁移失败。具体错误码及其含义、可能原因和解决措施请参见continueMission接口的错误码说明。 |
