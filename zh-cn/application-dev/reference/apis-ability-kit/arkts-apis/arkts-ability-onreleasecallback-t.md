# OnReleaseCallback

```TypeScript
export type OnReleaseCallback = (msg: string) => void
```

注册通用组件服务端Stub（桩）断开监听通知的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnReleaseCallback = (msg: string) => void--><!--Device-unnamed-export type OnReleaseCallback = (msg: string) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msg | string | 是 | 用于传递释放消息。 |

