# @ohos.resourceschedule.usageStatistics(Device Usage Statistics)

Provides methods for managing bundle usage statistics, including the methods for querying bundle usage information and state data.

You can use the methods defined in this class to query the usage history and states of bundles in a specified period. The system stores the query result in a [BundleStatsInfo](arkts-backgroundtasks-usagestatistics-bundlestatsinfo-i-sys.md) instance and then returns it to you.

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

## Modules to Import

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [isIdleState](arkts-backgroundtasks-usagestatistics-isidlestate-f-sys.md#isidlestate) | Checks whether the application with a specified bundle name is in the idle state. |
| [isIdleState](arkts-backgroundtasks-usagestatistics-isidlestate-f-sys.md#isidlestate-1) | Checks whether the application with a specified bundle name is in the idle state. |
| [isIdleStateSync](arkts-backgroundtasks-usagestatistics-isidlestatesync-f-sys.md) | Checks whether the application with a specified bundle name is in the idle state. |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup) | Queries the app group of the calling application. |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup-1) | Queries the app group of the calling application. |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup-2) | Queries the usage priority group by bundleName. |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup-3) | Queries the usage priority group by bundleName. |
| [queryAppGroupSync](arkts-backgroundtasks-usagestatistics-queryappgroupsync-f-sys.md#queryappgroupsync) | Queries the app group of the calling application. |
| [queryAppGroupSync](arkts-backgroundtasks-usagestatistics-queryappgroupsync-f-sys.md#queryappgroupsync-1) | Queries the usage priority group by bundleName. |
| [queryAppStatsInfos](arkts-backgroundtasks-usagestatistics-queryappstatsinfos-f-sys.md) | Queries usage information about each application within a specified period. |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents) | Queries state data of all bundles within a specified period identified by the start and end time. |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents-1) | Queries state data of all bundles within a specified period identified by the start and end time. |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents-2) | Queries state data of all bundles within a specified period identified by the start and end time. |
| [queryBundleStatsInfoByInterval](arkts-backgroundtasks-usagestatistics-querybundlestatsinfobyinterval-f-sys.md#querybundlestatsinfobyinterval) | Queries usage information about each bundle within a specified period at a specified interval. |
| [queryBundleStatsInfoByInterval](arkts-backgroundtasks-usagestatistics-querybundlestatsinfobyinterval-f-sys.md#querybundlestatsinfobyinterval-1) | Queries usage information about each bundle within a specified period at a specified interval. |
| [queryBundleStatsInfos](arkts-backgroundtasks-usagestatistics-querybundlestatsinfos-f-sys.md#querybundlestatsinfos) | Queries usage information about each bundle within a specified period. |
| [queryBundleStatsInfos](arkts-backgroundtasks-usagestatistics-querybundlestatsinfos-f-sys.md#querybundlestatsinfos-1) | Queries usage information about each bundle within a specified period. |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents) | Queries state data of the current bundle within a specified period. |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents-1) | Queries state data of the current bundle within a specified period. |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents-2) | Queries state data of the current bundle within a specified period. |
| [queryDeviceEventStats](arkts-backgroundtasks-usagestatistics-querydeviceeventstats-f-sys.md#querydeviceeventstats) | Queries device event states data within a specified period identified by the start and end time. |
| [queryDeviceEventStats](arkts-backgroundtasks-usagestatistics-querydeviceeventstats-f-sys.md#querydeviceeventstats-1) | Queries device event states data within a specified period identified by the start and end time. |
| [queryLastUseTime](arkts-backgroundtasks-usagestatistics-querylastusetime-f-sys.md) | Queries the last usage timestamp by bundleName and app index. |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords) | Queries recently module usage records with maxNum. |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords-1) | Queries recently module usage records with maxNum. |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords-2) | Queries recently module usage records. |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords-3) | Queries recently module usage records. |
| [queryNotificationEventStats](arkts-backgroundtasks-usagestatistics-querynotificationeventstats-f-sys.md#querynotificationeventstats) | Queries app notification number within a specified period identified by the start and end time. |
| [queryNotificationEventStats](arkts-backgroundtasks-usagestatistics-querynotificationeventstats-f-sys.md#querynotificationeventstats-1) | Queries app notification number within a specified period identified by the start and end time. |
| [registerAppGroupCallBack](arkts-backgroundtasks-usagestatistics-registerappgroupcallback-f-sys.md#registerappgroupcallback) | Register appGroup change callback to service. |
| [registerAppGroupCallBack](arkts-backgroundtasks-usagestatistics-registerappgroupcallback-f-sys.md#registerappgroupcallback-1) | Register appGroup change callback to service. |
| [setAppGroup](arkts-backgroundtasks-usagestatistics-setappgroup-f-sys.md#setappgroup) | Set app group by bundleName. |
| [setAppGroup](arkts-backgroundtasks-usagestatistics-setappgroup-f-sys.md#setappgroup-1) | Set app group by bundleName. |
| [unregisterAppGroupCallBack](arkts-backgroundtasks-usagestatistics-unregisterappgroupcallback-f-sys.md#unregisterappgroupcallback) | Unregister appGroup change callback from service. |
| [unregisterAppGroupCallBack](arkts-backgroundtasks-usagestatistics-unregisterappgroupcallback-f-sys.md#unregisterappgroupcallback-1) | Unregister appGroup change callback from service. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AppGroupCallbackInfo](arkts-backgroundtasks-usagestatistics-appgroupcallbackinfo-i-sys.md) |  |
| [BundleEvents](arkts-backgroundtasks-usagestatistics-bundleevents-i-sys.md) |  |
| [BundleStatsInfo](arkts-backgroundtasks-usagestatistics-bundlestatsinfo-i-sys.md) |  |
| [DeviceEventStats](arkts-backgroundtasks-usagestatistics-deviceeventstats-i-sys.md) |  |
| [HapFormInfo](arkts-backgroundtasks-usagestatistics-hapforminfo-i-sys.md) |  |
| [HapModuleInfo](arkts-backgroundtasks-usagestatistics-hapmoduleinfo-i-sys.md) |  |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [GroupType](arkts-backgroundtasks-usagestatistics-grouptype-e-sys.md) | Declares group type. |
| [IntervalType](arkts-backgroundtasks-usagestatistics-intervaltype-e-sys.md) | Declares interval type. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [AppStatsMap](arkts-backgroundtasks-usagestatistics-appstatsmap-t-sys.md) |  |
| [BundleStatsMap](arkts-backgroundtasks-usagestatistics-bundlestatsmap-t-sys.md) |  |
<!--DelEnd-->
