# @ohos.distributedHardware.mechanicManager

提供与本设备连接的机械设备的控制和交互能力。包括连接管理、控制和监控功能

**起始版本：** 20

<!--Device-unnamed-declare namespace mechanicManager--><!--Device-unnamed-declare namespace mechanicManager-End-->

**系统能力：** SystemCapability.Mechanic.Core

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAttachedMechDevices](arkts-mechanic-mechanicmanager-getattachedmechdevices-f.md#getattachedmechdevices-1) | 获取已连接的机械设备列表 |
| [getCameraTrackingEnabled](arkts-mechanic-mechanicmanager-getcameratrackingenabled-f.md#getcameratrackingenabled-1) | 获取相机跟踪状态 |
| [getCameraTrackingLayout](arkts-mechanic-mechanicmanager-getcameratrackinglayout-f.md#getcameratrackinglayout-1) | 获取当前摄像头跟踪布局 |
| [isControlSupported](arkts-mechanic-mechanicmanager-iscontrolsupported-f.md#iscontrolsupported-1) | 判断当前设备是否支持某类设备的具身控制 |
| [off('attachStateChange')](arkts-mechanic-mechanicmanager-off-f.md#offattachstatechange) | 取消注册连接状态变化事件的回调监听。使用callback异步回调。 |
| [off('trackingStateChange')](arkts-mechanic-mechanicmanager-off-f.md#offtrackingstatechange) | 设置相机跟踪布局 |
| [on('attachStateChange')](arkts-mechanic-mechanicmanager-on-f.md#onattachstatechange) | 注册连接状态变化事件的回调监听，等待连接状态变化。使用callback异步回调。 |
| [on('trackingStateChange')](arkts-mechanic-mechanicmanager-on-f.md#ontrackingstatechange) | 注册跟踪状态变化事件的回调监听。使用callback异步回调。 |
| [setCameraTrackingEnabled](arkts-mechanic-mechanicmanager-setcameratrackingenabled-f.md#setcameratrackingenabled-1) | 启用或禁用摄像机跟踪 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [connectDevice](arkts-mechanic-mechanicmanager-connectdevice-f-sys.md#connectdevice-1) | 基于地址连接设备 |
| [disconnectDevice](arkts-mechanic-mechanicmanager-disconnectdevice-f-sys.md#disconnectdevice-1) | 基于具身设备ID断开设备 |
| [doAction](arkts-mechanic-mechanicmanager-doaction-f-sys.md#doaction-1) | 执行一个动作序列 |
| [getCurrentAngles](arkts-mechanic-mechanicmanager-getcurrentangles-f-sys.md#getcurrentangles-1) | 获取机械设备的当前角度 |
| [getDeviceAdsorbState](arkts-mechanic-mechanicmanager-getdeviceadsorbstate-f-sys.md#getdeviceadsorbstate-1) | 获取对应的设备吸附状态 |
| [getMaxRotationSpeed](arkts-mechanic-mechanicmanager-getmaxrotationspeed-f-sys.md#getmaxrotationspeed-1) | Obtains the maximum rotation speed of a mechanical device. |
| [getMaxRotationTime](arkts-mechanic-mechanicmanager-getmaxrotationtime-f-sys.md#getmaxrotationtime-1) | Obtains the maximum continuous rotation duration of a mechanical device. |
| [getRotationAxesStatus](arkts-mechanic-mechanicmanager-getrotationaxesstatus-f-sys.md#getrotationaxesstatus-1) | 获取当前转轴状态 |
| [getRotationLimits](arkts-mechanic-mechanicmanager-getrotationlimits-f-sys.md#getrotationlimits-1) | Obtains the maximum rotation angles relative to the reference point for the specified mechanical device. |
| [isSupportAction](arkts-mechanic-mechanicmanager-issupportaction-f-sys.md#issupportaction-1) | 判断是否支持某个动作 |
| [move](arkts-mechanic-mechanicmanager-move-f-sys.md#move-1) | 以特定参数移动一个具身设备 |
| [moveBySpeed](arkts-mechanic-mechanicmanager-movebyspeed-f-sys.md#movebyspeed-1) | 以特定速度移动一个具身设备 |
| [off('rotationAxesStatusChange')](arkts-mechanic-mechanicmanager-off-f-sys.md#offrotationaxesstatuschange) | 取消注册旋转轴状态变化事件的回调监听。使用callback异步回调。 |
| [offBatteryLevelChange](arkts-mechanic-mechanicmanager-offbatterylevelchange-f-sys.md#offbatterylevelchange-1) | 取消订阅电池电量变化信息 |
| [on('rotationAxesStatusChange')](arkts-mechanic-mechanicmanager-on-f-sys.md#onrotationaxesstatuschange) | 注册旋转轴状态变化事件的回调监听。使用callback异步回调。 |
| [onBatteryLevelChange](arkts-mechanic-mechanicmanager-onbatterylevelchange-f-sys.md#onbatterylevelchange-1) | 订阅目标设备的电池电量变化信息 |
| [rotate](arkts-mechanic-mechanicmanager-rotate-f-sys.md#rotate-1) | 将机械设备旋转到相对角度 |
| [rotateBySpeed](arkts-mechanic-mechanicmanager-rotatebyspeed-f-sys.md#rotatebyspeed-1) | 以指定的速度旋转机械设备 |
| [rotateToEulerAngles](arkts-mechanic-mechanicmanager-rotatetoeulerangles-f-sys.md#rotatetoeulerangles-1) | 将机械设备旋转到绝对角度 |
| [searchTarget](arkts-mechanic-mechanicmanager-searchtarget-f-sys.md#searchtarget-1) | 旋转机械体一周搜索目标。使用Promise异步回调。 |
| [setCameraTrackingLayout](arkts-mechanic-mechanicmanager-setcameratrackinglayout-f-sys.md#setcameratrackinglayout-1) | 设置相机跟踪布局 |
| [setUserOperation](arkts-mechanic-mechanicmanager-setuseroperation-f-sys.md#setuseroperation-1) | 设置用户操作 |
| [stopMoving](arkts-mechanic-mechanicmanager-stopmoving-f-sys.md#stopmoving-1) | 停止转动 |
| [subscribe](arkts-mechanic-mechanicmanager-subscribe-f-sys.md#subscribe-1) | 订阅具身设备事件回调 |
| [turnBySpeed](arkts-mechanic-mechanicmanager-turnbyspeed-f-sys.md#turnbyspeed-1) | 以固定速度原地旋转 |
| [unSubscribe](arkts-mechanic-mechanicmanager-unsubscribe-f-sys.md#unsubscribe-1) | 取消事件注册 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md) | 设备吸附状态回调信息@typedef AttachStateChangeInfo |
| [MechInfo](arkts-mechanic-mechanicmanager-mechinfo-i.md) | 机械设备信息@typedef MechInfo |
| [TrackingEventInfo](arkts-mechanic-mechanicmanager-trackingeventinfo-i.md) | 跟踪事件信息 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AddressInfo](arkts-mechanic-mechanicmanager-addressinfo-i-sys.md) | 配件设备信息定义 |
| [BatteryLevelInfo](arkts-mechanic-mechanicmanager-batterylevelinfo-i-sys.md) | 设备电池电量信息 |
| [ConnectParam](arkts-mechanic-mechanicmanager-connectparam-i-sys.md) | 连接参数定义 |
| [EulerAngles](arkts-mechanic-mechanicmanager-eulerangles-i-sys.md) | 相对于初始位置的绝对欧拉角 |
| [MechEvent](arkts-mechanic-mechanicmanager-mechevent-i-sys.md) | 具身设备事件定义 |
| [MoveParams](arkts-mechanic-mechanicmanager-moveparams-i-sys.md) | 设备移动参数 |
| [RotationAngles](arkts-mechanic-mechanicmanager-rotationangles-i-sys.md) | 相对当前位置的旋转角度@typedef RotationAngles |
| [RotationAxesStateChangeInfo](arkts-mechanic-mechanicmanager-rotationaxesstatechangeinfo-i-sys.md) | 旋转轴状态变更信息@typedef RotationAxesStateChangeInfo |
| [RotationAxesStatus](arkts-mechanic-mechanicmanager-rotationaxesstatus-i-sys.md) | 旋转轴状态 |
| [RotationLimits](arkts-mechanic-mechanicmanager-rotationlimits-i-sys.md) | 相对于参考点的旋转角度限制@typedef RotationLimits |
| [RotationSpeed](arkts-mechanic-mechanicmanager-rotationspeed-i-sys.md) | 转速，负值表示顺时针旋转。正值表示逆时针旋转。@typedef RotationSpeed |
| [SearchParams](arkts-mechanic-mechanicmanager-searchparams-i-sys.md) | 指定搜索的方向 |
| [SearchResult](arkts-mechanic-mechanicmanager-searchresult-i-sys.md) | 显示搜索命令的执行结果 |
| [SpeedParams](arkts-mechanic-mechanicmanager-speedparams-i-sys.md) | 速度控制参数 |
| [TargetInfo](arkts-mechanic-mechanicmanager-targetinfo-i-sys.md) | 搜索目标的相关信息 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AttachState](arkts-mechanic-mechanicmanager-attachstate-e.md) | 设备连接状态的枚举 |
| [CameraTrackingLayout](arkts-mechanic-mechanicmanager-cameratrackinglayout-e.md) | 相机跟踪布局 |
| [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e.md) | 机械体设备类型的枚举 |
| [TrackingEvent](arkts-mechanic-mechanicmanager-trackingevent-e.md) | 跟踪事件 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionType](arkts-mechanic-mechanicmanager-actiontype-e-sys.md) | 动作序列类型 |
| [AddressType](arkts-mechanic-mechanicmanager-addresstype-e-sys.md) | 具身设备地址类型 |
| [AdsorbState](arkts-mechanic-mechanicmanager-adsorbstate-e-sys.md) | 手机吸附状态 |
| [MarchingMode](arkts-mechanic-mechanicmanager-marchingmode-e-sys.md) | 行进模式定义 |
| [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e-sys.md) | 机械体设备类型的枚举 |
| [MechEventType](arkts-mechanic-mechanicmanager-mecheventtype-e-sys.md) | 具身设备事件定义 |
| [Operation](arkts-mechanic-mechanicmanager-operation-e-sys.md) | 用户操作 |
| [Result](arkts-mechanic-mechanicmanager-result-e-sys.md) | 旋转执行结果的枚举 |
| [RotationAxisLimited](arkts-mechanic-mechanicmanager-rotationaxislimited-e-sys.md) | 旋转轴限位状态 |
| [SearchDirection](arkts-mechanic-mechanicmanager-searchdirection-e-sys.md) | 系统默认的搜索方向 |
| [SpeedGear](arkts-mechanic-mechanicmanager-speedgear-e-sys.md) | 速度档位定义 |
| [TargetType](arkts-mechanic-mechanicmanager-targettype-e-sys.md) | 目标人脸信息的枚举 |
<!--DelEnd-->
