# @ohos.resourceschedule.usageStatistics(Device Usage Statistics)

Provides methods for managing bundle usage statistics, including the methods for querying bundle usage information and state data.

You can use the methods defined in this class to query the usage history and states of bundles in a specified period. The system stores the query result in a [BundleStatsInfo](arkts-backgroundtasks-usagestatistics-bundlestatsinfo-i-sys.md) instance and then returns it to you.

**Since:** 9

<!--Device-unnamed-declare namespace usageStatistics--><!--Device-unnamed-declare namespace usageStatistics-End-->

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
| [isIdleState](arkts-backgroundtasks-usagestatistics-isidlestate-f-sys.md#isidlestate1) | Checks whether the application with a specified bundle name is in the idle state. |
| [isIdleState](arkts-backgroundtasks-usagestatistics-isidlestate-f-sys.md#isidlestate2) | Checks whether the application with a specified bundle name is in the idle state. |
| [isIdleStateSync](arkts-backgroundtasks-usagestatistics-isidlestatesync-f-sys.md#isidlestatesync) | Checks whether the application with a specified bundle name is in the idle state. |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup1) | Queries the app group of the calling application. |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup2) | Queries the app group of the calling application. |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup3) | Queries the usage priority group by bundleName. |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup4) | Queries the usage priority group by bundleName. |
| [queryAppGroupSync](arkts-backgroundtasks-usagestatistics-queryappgroupsync-f-sys.md#queryappgroupsync1) | Queries the app group of the calling application. |
| [queryAppGroupSync](arkts-backgroundtasks-usagestatistics-queryappgroupsync-f-sys.md#queryappgroupsync2) | Queries the usage priority group by bundleName. |
| [queryAppStatsInfos](arkts-backgroundtasks-usagestatistics-queryappstatsinfos-f-sys.md#queryappstatsinfos) | Queries usage information about each application within a specified period. |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents1) | Queries state data of all bundles within a specified period identified by the start and end time. |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents2) | Queries state data of all bundles within a specified period identified by the start and end time. |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents3) | Queries state data of all bundles within a specified period identified by the start and end time. |
| [queryBundleStatsInfoByInterval](arkts-backgroundtasks-usagestatistics-querybundlestatsinfobyinterval-f-sys.md#querybundlestatsinfobyinterval1) | Queries usage information about each bundle within a specified period at a specified interval. |
| [queryBundleStatsInfoByInterval](arkts-backgroundtasks-usagestatistics-querybundlestatsinfobyinterval-f-sys.md#querybundlestatsinfobyinterval2) | Queries usage information about each bundle within a specified period at a specified interval. |
| [queryBundleStatsInfos](arkts-backgroundtasks-usagestatistics-querybundlestatsinfos-f-sys.md#querybundlestatsinfos1) | Queries usage information about each bundle within a specified period. |
| [queryBundleStatsInfos](arkts-backgroundtasks-usagestatistics-querybundlestatsinfos-f-sys.md#querybundlestatsinfos2) | Queries usage information about each bundle within a specified period. |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents1) | Queries state data of the current bundle within a specified period. |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents2) | Queries state data of the current bundle within a specified period. |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents3) | Queries state data of the current bundle within a specified period. |
| [queryDeviceEventStats](arkts-backgroundtasks-usagestatistics-querydeviceeventstats-f-sys.md#querydeviceeventstats1) | Queries device event states data within a specified period identified by the start and end time. |
| [queryDeviceEventStats](arkts-backgroundtasks-usagestatistics-querydeviceeventstats-f-sys.md#querydeviceeventstats2) | Queries device event states data within a specified period identified by the start and end time. |
| [queryLastUseTime](arkts-backgroundtasks-usagestatistics-querylastusetime-f-sys.md#querylastusetime) | Queries the last usage timestamp by bundleName and app index. |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords1) | Queries recently module usage records with maxNum. |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords2) | Queries recently module usage records with maxNum. |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords3) | Queries recently module usage records. |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords4) | Queries recently module usage records. |
| [queryNotificationEventStats](arkts-backgroundtasks-usagestatistics-querynotificationeventstats-f-sys.md#querynotificationeventstats1) | Queries app notification number within a specified period identified by the start and end time. |
| [queryNotificationEventStats](arkts-backgroundtasks-usagestatistics-querynotificationeventstats-f-sys.md#querynotificationeventstats2) | Queries app notification number within a specified period identified by the start and end time. |
| [registerAppGroupCallBack](arkts-backgroundtasks-usagestatistics-registerappgroupcallback-f-sys.md#registerappgroupcallback1) | Register appGroup change callback to service. |
| [registerAppGroupCallBack](arkts-backgroundtasks-usagestatistics-registerappgroupcallback-f-sys.md#registerappgroupcallback2) | Register appGroup change callback to service. |
| [setAppGroup](arkts-backgroundtasks-usagestatistics-setappgroup-f-sys.md#setappgroup1) | Set app group by bundleName. |
| [setAppGroup](arkts-backgroundtasks-usagestatistics-setappgroup-f-sys.md#setappgroup2) | Set app group by bundleName. |
| [unregisterAppGroupCallBack](arkts-backgroundtasks-usagestatistics-unregisterappgroupcallback-f-sys.md#unregisterappgroupcallback1) | Unregister appGroup change callback from service. |
| [unregisterAppGroupCallBack](arkts-backgroundtasks-usagestatistics-unregisterappgroupcallback-f-sys.md#unregisterappgroupcallback2) | Unregister appGroup change callback from service. |
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
### Types(System API)

| Name | Description |
| --- | --- |
| [AppStatsMap](arkts-backgroundtasks-usagestatistics-appstatsmap-t-sys.md) |  |
| [BundleStatsMap](arkts-backgroundtasks-usagestatistics-bundlestatsmap-t-sys.md) |  |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [GroupType](arkts-backgroundtasks-usagestatistics-grouptype-e-sys.md) | Declares group type. |
| [IntervalType](arkts-backgroundtasks-usagestatistics-intervaltype-e-sys.md) | Declares interval type. |
<!--DelEnd-->
