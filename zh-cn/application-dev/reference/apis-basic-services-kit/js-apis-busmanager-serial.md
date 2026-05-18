# @ohos.busManager.serial (串口通信管理)

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块主要提供串口通信管理功能，包括获取串口设备列表、打开和关闭串口、读写数据、硬件流控信号管理等。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

## 导入模块

```ts
import serial from '@ohos.busManager.serial';
```

## serial.getSerialPortList

getSerialPortList(): Promise&lt;[SerialPort](#serialport)[]&gt;

查询串口设备列表，返回[SerialPort](#serialport)对象数组。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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
import serial from '@ohos.busManager.serial';

// 获取串口设备列表
serial.getSerialPortList().then((portList: serial.SerialPort[]) => {
  console.info(`getSerialPortList success, length: ${portList.length}`);
  if (portList.length > 0) {
    let portInfo: serial.SerialPortInfo = portList[0].portInfo;
    console.info(`portName: ${portInfo.portName}`);
  }
}).catch((error: Error) => {
  console.error(`getSerialPortList error: ${JSON.stringify(error)}`);
});
```

## SerialPort

串口对象，提供串口设备的信息和通信能力。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

### 属性

| 名称       | 类型                                       | 只读 | 可选 | 说明         |
| ---------- | ------------------------------------------ | ---- | ---- | ------------ |
| portInfo   | [SerialPortInfo](#serialportinfo)          | 是   | 否   | 串口设备信息。 |

### open

open(config?: [SerialConfigs](#serialconfigs)): Promise&lt;void&gt;

打开串口设备。首次打开时系统会弹窗请求用户授权访问目标串口，用户拒绝则抛出35700007错误码。授权在USB虚拟串口拔出、系统切换用户、整机重启后失效，需重新授权。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**系统能力：**  SystemCapability.BusManager.Serial

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                      | 必填 | 说明                                       |
| ------ | ----------------------------------------- | ---- | ------------------------------------------ |
| config | [SerialConfigs](#serialconfigs)           | 否   | 串口通信参数。默认值参考[SerialConfigs](#serialconfigs)各参数。 |

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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
import serial from '@ohos.busManager.serial';

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
}).catch((error: Error) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```

### close

close(): Promise&lt;void&gt;

关闭串口设备。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

```ts
import serial from '@ohos.busManager.serial';

// 关闭串口
port.close().then(() => {
  console.info('close success');
}).catch((error: Error) => {
  console.error(`close error: ${JSON.stringify(error)}`);
});
```

### write

ArkTS-Dyn: write(data: Uint8Array, timeout?: number): Promise&lt;number&gt;

ArkTS-Sta: write(data: Uint8Array, timeout?: int): Promise&lt;int&gt;

向串口设备发送数据，每次发送数据长度范围：(0, 4096]。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名   | 类型         | 必填 | 说明                                                                                                     |
| -------- | ------------ | ---- | -------------------------------------------------------------------------------------------------------- |
| data     | Uint8Array   | 是   | 待发送的数据。长度范围：(0, 4096]。                                                                        |
| timeout  | ArkTS-Dyn: number<br> ArkTS-Sta: int       | 否   | 超时时间。取值范围：[0, 300000]，整数，单位为毫秒。默认值0表示当数据无法写入端口时，不等待直接返回写入长度0。 |

**返回值：**

| 类型                    | 说明                        |
| ----------------------- | --------------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br> ArkTS-Sta: Promise&lt;int&gt;  | Promise对象，返回写入数据长度。 |

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

```ts
import { buffer } from '@kit.ArkTS';
import serial from '@ohos.busManager.serial';

// 向串口写入数据
let writeData: Uint8Array = new Uint8Array(buffer.from('Hello World', 'utf-8').buffer);
port.write(writeData, 2000).then((size: int) => {
  console.info('write success, size: ' + size);
}).catch((error: Error) => {
  console.error(`write error: ${JSON.stringify(error)}`);
});
```

### onDataRead

onDataRead(callback: Callback&lt;Uint8Array&gt;): void

监听串口接收数据事件。使用callback异步回调返回接收到的数据。调用[close](#close)后，所有回调将被清除。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

```ts
import serial from '@ohos.busManager.serial';

// 监听串口数据接收
port.onDataRead((data: Uint8Array) => {
  console.info(`onDataRead, length: ${data.length}`);
});
```

### offDataRead

offDataRead(callback?: Callback&lt;Uint8Array&gt;): void

取消监听串口接收数据事件。使用callback异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

```ts
import serial from '@ohos.busManager.serial';

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

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

```ts
import serial from '@ohos.busManager.serial';

// 刷新串口缓冲区
port.flush().then(() => {
  console.info('flush success');
}).catch((error: Error) => {
  console.error(`flush error: ${JSON.stringify(error)}`);
});
```

### drain

drain(): Promise&lt;void&gt;

等待所有写请求完成。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

```ts
import serial from '@ohos.busManager.serial';

// 等待所有写请求完成
port.drain().then(() => {
  console.info('drain success');
}).catch((error: Error) => {
  console.error(`drain error: ${JSON.stringify(error)}`);
});
```

### setRts

setRts(enable: boolean): Promise&lt;void&gt;

设置RTS（请求发送）信号状态。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

```ts
import serial from '@ohos.busManager.serial';

// 设置RTS信号
port.setRts(true).then(() => {
  console.info('setRts success');
}).catch((error: Error) => {
  console.error(`setRts error: ${JSON.stringify(error)}`);
});
```

### getCts

getCts(): Promise&lt;boolean&gt;

获取CTS（清除发送）信号状态。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

```ts
import serial from '@ohos.busManager.serial';

// 获取CTS信号状态
port.getCts().then((cts: boolean) => {
  console.info('getCts success, cts: ' + cts);
}).catch((error: Error) => {
  console.error(`getCts error: ${JSON.stringify(error)}`);
});
```

### sendBrk

sendBrk(): Promise&lt;void&gt;

发送BRK（中断）信号。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

```ts
import serial from '@ohos.busManager.serial';

// 发送BRK信号
port.sendBrk().then(() => {
  console.info('sendBrk success');
}).catch((error: Error) => {
  console.error(`sendBrk error: ${JSON.stringify(error)}`);
});
```

## SerialPortInfo

串口设备信息。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

| 名称          | 类型     | 只读 | 可选 | 说明                        |
| ------------- | -------- | ---- | ---- | --------------------------- |
| portName      | string   | 否   | 否   | 端口名称。                  |
| vendorId      | ArkTS-Dyn: number<br> ArkTS-Sta: int   | 否   | 是   | USB虚拟串口的厂商ID。       |
| productId     | ArkTS-Dyn: number<br> ArkTS-Sta: int   | 否   | 是   | USB虚拟串口设备的产品ID。   |
| manufacturer  | string   | 否   | 是   | USB虚拟串口设备的制造商名称。 |

## DataBits

表示数据位的枚举。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

| 名称 | 值 | 说明              |
| ---- | -- | ----------------- |
| ONE  | 1  | 1个停止位。       |
| TWO  | 2  | 2个停止位。       |

## Parity

表示校验位的枚举。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

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

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：**  SystemCapability.BusManager.Serial

| 名称     | 类型                     | 只读 | 可选 | 说明                                                                  |
| -------- | ------------------------ | ---- | ---- | --------------------------------------------------------------------- |
| baudRate | ArkTS-Dyn: number<br> ArkTS-Sta: int                   | 否   | 是   | 波特率。值为正整数，非标准波特率的具体支持情况依赖于硬件。单位：bit/s。默认值：115200。       |
| dataBits | [DataBits](#databits)    | 否   | 是   | 数据位。默认值：EIGHT。                                                |
| stopBits | [StopBits](#stopbits)    | 否   | 是   | 停止位。默认值：ONE。                                                  |
| parity   | [Parity](#parity)        | 否   | 是   | 校验位。默认值：NONE。                                                 |
| rtscts   | boolean                  | 否   | 是   | 是否启用RTS/CTS硬件自动流控。默认值：false。true表示启用，false表示未启用。                                   |
| xon      | boolean                  | 否   | 是   | 是否启用XON控制发送流。默认值：false。true表示启用，false表示未启用。                                  |
| xoff     | boolean                  | 否   | 是   | 是否启用XOFF控制接收流。默认值：false。true表示启用，false表示未启用。                                 |
| xany     | boolean                  | 否   | 是   | 是否启用XANY控制流。默认值：false。true表示启用，false表示未启用。                                     |
