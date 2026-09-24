# @ohos.bluetooth.pbap(蓝牙pbap模块)

本模块提供基于电话簿访问协议（Phone Book Access Profile，PBAP）的蓝牙电话簿访问能力，支持创建PSE服务端实例、获取设备间蓝牙电话簿服务连接状态等，适用于本端设备作为PSE对外提供电话簿访问服务的场景，可帮助开发者快速实现蓝牙电话簿的共享与连接管理功能。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { pbap } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createPbapClientProfile](arkts-connectivity-pbap-createpbapclientprofile-f.md) | 创建PBAP客户端配置文件的实例。 |
| [createPbapServerProfile](arkts-connectivity-pbap-createpbapserverprofile-f.md) | 创建蓝牙电话簿访问协议中的PSE实例。通过该实例可使用本端作为PSE设备的接口，如：获取本端和其他设备间的蓝牙电话簿服务连接状态。典型使用场景包括：车载蓝牙系统访问手机电话簿、跨设备联系人同步等需要本端作为电话簿服务端的场景。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PbapClientProfile](arkts-connectivity-pbap-pbapclientprofile-i-sys.md) | 管理PBAP客户端配置文件。 |
| [PbapServerProfile](arkts-connectivity-pbap-pbapserverprofile-i-sys.md) | 使用PbapServerProfile方法之前需要创建该类的实例进行操作，通过createPbapServerProfile()方法构造此实例。 |
| [SyncStateChangeParam](arkts-connectivity-pbap-syncstatechangeparam-i-sys.md) | 电话本同步状态变化信息。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-pbap-baseprofile-t.md) | 基础Profile接口定义，提供订阅和获取连接状态等公共能力。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessAuthorization](arkts-connectivity-pbap-accessauthorization-t-sys.md) | 枚举，蓝牙访问授权状态。表示对端蓝牙设备访问本端蓝牙Profile（如电话簿、消息等）的授权状态，用于蓝牙数据访问授权场景。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ShareType](arkts-connectivity-pbap-sharetype-e-sys.md) | 枚举，共享类型。 |
| [SyncStateType](arkts-connectivity-pbap-syncstatetype-e-sys.md) | 电话本同步状态类型。 |
<!--DelEnd-->
