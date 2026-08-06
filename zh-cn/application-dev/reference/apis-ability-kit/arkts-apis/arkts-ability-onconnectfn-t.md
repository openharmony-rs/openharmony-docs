# OnConnectFn

```TypeScript
type OnConnectFn = (elementName: ElementName, remote: rpc.IRemoteObject) => void
```

与指定的后台服务成功建立连接时，会触发该回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-type OnConnectFn = (elementName: ElementName, remote: rpc.IRemoteObject) => void--><!--Device-unnamed-type OnConnectFn = (elementName: ElementName, remote: rpc.IRemoteObject) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标Ability的elementName。  |
| remote | rpc.IRemoteObject | 是 | 用于与目标Ability进行IPC通信的IRemoteObject实例。  |

