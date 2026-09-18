# getBoundDevices

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## getBoundDevices

```TypeScript
function getBoundDevices(): PartnerDeviceAddress[]
```

获取应用当前注册过的所有设备。使用前建议先调用[isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md)判断本机是否支持外设互通功能，若不支持则本接口不可用。

可通过调用[bindDevice](arkts-connectivity-partneragent-binddevice-f.md)接口注册设备。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md)[] | 应用注册过的所有设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal error. |
