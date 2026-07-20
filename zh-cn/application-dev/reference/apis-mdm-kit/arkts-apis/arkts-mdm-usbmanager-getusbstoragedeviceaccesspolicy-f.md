# getUsbStorageDeviceAccessPolicy

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

<a id="getusbstoragedeviceaccesspolicy"></a>
## getUsbStorageDeviceAccessPolicy

```TypeScript
function getUsbStorageDeviceAccessPolicy(admin: Want): UsbPolicy
```

获取USB存储设备访问策略。

**起始版本：** 12

**需要权限：** 
- API版本26.0.0+：ohos.permission.ENTERPRISE_MANAGE_USB or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS
- API版本12 - 24：ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function getUsbStorageDeviceAccessPolicy(admin: Want): UsbPolicy--><!--Device-usbManager-function getUsbStorageDeviceAccessPolicy(admin: Want): UsbPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UsbPolicy](arkts-mdm-usbmanager-usbpolicy-e.md) | USB存储设备访问策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

