# getDisallowedPermissiveUsbDevices

## getDisallowedPermissiveUsbDevices

```TypeScript
function getDisallowedPermissiveUsbDevices(admin: Want | null): Array<PermissiveUsbDeviceType>
```

获取通过[addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md#addDisallowedPermissiveUsbDevices)接口禁用的USB设备类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function getDisallowedPermissiveUsbDevices(admin: Want | null): Array<PermissiveUsbDeviceType>--><!--Device-usbManager-function getDisallowedPermissiveUsbDevices(admin: Want | null): Array<PermissiveUsbDeviceType>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。当取值为null时，表示获取当前设备禁止使用的 USB设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[PermissiveUsbDeviceType](arkts-mdm-usbmanager-permissiveusbdevicetype-i.md)&gt; | 禁止使用的USB设备类型数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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
  let result: Array<usbManager.PermissiveUsbDeviceType> = usbManager.getDisallowedPermissiveUsbDevices(wantTemp);
  console.info(`Succeeded in getting disallowed permissive USB devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed permissive USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

