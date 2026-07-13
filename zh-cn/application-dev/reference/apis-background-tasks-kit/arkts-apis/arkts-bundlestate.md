# @ohos.bundleState

本模块提供设备使用信息统计能力。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [isIdleState](arkts-backgroundtasks-isidlestate-f.md#isidlestate-1) | 判断指定bundleName的应用当前是否是空闲状态，三方应用只能查询自身的空闲状态。系统应用支持查询其他应用的空闲状态，查询前需要申请权限ohos.permission.BUNDLE_ACTIVE_INFO。使用Callback异步回调。 |
| [isIdleState](arkts-backgroundtasks-isidlestate-f.md#isidlestate-2) | 判断指定bundleName的应用当前是否是空闲状态，三方应用只能查询自身的空闲状态。系统应用支持查询其他应用的空闲状态，查询前需要申请权限ohos.permission.BUNDLE_ACTIVE_INFO，使用Promise异步回调。 |
| [queryAppUsagePriorityGroup](arkts-backgroundtasks-queryappusageprioritygroup-f.md#queryappusageprioritygroup-1) | Queries the usage priority group of the calling application.The priority defined in a priority group restricts the resource usage of an application,for example, restricting the running of background tasks. |
| [queryAppUsagePriorityGroup](arkts-backgroundtasks-queryappusageprioritygroup-f.md#queryappusageprioritygroup-2) | Queries the usage priority group of the calling application.The priority defined in a priority group restricts the resource usage of an application,for example, restricting the running of background tasks. |
| [queryCurrentBundleActiveStates](arkts-backgroundtasks-querycurrentbundleactivestates-f.md#querycurrentbundleactivestates-1) | Queries state data of the current bundle within a specified period. |
| [queryCurrentBundleActiveStates](arkts-backgroundtasks-querycurrentbundleactivestates-f.md#querycurrentbundleactivestates-2) | Queries state data of the current bundle within a specified period. |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [queryBundleActiveStates](arkts-backgroundtasks-querybundleactivestates-f-sys.md#querybundleactivestates-1) | Queries state data of all bundles within a specified period identified by the start and end time. |
| [queryBundleActiveStates](arkts-backgroundtasks-querybundleactivestates-f-sys.md#querybundleactivestates-2) | Queries state data of all bundles within a specified period identified by the start and end time. |
| [queryBundleStateInfoByInterval](arkts-backgroundtasks-querybundlestateinfobyinterval-f-sys.md#querybundlestateinfobyinterval-1) | Queries usage information about each bundle within a specified period at a specified interval. |
| [queryBundleStateInfoByInterval](arkts-backgroundtasks-querybundlestateinfobyinterval-f-sys.md#querybundlestateinfobyinterval-2) | Queries usage information about each bundle within a specified period at a specified interval. |
| [queryBundleStateInfos](arkts-backgroundtasks-querybundlestateinfos-f-sys.md#querybundlestateinfos-1) | Queries usage information about each bundle within a specified period.This method queries usage information at the {@link #BY_OPTIMIZED} interval by default. |
| [queryBundleStateInfos](arkts-backgroundtasks-querybundlestateinfos-f-sys.md#querybundlestateinfos-2) | Queries usage information about each bundle within a specified period.This method queries usage information at the {@link #BY_OPTIMIZED} interval by default. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleActiveInfoResponse](arkts-backgroundtasks-bundleactiveinforesponse-i.md) |  |
| [BundleActiveState](arkts-backgroundtasks-bundleactivestate-i.md) |  |
| [BundleStateInfo](arkts-backgroundtasks-bundlestateinfo-i.md) |  |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IntervalType](arkts-backgroundtasks-intervaltype-e.md) | Declares interval type. |

