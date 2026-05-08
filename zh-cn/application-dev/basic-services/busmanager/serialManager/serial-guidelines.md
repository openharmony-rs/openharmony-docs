# 串口通信开发指导

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

## 简介

串口通信模块（`@ohos.busManager.serial`）提供面向对象的串口管理能力，支持获取设备可用串口列表、打开/关闭串口、数据读写、硬件信号控制以及流控配置等功能。该模块适用于工业自动化、物联网设备互联、嵌入式设备调试、GPS模块通信等需要通过串口进行数据交换的场景。

## 基本概念

在进行串口通信开发时，开发者应了解以下基本概念：

- **串口**

  即串行接口或串行通信接口，是采用串行通信方式的扩展接口。串行接口中数据是一位一位地顺序传送。串口特点是通信线路简单，只要一对传输线就可以实现双向通信，适用于远距离通信。

- **波特率（Baud Rate）**

  表示每秒钟传送的比特数，是衡量串口通信速率的指标。常用波特率有9600、19200、38400、57600、115200等。通信双方必须使用相同的波特率才能正确收发数据。

- **数据位（Data Bits）**

  表示通信中实际数据位的位数，通常可设置为5、6、7或8位。最常用的数据位长度为8位。

- **校验位（Parity）**

  用于检验数据传输正确性的位。支持无校验（NONE）、奇校验（ODD）、偶校验（EVEN）、标记校验（MARK）和空格校验（SPACE）等模式。

- **停止位（Stop Bits）**

  用于标识一个数据包的结束，可设置为1位或2位。最常用的停止位长度为1位。

- **流控（Flow Control）**

  用于控制数据传输速率，防止数据丢失。常见的流控方式包括硬件流控（RTS/CTS）和软件流控（XON/XOFF）。

## 实现原理

串口通信服务的核心流程如下：

1. **获取串口列表**：系统枚举当前可用的串口设备，返回串口对象列表。
2. **打开串口**：选择目标串口，配置波特率、数据位、校验位、停止位等通信参数并打开。首次打开时系统会弹窗请求用户授权，用户同意后方可访问串口设备；用户拒绝则接口抛出35700007错误码。
3. **数据收发**：通过写入接口发送数据，通过注册数据回调监听接收数据。
4. **硬件信号控制**：通过RTS/CTS等信号线进行硬件流控和状态检测。
5. **关闭串口**：通信结束后关闭串口，释放资源。

**图1** 串口通信数据流

```
应用层写入数据 → 串口驱动发送 → 物理串口线 → 对端串口设备
                                                          ↓
应用层读取数据 ← 串口驱动缓冲 ← 物理串口线 ← 对端串口设备
```

## 约束和限制

- 使用串口通信功能前，需要确保设备已正确连接串口硬件。
- 写入数据长度范围为(0, 4096]字节。
- 若开发者未主动设置配置参数，则使用默认配置参数（波特率：115200bps，数据位：8，停止位：1，校验位：无，硬件流控：关闭，软件流控：关闭）。
- 同一串口同一时间只能被一个应用打开。
- 用户授权在以下场景下会失效，再次访问串口需重新授权：USB虚拟串口拔出、系统切换用户、整机重启。

## 环境准备

### 环境要求

- **开发工具及配置**：

  DevEco Studio作为开发工具，是进行串口通信开发必备条件之一，开发者可以使用该工具进行开发、调试、打包等操作。请[下载安装](https://developer.huawei.com/consumer/cn/download/)该工具，并参考[DevEco Studio使用指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-tools-overview)中的[创建工程及运行](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-create-new-project)进行基本的操作验证，保证DevEco Studio可正常运行。

- **SDK版本配置**：

  本模块提供的ArkTS接口，所需SDK版本为API 26.0.0及以上才可使用。

### 搭建环境

- 在PC上安装[DevEco Studio](https://developer.huawei.com/consumer/cn/download/deveco-studio)，要求版本在6.1及以上。
- 将public-SDK更新到API 26.0.0或以上<!--Del-->，更新SDK的具体操作可参见[更新指南](../../../tools/openharmony_sdk_upgrade_assistant.md)<!--DelEnd-->。
- 准备串口连接线缆，将OpenHarmony设备的串口端口与目标设备的串口正确连接。

## 开发指导

### 接口说明

串口通信主要接口如下表所示。

| 接口名 | 描述 |
|--------|------|
| [SerialPort.getSerialPortList](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialgetserialportlist)(): Promise&lt;[SerialPort](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialport)[]&gt; | 查询串口设备列表，返回[SerialPort](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialport)对象数组。使用Promise异步回调。 |
| [SerialPort.open](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#open)(config?: [SerialConfigs](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialconfigs)): Promise&lt;void&gt; | 打开串口设备。首次打开时系统会弹窗请求用户授权访问目标串口，用户拒绝则抛出35700007错误码。授权在USB虚拟串口拔出、系统切换用户、整机重启后失效，需重新授权。使用Promise异步回调。 |
| [SerialPort.close](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#close)(): Promise&lt;void&gt; | 关闭串口设备。使用Promise异步回调。 |
| [SerialPort.write](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#write)(data: Uint8Array, timeout?: number): Promise&lt;number&gt; | 向串口设备发送数据，每次发送数据长度范围：(0, 4096]。使用Promise异步回调。 |
| [SerialPort.onDataRead](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#ondataread)(callback: Callback&lt;Uint8Array&gt;): void | 监听串口接收数据事件。使用callback异步回调返回接收到的数据。调用[close](#close)后，所有回调将被清除。 |
| [SerialPort.offDataRead](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#offdataread)(callback?: Callback&lt;Uint8Array&gt;): void | 取消监听串口接收数据事件。使用callback异步回调。 |
| [SerialPort.flush](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#flush)(): Promise&lt;void&gt; | 清空串口缓冲区，包括读缓冲区和写缓冲区，缓冲区中的数据将被直接丢弃，不再发送或读取。使用Promise异步回调。 |
| [SerialPort.drain](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#drain)(): Promise&lt;void&gt; | 等待所有写请求完成。使用Promise异步回调。 |
| [SerialPort.setRts](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#setrts)(enable: boolean): Promise&lt;void&gt; | 设置RTS（请求发送）信号状态。使用Promise异步回调。 |
| [SerialPort.getCts](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#getcts)(): Promise&lt;boolean&gt; |  获取CTS（清除发送）信号状态。使用Promise异步回调。 |
| [SerialPort.sendBrk](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#sendbrk)(): Promise&lt;void&gt; | 发送BRK（中断）信号。使用Promise异步回调。 |

[SerialConfigs](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#serialconfigs)配置参数说明：

| 参数名 | 类型 | 必填 | 默认值 | 描述 |
|--------|------|------|--------|------|
| baudRate | number | 否 | 115200 | 波特率。 |
| dataBits | [DataBits](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#databits) | 否 | DataBits.EIGHT | 数据位。 |
| stopBits | [StopBits](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#stopbits) | 否 | StopBits.ONE | 停止位。 |
| parity | [Parity](../../../reference/apis-basic-services-kit/js-apis-busmanager-serial.md#parity) | 否 | Parity.NONE | 校验位。 |
| rtscts | boolean | 否 | false | 检查是否启用RTS/CTS硬件自动流控。true表示启用，false表示未启用。 |
| xon | boolean | 否 | false | 检查是否启用XON软件流控。true表示启用，false表示未启用。 |
| xoff | boolean | 否 | false | 检查是否启用XOFF软件流控。true表示启用，false表示未启用。 |
| xany | boolean | 否 | false | 检查是否启用任意字符重启软件流控。true表示启用，false表示未启用。 |

### 开发步骤

> **说明：**
>
> 以下示例代码只是串口通信的必要流程，需要放入具体的方法中执行。

1. 导入模块。

   <!-- @[head](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // 导入串口通信模块
   import { serial, BusinessError } from "@kit.BasicServicesKit";
   ```

2. 获取串口设备列表。

   <!-- @[getSerialPortList](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // 获取可用串口设备列表
   try {
     let ports: serial.SerialPort[] = await serial.getSerialPortList();
     console.info('Serial port list: ' + JSON.stringify(ports));
     if (ports === undefined || ports.length === 0) {
       console.error('No serial port available');
       return;
     }
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to get serial port list: ${JSON.stringify(e)}`)
   }
   ```

3. 打开串口设备。

   <!-- @[open](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // 使用默认配置打开串口
   let port: serial.SerialPort = ports[0];
   try {
   await port.open();
   console.info('Open serial port success');
   } catch (error) {
   let e = error as BusinessError;
   console.error(`Failed to open serial port: ${JSON.stringify(e)}`)
   return;
   }

   // 也可指定配置参数打开串口
   try {
     await port.open({
       baudRate: 115200,
       dataBits: serial.DataBits.EIGHT,
       stopBits: serial.StopBits.ONE,
       parity: serial.Parity.NONE,
       rtscts: false
     });
     console.info('Open serial port with config success');
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to open serial port: ${JSON.stringify(e)}`);
   }
   ```

4. 注册数据接收回调，监听串口数据。

   <!-- @[onDataRead](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // 注册数据接收回调，当串口收到数据时会触发该回调
   port.onDataRead((data: Uint8Array) => {
     console.info(`Received data length: ${data.length}`);
     console.info(`Received data: ${Array.from(data).map(b => b.toString(16).padStart(2, '0')).join(' ')}`);

   });
   ```

5. 通过串口写入数据。

   <!-- @[write](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // 向串口写入数据
   try {
     let writeData: Uint8Array = new Uint8Array([0x01, 0x02, 0x03, 0x04, 0x05]);
     let writeLen: number = await port.write(writeData, 1000);
     console.info('Write success, length: ' + writeLen);
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to write data: ${JSON.stringify(e)}`);
   }
   ```

6. 刷新缓冲区与等待发送完成。

   <!-- @[flush](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
    // 清空串口缓冲区（包括读缓冲区和写缓冲区），缓冲区中的数据将被直接丢弃
   try {
     await port.flush();
     console.info('Flush success');
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to flush: ${JSON.stringify(e)}`);
   }

   // 等待所有已写入数据发送完成
   try {
     await port.drain();
     console.info('Drain success');
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to drain: ${JSON.stringify(e)}`);
   }
   ```

7. 硬件信号控制。

   <!-- @[setRts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // 设置RTS信号为高电平
   try {
     await port.setRts(true);
     console.info('Set RTS success');
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to set RTS: ${JSON.stringify(e)}`);
   }
   ```

   <!-- @[getCts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // 获取CTS信号状态
   try {
     let cts: boolean = await port.getCts();
     console.info('CTS signal status: ' + cts);
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to get CTS: ${JSON.stringify(e)}`);
   }
   ```

   <!-- @[sendBrk](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript

   // 发送break信号
   try {
     await port.sendBrk();
     console.info('Send break signal success');
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to send break: ${JSON.stringify(e)}`);
   }
   ```

8. 注销数据接收回调和关闭串口设备。

   <!-- @[close](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Serial/SerialManagerSample/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // 注销数据接收回调
   port.offDataRead();

   // 关闭串口设备
   try {
     await port.close();
     console.info('Close serial port success');
   } catch (error) {
     let e = error as BusinessError;
     console.error(`Failed to close serial port: ${JSON.stringify(e)}`);
   }
   ```

### 调测验证

1. 准备串口连接线缆，将OpenHarmony设备的串口端口与目标设备的串口正确连接。
2. 在OpenHarmony设备上执行上述示例代码。
3. 返回`success`日志，表示相关接口调用成功，设备串口通信能力正常；返回`Failed`或`error`日志，表示接口调用失败，请检查硬件连接和配置参数。
4. 可通过回环测试（将串口的TX和RX短接）验证数据的自发自收功能是否正常。
