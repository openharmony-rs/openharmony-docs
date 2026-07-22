# SerialPort

串口对象，提供串口设备信息和通信相关能力

**起始版本：** 26.0.0

<!--Device-serial-interface SerialPort--><!--Device-serial-interface SerialPort-End-->

**系统能力：** SystemCapability.BusManager.Serial

## 导入模块

```TypeScript
import { serial } from '@kit.BasicServicesKit';
```

## close

```TypeScript
close(): Promise<void>
```

关闭串口。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-close(): Promise<void>--><!--Device-SerialPort-close(): Promise<void>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## drain

```TypeScript
drain(): Promise<void>
```

等待所有写入请求完成。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-drain(): Promise<void>--><!--Device-SerialPort-drain(): Promise<void>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## flush

```TypeScript
flush(): Promise<void>
```

flush串口缓冲区。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-flush(): Promise<void>--><!--Device-SerialPort-flush(): Promise<void>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## getCts

```TypeScript
getCts(): Promise<boolean>
```

获取cts信号状态。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-getCts(): Promise<boolean>--><!--Device-SerialPort-getCts(): Promise<boolean>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise对象，返回CTS信号状态，表示是否允许发送数据 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## getDsr

```TypeScript
getDsr(): Promise<boolean>
```

获取DSR信号状态，使用Promise异步返回

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-getDsr(): Promise<boolean>--><!--Device-SerialPort-getDsr(): Promise<boolean>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | DSR信号状态，true表示对端已就绪，false表示对端未就绪 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## offDataRead

```TypeScript
offDataRead(callback?: Callback<Uint8Array>): void
```

取消监听串口端口接收数据事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-offDataRead(callback?: Callback<Uint8Array>): void--><!--Device-SerialPort-offDataRead(callback?: Callback<Uint8Array>): void-End-->

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Uint8Array&gt; | 否 | 回调函数，返回串口端口接收到的数据<br>默认值:缺省行为：清除串口端口接收数据事件的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## offDisconnect

```TypeScript
offDisconnect(callback?: Callback<void>): void
```

取消监听USB虚拟串口断开事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-offDisconnect(callback?: Callback<void>): void--><!--Device-SerialPort-offDisconnect(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | USB虚拟串口断开的回调函数。<br>默认值：清除所有USB虚拟串口断开事件的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## onDataRead

```TypeScript
onDataRead(callback: Callback<Uint8Array>): void
```

监听串口端口接收到的数据。使用Callback异步回调。调用{@link close}接口时，会清理全部回调

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-onDataRead(callback: Callback<Uint8Array>): void--><!--Device-SerialPort-onDataRead(callback: Callback<Uint8Array>): void-End-->

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Uint8Array&gt; | 是 | 回调函数，返回串口端口接收到的数据 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## onDisconnect

```TypeScript
onDisconnect(callback: Callback<void>): void
```

监听USB虚拟串口断开事件。使用Callback异步回调。调用{@link close}接口时，会清理全部回调

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-onDisconnect(callback: Callback<void>): void--><!--Device-SerialPort-onDisconnect(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | USB虚拟串口断开事件的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## open

```TypeScript
open(config?: SerialConfigs): Promise<void>
```

打开端口。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-open(config?: SerialConfigs): Promise<void>--><!--Device-SerialPort-open(config?: SerialConfigs): Promise<void>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [SerialConfigs](arkts-basicservices-serial-serialconfigs-i.md) | 否 | 串口通信参数<br>默认值:默认值：参考SerialConfigs的默认值。<br>Default value: Refer to the default value of SerialConfigs.. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700002](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700002-参数错误) | Invalid parameter. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700004](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700004-端口已被占用) | Port already in use. |
| [35700007](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700007-需要用户授权) | User authorization required. |

## sendBrk

```TypeScript
sendBrk(): Promise<void>
```

发送brk信号。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-sendBrk(): Promise<void>--><!--Device-SerialPort-sendBrk(): Promise<void>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## setDtr

```TypeScript
setDtr(enable: boolean): Promise<void>
```

设置DTR信号状态，使用Promise异步返回

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-setDtr(enable: boolean): Promise<void>--><!--Device-SerialPort-setDtr(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | DTR信号状态，表示本端是否就绪。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## setRts

```TypeScript
setRts(enable: boolean): Promise<void>
```

设置rts信号。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-setRts(enable: boolean): Promise<void>--><!--Device-SerialPort-setRts(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | RTS信号状态，表示是否请求发送。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise对象，无返回结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |

## write

```TypeScript
write(data: Uint8Array, timeout?: number): Promise<number>
```

发送数据。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-write(data: Uint8Array, timeout?: int): Promise<int>--><!--Device-SerialPort-write(data: Uint8Array, timeout?: int): Promise<int>-End-->

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Uint8Array | 是 | 要发送的数据<br>长度范围:(0,4096]。 |
| timeout | number | 否 | 超时时间<br>长度范围:[0,300000]。取值限定为整数。单位:毫秒。默认值:0。<br>表示端口无法写入数据时不等待，直接返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | - Promise对象，返回成功写入的长度 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700001-服务异常) | Service error. |
| [35700002](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700002-参数错误) | Invalid parameter. |
| [35700003](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700003-虚拟串口断开) | Virtual serial port disconnected. |
| [35700005](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700005-端口未打开) | Port not open. |
| [35700006](../../apis-basic-services-kit/errorcode-busmanager-serial.md#35700006-传输超时) | Transmission timeout. |

## portInfo

```TypeScript
readonly portInfo: SerialPortInfo
```

串口端口信息

**类型：** SerialPortInfo

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SerialPort-readonly portInfo: SerialPortInfo--><!--Device-SerialPort-readonly portInfo: SerialPortInfo-End-->

**系统能力：** SystemCapability.BusManager.Serial

