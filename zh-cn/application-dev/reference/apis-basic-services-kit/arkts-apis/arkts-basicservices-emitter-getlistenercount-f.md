# getListenerCount

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## getListenerCount

```TypeScript
function getListenerCount(eventId: number | string): number
```

获取指定事件的订阅数。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | number \| string | 是 | 事件ID，由开发者定义，用于辨别事件。 string类型：不可为空字符串，大小不超过10240字节，超出部分会被截断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 指定事件的订阅数。 |

**示例**

```TypeScript
let count: number = emitter.getListenerCount('eventId');
```
