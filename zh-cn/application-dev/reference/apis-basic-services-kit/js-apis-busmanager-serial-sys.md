# @ohos.busManager.serial (串口通信管理)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: BusManager-->
<!--Owner: @hwymlgitcode-->
<!--Designer: @hwymlgitcode-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块主要提供串口通信管理功能，包括获取串口设备列表、打开和关闭串口、读写数据、硬件流控信号管理、权限授权等。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

## 导入模块

```ts
import serial from '@ohos.busManager.serial';
```

## serial.addPortAuthorization

addPortAuthorization(tokenId: string, deviceId: string): Promise&lt;void&gt;

添加应用程序访问串口的权限。仅用于弹出串口授权弹窗的系统应用。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：**  SystemCapability.BusManager.Serial

**参数：**

| 参数名     | 类型     | 必填 | 说明                                                         |
| --------- | -------- | ---- | ------------------------------------------------------------ |
| tokenId   | string   | 是   | 被授权应用的Token ID。                                       |
| deviceId  | string   | 是   | 串口设备ID。板载串口取值为portName；USB虚拟串口取值为VID+PID+SN的组合。 |

**返回值：**

| 类型                | 说明                    |
| ------------------- | ----------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍参见[通用错误码](../errorcode-universal.md)和[串口管理错误码](errorcode-busmanager-serial.md)。

| 错误码ID | 错误信息                                          |
| -------- | ------------------------------------------------- |
| 202      | Permission denied. Called by non-system application. |
| 35700001 | Service error.                                    |
| 35700002 | Invalid parameter.                                |
| 35700008 | Permission denied.                                |

**示例：**

```ts
import serial from '@ohos.busManager.serial';

// 添加串口访问权限（仅系统应用可用）
let tokenId: string = '123456';
let deviceId: string = '/dev/ttyUSB0';
serial.addPortAuthorization(tokenId, deviceId).then(() => {
  console.info('addPortAuthorization success');
}).catch((error: Error) => {
  console.error(`addPortAuthorization error: ${JSON.stringify(error)}`);
});
```
