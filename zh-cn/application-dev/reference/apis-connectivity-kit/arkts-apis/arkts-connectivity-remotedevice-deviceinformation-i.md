# DeviceInformation

描述远端设备信息。

**起始版本：** 26.0.0

<!--Device-remoteDevice-interface DeviceInformation--><!--Device-remoteDevice-interface DeviceInformation-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## manufacturerData

```TypeScript
manufacturerData: string
```

远端设备的制造商数据最大长度为255。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceInformation-manufacturerData: string--><!--Device-DeviceInformation-manufacturerData: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## modelData

```TypeScript
modelData: string
```

远程设备的模型数据。最大长度为255。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceInformation-modelData: string--><!--Device-DeviceInformation-modelData: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

