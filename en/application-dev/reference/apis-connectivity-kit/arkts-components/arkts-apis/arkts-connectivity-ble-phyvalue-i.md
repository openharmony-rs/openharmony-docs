# PhyValue

```TypeScript
interface PhyValue
```

Describes the parameters of the Ble phy.

**Since:** 23

<!--Device-ble-interface PhyValue--><!--Device-ble-interface PhyValue-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## phyMode

```TypeScript
phyMode?: CodedPhyMode
```

Preferred coded phy mode.

**Type:** [CodedPhyMode](arkts-connectivity-ble-codedphymode-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhyValue-phyMode?: CodedPhyMode--><!--Device-PhyValue-phyMode?: CodedPhyMode-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## rxPhy

```TypeScript
rxPhy: BlePhy
```

Receiver phy.

**Type:** [BlePhy](arkts-connectivity-ble-blephy-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhyValue-rxPhy: BlePhy--><!--Device-PhyValue-rxPhy: BlePhy-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## txPhy

```TypeScript
txPhy: BlePhy
```

Transmitter phy.

**Type:** [BlePhy](arkts-connectivity-ble-blephy-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PhyValue-txPhy: BlePhy--><!--Device-PhyValue-txPhy: BlePhy-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
