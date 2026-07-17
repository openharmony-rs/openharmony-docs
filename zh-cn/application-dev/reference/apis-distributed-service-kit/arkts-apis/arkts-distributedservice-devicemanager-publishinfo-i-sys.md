# PublishInfo（系统接口）

发布设备参数

**起始版本：** 9

**废弃版本：** 11

<!--Device-deviceManager-interface PublishInfo--><!--Device-deviceManager-interface PublishInfo-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## freq

```TypeScript
freq: ExchangeFreq
```

发现频率。

**类型：** ExchangeFreq

**起始版本：** 9

**废弃版本：** 11

<!--Device-PublishInfo-freq: ExchangeFreq--><!--Device-PublishInfo-freq: ExchangeFreq-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode: DiscoverMode
```

发现模式。

**类型：** DiscoverMode

**起始版本：** 9

**废弃版本：** 11

<!--Device-PublishInfo-mode: DiscoverMode--><!--Device-PublishInfo-mode: DiscoverMode-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## publishId

```TypeScript
publishId: number
```

发布设备标识，用于标识不同的发布周期。

**类型：** number

**起始版本：** 9

**废弃版本：** 11

<!--Device-PublishInfo-publishId: number--><!--Device-PublishInfo-publishId: number-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## ranging

```TypeScript
ranging: boolean
```

发布的设备是否支持测距能力，true表示支持测距能力，false表示不支持测距能力。

**类型：** boolean

**起始版本：** 9

**废弃版本：** 11

<!--Device-PublishInfo-ranging: boolean--><!--Device-PublishInfo-ranging: boolean-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

