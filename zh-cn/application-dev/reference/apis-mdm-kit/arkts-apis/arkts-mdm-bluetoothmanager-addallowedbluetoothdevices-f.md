# addAllowedBluetoothDevices

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
```

## addAllowedBluetoothDevices

```TypeScript
function addAllowedBluetoothDevices(admin: Want, deviceIds: Array<string>): void
```

添加蓝牙设备可用名单。添加蓝牙设备可用名单后当前设备仅允许连接该名单下的蓝牙设备。从API version 22开始，数组中的MAC地址必须符合蓝牙MAC规范（例如：00:1A:2B:3C:4D:5E），添加时会移除不合法的MAC地址，仅添加合法的MAC地址。

以下情况下，通过本接口添加蓝牙设备可用名单，会报策略冲突：

1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了蓝牙。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口启用蓝牙后，可解除冲突。2. 已经通过[addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md#adddisallowedbluetoothdevices)接口添加了蓝牙设备禁用名单。通过[removeDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-removedisallowedbluetoothdevices-f.md#removedisallowedbluetoothdevices)移除蓝牙设备禁用名单后，可解除冲突。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bluetoothManager-function addAllowedBluetoothDevices(admin: Want, deviceIds: Array<string>): void--><!--Device-bluetoothManager-function addAllowedBluetoothDevices(admin: Want, deviceIds: Array<string>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| deviceIds | Array&lt;string&gt; | 是 | 蓝牙设备MAC地址的数组。蓝牙设备允许名单数组长度上限为1000，若当前允许名单中已有300个蓝牙设备MAC地址，则只允许再添加700个。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-策略冲突) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

// 创建企业设备管理扩展组件
let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 定义蓝牙设备MAC地址数组（需根据实际情况进行替换）
let deviceIds: Array<string> = ["00:1A:2B:3C:4D:5E","AA:BB:CC:DD:EE:FF"];
try {
  // 添加蓝牙设备允许名单
  bluetoothManager.addAllowedBluetoothDevices(wantTemp,deviceIds);
  console.info(`Succeeded in adding allowed bluetooth devices.`);
} catch(err) {
  console.error(`Failed to add allowed bluetooth devices. Code: ${err.code}, message: ${err.message}`);
}

```

