# getListenerCount

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## getListenerCount

```TypeScript
function getListenerCount(eventId: long | string): long
```

获取指定事件的订阅数。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function getListenerCount(eventId: long | string): long--><!--Device-emitter-function getListenerCount(eventId: long | string): long-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | long \| string | 是 | 事件ID，由开发者定义，用于辨别事件。 string类型：不可为空字符串，大小不超过10240字节，超出部分会被截断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 指定事件的订阅数。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
let count: number = emitter.getListenerCount("eventId");
```

ArkTS-Sta示例：

```TypeScript
let count: long = emitter.getListenerCount("eventId");
```

