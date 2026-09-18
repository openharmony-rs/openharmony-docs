# cloudData(端云服务)

端云服务提供端云策略能力。<br> <br>端云策略提供端云同步策略配置的能力。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [sharing](arkts-arkdata-clouddata-sharing-n.md) | 提供端云共享的方法，包括发起共享、取消共享、退出共享、更改共享数据权限、查询共享参与者、确认邀请、更改已确认的邀请、查询共享资源。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [setCloudStrategy](arkts-arkdata-clouddata-setcloudstrategy-f.md) | 设置应用自身的云同步策略，使用Promise异步回调。 |
| [onAutoSyncTrigger](arkts-arkdata-clouddata-onautosynctrigger-f.md) | 在已打开端云同步且应用关闭自动同步的条件下，注册自动同步触发事件通知。当满足自动触发条件时，回调函数会被调用。 |
| [offAutoSyncTrigger](arkts-arkdata-clouddata-offautosynctrigger-f.md) | 取消订阅自动同步触发事件通知。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Config](arkts-arkdata-clouddata-config-c-sys.md) | 提供配置端云协同的方法，包括云同步打开、关闭、清除数据、数据变化通知。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AutoSyncTriggerInfo](arkts-arkdata-clouddata-autosynctriggerinfo-i.md) | 自动同步触发信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExtraData](arkts-arkdata-clouddata-extradata-i-sys.md) | 透传数据，携带通知数据变更所需要的信息。 |
| [StatisticInfo](arkts-arkdata-clouddata-statisticinfo-i-sys.md) | 端云同步的统计信息。 |
| [SyncInfo](arkts-arkdata-clouddata-syncinfo-i-sys.md) | 端云同步信息，包含最近一次端云同步的时间、结果和状态。 |
| [DBSwitchInfo](arkts-arkdata-clouddata-dbswitchinfo-i-sys.md) | 端云协同数据库开关配置信息。 |
| [SwitchConfig](arkts-arkdata-clouddata-switchconfig-i-sys.md) | 端云协同数据库级配置。 |
| [DBActionInfo](arkts-arkdata-clouddata-dbactioninfo-i-sys.md) | 端云协同数据库级清除规则。 |
| [ClearConfig](arkts-arkdata-clouddata-clearconfig-i-sys.md) | 端云协同数据库级清除规则。 |
| [BundleInfo](arkts-arkdata-clouddata-bundleinfo-i-sys.md) | 端云协同应用信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StrategyType](arkts-arkdata-clouddata-strategytype-e.md) | 云同步策略类型枚举。 |
| [NetWorkStrategy](arkts-arkdata-clouddata-networkstrategy-e.md) | 网络策略参数枚举。 |
| [AutoSyncTriggerMode](arkts-arkdata-clouddata-autosynctriggermode-e.md) | 自动同步触发模式枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ClearAction](arkts-arkdata-clouddata-clearaction-e-sys.md) | 清除本地下载的云端数据的行为枚举。 |
| [SyncStatus](arkts-arkdata-clouddata-syncstatus-e-sys.md) | 端云同步任务的状态。 |
<!--DelEnd-->

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DATA_CHANGE_EVENT_ID](arkts-arkdata-clouddata-con-sys.md#data_change_event_id) | 表示云数据变更。 |
<!--DelEnd-->
