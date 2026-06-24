# @ohos.distributedHardware.deviceManager

本模块能力已更新至新模块。建议使用新模块的接口进行开发，参见
[@ohos.distributedDeviceManager](arkts-distributeddevicemanager.md#distributedDeviceManager)。
本模块提供分布式设备管理能力。
系统应用可调用接口实现如下功能：

- 注册和解除注册设备上下线变化监听。
- 发现周边不可信设备。
- 认证和取消认证设备。
- 查询可信设备列表。
- 查询本地设备信息，包括设备名称，设备类型和设备标识。
- 发布设备发现。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [distributedDeviceManager:distributedDeviceManager](arkts-distributeddevicemanager.md#distributedDeviceManager)

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[createDeviceManager](arkts-distributedservice-devicemanager-createdevicemanager-f-sys.md#createDeviceManager-1) | 创建一个设备管理器实例。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[AuthInfo](arkts-distributedservice-devicemanager-authinfo-i-sys.md) | 认证信息。<br/> |
| <!--DelRow-->[AuthParam](arkts-distributedservice-devicemanager-authparam-i-sys.md) | 认证参数。<br/> |
| <!--DelRow-->[DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md) | 设备信息。<br/> |
| <!--DelRow-->[DeviceManager](arkts-distributedservice-devicemanager-devicemanager-i-sys.md) | 设备管理实例，用于获取可信设备和本地设备的相关信息。在调用DeviceManager的方法前，需要先通过createDeviceManager构建一个DeviceManager实例dmInstance。<br/> |
| <!--DelRow-->[PublishInfo](arkts-distributedservice-devicemanager-publishinfo-i-sys.md) | 发布设备参数<br/> |
| <!--DelRow-->[SubscribeInfo](arkts-distributedservice-devicemanager-subscribeinfo-i-sys.md) | 发现信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[AuthForm](arkts-distributedservice-devicemanager-authform-e-sys.md) | 表示设备认证类型的枚举类。<br/> |
| <!--DelRow-->[DeviceStateChangeAction](arkts-distributedservice-devicemanager-devicestatechangeaction-e-sys.md) | 表示设备状态变化的枚举。<br/> |
| <!--DelRow-->[DeviceType](arkts-distributedservice-devicemanager-devicetype-e-sys.md) | 表示设备类型的枚举类。<br/> |
| <!--DelRow-->[DiscoverMode](arkts-distributedservice-devicemanager-discovermode-e-sys.md) | 表示发现模式的枚举。<br/> |
| <!--DelRow-->[ExchangeFreq](arkts-distributedservice-devicemanager-exchangefreq-e-sys.md) | 表示发现频率的枚举。<br/> |
| <!--DelRow-->[ExchangeMedium](arkts-distributedservice-devicemanager-exchangemedium-e-sys.md) | 表示发现类型的枚举。<br/> |
| <!--DelRow-->[SubscribeCap](arkts-distributedservice-devicemanager-subscribecap-e-sys.md) | 表示发现能力的枚举。<br/> |

