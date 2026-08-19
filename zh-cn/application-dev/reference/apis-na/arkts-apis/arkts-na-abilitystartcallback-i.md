# AbilityStartCallback

定义拉起UIExtensionAbility执行结果的回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare interface AbilityStartCallback--><!--Device-unnamed-declare interface AbilityStartCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onError

```TypeScript
onError(code: int, name: string, message: string): void
```

拉起UIExtensionAbility执行失败的回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStartCallback-onError(code: int, name: string, message: string): void--><!--Device-AbilityStartCallback-onError(code: int, name: string, message: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 拉起UIExtensionAbility执行失败时返回的结果码。 |
| name | string | 是 | 拉起UIExtensionAbility执行失败时返回的名称。 |
| message | string | 是 | 拉起UIExtensionAbility执行失败时返回的错误信息。 |

## completionHandler

```TypeScript
completionHandler?: CompletionHandlerForAbilityStartCallback
```

用于返回拉起指定类型的Ability组件的回调结果。

**类型：** [CompletionHandlerForAbilityStartCallback](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-completionhandlerforabilitystartcallback-completionhandlerforabilitystartcallback-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStartCallback-completionHandler?: CompletionHandlerForAbilityStartCallback--><!--Device-AbilityStartCallback-completionHandler?: CompletionHandlerForAbilityStartCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onResult

```TypeScript
onResult?: OnResultFn
```

拉起UIExtensionAbility终止时的回调。

**类型：** [OnResultFn](arkts-na-onresultfn-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityStartCallback-onResult?: OnResultFn--><!--Device-AbilityStartCallback-onResult?: OnResultFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

