# @ohos.nearlink.advertising(NearLink Advertising Capability)

This module provides Nearlink advertising functions, including starting and stopping advertising as well as subscribing to the advertising status.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [offAdvertisingStateChange](arkts-connectivity-advertising-offadvertisingstatechange-f.md) | Unsubscribes from the NearLink advertising state change event. This API uses an asynchronous callback to return the result. |
| [onAdvertisingStateChange](arkts-connectivity-advertising-onadvertisingstatechange-f.md) | Subscribes to the NearLink advertising state change event. This API uses an asynchronous callback to return the result. When [advertising.startAdvertising](arkts-connectivity-advertising-startadvertising-f.md) is called to start advertising or [advertising.stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md) is called to stop advertising, the callback is triggered to return the corresponding advertising ID and advertising status. This API must be used in pairs with [advertising.offAdvertisingStateChange](arkts-connectivity-advertising-offadvertisingstatechange-f.md). |
| [startAdvertising](arkts-connectivity-advertising-startadvertising-f.md) | Starts NearLink advertising. This API uses a promise to return the result. This API is applicable to scenarios where the local device capabilities or data needs to be advertised, such as device discovery and device information advertising. You can use [advertising.onAdvertisingStateChange](arkts-connectivity-advertising-onadvertisingstatechange-f.md) to monitor the advertising status. |
| [stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md) | Stops NearLink advertising. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [AdvertisingData](arkts-connectivity-advertising-advertisingdata-i.md) | Represents an advertising data packet. |
| [AdvertisingParams](arkts-connectivity-advertising-advertisingparams-i.md) | Enumerates the advertising parameters. |
| [AdvertisingSettings](arkts-connectivity-advertising-advertisingsettings-i.md) | Represents the advertising settings. |
| [AdvertisingStateChangeInfo](arkts-connectivity-advertising-advertisingstatechangeinfo-i.md) | Represents the advertising state change information. |
| [ManufacturerData](arkts-connectivity-advertising-manufacturerdata-i.md) | Represents the manufacturer data. |
| [ServiceData](arkts-connectivity-advertising-servicedata-i.md) | Represents the service data. |

### Enums

| Name | Description |
| --- | --- |
| [AdvertisingState](arkts-connectivity-advertising-advertisingstate-e.md) | Enumerates the advertising states. |
| [TxPowerMode](arkts-connectivity-advertising-txpowermode-e.md) | Enumerates the advertising transmission power modes. |
