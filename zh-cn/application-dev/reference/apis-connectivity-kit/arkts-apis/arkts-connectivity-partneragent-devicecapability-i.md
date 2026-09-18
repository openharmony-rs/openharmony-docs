# DeviceCapability

描述设备支持的被发现能力。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## supportBleAdvertiser

```TypeScript
supportBleAdvertiser?: boolean
```

该设备是否支持通过BLE扫描的方式发现，扫描到该设备后会认为成功发现了该设备。发现设备后，在BusinessCapability中至少一项为true的情况下，会拉起PartnerAgentExtensionAbility进程，并调用进程中onDeviceDiscovered方法。true表示支持通过BLE扫描的方式发现，false表示不支持通过BLE扫描的方式发现。未指定默认为false。

注意：

选择[DeviceCapability](arkts-connectivity-partneragent-devicecapability-i.md)中的supportBleAdvertiser选项，若扫描到该设备，3分钟内无ACL连接，会调用[onDestroyWithReason](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md#ondestroywithreason)并销毁已拉起的PartnerAgentExtensionAbility进程。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## supportBR

```TypeScript
supportBR?: boolean
```

该设备是否支持通过ACL连接的方式发现，建立ACL连接后会认为成功发现了该设备。发现设备后，在BusinessCapability中至少一项为true的情况下，会拉起[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)进程，并调用进程中[onDeviceDiscovered](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md#ondevicediscovered)方法。true表示支持通过连接的方式发现，false表示不支持通过连接的方式发现。未指定默认为false。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
