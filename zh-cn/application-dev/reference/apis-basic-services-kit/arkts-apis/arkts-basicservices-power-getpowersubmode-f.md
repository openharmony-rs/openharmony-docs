# getPowerSubMode

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## getPowerSubMode

```TypeScript
function getPowerSubMode(): DevicePowerSubMode
```

获取当前设备的电源模式子模式。各子模式定义及说明请参见DevicePowerSubMode。如需获取当前设备的电源模式，请使用[getPowerMode](arkts-basicservices-power-getpowermode-f.md)。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-power-function getPowerSubMode(): DevicePowerSubMode--><!--Device-power-function getPowerSubMode(): DevicePowerSubMode-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DevicePowerSubMode](arkts-basicservices-power-devicepowersubmode-e.md) | 电源模式子模式。当前电源模式不支持子模式时返回 SUB_MODE_INVALID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
