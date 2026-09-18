# enableDeviceControl（系统接口）

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## enableDeviceControl

```TypeScript
function enableDeviceControl(deviceAddress: PartnerDeviceAddress): Promise<void>
```

开启外设互通功能，使用Promise异步回调。适用于应用需要为已绑定蓝牙设备提供外设互通能力的场景。

该接口仅对应用调用[BindDevice](arkts-connectivity-partneragent-binddevice-f.md)注册过的设备生效，调用后给应用提供设备互通能力[partnerAgent](arkts-connectivity-fusionconnectivity-partneragent.md)。可以通过[isDeviceControlEnabled](arkts-connectivity-partneragent-isdevicecontrolenabled-f.md)判断设备的外设互通是否已开启，若已开启，重复调用不生效。可以通过[disableDeviceControl](arkts-connectivity-partneragent-disabledevicecontrol-f-sys.md)关闭外设互通功能。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | 是 | 应用注册的设备地址信息。应用需配置PartnerDeviceAddress类型的bluetoothAddress选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900001](../errorcode-fusionConnectivity.md#34900001-设备未注册) | The device is not bound. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal error. |
