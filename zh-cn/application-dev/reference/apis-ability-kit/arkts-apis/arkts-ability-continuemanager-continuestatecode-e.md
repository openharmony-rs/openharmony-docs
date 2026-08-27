# ContinueStateCode

快速拉起的结果状态码的枚举值。模型约束：此接口仅可在Stage模型下使用。

**起始版本：** 18

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## SUCCESS

```TypeScript
SUCCESS = 0
```

操作成功。表示快速拉起已成功完成，应用可以继续执行跨端迁移流程。此接口仅可在Stage模型下使用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## SYSTEM_ERROR

```TypeScript
SYSTEM_ERROR = 1
```

操作失败。表示快速拉起过程中发生系统错误，应用需要提示用户迁移失败，并根据业务场景决定是否需要重试。此接口仅可在Stage模型下使用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission
