# cloudData

端云服务提供端云协同和端云共享能力。
端云协同提供结构化数据（RDB Store，关系型数据库）端云同步的能力。即：云作为数据的中心节点，通过与云空间的数据同步，实现数据云备份、同账号设备间的数据一致性。
端云共享是在端云协同能力基础上，实现跨账号的数据共享。其中，端云共享资源标识是指：对于应用发起共享的每一条数据记录，该条数据在进行端云同步时会生成唯一的共享资源标识（字符串类型的值），此标识作为该条数据记录共享时的识别标识。
端云共享参与者是指：共享发起者根据好友列表选中的参与当前数据共享的所有人员。
端云共享邀请码是指：共享发起后，在共享的服务端会生成当前共享操作的邀请码，并将该邀请码附加到当前共享邀请中，通过推送消息推送到被邀请者的设备端，被邀请者可以通过该邀请码进行邀请的确认。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [sharing](arkts-arkdata-sharing-n.md) | 提供端云共享的方法，包括发起共享、取消共享、退出共享、更改共享数据权限、查找共享参与者、确认邀请、更改已确认的邀请、查找共享资源。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [setCloudStrategy](arkts-arkdata-setcloudstrategy-f.md#setcloudstrategy-1) | 设置应用自身的云同步策略，使用Promise异步回调。 |
| [onAutoSyncTrigger](arkts-arkdata-onautosynctrigger-f.md#onautosynctrigger-1) | 在已打开端云同步且应用关闭自动同步的条件下，注册自动同步触发事件通知。当满足自动触发条件时，回调函数会被调用。 |
| [offAutoSyncTrigger](arkts-arkdata-offautosynctrigger-f.md#offautosynctrigger-1) | 取消订阅自动同步触发事件通知。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Config](arkts-arkdata-config-c-sys.md) | 提供配置端云协同的方法，包括云同步打开、关闭、清除数据、数据变化通知。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AutoSyncTriggerInfo](arkts-arkdata-autosynctriggerinfo-i.md) | 自动同步触发信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ExtraData](arkts-arkdata-extradata-i-sys.md) | 透传数据，携带通知数据变更所需要的信息。 |
| [StatisticInfo](arkts-arkdata-statisticinfo-i-sys.md) | 端云同步的统计信息。 |
| [SyncInfo](arkts-arkdata-syncinfo-i-sys.md) | 端云同步信息，包含最近一次端云同步的时间、结果和状态。 |
| [DBSwitchInfo](arkts-arkdata-dbswitchinfo-i-sys.md) | 端云协同数据库开关配置信息。 |
| [SwitchConfig](arkts-arkdata-switchconfig-i-sys.md) | 端云协同数据库级配置。 |
| [DBActionInfo](arkts-arkdata-dbactioninfo-i-sys.md) | 端云协同数据库级清除配置信息。 |
| [ClearConfig](arkts-arkdata-clearconfig-i-sys.md) | 端云协同数据库级清除配置。 |
| [BundleInfo](arkts-arkdata-bundleinfo-i-sys.md) | 端云协同应用信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [StrategyType](arkts-arkdata-strategytype-e.md) | 云同步策略类型枚举。 |
| [NetWorkStrategy](arkts-arkdata-networkstrategy-e.md) | 网络策略参数枚举。 |
| [AutoSyncTriggerMode](arkts-arkdata-autosynctriggermode-e.md) | 自动同步触发模式枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ClearAction](arkts-arkdata-clearaction-e-sys.md) | 清除本地下载的云端数据的行为枚举。 |
| [SyncStatus](arkts-arkdata-syncstatus-e-sys.md) | 端云同步任务的状态。 |
<!--DelEnd-->

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DATA_CHANGE_EVENT_ID](arkts-arkdata-clouddata-con-sys.md#data_change_event_id) | 表示云数据变更。 |
<!--DelEnd-->

