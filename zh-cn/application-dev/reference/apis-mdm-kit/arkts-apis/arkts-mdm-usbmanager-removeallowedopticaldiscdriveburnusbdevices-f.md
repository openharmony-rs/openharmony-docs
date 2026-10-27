# removeAllowedOpticalDiscDriveBurnUsbDevices

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## removeAllowedOpticalDiscDriveBurnUsbDevices

```TypeScript
function removeAllowedOpticalDiscDriveBurnUsbDevices(usbDevices: Array<UsbDevice>): Promise<void>
```

将USB设备从支持CD/DVD刻录的USB设备列表中移除。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function removeAllowedOpticalDiscDriveBurnUsbDevices(usbDevices: Array<UsbDevice>): Promise<void>--><!--Device-usbManager-function removeAllowedOpticalDiscDriveBurnUsbDevices(usbDevices: Array<UsbDevice>): Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| usbDevices | Array&lt;[UsbDevice](arkts-mdm-usbmanager-usbdevice-i.md)&gt; | 是 | 要删除的USB设备类型的数组。<br>最大长度为10000且不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9200019](../errorcode-enterpriseDeviceManager.md#9200019-策略列表超限) | The policy list has exceeded the limit. |

**示例**

```TypeScript
import { usbManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

let usbDevices: Array<usbManager.UsbDevice> = [{
  vendorId: 1234,
  productId: 5678,
  serial: 'SN123456789'
}];
usbManager.removeAllowedOpticalDiscDriveBurnUsbDevices(usbDevices).then(() => {
  console.info('Succeeded in removing allowed optical disc drive burn USB devices.');
}).catch((err: BusinessError) => {
  console.error(`Failed to remove allowed optical disc drive burn USB devices. Code is ${err.code}, message is ${err.message}`);
});
```
