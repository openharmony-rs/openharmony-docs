# cloudData(Device-Cloud Service)

```TypeScript
declare namespace cloudData
```

The **cloudData** module provides APIs for implementing device-cloud synergy and device-cloud sharing, and setting the device-cloud sync strategy.

Device-cloud synergy enables sync of the structured data (in RDB stores) between devices and the cloud. The cloud serves as a data hub to implement data backup in the cloud and data consistency between the devices with the same account. This module also provides the capability of setting the device-cloud sync strategy.

**Since:** 10

<!--Device-unnamed-declare namespace cloudData--><!--Device-unnamed-declare namespace cloudData-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [sharing](arkts-arkdata-clouddata-sharing-n.md) | Provides APIs for device-cloud data sharing, including sharing or unsharing data, exiting a share, changing the privilege on the shared data, querying participants, confirming an invitation, changing a confirmed invitation, and querying the shared resource. |

### Functions

| Name | Description |
| --- | --- |
| [offAutoSyncTrigger](arkts-arkdata-clouddata-offautosynctrigger-f.md#offautosynctrigger-1) | Unsubscribes from the auto sync trigger event notification. |
| [onAutoSyncTrigger](arkts-arkdata-clouddata-onautosynctrigger-f.md#onautosynctrigger-1) | Registers the auto sync trigger event notification when device-cloud sync is enabled and automatic sync is disabled for the application. When the auto trigger condition is met, the callback function is invoked. |
| [setCloudStrategy](arkts-arkdata-clouddata-setcloudstrategy-f.md#setcloudstrategy-1) | Sets the cloud sync strategy of the application itself. This API uses a promise to return the result. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [Config](arkts-arkdata-clouddata-config-c-sys.md) | Provides APIs for setting device-cloud synergy, including enabling and disabling device-cloud synergy, clearing data, and notifying data changes. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AutoSyncTriggerInfo](arkts-arkdata-clouddata-autosynctriggerinfo-i.md) | Automatic synchronization trigger information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BundleInfo](arkts-arkdata-clouddata-bundleinfo-i-sys.md) | Defines the device-cloud synergy application information. |
| [ClearConfig](arkts-arkdata-clouddata-clearconfig-i-sys.md) | Defines the database-level clearing rules for device-cloud synergy. |
| [DBActionInfo](arkts-arkdata-clouddata-dbactioninfo-i-sys.md) | Defines the database-level clearing rules for device-cloud synergy. |
| [DBSwitchInfo](arkts-arkdata-clouddata-dbswitchinfo-i-sys.md) | Defines the switch information of a device-cloud synergy database. |
| [ExtraData](arkts-arkdata-clouddata-extradata-i-sys.md) | Represents the transparently transmitted data, which contains information required for a data change notification. |
| [StatisticInfo](arkts-arkdata-clouddata-statisticinfo-i-sys.md) | Represents the device-cloud sync statistics. |
| [SwitchConfig](arkts-arkdata-clouddata-switchconfig-i-sys.md) | Defines the switch configuration of a device-cloud synergy database. |
| [SyncInfo](arkts-arkdata-clouddata-syncinfo-i-sys.md) | Represents information about the last device-cloud sync. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AutoSyncTriggerMode](arkts-arkdata-clouddata-autosynctriggermode-e.md) | Enumerates the trigger modes of automatic synchronization. |
| [NetWorkStrategy](arkts-arkdata-clouddata-networkstrategy-e.md) | Enumerates the network policy parameters. |
| [StrategyType](arkts-arkdata-clouddata-strategytype-e.md) | Enumerates the cloud sync strategy types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ClearAction](arkts-arkdata-clouddata-clearaction-e-sys.md) | Enumerates the operations for clearing the downloaded cloud data locally. |
| [SyncStatus](arkts-arkdata-clouddata-syncstatus-e-sys.md) | Enumerates the device-cloud sync task statuses. |
<!--DelEnd-->

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [DATA_CHANGE_EVENT_ID](arkts-arkdata-clouddata-con-sys.md#data_change_event_id) | ID of the event, which indicates the change of the data in the cloud. |
<!--DelEnd-->
