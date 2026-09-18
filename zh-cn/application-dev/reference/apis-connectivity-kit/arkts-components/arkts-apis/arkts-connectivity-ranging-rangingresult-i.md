# RangingResult

描述测距结果，每次测距测量完成后通过[startRanging](arkts-connectivity-ranging-startranging-f.md)的callback回调返回。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## angle

```TypeScript
angle: RangingMeasurement
```

测距输出的方位角，value单位：度，有效值的取值范围：[0, 360)，返回-1表示不支持测角。

**类型：** [RangingMeasurement](arkts-connectivity-ranging-rangingmeasurement-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## deviceId

```TypeScript
deviceId: string
```

测距设备的地址。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## distance

```TypeScript
distance: RangingMeasurement
```

测距输出的距离测量结果，value单位：cm。

**类型：** [RangingMeasurement](arkts-connectivity-ranging-rangingmeasurement-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## rssi

```TypeScript
rssi: number
```

接收信号强度指示RSSI，单位：dBm。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
