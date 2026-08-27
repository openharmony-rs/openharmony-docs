# @ohos.distributedDeviceManager

本模块提供分布式设备管理能力，包括设备的发现、认证、状态监听和信息查询等功能。设备管理基于设备信任模型， 通过发现周边设备并进行认证绑定来建立可信连接，已认证的可信设备可用于分布式业务。应用可调用接口实现如下功能：  
- 注册和解除注册设备上下线变化监听。  
- 发现周边不可信设备。  
- 认证和取消认证设备。  
- 查询可信设备列表。  
- 查询本地设备信息，包括设备名称，设备类型和设备标识等。

> **说明：**
> 
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createDeviceManager](arkts-distributedservice-distributeddevicemanager-createdevicemanager-f.md) | 创建一个设备管理实例，是分布式设备管理方法的调用入口。该实例用于获取可信设备列表以及本地设备的名称、 类型、标识和网络标识等信息。当设备管理实例不再使用时，应调用releaseDeviceManager释放该实例，避免资源泄漏。 |
| [releaseDeviceManager](arkts-distributedservice-distributeddevicemanager-releasedevicemanager-f.md) | 设备管理实例不再使用后，通过该方法释放DeviceManager实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DeviceBasicInfo](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md) | 分布式设备基本信息。 |
| [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md) | 设备管理实例，是分布式设备管理方法的调用入口，提供设备发现、设备认证、状态监听和信息查询等能力。 在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceIconInfo](arkts-distributedservice-distributeddevicemanager-deviceiconinfo-i-sys.md) | 设备图标信息。 |
| [DeviceIconInfoFilterOptions](arkts-distributedservice-distributeddevicemanager-deviceiconinfofilteroptions-i-sys.md) | 设备图标信息过滤选项。 |
| [DeviceIdentification](arkts-distributedservice-distributeddevicemanager-deviceidentification-i-sys.md) | 用于分布式设备识别的结构体。 |
| [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i-sys.md) | 设备管理实例，是分布式设备管理方法的调用入口，提供设备发现、设备认证、状态监听和信息查询等能力。 在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。 |
| [DeviceProfileInfo](arkts-distributedservice-distributeddevicemanager-deviceprofileinfo-i-sys.md) | 设备信息。 |
| [DeviceProfileInfoFilterOptions](arkts-distributedservice-distributeddevicemanager-deviceprofileinfofilteroptions-i-sys.md) | 设备信息过滤器选项。 |
| [NetworkIdQueryFilter](arkts-distributedservice-distributeddevicemanager-networkidqueryfilter-i-sys.md) | 设备网络ID过滤器选项。 |
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
