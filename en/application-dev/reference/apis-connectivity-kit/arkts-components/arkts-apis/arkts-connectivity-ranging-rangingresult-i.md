# RangingResult

Describes the contents of the ranging results.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## angle

```TypeScript
angle: RangingMeasurement
```

Azimuth angle output from ranging.

**Type:** [RangingMeasurement](arkts-connectivity-ranging-rangingmeasurement-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## deviceId

```TypeScript
deviceId: string
```

Address of the ranging device.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## distance

```TypeScript
distance: RangingMeasurement
```

The distance measured by the ranging output.

**Type:** [RangingMeasurement](arkts-connectivity-ranging-rangingmeasurement-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## rssi

```TypeScript
rssi: number
```

Received signal strength.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core
