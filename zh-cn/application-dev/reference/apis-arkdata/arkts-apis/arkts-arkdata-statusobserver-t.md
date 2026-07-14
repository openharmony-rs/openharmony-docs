# StatusObserver

```TypeScript
type StatusObserver = (sessionId: string, networkId: string, status: string) => void
```

定义获取分布式对象状态变更的监听回调函数。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 标识变更对象的sessionId。长度不大于128字节，且只能包含字母、数字或下划线_。 |
| networkId | string | 是 | 对端设备的网络标识。要求字符串非空且长度不超过255字节。 |
| status | string | 是 | 标识分布式对象的状态，可能的取值有'online'（上线）、'offline'（下线）和'restore'（恢复）。 |

