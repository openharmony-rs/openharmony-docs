# getAllowedUsbDevices

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## getAllowedUsbDevices

```TypeScript
function getAllowedUsbDevices(admin: Want): Array<UsbDeviceId>
```

获取USB设备可用名单。一般使用场景：在修改策略前，需要先获取现有策略进行评估；管理界面需要展示当前的USB存储设备访问控制状态。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function getAllowedUsbDevices(admin: Want): Array<UsbDeviceId>--><!--Device-usbManager-function getAllowedUsbDevices(admin: Want): Array<UsbDeviceId>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[UsbDeviceId](arkts-mdm-usbmanager-usbdeviceid-i.md)&gt; | USB设备可用名单的设备ID数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: Array<usbManager.UsbDeviceId> = usbManager.getAllowedUsbDevices(wantTemp);
  console.info(`Succeeded in getting allowed USB devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```


## getAllowedUsbDevices

```TypeScript
function getAllowedUsbDevices(admin: Want | null): Array<UsbDeviceId>
```

获取USB设备可用名单。一般使用场景：在修改策略前，需要先获取现有策略进行评估；管理界面需要展示当前的USB存储设备访问控制状态。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function getAllowedUsbDevices(admin: Want | null): Array<UsbDeviceId>--><!--Device-usbManager-function getAllowedUsbDevices(admin: Want | null): Array<UsbDeviceId>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[UsbDeviceId](arkts-mdm-usbmanager-usbdeviceid-i.md)&gt; | USB设备可用名单的设备ID数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { usbManager } from '@kit.MDMKit';

try {
  // 参数需根据实际情况进行替换
  let result: Array<usbManager.UsbDeviceId> = usbManager.getAllowedUsbDevices(null);
  console.info(`Succeeded in getting allowed USB devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

