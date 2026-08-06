# @ohos.distributedDeviceManager

本模块提供分布式设备管理能力。 应用可调用接口实现如下功能： - 注册和解除注册设备上下线变化监听。 - 发现周边不可信设备。 - 认证和取消认证设备。 - 查询可信设备列表。 - 查询本地设备信息，包括设备名称，设备类型和设备标识等。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace distributedDeviceManager--><!--Device-unnamed-declare namespace distributedDeviceManager-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createDeviceManager](arkts-distributedservice-distributeddevicemanager-createdevicemanager-f.md#createdevicemanager) | 创建一个设备管理实例。设备管理实例是分布式设备管理方法的调用入口。用于获取可信设备和本地设备的相关信息。 |
| [releaseDeviceManager](arkts-distributedservice-distributeddevicemanager-releasedevicemanager-f.md#releasedevicemanager) | 设备管理实例不再使用后，通过该方法释放DeviceManager实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BindTargetResult](arkts-distributedservice-distributeddevicemanager-bindtargetresult-i.md) | 认证设备结果信息。 |
| [DeviceBasicInfo](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md) | 分布式设备基本信息。 |
| [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md) | 设备管理实例，用于获取可信设备和本地设备的相关信息。在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。 |
| [DeviceNameChangeResult](arkts-distributedservice-distributeddevicemanager-devicenamechangeresult-i.md) | 设备名字改变结果信息。 |
| [DeviceStateChangeResult](arkts-distributedservice-distributeddevicemanager-devicestatechangeresult-i.md) | 设备状态改变结果信息。 |
| [DiscoveryFailureResult](arkts-distributedservice-distributeddevicemanager-discoveryfailureresult-i.md) | 设备发现失败原因。 |
| [DiscoverySuccessResult](arkts-distributedservice-distributeddevicemanager-discoverysuccessresult-i.md) | 设备发现成功，发现的设备信息。 |
| [ServiceDieData](arkts-distributedservice-distributeddevicemanager-servicediedata-i.md) | DeviceManager 服务进程退出信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceIconInfo](arkts-distributedservice-distributeddevicemanager-deviceiconinfo-i-sys.md) | 设备图标信息。 |
| [DeviceIconInfoFilterOptions](arkts-distributedservice-distributeddevicemanager-deviceiconinfofilteroptions-i-sys.md) | 设备图标信息过滤选项。 |
| [DeviceIdentification](arkts-distributedservice-distributeddevicemanager-deviceidentification-i-sys.md) | 用于分布式设备识别的结构体。 |
| [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i-sys.md) | 设备管理实例，用于获取可信设备和本地设备的相关信息。在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。 |
| [DeviceProfileInfo](arkts-distributedservice-distributeddevicemanager-deviceprofileinfo-i-sys.md) | 设备信息。 |
| [DeviceProfileInfoFilterOptions](arkts-distributedservice-distributeddevicemanager-deviceprofileinfofilteroptions-i-sys.md) | 设备信息过滤器选项。 |
| [NetworkIdQueryFilter](arkts-distributedservice-distributeddevicemanager-networkidqueryfilter-i-sys.md) | 设备网络ID过滤器选项。 |
| [ReplyResult](arkts-distributedservice-distributeddevicemanager-replyresult-i-sys.md) | 分布式设备基本信息。 |
| [ServiceProfileInfo](arkts-distributedservice-distributeddevicemanager-serviceprofileinfo-i-sys.md) | 服务配置信息。根据云端返回的数据填充。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DeviceStateChange](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md) | 表示设备状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [StrategyForHeartbeat](arkts-distributedservice-distributeddevicemanager-strategyforheartbeat-e-sys.md) | 表示心跳广播策略。 |
<!--DelEnd-->

