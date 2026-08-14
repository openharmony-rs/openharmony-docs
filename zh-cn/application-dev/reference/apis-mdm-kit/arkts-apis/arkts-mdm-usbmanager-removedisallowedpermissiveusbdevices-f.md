# removeDisallowedPermissiveUsbDevices

## removeDisallowedPermissiveUsbDevices

```TypeScript
function removeDisallowedPermissiveUsbDevices(admin: Want, usbDevices: Array<PermissiveUsbDeviceType>): void
```

移除通过[addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md#addDisallowedPermissiveUsbDevices)接口禁用的USB设备类型。被移除的USB设备类型 可恢复正常使用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function removeDisallowedPermissiveUsbDevices(admin: Want, usbDevices: Array<PermissiveUsbDeviceType>): void--><!--Device-usbManager-function removeDisallowedPermissiveUsbDevices(admin: Want, usbDevices: Array<PermissiveUsbDeviceType>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| usbDevices | Array&lt;[PermissiveUsbDeviceType](arkts-mdm-usbmanager-permissiveusbdevicetype-i.md)&gt; | 是 | 要移除的USB设备类型的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let usbDevices: Array<usbManager.PermissiveUsbDeviceType> = [{
    baseClass: 8
  }];
  usbManager.removeDisallowedPermissiveUsbDevices(wantTemp, usbDevices);
  console.info(`Succeeded in removing disallowed permissive USB devices.`);
} catch (err) {
  console.error(`Failed to remove disallowed permissive USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

