# isDeviceBound

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## isDeviceBound

```TypeScript
function isDeviceBound(deviceAddress: PartnerDeviceAddress): boolean
```

判断当前应用是否已注册过该设备。使用前建议先调用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能，若不支持则本接口不可用。

通过调用[bindDevice](arkts-connectivity-partneragent-binddevice-f.md)接口进行注册。通过调用[unbindDevice](arkts-connectivity-partneragent-unbinddevice-f.md)接口进行解注册。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | 是 | 应用注册的设备地址信息。应用需配置PartnerDeviceAddress类型的bluetoothAddress选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 应用是否注册过该设备。 true表示已注册设备，false表示未注册设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal error. |
