# getAllowedOpticalDiscDriveBurnUsbDevices

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## getAllowedOpticalDiscDriveBurnUsbDevices

```TypeScript
function getAllowedOpticalDiscDriveBurnUsbDevices(queryPolicy?: common.QueryPolicy): Promise<Array<UsbDevice>>
```

获取支持CD/DVD刻录的USB设备列表。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function getAllowedOpticalDiscDriveBurnUsbDevices(queryPolicy?: common.QueryPolicy): Promise<Array<UsbDevice>>--><!--Device-usbManager-function getAllowedOpticalDiscDriveBurnUsbDevices(queryPolicy?: common.QueryPolicy): Promise<Array<UsbDevice>>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryPolicy | [common.QueryPolicy](arkts-mdm-common-querypolicy-e.md) | 否 | queryPolicy表示查询的策略。<br>默认值：common.QueryPolicy.SELF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[UsbDevice](arkts-mdm-usbmanager-usbdevice-i.md)&gt;&gt; | 允许的USB设备数组，使用Promise异步回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |

**示例**

```TypeScript
import { usbManager, common } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

usbManager.getAllowedOpticalDiscDriveBurnUsbDevices(common.QueryPolicy.SELF).then((result: Array<usbManager.UsbDevice>) => {
  console.info(`Succeeded in getting allowed optical disc drive burn USB devices. Result: ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get allowed optical disc drive burn USB devices. Code is ${err.code}, message is ${err.message}`);
});
```
