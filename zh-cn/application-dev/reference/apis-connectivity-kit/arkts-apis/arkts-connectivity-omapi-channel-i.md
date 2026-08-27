# Channel

Channel的实例表示在某个Session实例上创建通道，可能为基础通道或逻辑通道。通过 [Session.openBasicChannel](arkts-connectivity-omapi-session-i.md#openbasicchannel)或 [Session.openLogicalChannel](arkts-connectivity-omapi-session-i.md#openlogicalchannel)获取Channel实例。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

## 导入模块

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## close

```TypeScript
close(): void
```

关闭Channel。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;

// 在使用seSession之前，需要对seSession进行初始化

try {
    seSession.close();
} catch (error) {
    hilog.error(0x0000, 'testTag', 'close error %{public}s', JSON.stringify(error));
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// 在使用seChannel之前，需要对seChannel进行初始化
try {
    seChannel.close();
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'close exception %{public}s', JSON.stringify(exception));
}
```

## getSelectResponse

```TypeScript
getSelectResponse(): number[]
```

获取SELECT Applet时的响应数据，包含状态字。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | SELECT Applet时的响应数据，包含状态字。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// 在使用seChannel之前，需要对seChannel进行初始化
try {
    let response = seChannel.getSelectResponse();
    hilog.info(0x0000, 'testTag', 'response = %{public}s', JSON.stringify(response));
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'getSelectResponse exception %{public}s', JSON.stringify(exception));
}
```

## getSession

```TypeScript
getSession(): Session
```

获取打开该Channel的Session对象。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Session | 该Channel绑定的Session 对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;

// 在使用seChannel之前，需要对seChannel进行初始化

try {
    seSession = seChannel.getSession();
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'getSession exception %{public}s', JSON.stringify(exception));
}
```

## isBasicChannel

```TypeScript
isBasicChannel(): boolean
```

检查该Channel是否为基础Channel。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 该Channel是基础Channel, false：该Channel逻辑Channel 。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// 在使用seChannel之前，需要对seChannel进行初始化
try {
    let isBasic = seChannel.isBasicChannel();
    hilog.info(0x0000, 'testTag', 'isBasic = %{public}s', JSON.stringify(isBasic));
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'isBasicChannel exception %{public}s', JSON.stringify(exception));
}
```

## isClosed

```TypeScript
isClosed(): boolean
```

检查该Channel是否已被关闭。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: Channel是关闭的，false: 不是关闭的。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;

// 在使用seSession之前，需要对seSession进行初始化

try {
    let isClosed = seSession.isClosed();
    hilog.info(0x0000, 'testTag', 'isClosed %{public}s', JSON.stringify(isClosed));
} catch (error) {
    hilog.error(0x0000, 'testTag', 'isClosed error %{public}s', JSON.stringify(error));
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// 在使用seChannel之前，需要对seChannel进行初始化
try {
    let isClosed = seChannel.isClosed();
    hilog.info(0x0000, 'testTag', 'isClosed = %{public}s', JSON.stringify(isClosed));
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'isClosed exception %{public}s', JSON.stringify(exception));
}
```

## transmit

```TypeScript
transmit(command: number[]): Promise<number[]>
```

向SE发送APDU数据，数据符合ISO/IEC 7816规范。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | number[] | 是 | 需要发送到SE的APDU数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number[] & gt; | 以Promise形式异步返回接收到的响应APDU数据，number数组。若芯片捕获异常则返回全0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session or channel that has been closed. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the command is filtered by the security policy. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// 在使用seChannel之前，需要对seChannel进行初始化
let cmdData = [0x01, 0x02, 0x03, 0x04]; // 请更改为正确的data
try {
    seChannel.transmit(cmdData).then((response) => {
        // 若芯片捕获异常则response返回全0
        hilog.info(0x0000, 'testTag', 'transmit response = %{public}s.', JSON.stringify(response));
    }).catch((error : BusinessError) => {
        hilog.error(0x0000, 'testTag', 'transmit error = %{public}s.', JSON.stringify(error));
    });
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'transmit exception = %{public}s.', JSON.stringify(exception));
}
```

## transmit

```TypeScript
transmit(command: number[], callback: AsyncCallback<number[]>): void
```

向SE发送APDU数据，数据符合ISO/IEC 7816规范。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | number[] | 是 | 需要发送到SE的APDU数据。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | 是 | 返回接收到的响应APDU数据，number数组。若芯片捕获异常则返回全0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session or channel that has been closed. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the command is filtered by the security policy. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// 在使用seChannel之前，需要对seChannel进行初始化
let cmdData = [0x01, 0x02, 0x03, 0x04]; // 请更改为正确的data
try {
    seChannel.transmit(cmdData, (error, response) => {
    if (error) {
        hilog.error(0x0000, 'testTag', 'transmit error %{public}s', JSON.stringify(error));
    } else {
        // 若芯片捕获异常则response返回全0
        hilog.info(0x0000, 'testTag', 'transmit response = %{public}s.', JSON.stringify(response));
    }
    });
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'transmit exception %{public}s', JSON.stringify(exception));
}
```
