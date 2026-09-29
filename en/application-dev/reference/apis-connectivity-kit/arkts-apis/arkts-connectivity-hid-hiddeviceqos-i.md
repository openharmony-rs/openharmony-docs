# HidDeviceQos

```TypeScript
interface HidDeviceQos
```

Represents the Quality of Service (QoS) settings for a bluetooth hid device application.

**Since:** 23

<!--Device-hid-interface HidDeviceQos--><!--Device-hid-interface HidDeviceQos-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## delayVariation

```TypeScript
delayVariation?: number
```

L2CAP delay variation, default = -1.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-HidDeviceQos-delayVariation?: int--><!--Device-HidDeviceQos-delayVariation?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## latency

```TypeScript
latency?: number
```

L2CAP latency, default = -1.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-HidDeviceQos-latency?: int--><!--Device-HidDeviceQos-latency?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## peakBandwidth

```TypeScript
peakBandwidth?: number
```

L2CAP peak bandwidth, default = 0.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-HidDeviceQos-peakBandwidth?: int--><!--Device-HidDeviceQos-peakBandwidth?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceType

```TypeScript
serviceType?: ServiceType
```

L2CAP service type, default = SERVICE_BEST_EFFORT.

**Type:** [ServiceType](arkts-connectivity-hid-servicetype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-HidDeviceQos-serviceType?: ServiceType--><!--Device-HidDeviceQos-serviceType?: ServiceType-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## tokenBucketSize

```TypeScript
tokenBucketSize?: number
```

L2CAP token bucket size, default = 0.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-HidDeviceQos-tokenBucketSize?: int--><!--Device-HidDeviceQos-tokenBucketSize?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## tokenRate

```TypeScript
tokenRate?: number
```

L2CAP tokenRate, means transmission rate, default = 0.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-HidDeviceQos-tokenRate?: int--><!--Device-HidDeviceQos-tokenRate?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
