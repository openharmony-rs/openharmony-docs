# OnRemoteStateChangeCallback

```TypeScript
export type OnRemoteStateChangeCallback = (msg: string) => void
```

注册协同场景下跨设备组件状态变化监听通知的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnRemoteStateChangeCallback = (msg: string) => void--><!--Device-unnamed-export type OnRemoteStateChangeCallback = (msg: string) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msg | string | 是 | 用于传递释放消息。  |

