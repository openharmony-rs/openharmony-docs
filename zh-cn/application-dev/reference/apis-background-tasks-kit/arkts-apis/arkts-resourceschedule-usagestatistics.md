# @ohos.resourceschedule.usageStatistics

本模块提供设备使用信息统计能力，包括查询应用是否为常用应用、优先级分组、使用时长、系统事件（休眠、唤醒、解锁、锁屏）信息、应用事件（前台、后台、长时任务开始和结束）信息、通知次数等不同类型信息。
> **说明：**  
>  
> 本模块接口为系统接口。

**起始版本：** 9

<!--Device-unnamed-declare namespace usageStatistics--><!--Device-unnamed-declare namespace usageStatistics-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## 导入模块

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [isIdleState](arkts-backgroundtasks-usagestatistics-isidlestate-f-sys.md#isidlestate) | 查询指定的应用是否为常用应用（GroupType值≤30），使用Callback形式返回。 |
| [isIdleState](arkts-backgroundtasks-usagestatistics-isidlestate-f-sys.md#isidlestate-1) | 查询指定的应用是否为常用应用（GroupType值≤30），使用Promise异步回调。 |
| [isIdleStateSync](arkts-backgroundtasks-usagestatistics-isidlestatesync-f-sys.md#isidlestatesync) | 查询指定的应用是否为常用应用（GroupType值≤30），使用同步方式返回。 |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup) | 查询当前应用的优先级分组，使用Callback异步回调。 |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup-1) | 查询当前应用的优先级分组，使用Promise异步回调。 |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup-2) | 查询指定bundleName应用的优先级分组，使用Callback异步回调。 |
| [queryAppGroup](arkts-backgroundtasks-usagestatistics-queryappgroup-f-sys.md#queryappgroup-3) | 查询指定bundleName应用的优先级分组，使用Promise异步回调。 |
| [queryAppGroupSync](arkts-backgroundtasks-usagestatistics-queryappgroupsync-f-sys.md#queryappgroupsync) | 查询当前应用的优先级分组，使用同步方式返回。 |
| [queryAppGroupSync](arkts-backgroundtasks-usagestatistics-queryappgroupsync-f-sys.md#queryappgroupsync-1) | 查询指定bundleName应用的优先级分组，使用同步方式返回。 |
| [queryAppStatsInfos](arkts-backgroundtasks-usagestatistics-queryappstatsinfos-f-sys.md#queryappstatsinfos) | 通过指定起始和结束时间，查询应用使用时长的具体信息（包含分身应用），统计的最小颗粒度是天。使用Promise异步回调。 |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents) | 通过指定起始和结束时间，查询所有应用的事件集合，使用Callback异步回调。 |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents-1) | 通过指定起始和结束时间，查询所有应用的事件集合，使用Promise异步回调。 |
| [queryBundleEvents](arkts-backgroundtasks-usagestatistics-querybundleevents-f-sys.md#querybundleevents-2) | 通过指定起始时间、结束时间及最大返回条数，查询指定时间段内所有应用的事件集合。若条数大于maxNum，则按事件发生时间降序排列，返回前maxNum条，否则返回所有数据。使用Promise异步回调。 |
| [queryBundleStatsInfoByInterval](arkts-backgroundtasks-usagestatistics-querybundlestatsinfobyinterval-f-sys.md#querybundlestatsinfobyinterval) | 通过指定时间段间隔（天、周、月、年），查询应用使用时长的统计信息，使用Callback异步回调。 |
| [queryBundleStatsInfoByInterval](arkts-backgroundtasks-usagestatistics-querybundlestatsinfobyinterval-f-sys.md#querybundlestatsinfobyinterval-1) | 通过指定时间段间隔（天、周、月、年），查询应用使用时长的统计信息，使用Promise异步回调。 |
| [queryBundleStatsInfos](arkts-backgroundtasks-usagestatistics-querybundlestatsinfos-f-sys.md#querybundlestatsinfos) | 通过指定起始和结束时间，查询应用使用时长的具体信息，统计的最小颗粒度是天，使用Callback异步回调。 |
| [queryBundleStatsInfos](arkts-backgroundtasks-usagestatistics-querybundlestatsinfos-f-sys.md#querybundlestatsinfos-1) | 通过指定起始和结束时间，查询应用使用时长的具体信息，统计的最小颗粒度是天，使用Promise异步回调。 |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents) | 通过指定起始和结束时间，查询当前应用的事件集合，使用Callback异步回调。 |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents-1) | 通过指定起始和结束时间段内，查询当前应用的事件集合，使用Promise异步回调。 |
| [queryCurrentBundleEvents](arkts-backgroundtasks-usagestatistics-querycurrentbundleevents-f-sys.md#querycurrentbundleevents-2) | 通过指定起始时间、结束时间及最大返回条数，查询指定时间段内当前应用的事件集合。若条数大于maxNum，则按事件发生时间降序排列，返回前maxNum条，否则返回所有数据。使用Promise异步回调。 |
| [queryDeviceEventStats](arkts-backgroundtasks-usagestatistics-querydeviceeventstats-f-sys.md#querydeviceeventstats) | 通过指定起始和结束时间，查询系统事件（休眠、唤醒、解锁、锁屏）的统计信息，使用Callback异步回调。 |
| [queryDeviceEventStats](arkts-backgroundtasks-usagestatistics-querydeviceeventstats-f-sys.md#querydeviceeventstats-1) | 通过指定起始和结束时间，查询系统事件（休眠、唤醒、解锁、锁屏）的统计信息，使用Promise异步回调。 |
| [queryLastUseTime](arkts-backgroundtasks-usagestatistics-querylastusetime-f-sys.md#querylastusetime) | 通过指定bundleName和应用的index，查询应用使用具体信息，统计的最小颗粒度是天，使用Promise异步回调。 |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords) | 根据设置的maxNum，查询FA模型下各应用不用Hap包的使用记录。若Hap包中存在FA卡片，使用信息中也包含卡片信息。使用Callback异步回调。 |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords-1) | 根据设置的maxNum，查询FA模型下各应用不用Hap包的使用记录。若Hap包中存在FA卡片，使用信息中也包含卡片信息。使用Promise异步回调。 |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords-2) | 查询FA模型下各应用不用Hap包的使用记录（不超过1000条）。若Hap包中存在FA卡片，使用信息中也包含卡片信息。使用CallBack异步回调。 |
| [queryModuleUsageRecords](arkts-backgroundtasks-usagestatistics-querymoduleusagerecords-f-sys.md#querymoduleusagerecords-3) | 查询FA模型下各应用不用Hap包的使用记录（不超过1000条）。若Hap包中存在FA卡片，使用信息中也包含卡片信息。使用Promise异步回调。  使用Promise形式返回不超过1000条FA使用记录，FA使用记录由近及远排序。 |
| [queryNotificationEventStats](arkts-backgroundtasks-usagestatistics-querynotificationeventstats-f-sys.md#querynotificationeventstats) | 通过指定起始和结束时间，查询所有应用的通知次数，使用Callback异步回调。 |
| [queryNotificationEventStats](arkts-backgroundtasks-usagestatistics-querynotificationeventstats-f-sys.md#querynotificationeventstats-1) | 通过指定起始和结束时间，查询所有应用的通知次数，使用Promise异步回调。 |
| [registerAppGroupCallBack](arkts-backgroundtasks-usagestatistics-registerappgroupcallback-f-sys.md#registerappgroupcallback) | 应用注册分组变化监听，即用户名下的某个应用分组发生变化时，向所有已注册分组变化监听的应用返回[AppGroupCallbackInfo](arkts-backgroundtasks-usagestatistics-appgroupcallbackinfo-i-sys.md)信息。使用Callback异步回调。 |
| [registerAppGroupCallBack](arkts-backgroundtasks-usagestatistics-registerappgroupcallback-f-sys.md#registerappgroupcallback-1) | 注册应用分组变化监听，即用户名下的某个应用分组发生变化时，向所有已注册分组变化监听的应用返回[AppGroupCallbackInfo](arkts-backgroundtasks-usagestatistics-appgroupcallbackinfo-i-sys.md)信息。使用Promise异步回调。 |
| [setAppGroup](arkts-backgroundtasks-usagestatistics-setappgroup-f-sys.md#setappgroup) | 将指定bundleName应用的分组设置为newGroup，仅支持当前应用为其他应用设置，使用CallBack异步回调。 |
| [setAppGroup](arkts-backgroundtasks-usagestatistics-setappgroup-f-sys.md#setappgroup-1) | 将指定bundleName应用的分组设置为newGroup，仅支持当前应用为其他应用设置，使用Promise异步回调。 |
| [unregisterAppGroupCallBack](arkts-backgroundtasks-usagestatistics-unregisterappgroupcallback-f-sys.md#unregisterappgroupcallback) | 应用解除分组变化监听。使用callback异步回调。 |
| [unregisterAppGroupCallBack](arkts-backgroundtasks-usagestatistics-unregisterappgroupcallback-f-sys.md#unregisterappgroupcallback-1) | 应用解除分组变化监听。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppGroupCallbackInfo](arkts-backgroundtasks-usagestatistics-appgroupcallbackinfo-i-sys.md) | 应用分组变化回调返回的属性集合 |
| [BundleEvents](arkts-backgroundtasks-usagestatistics-bundleevents-i-sys.md) | FA模型的使用信息属性集合。 |
| [BundleStatsInfo](arkts-backgroundtasks-usagestatistics-bundlestatsinfo-i-sys.md) | FA模型的使用信息属性集合。 |
| [DeviceEventStats](arkts-backgroundtasks-usagestatistics-deviceeventstats-i-sys.md) | FA模型的使用信息属性集合。 |
| [HapFormInfo](arkts-backgroundtasks-usagestatistics-hapforminfo-i-sys.md) | FA模型的使用信息属性集合。 |
| [HapModuleInfo](arkts-backgroundtasks-usagestatistics-hapmoduleinfo-i-sys.md) | FA模型的使用信息属性集合。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [GroupType](arkts-backgroundtasks-usagestatistics-grouptype-e-sys.md) | 应用分组的设置类型。 |
| [IntervalType](arkts-backgroundtasks-usagestatistics-intervaltype-e-sys.md) | 应用使用时长的查询类型。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppStatsMap](arkts-backgroundtasks-usagestatistics-appstatsmap-t-sys.md) |  |
| [BundleStatsMap](arkts-backgroundtasks-usagestatistics-bundlestatsmap-t-sys.md) | FA模型的使用信息属性集合。 |
<!--DelEnd-->

