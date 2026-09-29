# ControlDeviceActionParams（系统接口）

```TypeScript
interface ControlDeviceActionParams
```

控制命令的配置参数。

**起始版本：** 15

<!--Device-connection-interface ControlDeviceActionParams--><!--Device-connection-interface ControlDeviceActionParams-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## controlObject

```TypeScript
controlObject: ControlObject
```

表示控制对象。

**类型：** [ControlObject](arkts-connectivity-connection-controlobject-e-sys.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ControlDeviceActionParams-controlObject: ControlObject--><!--Device-ControlDeviceActionParams-controlObject: ControlObject-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: string
```

表示要控制的设备地址，例如："XX:XX:XX:XX:XX:XX"。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ControlDeviceActionParams-deviceId: string--><!--Device-ControlDeviceActionParams-deviceId: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: ControlType
```

表示控制类型。

**类型：** [ControlType](arkts-connectivity-connection-controltype-e-sys.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ControlDeviceActionParams-type: ControlType--><!--Device-ControlDeviceActionParams-type: ControlType-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## typeValue

```TypeScript
typeValue: ControlTypeValue
```

表示控制动作。

**类型：** [ControlTypeValue](arkts-connectivity-connection-controltypevalue-e-sys.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ControlDeviceActionParams-typeValue: ControlTypeValue--><!--Device-ControlDeviceActionParams-typeValue: ControlTypeValue-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
