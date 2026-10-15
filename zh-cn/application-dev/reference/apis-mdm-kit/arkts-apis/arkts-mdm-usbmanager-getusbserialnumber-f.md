# getUsbSerialNumber

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## getUsbSerialNumber

```TypeScript
function getUsbSerialNumber(busNum: number, devAddress: number): string
```

获取USB设备的序列号。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function getUsbSerialNumber(busNum: number, devAddress: number): string--><!--Device-usbManager-function getUsbSerialNumber(busNum: number, devAddress: number): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| busNum | number | 是 | USB设备的总线号。 |
| devAddress | number | 是 | USB设备的地址。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | USB设备的序列号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9201055](../errorcode-enterpriseDeviceManager.md#9201055-获取usb设备序列号失败) | Failed to obtain the USB serial number. |

**示例**

```TypeScript
import { usbManager } from '@kit.MDMKit';
import { usbManager as baseUsbManager } from '@kit.BasicServicesKit';

// 获取已接入主设备的USB设备列表
let devicesList: Array<baseUsbManager.USBDevice> = baseUsbManager.getDevices();
console.info(`devicesList = ${devicesList}`);

// 选取目标USB设备（此处以第一个设备为例），取出busNum和devAddress作为入参
let device: baseUsbManager.USBDevice = devicesList[0];

try {
  let result: string = usbManager.getUsbSerialNumber(device.busNum, device.devAddress);
  console.info(`Succeeded in getting USB serial number. Result: ${result}`);
} catch (err) {
  console.error(`Failed to get USB serial number. Code: ${err.code}, message: ${err.message}`);
}
```
