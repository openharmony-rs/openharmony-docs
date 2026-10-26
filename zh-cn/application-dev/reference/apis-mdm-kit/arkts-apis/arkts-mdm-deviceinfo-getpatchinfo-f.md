# getPatchInfo

## 导入模块

```TypeScript
import { deviceInfo } from '@kit.MDMKit';
```

## getPatchInfo

```TypeScript
function getPatchInfo(): Promise<Array<PatchInfo>>
```

获取设备补丁信息。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_GET_DEVICE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceInfo-function getPatchInfo(): Promise<Array<PatchInfo>>--><!--Device-deviceInfo-function getPatchInfo(): Promise<Array<PatchInfo>>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[PatchInfo](arkts-mdm-deviceinfo-patchinfo-i.md)&gt;&gt; | Promise 形式返回补丁信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
