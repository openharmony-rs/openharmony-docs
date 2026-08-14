# addDisallowedBluetoothProtocols

## addDisallowedBluetoothProtocols

```TypeScript
function addDisallowedBluetoothProtocols(admin: Want, accountId: number,  protocols: Array<Protocol>): void
```

添加蓝牙协议禁用名单。添加后，指定用户将无法使用该禁用名单中的蓝牙协议向其他设备外发文件。通过该接口禁用GATT或SPP协议，对系统服务和系统应用不生效。当传入SPP协议时，会同时禁用接收和发送功能。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bluetoothManager-function addDisallowedBluetoothProtocols(admin: Want, accountId: number,  protocols: Array<Protocol>): void--><!--Device-bluetoothManager-function addDisallowedBluetoothProtocols(admin: Want, accountId: number,  protocols: Array<Protocol>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。 &lt;br&gt; accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId)等接口来获取。 |
| protocols | Array&lt;Protocol&gt; | 是 | 蓝牙协议的数组。数组长度上限为10000。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { Want } from '@kit.AbilityKit';
import { bluetoothManager } from '@kit.MDMKit';

// 创建企业设备管理扩展组件
let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 定义用户ID（需根据实际情况进行替换）
let accountId: number = 100;
// 定义蓝牙协议数组（需根据实际情况进行替换）
let protocols: Array<bluetoothManager.Protocol> = [bluetoothManager.Protocol.GATT, bluetoothManager.Protocol.SPP];
try {
  // 添加蓝牙协议禁用名单
  bluetoothManager.addDisallowedBluetoothProtocols(wantTemp, accountId, protocols);
  console.info('Succeeded in adding disallowed bluetooth protocols policy.');
} catch (err) {
  console.error(`Failed to add disallowed bluetooth protocols. Code: ${err.code}, message: ${err.message}`);
}
```


## addDisallowedBluetoothProtocols

```TypeScript
function addDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array<Protocol>, policy: TransferPolicy): void
```

添加蓝牙协议至禁用名单。添加后，指定用户将无法根据指定的传输策略使用该禁用名单中的蓝牙协议。 > **说明：** > > 1. 通过该接口禁用GATT或SPP协议，对系统服务和系统应用不生效。 > > 2. 当传入SPP协议时，policy参数只能传入TransferPolicy.RECEIVE_SEND，否则会返回错误码9200012。 > > 3. 本接口与[addDisallowedBluetoothProtocols&lt;sup&gt;20+&lt;/sup&gt;](#addDisallowedBluetoothProtocols)接口为 > 重载接口。本接口增加了policy参数用于指定传输策略，可以更精细地控制蓝牙协议的禁用行为（如仅禁止发送、仅禁止接收或同时禁止发送和接收）。如果同时使用两个接口配置了禁用策略，策略会合并生效。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bluetoothManager-function addDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array<Protocol>, policy: TransferPolicy): void--><!--Device-bluetoothManager-function addDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array<Protocol>, policy: TransferPolicy): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。 &lt;br&gt; accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId)等接口来获取。 |
| protocols | Array&lt;Protocol&gt; | 是 | 蓝牙协议数组，指定需要添加至禁用名单的协议。 |
| policy | [TransferPolicy](arkts-mdm-bluetoothmanager-transferpolicy-e.md) | 是 | 传输策略,用于指定蓝牙协议的禁用方式。可选值包括:SEND_ONLY(禁止发送)、RECEIVE_ONLY(禁止接收)、RECEIVE_SEND(禁止发送和接收 )。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { Want } from '@kit.AbilityKit';
import { bluetoothManager } from '@kit.MDMKit';

// 创建企业设备管理扩展组件
let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 定义用户ID
let accountId: number = 100;
// 定义蓝牙协议数组
let protocols: Array<bluetoothManager.Protocol> = [
  bluetoothManager.Protocol.GATT,
  bluetoothManager.Protocol.SPP,
  bluetoothManager.Protocol.OPP
];

try {
  // 添加蓝牙协议禁用名单，指定传输策略为禁止发送和接收
  bluetoothManager.addDisallowedBluetoothProtocols(wantTemp, accountId, protocols, bluetoothManager.TransferPolicy.RECEIVE_SEND);
  console.info('Succeeded in adding disallowed bluetooth protocols.');
} catch (err) {
  console.error(`Failed to add disallowed bluetooth protocols. Code is ${err.code}, message is ${err.message}`);
}
```

