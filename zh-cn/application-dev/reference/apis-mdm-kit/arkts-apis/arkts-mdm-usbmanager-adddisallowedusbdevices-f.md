# addDisallowedUsbDevices

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## addDisallowedUsbDevices

```TypeScript
function addDisallowedUsbDevices(admin: Want, usbDevices: Array<UsbDeviceType>): void
```

添加禁止使用的USB设备类型。 **使用场景**： - 企业安全管理场景，需要禁用特定类型的USB设备 - 防止数据泄露：禁用USB存储设备类型 - 设备管理员需要根据安全策略，禁止使用某些类型的USB设备 - 配合[removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md)接口实现USB设备类型的动态管理 > **说明：** > > 推荐使用[addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md)接口。 > 以下情况下，调用本接口会报策略冲突： 1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)接口禁用了设备USB能力。 2. 已经通过[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md)接口添加了USB设备可用名单。 3. 已经通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md)接口禁用了某用户USB存储设备写入能力。 4. 已经通过[addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md)接口添加了禁止使用的USB设备类型。

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function addDisallowedUsbDevices(admin: Want, usbDevices: Array<UsbDeviceType>): void--><!--Device-usbManager-function addDisallowedUsbDevices(admin: Want, usbDevices: Array<UsbDeviceType>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| usbDevices | Array&lt;[UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md)&gt; | 是 | 要添加的USB设备类型的数组，UsbDeviceType信息可以通过 [getDevices](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-usbmanager-getdevices-f.md)接口获取。USB设备禁用名单数组长度上限为200，若当前禁用名单中已有100个USB设备ID，则只允许再添 加100个。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-策略冲突) | A conflict policy has been configured. |
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
  usbManager.addDisallowedUsbDevices(wantTemp, usbDevices);
  console.info(`Succeeded in adding disallowed USB devices.`);
} catch (err) {
  console.error(`Failed to add disallowed USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

