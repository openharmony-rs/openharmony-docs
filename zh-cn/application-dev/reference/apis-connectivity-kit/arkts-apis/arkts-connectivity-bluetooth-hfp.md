# @ohos.bluetooth.hfp(蓝牙hfp模块)

本模块提供基于免提协议（Hands-Free Profile， HFP）的蓝牙通话音频能力，支持创建HFP AG和HF实例、获取连接状态等。适用于需要在应用中实现蓝牙通话音频连接管理、监听通话音频连接状态等场景。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { hfp } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createHfpAgProfile](arkts-connectivity-hfp-createhfpagprofile-f.md) | 创建蓝牙通话音频中的HFP AG实例。通过该实例可使用本端作为HFP AG设备的接口，如：获取和其他设备间的蓝牙通话音频连接状态。典型应用场景包括车载信息娱乐系统的蓝牙通话功能、平板电脑蓝牙通话等，本端设备作为音频网关（AG）角色管理通话音频路由。 |
| [createHfpHfProfile](arkts-connectivity-hfp-createhfphfprofile-f.md) | 创建蓝牙通话音频中的HF实例。通过该实例可使用本端作为HF设备的接口，如：获取和其他设备间的蓝牙通话音频连接状态。典型应用场景包括蓝牙耳机的免提通话功能、车载免提系统等，本端设备作为免提（HF）角色接收和处理通话音频。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HandsFreeAudioGatewayProfile](arkts-connectivity-hfp-handsfreeaudiogatewayprofile-i-sys.md) | 该实例表示蓝牙通话音频中的HFP AG角色‌。 |
| [HandsFreeHfProfile](arkts-connectivity-hfp-handsfreehfprofile-i-sys.md) | 该实例表示蓝牙通话音频中的HF角色‌。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-hfp-baseprofile-t.md) | 基础Profile接口定义，提供订阅和获取连接状态等公共能力。 |
