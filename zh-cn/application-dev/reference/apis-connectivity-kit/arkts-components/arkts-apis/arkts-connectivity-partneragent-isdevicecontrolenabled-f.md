# isDeviceControlEnabled

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## isDeviceControlEnabled

```TypeScript
function isDeviceControlEnabled(deviceAddress: PartnerDeviceAddress): boolean
```

判断当前设备的互通功能是否已经打开。使用前建议先调用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能，若不支持则本接口不可用。

调用[bindDevice](arkts-connectivity-partneragent-binddevice-f.md)接口注册设备后，设备的互通功能将默认开启，且可在系统设置应用设备详情页显示该功能已开启。如果该功能已关闭，可通过系统设置应用设备详情页中的信息互通功能开关开启该功能。如果系统设置应用设备详情页未显示此功能开关，请先调用[bindDevice](arkts-connectivity-partneragent-binddevice-f.md)接口注册设备，之后此功能开关按钮会出现。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | 是 | 应用注册的设备地址信息。应用需在PartnerDeviceAddress中设置bluetoothAddress字段值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前设备是否已经打开互通功能。true表示已打开，false表示未打开。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal error. |
