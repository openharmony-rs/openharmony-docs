# @ohos.FusionConnectivity.ranging(融合测距模块)

本模块基于星闪技术，为应用提供设备测距功能，适用于智能防丢、近场找物、数字钥匙等需要获取设备间精确距离的场景。主要功能特性包括：

支持近场链路星闪HADM测距类型，实现高精度距离测量。支持主动测距模式，获取目标设备的距离、角度和信号强度信息。支持被动测距模式，设备可作为测距信标被其他设备发现和测量。支持测距状态变化订阅，实时监听设备测距开始、停止等状态通知。

**起始版本**：26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getRangingCapability](arkts-connectivity-ranging-getrangingcapability-f.md) | 查询本端设备支持的测距能力，使用Promise异步回调。 |
| [isRangingSupported](arkts-connectivity-ranging-israngingsupported-f.md) | 判断本端设备是否支持测距特性。 |
| [offRangingStateChange](arkts-connectivity-ranging-offrangingstatechange-f.md) | 注销测距状态变化回调。 |
| [onRangingStateChange](arkts-connectivity-ranging-onrangingstatechange-f.md) | 注册测距状态变化回调，监听测距状态通知。 |
| [startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md) | 启动被动测距模式。本端设备将作为测距信标广播测距数据包，允许其他支持对应测距类型的主动测距设备发现本端设备。典型应用场景包括：本端设备作为被定位标签或防丢贴片、固定信标部署等，适用于本端需要被其他设备测量距离的场景。 |
| [startRanging](arkts-connectivity-ranging-startranging-f.md) | 向指定设备发起主动测距，获取目标设备的距离和信号强度等信息。典型应用场景包括：智能防丢与寻找、近场找物、数字钥匙等。 |
| [stopPassiveRanging](arkts-connectivity-ranging-stoppassiveranging-f.md) | 停止被动测距模式。根据指定的句柄和测距类型停止对应的被动测距广播，并清理相关资源。 |
| [stopRanging](arkts-connectivity-ranging-stopranging-f.md) | 停止正在进行中的主动测距。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [RangingCapabilitySupported](arkts-connectivity-ranging-rangingcapabilitysupported-i.md) | 描述设备支持的测距类型。 |
| [RangingMeasurement](arkts-connectivity-ranging-rangingmeasurement-i.md) | 描述测量结果，包含测量值和对应的置信度。测量结果可用于距离测量或角度测量。 |
| [RangingParams](arkts-connectivity-ranging-rangingparams-i.md) | 测距参数，用于指定主动测距的目标设备和测距类型。 |
| [RangingResult](arkts-connectivity-ranging-rangingresult-i.md) | 描述测距结果，每次测距测量完成后通过[startRanging](arkts-connectivity-ranging-startranging-f.md)的callback回调返回。 |
| [RangingStateChangeInfo](arkts-connectivity-ranging-rangingstatechangeinfo-i.md) | 描述测距状态变化信息，主动测距和被动测距的状态变化共用此结构。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RangingConfidence](arkts-connectivity-ranging-rangingconfidence-e.md) | 枚举，测距测量置信度，表示测量结果值的可信程度。 |
| [RangingState](arkts-connectivity-ranging-rangingstate-e.md) | 枚举，测距状态。 |
| [RangingStoppedCause](arkts-connectivity-ranging-rangingstoppedcause-e.md) | 枚举，测距停止原因。 |
| [RangingTypes](arkts-connectivity-ranging-rangingtypes-e.md) | 枚举，测距能力类型。 |
