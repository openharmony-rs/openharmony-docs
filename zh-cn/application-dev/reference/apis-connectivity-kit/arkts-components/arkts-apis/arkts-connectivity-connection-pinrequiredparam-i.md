# PinRequiredParam

```TypeScript
interface PinRequiredParam
```

描述配对请求的参数结构。

**起始版本：** 10

<!--Device-connection-interface PinRequiredParam--><!--Device-connection-interface PinRequiredParam-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

要配对的对端设备地址。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinRequiredParam-deviceId: string--><!--Device-PinRequiredParam-deviceId: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## pinCode

```TypeScript
pinCode: string
```

配对过程中的密钥。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinRequiredParam-pinCode: string--><!--Device-PinRequiredParam-pinCode: string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core
