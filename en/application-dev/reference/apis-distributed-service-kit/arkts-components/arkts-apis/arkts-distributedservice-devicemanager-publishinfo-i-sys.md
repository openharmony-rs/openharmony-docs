# PublishInfo (System API)

```TypeScript
interface PublishInfo
```

Defines published device information.

**Since:** 9

**Deprecated since:** 11

<!--Device-deviceManager-interface PublishInfo--><!--Device-deviceManager-interface PublishInfo-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## freq

```TypeScript
freq: ExchangeFreq
```

Frequency of device discovery.

**Type:** [ExchangeFreq](arkts-distributedservice-devicemanager-exchangefreq-e-sys.md)

**Since:** 9

**Deprecated since:** 11

<!--Device-PublishInfo-freq: ExchangeFreq--><!--Device-PublishInfo-freq: ExchangeFreq-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## mode

```TypeScript
mode: DiscoverMode
```

Device discovery mode.

**Type:** [DiscoverMode](arkts-distributedservice-devicemanager-discovermode-e-sys.md)

**Since:** 9

**Deprecated since:** 11

<!--Device-PublishInfo-mode: DiscoverMode--><!--Device-PublishInfo-mode: DiscoverMode-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## publishId

```TypeScript
publishId: number
```

ID used to identify a publication period.

**Type:** number

**Since:** 9

**Deprecated since:** 11

<!--Device-PublishInfo-publishId: number--><!--Device-PublishInfo-publishId: number-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## ranging

```TypeScript
ranging: boolean
```

Whether the device supports ranging. The value **true** indicates that the device supports ranging and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 9

**Deprecated since:** 11

<!--Device-PublishInfo-ranging: boolean--><!--Device-PublishInfo-ranging: boolean-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
