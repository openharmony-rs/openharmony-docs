# RangingResult

```TypeScript
interface RangingResult
```

Describes the contents of the ranging results.

**Since:** 26.0.0

<!--Device-ranging-interface RangingResult--><!--Device-ranging-interface RangingResult-End-->

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

<!--Device-RangingResult-angle: RangingMeasurement--><!--Device-RangingResult-angle: RangingMeasurement-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## deviceId

```TypeScript
deviceId: string
```

Address of the ranging device.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RangingResult-deviceId: string--><!--Device-RangingResult-deviceId: string-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## distance

```TypeScript
distance: RangingMeasurement
```

The distance measured by the ranging output.

**Type:** [RangingMeasurement](arkts-connectivity-ranging-rangingmeasurement-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RangingResult-distance: RangingMeasurement--><!--Device-RangingResult-distance: RangingMeasurement-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## rssi

```TypeScript
rssi: number
```

Received signal strength.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RangingResult-rssi: int--><!--Device-RangingResult-rssi: int-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core
