# getListenerCount

## getListenerCount

```TypeScript
function getListenerCount(eventId: number | string): number
```

获取指定事件的订阅数。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | number \| string | 是 | 事件ID，string类型的eventId取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 指定事件的订阅数。 |

**示例：**

```TypeScript
let count: number = emitter.getListenerCount("eventId");

```

