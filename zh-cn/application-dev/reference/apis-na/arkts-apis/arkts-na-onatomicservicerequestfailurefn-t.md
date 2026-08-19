# OnAtomicServiceRequestFailureFn

```TypeScript
type OnAtomicServiceRequestFailureFn = (appId: string, failureCode: FailureCode, failureMessage: string) => void
```

打开原子化服务失败时的回调函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type OnAtomicServiceRequestFailureFn = (appId: string, failureCode: FailureCode, failureMessage: string) => void--><!--Device-unnamed-type OnAtomicServiceRequestFailureFn = (appId: string, failureCode: FailureCode, failureMessage: string) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 被拉起原子化服务的appId。 |
| failureCode | [FailureCode](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-completionhandlerforatomicservice-failurecode-e.md) | 是 | 失败原因的错误码。 |
| failureMessage | string | 是 | 失败原因的描述。 |

