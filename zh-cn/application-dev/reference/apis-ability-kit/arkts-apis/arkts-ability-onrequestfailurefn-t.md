# OnRequestFailureFn

```TypeScript
export type OnRequestFailureFn = (name: string, failureCode: AbilityStartFailureCode, failureMessage: string) => void
```

拉起指定类型的Ability组件失败时的回调函数类型。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type OnRequestFailureFn = (name: string, failureCode: AbilityStartFailureCode, failureMessage: string) => void--><!--Device-unnamed-export type OnRequestFailureFn = (name: string, failureCode: AbilityStartFailureCode, failureMessage: string) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 被拉起Ability组件或系统操作的名称。Ability组件名称采用'[bundleName]#[moduleName]#[abilityName]'格式拼接。如果用户自动取消拉起，name为空。 |
| failureCode | AbilityStartFailureCode | 是 | 失败原因的错误码。 |
| failureMessage | string | 是 | 失败原因的描述。 |

