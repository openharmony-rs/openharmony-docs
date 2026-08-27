# Session

Session的实例表示在某个SE Reader实例上创建连接会话。通过[Reader.openSession](arkts-connectivity-omapi-reader-i.md#opensession)获取Session实例。

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

关闭与SE的当前会话连接。这将关闭此Session打开的所有Channel。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, service state exception. |

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

## closeChannels

```TypeScript
closeChannels(): void
```

关闭此Session上打开的所有Channel。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, service state exception. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;

// 在使用seSession之前，需要对seSession进行初始化

try {
    seSession.closeChannels();
} catch (error) {
    hilog.error(0x0000, 'testTag', 'closeChannels error %{public}s', JSON.stringify(error));
}
```

## getATR

```TypeScript
getATR(): number[]
```

获取该SE的ATR。如果该SE的ATR不可用，则应返回空数组。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 返回SE的ATR，SE的ATR不可用时，返回空的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, service state exception. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;

// 在使用seSession之前，需要对seSession进行初始化

try {
    let atr = seSession.getATR();
    hilog.info(0x0000, 'testTag', 'atr %{public}s', JSON.stringify(atr));
} catch (error) {
    hilog.error(0x0000, 'testTag', 'getATR error %{public}s', JSON.stringify(error));
}
```

## getReader

```TypeScript
getReader(): Reader
```

获取提供此Session的Reader实例。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Reader](arkts-connectivity-omapi-reader-i.md) | 返回此Session的Reader实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seReaders : omapi.Reader[];
let seSession : omapi.Session;
let reader : omapi.Reader;

// 在使用seReaders之前，需要对seReaders进行初始化
function secureElementDemo() {
    try {
        reader = seReaders[0]; // 将其更改为所选的reader：eSE、SIM、SIM2
        seSession = reader.openSession();
    } catch (error) {
        hilog.error(0x0000, 'testTag', 'openSession error %{public}s', JSON.stringify(error));
    }
    if (seSession == undefined) {
        hilog.error(0x0000, 'testTag', 'seSession invalid.');
        return;
    }
    try {
        let sessionReader = seSession.getReader();
    } catch (error) {
        hilog.error(0x0000, 'testTag', 'getReader error %{public}s', JSON.stringify(error));
    }
}
```

## isClosed

```TypeScript
isClosed(): boolean
```

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if the session is closed, false otherwise. |

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

## openBasicChannel

```TypeScript
openBasicChannel(aid: number[]): Promise<Channel>
```

打开基础通道，参考[ISO 7816-4]协议，返回基础Channel实例对象。SE不能提供基础Channel或应用程序没有访问SE的权限时，返回null。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aid | number[] | 是 | 在此Channel上选择的Applet的AID或如果没有Applet被选择时空的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | 以Promise形式异步返回可用的基础Channel对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-找不到对应se安全单元异常) | NoSuchElementError, the AID on the SE is not available or cannot be selected. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];

// 在使用seSession之前，需要对seSession进行初始化
function secureElementDemo() {
    try {
        // 改为在此channel上选择的App的aid
        seSession.openBasicChannel(aidArray).then((data) => {
            seChannel = data;
        }).catch((error : BusinessError)=> {
            hilog.error(0x0000, 'testTag', 'openBasicChannel error %{public}s', JSON.stringify(error));
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openBasicChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openBasicChannel

```TypeScript
openBasicChannel(aid: number[], callback: AsyncCallback<Channel>): void
```

打开基础通道，参考[ISO 7816-4]协议，返回基础Channel实例对象。SE不能提供基础Channel或应用程序没有访问SE的权限时，返回null。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aid | number[] | 是 | 在此Channel上选择的Applet的AID或如果没有Applet被选择时空的数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | 是 | 以callback形式异步返回可用的基础Channel对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-找不到对应se安全单元异常) | NoSuchElementError, the AID on the SE is not available or cannot be selected. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];

// 在使用seSession之前，需要对seSession进行初始化
function secureElementDemo() {
    try {
        // 改为在此channel上选择的App的aid
        seSession.openBasicChannel(aidArray, (error, data) => {
            if (error) {
                hilog.error(0x0000, 'testTag', 'openBasicChannel error %{public}s', JSON.stringify(error));
            } else {
                seChannel = data;
            }
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openBasicChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openBasicChannel

```TypeScript
openBasicChannel(aid: number[], p2: number): Promise<Channel>
```

打开基础通道，参考[ISO 7816-4]协议，返回基础Channel实例对象。SE不能提供基础Channel或应用程序没有访问SE的权限时，返回null。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aid | number[] | 是 | 在此Channel上选择的Applet的AID或如果没有Applet被选择时空的数组。 |
| p2 | number | 是 | 在该Channel上执行的SELECT APDU的P2参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | 以Promise形式异步返回可用的基础Channel对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-找不到对应se安全单元异常) | NoSuchElementError, the AID on the SE is not available or cannot be selected. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

// 在使用seSession之前，需要对seSession进行初始化
function secureElementDemo() {
    try {
        // 改为在此channel上选择的App的aid
        seSession.openBasicChannel(aidArray, p2).then((data) => {
            seChannel = data;
        }).catch((error : BusinessError)=> {
            hilog.error(0x0000, 'testTag', 'openBasicChannel error %{public}s', JSON.stringify(error));
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openBasicChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openBasicChannel

```TypeScript
openBasicChannel(aid: number[], p2: number, callback: AsyncCallback<Channel>): void
```

打开基础通道，参考[ISO 7816-4]协议，返回基础Channel实例对象。SE不能提供基础Channel或应用程序没有访问SE的权限时，返回null。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aid | number[] | 是 | 在此Channel上选择的Applet的AID或如果没有Applet被选择时空的数组。 |
| p2 | number | 是 | 此Channel上执行SELECT APDU命令的P2参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | 是 | 以callback形式异步返回可用的基础Channel对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-找不到对应se安全单元异常) | NoSuchElementError, the AID on the SE is not available or cannot be selected. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

// 在使用seSession之前，需要对seSession进行初始化
function secureElementDemo() {
    try {
        // 改为在此channel上选择的App的aid
        seSession.openBasicChannel(aidArray, p2, (error, data) => {
            if (error) {
                hilog.error(0x0000, 'testTag', 'openBasicChannel error %{public}s', JSON.stringify(error));
            } else {
                seChannel = data;
            }
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openBasicChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openLogicalChannel

```TypeScript
openLogicalChannel(aid: number[]): Promise<Channel>
```

打开逻辑通道，参考[ISO 7816-4]协议，返回逻辑Channel实例对象。SE不能提供逻辑Channel或应用程序没有访问SE的权限时，返回null。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aid | number[] | 是 | 在此Channel上选择的Applet的AID或如果没有Applet被选择时空的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Promise used to return the logical channel instance obtained. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-找不到对应se安全单元异常) | NoSuchElementError, the AID on the SE is not available or cannot be selected or a logical channel is already open to a non-multi-selectable applet. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];

// 在使用seSession之前，需要对seSession进行初始化
function secureElementDemo() {
    try {
        // 改为在此channel上选择的App的aid
        seSession.openLogicalChannel(aidArray).then((data) => {
            seChannel = data;
        }).catch((error : BusinessError)=> {
            hilog.error(0x0000, 'testTag', 'openLogicalChannel error %{public}s', JSON.stringify(error));
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openLogicalChannel

```TypeScript
openLogicalChannel(aid: number[], callback: AsyncCallback<Channel>): void
```

打开逻辑通道，参考[ISO 7816-4]协议，返回逻辑Channel实例对象。SE不能提供逻辑Channel或应用程序没有访问SE的权限时，返回null。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aid | number[] | 是 | 在此Channel上选择的Applet的AID或如果没有Applet被选择时空的数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | 是 | 以callback形式异步返回可用的逻辑Channel对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-找不到对应se安全单元异常) | NoSuchElementError, the AID on the SE is not available or cannot be selected or a logical channel is already open to a non-multi-selectable applet. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];

// 在使用seSession之前，需要对seSession进行初始化
function secureElementDemo() {
    try {
        // 改为在此channel上选择的App的aid
        seSession.openLogicalChannel(aidArray, (error, data) => {
            if (error) {
                hilog.error(0x0000, 'testTag', 'openLogicalChannel error %{public}s', JSON.stringify(error));
            } else {
                seChannel = data;
            }
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openLogicalChannel

```TypeScript
openLogicalChannel(aid: number[], p2: number): Promise<Channel>
```

打开逻辑通道，参考[ISO 7816-4]协议，返回逻辑Channel实例对象。SE不能提供逻辑Channel或应用程序没有访问SE的权限时，返回null。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aid | number[] | 是 | 在此Channel上选择的Applet的AID或如果没有Applet被选择时空的数组。 |
| p2 | number | 是 | 此Channel上执行SELECT APDU命令的P2参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | 以Promise形式异步返回可用的逻辑Channel实例对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-找不到对应se安全单元异常) | NoSuchElementError, the AID on the SE is not available or cannot be selected or a logical channel is already open to a non-multi-selectable applet. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

// 在使用seSession之前，需要对seSession进行初始化
function secureElementDemo() {
    try {
        // 改为在此channel上选择的App的aid
        seSession.openLogicalChannel(aidArray, p2).then((data) => {
            seChannel = data;
        }).catch((error : BusinessError)=> {
            hilog.error(0x0000, 'testTag', 'openLogicalChannel error %{public}s', JSON.stringify(error));
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openLogicalChannel

```TypeScript
openLogicalChannel(aid: number[], p2: number, callback: AsyncCallback<Channel>): void
```

打开逻辑通道，参考[ISO 7816-4]协议，返回Channel实例对象。SE不能提供逻辑Channel或应用程序没有访问SE的权限时，返回null。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aid | number[] | 是 | 在此Channel上选择的Applet的AID或如果没有Applet被选择时空的数组。 |
| p2 | number | 是 | 此Channel上执行SELECT APDU命令的P2参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | 是 | 以callback形式异步返回可用的逻辑Channel对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-se服务状态异常) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-找不到对应se安全单元异常) | NoSuchElementError, the AID on the SE is not available or cannot be selected or a logical channel is already open to a non-multi-selectable applet. |
| [3300103](../errorcode-se.md#3300103-无法获取访问控制规则异常) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se芯片io异常) | IOError, there is a communication problem to the reader or the SE. |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

// 在使用seSession之前，需要对seSession进行初始化
function secureElementDemo() {
    try {
    // 改为在此channel上选择的App的aid
        seSession.openLogicalChannel(aidArray, p2, (error, data) => {
            if (error) {
                hilog.error(0x0000, 'testTag', 'openLogicalChannel error %{public}s', JSON.stringify(error));
            } else {
                seChannel = data;
            }
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```
