# @ohos.busManager.serial (串口通信管理)

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块主要提供串口通信管理功能，包括获取串口设备列表、打开和关闭串口、读写数据、硬件流控信号管理等。

**起始版本：** 26.0.0

## 导入模块

```ts
import { serial } from "@kit.BasicServicesKit";
```

## serial.getSerialPortList

getSerialPortList(): Promise&lt;[SerialPort](#serialport)[]&gt;

查询串口设备列表，返回[SerialPort](#serialport)对象数组。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**返回值：**

| 类型                                      | 说明                |
|-----------------------------------------|-------------------|
| Promise&lt;[SerialPort](#serialport)[]&gt; | Promise对象，返回串口设备列表。 |

**错误码：**

以下错误码的详细介绍参见[通用错误码](../errorcode-universal.md)和[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                                         |
| -------- | ------------------------------------------------ |
| 203      | This function is prohibited by enterprise management policies. |
| 35700001 | Service error.                                   |

**示例：**

```ts
// 获取串口设备列表
serial.getSerialPortList().then((portList: serial.SerialPort[]) => {
  console.info(`getSerialPortList success, length: ${portList.length}`);
  if (portList.length > 0) {
    let portInfo: serial.SerialPortInfo = portList[0].portInfo;
    console.info(`portName: ${portInfo.portName}`);
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to get serial port list. Code: ${error.code}, message: ${error.message}`);
});
```

## SerialPort

串口对象，提供串口设备的信息和通信能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

### 属性

| 名称       | 类型                                       | 只读 | 可选 | 说明         |
| ---------- | ------------------------------------------ | ---- | ---- | ------------ |
| portInfo   | [SerialPortInfo](#serialportinfo)          | 是   | 否   | 串口设备信息。 |

### open

open(config?: [SerialConfigs](#serialconfigs)): Promise&lt;void&gt;

打开串口设备。使用Promise异步回调。首次打开时系统会弹窗请求用户授权访问目标串口，用户拒绝则抛出35700007错误码。授权在USB虚拟串口拔出、系统切换用户、整机重启后失效，需重新授权。

**起始版本：** 26.0.0

**系统能力：**  SystemCapability.BusManager.Serial

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                      | 必填 | 说明                                       |
| ------ | ----------------------------------------- | ---- | ------------------------------------------ |
| config | [SerialConfigs](#serialconfigs)           | 否   | 串口通信参数。不传入config参数时，使用SerialConfigs的默认配置打开串口。 |

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回值，用于异步操作。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700002 | Invalid parameter.                |
| 35700003 | Virtual serial port disconnected. |
| 35700004 | Port already in use.              |
| 35700007 | User authorization required.      |

**示例：**

```ts
// 获取串口列表并打开第一个串口
serial.getSerialPortList().then(async (portList: serial.SerialPort[]) => {
  if (portList.length === 0) {
    console.error('portList is empty');
    return;
  }
  let port: serial.SerialPort = portList[0];
  let config: serial.SerialConfigs = {
    baudRate: 115200,
    dataBits: serial.DataBits.EIGHT,
    stopBits: serial.StopBits.ONE,
    parity: serial.Parity.NONE
  };
  await port.open(config);
  console.info('open success');
}).catch((error: BusinessError) => {
  console.error(`Failed to open serial port. Code: ${error.code}, message: ${error.message}`);
});
```

### close

close(): Promise&lt;void&gt;

关闭串口设备。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息             |
| -------- | -------------------- |
| 35700001 | Service error.       |
| 35700005 | Port not open.       |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 关闭串口
port.close().then(() => {
  console.info('close success');
}).catch((error: BusinessError) => {
  console.error(`Failed to close serial port. Code: ${error.code}, message: ${error.message}`);
});
```

### write

write(data: Uint8Array, timeout?: number): Promise&lt;number&gt;

向串口设备发送数据，每次发送数据长度范围：(0, 4096]。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名   | 类型         | 必填 | 说明                                                                                                     |
| -------- | ------------ | ---- | -------------------------------------------------------------------------------------------------------- |
| data     | Uint8Array   | 是   | 待发送的数据。长度范围：(0, 4096]。发送超过4096字节的数据时，建议分多次调用write方法发送。                                                                        |
| timeout  | number       | 否   | 超时时间，取值范围：[0, 300000]，整数，单位为毫秒。默认值0表示当数据无法写入端口时，不等待直接返回写入长度0。传入负数、非整数或大于300000时返回错误码35700002。 |

**返回值：**

| 类型                    | 说明                        |
| ----------------------- | --------------------------- |
| Promise&lt;number&gt;   | Promise对象，返回写入数据长度。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700002 | Invalid parameter.                |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |
| 35700006 | Transmission timeout.             |

**示例：**

<!--code_no_check-->
```ts
import { buffer } from '@kit.ArkTS';
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 向串口写入数据
let writeData: Uint8Array = new Uint8Array(buffer.from('Hello World', 'utf-8').buffer);
port.write(writeData, 2000).then((size: number) => {
  console.info('write success, size: ' + size);
}).catch((error: BusinessError) => {
  console.error(`Failed to write to serial port. Code: ${error.code}, message: ${error.message}`);
});
```

### onDataRead

onDataRead(callback: Callback&lt;Uint8Array&gt;): void

监听串口接收数据事件。使用callback异步回调返回接收到的数据。调用[close](#close)后，所有回调将被清除。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名   | 类型                       | 必填 | 说明                             |
| -------- | -------------------------- | ---- | -------------------------------- |
| callback | Callback&lt;Uint8Array&gt; | 是   | 回调函数，返回串口接收到的数据。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 监听串口数据接收
port.onDataRead((data: Uint8Array) => {
  console.info(`onDataRead, length: ${data.length}`);
});
```

### offDataRead

offDataRead(callback?: Callback&lt;Uint8Array&gt;): void

取消监听串口接收数据事件。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名   | 类型                       | 必填 | 说明                                                   |
| -------- | -------------------------- | ---- | ------------------------------------------------------ |
| callback | Callback&lt;Uint8Array&gt; | 否   | 回调函数。不传入callback时，清除所有串口数据接收监听。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息             |
| -------- | -------------------- |
| 35700001 | Service error.       |
| 35700005 | Port not open.       |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 取消监听串口数据接收
port.offDataRead();

// 取消指定的监听回调
let callback = (data: Uint8Array) => {
  console.info(`received data length: ${data.length}`);
};
port.offDataRead(callback);
```

### flush

flush(): Promise&lt;void&gt;

清空串口缓冲区，包括读缓冲区和写缓冲区，缓冲区中的数据将被直接丢弃，不再发送或读取。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 刷新串口缓冲区
port.flush().then(() => {
  console.info('flush success');
}).catch((error: BusinessError) => {
  console.error(`Failed to flush serial port. Code: ${error.code}, message: ${error.message}`);
});
```

### drain

drain(): Promise&lt;void&gt;

等待所有写请求完成。使用Promise异步回调。需在串口打开后调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 等待所有写请求完成
port.drain().then(() => {
  console.info('drain success');
}).catch((error: BusinessError) => {
  console.error(`Failed to drain serial port. Code: ${error.code}, message: ${error.message}`);
});
```

### setRts

setRts(enable: boolean): Promise&lt;void&gt;

设置RTS（请求发送）信号状态。使用Promise异步回调。需在串口打开后调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型     | 必填 | 说明                                       |
| ------ | -------- | ---- | ------------------------------------------ |
| enable | boolean  | 是   | RTS信号状态，true表示请求发送数据，false表示不请求发送数据。 |

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 设置RTS信号
port.setRts(true).then(() => {
  console.info('setRts success');
}).catch((error: BusinessError) => {
  console.error(`Failed to set RTS. Code: ${error.code}, message: ${error.message}`);
});
```

### getCts

getCts(): Promise&lt;boolean&gt;

获取CTS（清除发送）信号状态。使用Promise异步回调。需在串口打开后调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**返回值：**

| 类型                     | 说明                                             |
| ------------------------ | ------------------------------------------------ |
| Promise&lt;boolean&gt;   | Promise对象，返回CTS信号状态，返回true表示可以发送数据，返回false表示不可以发送数据。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 获取CTS信号状态
port.getCts().then((cts: boolean) => {
  console.info('getCts success, cts: ' + cts);
}).catch((error: BusinessError) => {
  console.error(`Failed to get CTS. Code: ${error.code}, message: ${error.message}`);
});
```

### sendBrk

sendBrk(): Promise&lt;void&gt;

发送BRK（中断）信号。使用Promise异步回调。需在串口打开后调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回值。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 发送BRK信号
port.sendBrk().then(() => {
  console.info('sendBrk success');
}).catch((error: BusinessError) => {
  console.error(`Failed to send BRK. Code: ${error.code}, message: ${error.message}`);
});
```

### setDtr

setDtr(enable: boolean): Promise&lt;void&gt;

设置DTR（数据终端就绪）信号状态。使用Promise异步回调。需在串口打开后调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型     | 必填 | 说明                                       |
| ------ | -------- | ---- | ------------------------------------------ |
| enable | boolean  | 是   | DTR信号状态，true表示数据终端就绪；false表示数据终端未就绪。 |

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回值，用于异步操作。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 设置DTR信号
port.setDtr(true).then(() => {
  console.info('setDtr success');
}).catch((error: BusinessError) => {
  console.error(`Failed to set DTR. Code: ${error.code}, message: ${error.message}`);
});
```

### getDsr

getDsr(): Promise&lt;boolean&gt;

获取DSR（数据设备就绪）信号状态。使用Promise异步回调。需在串口打开后调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**返回值：**

| 类型                     | 说明                                             |
| ------------------------ | ------------------------------------------------ |
| Promise&lt;boolean&gt;   | Promise对象，返回DSR信号状态；true表示数据设备就绪；false表示数据设备未就绪。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 35700001 | Service error.                    |
| 35700003 | Virtual serial port disconnected. |
| 35700005 | Port not open.                    |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 获取DSR信号状态
port.getDsr().then((dsr: boolean) => {
  console.info('getDsr success, dsr: ' + dsr);
}).catch((error: BusinessError) => {
  console.error(`Failed to get DSR. Code: ${error.code}, message: ${error.message}`);
});
```

### onDisconnect

onDisconnect(callback: Callback&lt;void&gt;): void

监听串口断开事件。使用callback异步回调。调用close后，所有回调将被清除。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名   | 类型                  | 必填 | 说明                             |
| -------- | --------------------- | ---- | -------------------------------- |
| callback | Callback&lt;void&gt;  | 是   | 回调函数，串口断开时触发。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息             |
| -------- | -------------------- |
| 35700001 | Service error.       |
| 35700005 | Port not open.       |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 监听串口断开事件
port.onDisconnect(() => {
  console.info('serial port disconnected');
});
```

### offDisconnect

offDisconnect(callback?: Callback&lt;void&gt;): void

取消监听串口断开事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名   | 类型                  | 必填 | 说明                                                   |
| -------- | --------------------- | ---- | ------------------------------------------------------ |
| callback | Callback&lt;void&gt;  | 否   | 回调函数。不传入callback时，清除所有串口断开事件监听。 |

**错误码：**

以下错误码的详细介绍参见[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息             |
| -------- | -------------------- |
| 35700001 | Service error.       |
| 35700005 | Port not open.       |

**示例：**

<!--code_no_check-->
```ts
// port为串口对象，需要先通过serial.getSerialPortList()获取
// 取消监听串口断开事件
port.offDisconnect();

// 取消指定的监听回调
let disconnectedCallback = () => {
  console.info('serial port disconnected');
};
port.offDisconnect(disconnectedCallback);
```

## SerialPortInfo

串口设备信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

| 名称          | 类型     | 只读 | 可选 | 说明                        |
| ------------- | -------- | ---- | ---- | --------------------------- |
| portName      | string   | 否   | 否   | 端口名称。                  |
| vendorId      | number   | 否   | 是   | USB虚拟串口的厂商ID。       |
| productId     | number   | 否   | 是   | USB虚拟串口设备的产品ID。   |
| manufacturer  | string   | 否   | 是   | USB虚拟串口设备的制造商名称。 |

## DataBits

表示数据位的枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

| 名称   | 值 | 说明              |
| ------ | -- | ----------------- |
| FIVE   | 5  | 5个数据位。       |
| SIX    | 6  | 6个数据位。       |
| SEVEN  | 7  | 7个数据位。       |
| EIGHT  | 8  | 8个数据位。       |

## StopBits

表示停止位的枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

| 名称 | 值 | 说明              |
| ---- | -- | ----------------- |
| ONE  | 1  | 1个停止位。       |
| TWO  | 2  | 2个停止位。       |

## Parity

表示校验位的枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

| 名称  | 值       | 说明                    |
| ----- | -------- | ----------------------- |
| NONE  | 'none'   | 无校验。                |
| EVEN  | 'even'   | 偶校验。                |
| ODD   | 'odd'    | 奇校验。                |
| MARK  | 'mark'   | 标记校验，校验位始终为1。 |
| SPACE | 'space'  | 空格校验，校验位始终为0。 |

## SerialConfigs

串口通信配置参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

| 名称     | 类型                     | 只读 | 可选 | 说明                                                                  |
| -------- | ------------------------ | ---- | ---- | --------------------------------------------------------------------- |
| baudRate | number                   | 否   | 是   | 波特率。值为正整数，非标准波特率的具体支持情况依赖于硬件。单位：bit/s。默认值：115200。       |
| dataBits | [DataBits](#databits) | 否 | 是   | 数据位。默认值：EIGHT（8数据位，标准通信）。FIVE/SIX/SEVEN用于老旧设备或特殊协议。 |
| stopBits | [StopBits](#stopbits)    | 否   | 是   | 停止位。默认值：ONE。                                                  |
| parity | [Parity](#parity) | 否 | 是   | 校验位。默认值：NONE（无校验）。EVEN/ODD用于数据准确性要求高的场景；MARK/SPACE用于特殊通信协议。 |
| rtscts   | boolean                  | 否   | 是   | 是否启用RTS/CTS硬件自动流控。RTS/CTS硬件流控是一种通过硬件信号实现的自动数据流控制机制，RTS和CTS信号线协同工作以防止缓冲区溢出。启用后，系统会自动控制RTS和CTS信号来管理数据流量。默认值：false。true表示启用，false表示未启用。                                   |
| xon      | boolean                  | 否   | 是   | 是否启用XON控制发送流。XON是软件流控协议中的一个控制字符（ASCII值为17），当接收端缓冲区有空间时发送XON字符通知发送端恢复发送数据。默认值：false。true表示启用，false表示未启用。                                  |
| xoff     | boolean                  | 否   | 是   | 是否启用XOFF控制接收流。XOFF是软件流控协议中的一个控制字符（ASCII值为19），当接收端缓冲区即将溢出时发送XOFF字符通知发送端暂停发送数据。默认值：false。true表示启用，false表示未启用。                                 |
| xany     | boolean                  | 否   | 是   | 是否启用XANY控制流。XANY是软件流控协议中的一种扩展模式，当启用XANY时，任何字符都可以作为恢复发送的信号，而不仅仅是XON字符。默认值：false。true表示启用，false表示未启用。                                     |
