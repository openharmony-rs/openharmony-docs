# removeDisallowedUsbDevices

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## removeDisallowedUsbDevices

```TypeScript
function removeDisallowedUsbDevices(admin: Want, usbDevices: Array<UsbDeviceType>): void
```

移除禁止使用的USB设备类型。 **使用场景**： - 企业安全管理场景，需要解除对某些USB设备类型的禁用 - 设备管理员需要动态调整禁止使用的USB设备类型列表 - 当某些USB设备类型不再存在安全风险时，从禁用名单中移除

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function removeDisallowedUsbDevices(admin: Want, usbDevices: Array<UsbDeviceType>): void--><!--Device-usbManager-function removeDisallowedUsbDevices(admin: Want, usbDevices: Array<UsbDeviceType>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| usbDevices | Array&lt;[UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md)&gt; | 是 | 要移除的USB设备类型的数组，UsbDeviceType信息可以通过 [getDevices](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md)接口获取。 |

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
  let usbDevices: Array<usbManager.UsbDeviceType> = [{
    baseClass: 8,
    subClass: 0,
    protocol: 0,
    descriptor: usbManager.Descriptor.INTERFACE
  }];
  usbManager.removeDisallowedUsbDevices(wantTemp, usbDevices);
  console.info(`Succeeded in removing disallowed USB devices.`);
} catch (err) {
  console.error(`Failed to remove disallowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

