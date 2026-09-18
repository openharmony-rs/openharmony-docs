# @ohos.FusionConnectivity.partnerAgent(系统接口)

本模块基于蓝牙通信技术，为应用提供设备发现与设备下线的通知功能，主要功能特性包括：

动态监听并发现应用预先注册的蓝牙设备。采用进程启动机制，当目标设备出现时自动启动应用的[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)进程。采用进程销毁机制，当所有设备下线时自动销毁应用的[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)进程。通过[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)的接口通知应用发现已注册设备。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [bindDevice](arkts-connectivity-partneragent-binddevice-f.md) | 应用注册设备，使用Promise异步回调。 |
| [getBoundDevices](arkts-connectivity-partneragent-getbounddevices-f.md) | 获取应用当前注册过的所有设备。使用前建议先调用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能，若不支持则本接口不可用。 |
| [isDeviceBound](arkts-connectivity-partneragent-isdevicebound-f.md) | 判断当前应用是否已注册过该设备。使用前建议先调用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能，若不支持则本接口不可用。 |
| [isDeviceControlEnabled](arkts-connectivity-partneragent-isdevicecontrolenabled-f.md) | 判断当前设备的互通功能是否已经打开。使用前建议先调用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能，若不支持则本接口不可用。 |
| [isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md) | 判断本机设备是否支持外设互通功能，若该接口返回值是false，该文件内的其他接口均无法使用。 |
| [unbindDevice](arkts-connectivity-partneragent-unbinddevice-f.md) | 应用解注册设备，使用Promise异步回调。使用前建议先调用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能，若不支持则本接口不可用。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableDeviceControl](arkts-connectivity-partneragent-disabledevicecontrol-f-sys.md) | 关闭外设互通功能，使用Promise异步回调。适用于应用不再需要外设互通能力的场景。 |
| [enableDeviceControl](arkts-connectivity-partneragent-enabledevicecontrol-f-sys.md) | 开启外设互通功能，使用Promise异步回调。适用于应用需要为已绑定蓝牙设备提供外设互通能力的场景。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BusinessCapability](arkts-connectivity-partneragent-businesscapability-i.md) | 描述设备支持的业务功能。 |
| [DeviceCapability](arkts-connectivity-partneragent-devicecapability-i.md) | 描述设备支持的被发现能力。 |
| [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | 描述设备地址信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PartnerAgentExtensionAbilityDestroyReason](arkts-connectivity-partneragent-partneragentextensionabilitydestroyreason-e.md) | 枚举，PartnerAgentExtensionAbility被销毁的原因。 |
