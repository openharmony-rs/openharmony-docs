# OnAtomicServiceRequestSuccessFn

```TypeScript
type OnAtomicServiceRequestSuccessFn = (appId: string) => void
```

打开原子化服务成功时的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type OnAtomicServiceRequestSuccessFn = (appId: string) => void--><!--Device-unnamed-type OnAtomicServiceRequestSuccessFn = (appId: string) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 被拉起原子化服务的appId。 |

