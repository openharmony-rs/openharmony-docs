# NotifyNetDisconnectCallback（系统接口）

```TypeScript
type NotifyNetDisconnectCallback = (deviceId: string, state: number) => void
```

断开连接时的回调函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type NotifyNetDisconnectCallback = (deviceId: string, state: int) => void--><!--Device-unnamed-type NotifyNetDisconnectCallback = (deviceId: string, state: int) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | Indicates the deviceId network disconnect.  |
| state | number | 是 | Indicates the state of network.  |

