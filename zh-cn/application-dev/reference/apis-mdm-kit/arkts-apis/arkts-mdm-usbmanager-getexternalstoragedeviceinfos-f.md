# getExternalStorageDeviceInfos

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## getExternalStorageDeviceInfos

```TypeScript
function getExternalStorageDeviceInfos(): Array<common.ExternalStorageDeviceInfo>
```

获取当前设备的卷信息。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function getExternalStorageDeviceInfos(): Array<common.ExternalStorageDeviceInfo>--><!--Device-usbManager-function getExternalStorageDeviceInfos(): Array<common.ExternalStorageDeviceInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[common.ExternalStorageDeviceInfo](arkts-mdm-common-externalstoragedeviceinfo-i.md)&gt; | Array of device disk information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
