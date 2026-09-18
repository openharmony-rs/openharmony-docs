# cloudData(Device-Cloud Service)

The **cloudData** module provides APIs for implementing device-cloud synergy and device-cloud sharing, and setting the device-cloud sync strategy.

Device-cloud synergy enables sync of the structured data (in RDB stores) between devices and the cloud. The cloud serves as a data hub to implement data backup in the cloud and data consistency between the devices with the same account. This module also provides the capability of setting the device-cloud sync strategy.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [sharing](arkts-arkdata-clouddata-sharing-n.md) | Provides APIs for device-cloud data sharing, including sharing or unsharing data, exiting a share, changing the privilege on the shared data, querying participants, confirming an invitation, changing the invitation confirmation state, and querying the shared resource. |

### Functions

| Name | Description |
| --- | --- |
| [setCloudStrategy](arkts-arkdata-clouddata-setcloudstrategy-f.md) | Sets the cloud sync strategy of an application. This API uses a promise to return the result. |
| [onAutoSyncTrigger](arkts-arkdata-clouddata-onautosynctrigger-f.md) | Describes the triggering method for automatic device-cloud synchronization subscription. |
| [offAutoSyncTrigger](arkts-arkdata-clouddata-offautosynctrigger-f.md) | Describes unsubscribing from the device-cloud automatic synchronization trigger mode. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [Config](arkts-arkdata-clouddata-config-c-sys.md) | Provides APIs for setting device-cloud synergy, including enabling and disabling device-cloud synergy, clearing data, and notifying data changes. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AutoSyncTriggerInfo](arkts-arkdata-clouddata-autosynctriggerinfo-i.md) | Describes information about the automatic synchronization trigger mode. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ExtraData](arkts-arkdata-clouddata-extradata-i-sys.md) | Represents the transparently transmitted data, which contains information required for a data change notification. |
| [StatisticInfo](arkts-arkdata-clouddata-statisticinfo-i-sys.md) | Represents the device-cloud sync statistics. |
| [SyncInfo](arkts-arkdata-clouddata-syncinfo-i-sys.md) | Represents information about the last device-cloud sync. |
| [DBSwitchInfo](arkts-arkdata-clouddata-dbswitchinfo-i-sys.md) | Defines the switch information of a device-cloud synergy database. |
| [SwitchConfig](arkts-arkdata-clouddata-switchconfig-i-sys.md) | Defines the switch configuration of a device-cloud synergy database. |
| [DBActionInfo](arkts-arkdata-clouddata-dbactioninfo-i-sys.md) | Defines the clearance information of a device-cloud synergy database. |
| [ClearConfig](arkts-arkdata-clouddata-clearconfig-i-sys.md) | Defines the clearance configuration of a device-cloud synergy database. |
| [BundleInfo](arkts-arkdata-clouddata-bundleinfo-i-sys.md) | Bundle information configuration. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [StrategyType](arkts-arkdata-clouddata-strategytype-e.md) | Enumerates the types of the cloud-device sync strategy. |
| [NetWorkStrategy](arkts-arkdata-clouddata-networkstrategy-e.md) | Enumerates the network sync options. |
| [AutoSyncTriggerMode](arkts-arkdata-clouddata-autosynctriggermode-e.md) | Indicates automatic synchronization triggering method for Device-Cloud data. |

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
