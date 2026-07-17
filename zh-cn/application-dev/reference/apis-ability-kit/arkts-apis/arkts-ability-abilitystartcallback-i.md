# AbilityStartCallback

定义拉起UIExtensionAbility执行结果的回调。

<!--Device-unnamed-declare interface AbilityStartCallback--><!--Device-unnamed-declare interface AbilityStartCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onError

```TypeScript
onError(code: number, name: string, message: string): void
```

拉起UIExtensionAbility执行失败的回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStartCallback-onError(code: int, name: string, message: string): void--><!--Device-AbilityStartCallback-onError(code: int, name: string, message: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 拉起UIExtensionAbility执行失败时返回的结果码。 |
| name | string | 是 | 拉起UIExtensionAbility执行失败时返回的名称。 |
| message | string | 是 | 拉起UIExtensionAbility执行失败时返回的错误信息。 |

## onResult

```TypeScript
onResult?(parameter: AbilityResult): void
```

拉起UIExtensionAbility终止时的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStartCallback-onResult?(parameter: AbilityResult): void--><!--Device-AbilityStartCallback-onResult?(parameter: AbilityResult): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | 是 | 当调用[terminateSelfWithResult](arkts-ability-uiextensioncontext-c.md#terminateselfwithresult-1)方法终止UIExtensionAbility时返回的结果。 |

## completionHandler

```TypeScript
completionHandler?: CompletionHandlerForAbilityStartCallback
```

用于返回拉起指定类型的Ability组件的回调结果。

**类型：** CompletionHandlerForAbilityStartCallback

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStartCallback-completionHandler?: CompletionHandlerForAbilityStartCallback--><!--Device-AbilityStartCallback-completionHandler?: CompletionHandlerForAbilityStartCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

