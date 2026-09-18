# unbindDevice

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## unbindDevice

```TypeScript
function unbindDevice(deviceAddress: PartnerDeviceAddress): Promise<void>
```

应用解注册设备，使用Promise异步回调。使用前建议先调用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能，若不支持则本接口不可用。

调用本接口进行解注册后，应用的[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)进程将不再接收此设备的发现和下线状态通知。应用解注册的设备需是已通过[bindDevice](arkts-connectivity-partneragent-binddevice-f.md)接口注册过的设备，建议与bindDevice接口成对使用。建议使用前通过接口[isDeviceBound](arkts-connectivity-partneragent-isdevicebound-f.md)判断设备是否已注册。若已注册，可调用该接口。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | 是 | 应用注册的设备地址信息。应用必须配置PartnerDeviceAddress类型的bluetoothAddress选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900001](../errorcode-fusionConnectivity.md#34900001-设备未注册) | The device is not bound. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal error. |
