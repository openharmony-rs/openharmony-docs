# AdvertisingSettings

```TypeScript
interface AdvertisingSettings
```

表示广播配置参数。

**起始版本：** 26.0.0

<!--Device-advertising-interface AdvertisingSettings--><!--Device-advertising-interface AdvertisingSettings-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## frameType

```TypeScript
frameType?: nearlinkConstant.FrameType
```

表示星闪帧类型。默认值为**FRAME_TYPE_1**。

**类型：** [nearlinkConstant.FrameType](arkts-connectivity-nearlinkconstant-frametype-e.md)

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-AdvertisingSettings-frameType?: nearlinkConstant.FrameType--><!--Device-AdvertisingSettings-frameType?: nearlinkConstant.FrameType-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## interval

```TypeScript
interval?: number
```

广播间隔配置参数。单位slot，范围160-16777215，默认值为5000。1个slot对应的时间长度是0.125ms，例如：5000*0.125=625ms。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-AdvertisingSettings-interval?: int--><!--Device-AdvertisingSettings-interval?: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## isConnectable

```TypeScript
isConnectable?: boolean
```

表示广播能否连接。true：表示可连接的广播。false：表示不可连接的广播。默认值为true。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-AdvertisingSettings-isConnectable?: boolean--><!--Device-AdvertisingSettings-isConnectable?: boolean-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## power

```TypeScript
power?: TxPowerMode
```

广播发射功率配置参数。如果不配置，则默认值为ADV_TX_POWER_LOW。

**类型：** [TxPowerMode](arkts-connectivity-advertising-txpowermode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-AdvertisingSettings-power?: TxPowerMode--><!--Device-AdvertisingSettings-power?: TxPowerMode-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base
