# @ohos.bundleState

本模块提供设备使用信息统计能力。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [isIdleState](arkts-backgroundtasks-bundlestate-isidlestate-f.md#isIdleState-1) | 判断指定bundleName的应用当前是否是空闲状态，三方应用只能查询自身的空闲状态。系统应用支持查询其他应用的空闲状态，查询前需要申请权限ohos.permission.BUNDLE_ACTIVE_INFO。使用Callback<br/>异步回调。<br/> |
| [isIdleState](arkts-backgroundtasks-bundlestate-isidlestate-f.md#isIdleState-2) | 判断指定bundleName的应用当前是否是空闲状态，三方应用只能查询自身的空闲状态。系统应用支持查询其他应用的空闲状态，查询前需要申请权限ohos.permission.BUNDLE_ACTIVE_INFO，使用Promise异<br/>步回调。<br/> |
| [queryAppUsagePriorityGroup](arkts-backgroundtasks-bundlestate-queryappusageprioritygroup-f.md#queryAppUsagePriorityGroup-1) | Queries the usage priority group of the calling application.<br/><br/>The priority defined in a priority group restricts the resource usage of an application,<br/>for example, restricting the running of background tasks.<br/> |
| [queryAppUsagePriorityGroup](arkts-backgroundtasks-bundlestate-queryappusageprioritygroup-f.md#queryAppUsagePriorityGroup-2) | Queries the usage priority group of the calling application.<br/><br/>The priority defined in a priority group restricts the resource usage of an application,<br/>for example, restricting the running of background tasks.<br/> |
| <!--DelRow-->[queryBundleActiveStates](arkts-backgroundtasks-bundlestate-querybundleactivestates-f-sys.md#queryBundleActiveStates-1) | Queries state data of all bundles within a specified period identified by the start and end time.<br/> |
| <!--DelRow-->[queryBundleActiveStates](arkts-backgroundtasks-bundlestate-querybundleactivestates-f-sys.md#queryBundleActiveStates-2) | Queries state data of all bundles within a specified period identified by the start and end time.<br/> |
| <!--DelRow-->[queryBundleStateInfoByInterval](arkts-backgroundtasks-bundlestate-querybundlestateinfobyinterval-f-sys.md#queryBundleStateInfoByInterval-1) | Queries usage information about each bundle within a specified period at a specified interval.<br/> |
| <!--DelRow-->[queryBundleStateInfoByInterval](arkts-backgroundtasks-bundlestate-querybundlestateinfobyinterval-f-sys.md#queryBundleStateInfoByInterval-2) | Queries usage information about each bundle within a specified period at a specified interval.<br/> |
| <!--DelRow-->[queryBundleStateInfos](arkts-backgroundtasks-bundlestate-querybundlestateinfos-f-sys.md#queryBundleStateInfos-1) | Queries usage information about each bundle within a specified period.<br/><br/>This method queries usage information at the {@link #BY_OPTIMIZED} interval by default.<br/> |
| <!--DelRow-->[queryBundleStateInfos](arkts-backgroundtasks-bundlestate-querybundlestateinfos-f-sys.md#queryBundleStateInfos-2) | Queries usage information about each bundle within a specified period.<br/><br/>This method queries usage information at the {@link #BY_OPTIMIZED} interval by default.<br/> |
| [queryCurrentBundleActiveStates](arkts-backgroundtasks-bundlestate-querycurrentbundleactivestates-f.md#queryCurrentBundleActiveStates-1) | Queries state data of the current bundle within a specified period.<br/> |
| [queryCurrentBundleActiveStates](arkts-backgroundtasks-bundlestate-querycurrentbundleactivestates-f.md#queryCurrentBundleActiveStates-2) | Queries state data of the current bundle within a specified period.<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleActiveInfoResponse](arkts-backgroundtasks-bundlestate-bundleactiveinforesponse-i.md) |  |
| [BundleActiveState](arkts-backgroundtasks-bundlestate-bundleactivestate-i.md) |  |
| [BundleStateInfo](arkts-backgroundtasks-bundlestate-bundlestateinfo-i.md) |  |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IntervalType](arkts-backgroundtasks-bundlestate-intervaltype-e.md) | Declares interval type.<br/> |

