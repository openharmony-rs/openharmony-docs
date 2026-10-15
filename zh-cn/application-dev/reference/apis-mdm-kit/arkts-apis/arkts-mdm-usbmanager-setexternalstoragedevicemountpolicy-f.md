# setExternalStorageDeviceMountPolicy

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## setExternalStorageDeviceMountPolicy

```TypeScript
function setExternalStorageDeviceMountPolicy(volumeId: string, policy: MountPolicy): void
```

设置外部存储设备的挂载策略。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function setExternalStorageDeviceMountPolicy(volumeId: string, policy: MountPolicy): void--><!--Device-usbManager-function setExternalStorageDeviceMountPolicy(volumeId: string, policy: MountPolicy): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeId | string | 是 | 卷ID。 |
| policy | [MountPolicy](arkts-mdm-usbmanager-mountpolicy-e.md) | 是 | 挂载策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| 9201056 | Invalid external storage mount policy. |
