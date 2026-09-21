# @ohos.distributed.softbusBase(This module provides the capabilities for device perception.)

**softbusBase**模块提供设备感知的API，包括启动感知和停止感知。广告、启动和停止感知扫描、广告主切换到高频、获取发现的设备列表。通过这些API，系统应用程序可以在感知中携带自定义负载广告以唤醒周围的协作设备，扫描以发现周围的感知设备。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPerceptionDeviceList](arkts-distributedservice-softbusbase-getperceptiondevicelist-f-sys.md) | 获取感知扫描发现的设备列表。在调用该接口之前，请先调用[startPerceptionScan](arkts-distributedservice-softbusbase-startperceptionscan-f-sys.md)开始扫描。停止扫描后调用[stopPerceptionScan](arkts-distributedservice-softbusbase-stopperceptionscan-f-sys.md)，清除已发现设备列表。 |
| [setPerceptionAdvHighFreq](arkts-distributedservice-softbusbase-setperceptionadvhighfreq-f-sys.md) | 将活跃感知广播主切换为高频，持续10s。高频期后到期后，广播会自动恢复到之前的频率。自定义负载可以在同样的时间。 |
| [startPerceptionAdv](arkts-distributedservice-softbusbase-startperceptionadv-f-sys.md) | 启动感知广播或更新当前所有者的广告中携带的自定义负载。广播开始，周围正在扫描的设备可以发现当前设备。 |
| [startPerceptionScan](arkts-distributedservice-softbusbase-startperceptionscan-f-sys.md) | 开始对当前owner进行感知扫描。启动扫描后，周围的设备广播可以被发现。发现的设备可以通过调用[getPerceptionDeviceList](arkts-distributedservice-softbusbase-getperceptiondevicelist-f-sys.md). |
| [stopPerceptionAdv](arkts-distributedservice-softbusbase-stopperceptionadv-f-sys.md) | 停止当前所有者的感知广播。停止广播后，周边设备无法通过扫描发现当前设备。 |
| [stopPerceptionScan](arkts-distributedservice-softbusbase-stopperceptionscan-f-sys.md) | 停止感知扫描，清除当前所有者的已发现设备列表。扫描后是停止，以前发现的设备列表将被清除，并且无法再通过调用[getPerceptionDeviceList](arkts-distributedservice-softbusbase-getperceptiondevicelist-f-sys.md). |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PerceptionDeviceInfo](arkts-distributedservice-softbusbase-perceptiondeviceinfo-i-sys.md) | 定义感知扫描发现的设备信息，包括设备类型、设备ID、自定义广告中携带的数据。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PerceptionCycle](arkts-distributedservice-softbusbase-perceptioncycle-e-sys.md) | 定义感知扫描的保活周期级别。级别越高，保活周期越短。 |
| [PerceptionType](arkts-distributedservice-softbusbase-perceptiontype-e-sys.md) | 定义感知业务类型。 |
<!--DelEnd-->
