# bindDevice

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## bindDevice

```TypeScript
function bindDevice(deviceAddress: PartnerDeviceAddress, deviceCapability: DeviceCapability,
    businessCapability: BusinessCapability, partnerAgentExtensionAbilityName: string): Promise<void>
```

应用注册设备，使用Promise异步回调。

建议先使用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能。仅支持情况下才能使用融合短距外设互通模块功能。可以通过接口[isDeviceBound](arkts-connectivity-partneragent-isdevicebound-f.md)判断设备是否已注册。若已注册，无需重复调用。应用需要先实现[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)。应用注册该设备后，如果外设互通子系统检测到该设备，且BusinessCapability中至少一项为true时，会激活应用的[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)进程。应用可以在新进程中执行业务操作。每当已注册设备被发现或者已断连时，该进程将被激活并保持运行3分钟（时间随着新的通知刷新）。在应用注册前，需先调用[connection.pairDevice](arkts-connectivity-connection-pairdevice-f.md)与该设备完成蓝牙配对。如果该设备已注册，且用户在注册后取消了与该设备的配对，该设备的发现和下线通知功能将自动关闭，但注册信息会保留30天。若在这30天内重新与该设备进行蓝牙配对，外设互通子系统可以恢复设备的发现和下线通知功能。否则，注册信息会被清除。可以通过接口[getBoundDevices](arkts-connectivity-partneragent-getbounddevices-f.md)获取所有已注册过的设备。应用在使用该接口前，建议提示用户并获取应用注册该设备的授权。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | 是 | 应用注册的设备地址信息。应用需配置PartnerDeviceAddress类型的bluetoothAddress选项。 |
| deviceCapability | [DeviceCapability](arkts-connectivity-partneragent-devicecapability-i.md) | 是 | 注册设备支持的能力。配置supportBR选项后，外设互通子系统将监听与该设备的[ACL](../../../connectivity/bluetooth/terminology.md#acl)连接状态，一旦建立ACL连接，即视为成功发现该设备；配置supportBleAdvertiser选项后，系统将启动该设备的[BLE](../../../connectivity/bluetooth/terminology.md#ble)扫描，扫描到该设备后，同样视为成功发现该设备。注意：为了减少系统功耗，BLE扫描到该设备后，若应用在3分钟内未与该设备建立ACL连接，外设互通子系统将自动终止应用的PartnerAgentExtensionAbility进程。 |
| businessCapability | [BusinessCapability](arkts-connectivity-partneragent-businesscapability-i.md) | 是 | 应用注册设备的业务功能，包括媒体控制、通话控制。注意：supportMediaControl和supportTelephonyControl均选择false时，设备发现时不会拉起[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)进程。 |
| partnerAgentExtensionAbilityName | string | 是 | 该参数需与应用模块级配置文件[module.json5](../../../quick-start/module-configuration-file.md) 中的[extensionabilities](../../../quick-start/module-configuration-file.md#extensionabilities标签) name属性值相同。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900003](../errorcode-fusionConnectivity.md#34900003-设备未配对) | The device is not paired. |
| [34900004](../errorcode-fusionConnectivity.md#34900004-设备地址已被注册) | The device has already been bound to the PartnerAgentExtensionAbility. |
| [34900005](../errorcode-fusionConnectivity.md#34900005-蓝牙关闭) | Bluetooth disabled. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal error. |
