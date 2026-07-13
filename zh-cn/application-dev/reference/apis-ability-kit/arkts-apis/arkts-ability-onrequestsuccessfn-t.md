# OnRequestSuccessFn

```TypeScript
export type OnRequestSuccessFn = (name: string) => void
```

拉起指定类型的Ability组件成功时的回调函数类型。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 被拉起Ability组件或系统操作的名称。Ability组件名称采用'[bundleName]#[moduleName]#[abilityName]'格式拼接。 |

