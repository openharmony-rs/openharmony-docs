# AdvertisingSettings

Represents the advertising settings.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## interval

```TypeScript
interval?: number
```

Advertising interval, in slots. The value ranges from 160 to 16777215, and the default value is **5000**. One slot equals to 0.125 ms. For example, 5000 slots equal to 625 ms.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## isConnectable

```TypeScript
isConnectable?: boolean
```

Whether advertising is connectable. **true**: Advertising is connectable. **false**: Advertising is not connectable. The default value is **true**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## power

```TypeScript
power?: TxPowerMode
```

Advertising transmission power. If this parameter is not specified, the default value **ADV_TX_POWER_LOW** is used.

**Type:** [TxPowerMode](arkts-connectivity-advertising-txpowermode-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base
