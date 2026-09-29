# AdvertisingStateChangeInfo

```TypeScript
interface AdvertisingStateChangeInfo
```

Represents the advertising state change information.

**Since:** 26.0.0

<!--Device-advertising-interface AdvertisingStateChangeInfo--><!--Device-advertising-interface AdvertisingStateChangeInfo-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## advertisingId

```TypeScript
advertisingId: number
```

Advertising ID. The value range is [0, 255].

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AdvertisingStateChangeInfo-advertisingId: int--><!--Device-AdvertisingStateChangeInfo-advertisingId: int-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: AdvertisingState
```

Advertising state.

**Type:** [AdvertisingState](arkts-connectivity-advertising-advertisingstate-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AdvertisingStateChangeInfo-state: AdvertisingState--><!--Device-AdvertisingStateChangeInfo-state: AdvertisingState-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
