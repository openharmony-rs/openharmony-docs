# addDisallowedPermissiveUsbDevices

## addDisallowedPermissiveUsbDevices

```TypeScript
function addDisallowedPermissiveUsbDevices(admin: Want, usbDevices: Array<PermissiveUsbDeviceType>): void
```

添加禁止使用的USB设备类型。与[addDisallowedUsbDevices]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口不同的是，本接口可以不按照 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_标准进行匹配。对已连接的USB设备热生效，无需重新插拔，例如USB线控耳机正常使用时，调用本接口禁用该耳 机，会导致耳机不可用。 以下情况下，调用本接口会报策略冲突： 1. 已经通过[addDisallowedUsbDevices]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口添加了禁止使用的USB设备类型。 2. 已经通过[setDisallowedPolicy]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口禁用了设备USB能力。 3. 已经通过[addAllowedUsbDevices]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_接口添加了USB设备可用名单。 4. 已经通过[setDisallowedPolicyForAccount]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_接口禁用了某用户USB存储设备写入能力。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_USB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function addDisallowedPermissiveUsbDevices(admin: Want, usbDevices: Array<PermissiveUsbDeviceType>): void--><!--Device-usbManager-function addDisallowedPermissiveUsbDevices(admin: Want, usbDevices: Array<PermissiveUsbDeviceType>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| usbDevices | Array&lt;PermissiveUsbDeviceType&gt; | 是 | 要添加的USB设备类型的数组，支持部分字段匹配。USB设备禁用名单数组长度上限为1000，若当前禁用名单中已有500个USB设备ID，则只允许再添加500个。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-策略冲突) | A conflict policy has been configured. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { usbManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 禁用USB存储设备（以实际USB设备类型参数为准）
  let usbDevices1: Array<usbManager.PermissiveUsbDeviceType> = [{
    baseClass: 8
  }];
  usbManager.addDisallowedPermissiveUsbDevices(wantTemp, usbDevices1);

  // 禁用USB线控耳机（以实际USB设备类型参数为准）
  let usbDevices2: Array<usbManager.PermissiveUsbDeviceType> = [{
    baseClass: 0,
    subClass: 0,
    protocol: 0,
    descriptor: usbManager.Descriptor.DEVICE
  }];
  usbManager.addDisallowedPermissiveUsbDevices(wantTemp, usbDevices2);

  // 禁用USB线控键盘输入（以实际USB设备类型参数为准）
  let usbDevices3: Array<usbManager.PermissiveUsbDeviceType> = [{
    baseClass: 3,
    subClass: 1,
    protocol: 1,
    descriptor: usbManager.Descriptor.INTERFACE
  }];
  usbManager.addDisallowedPermissiveUsbDevices(wantTemp, usbDevices3);
  console.info(`Succeeded in adding disallowed permissive USB devices.`);
} catch (err) {
  console.error(`Failed to add disallowed permissive USB devices. Code: ${err.code}, message: ${err.message}`);
}
```

