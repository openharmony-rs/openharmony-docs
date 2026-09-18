# @ohos.multimodalAwareness.deviceStatus(设备状态感知)

**deviceStatus**本模块提供对设备状态的感知能力，通过传感器实时感知设备物理状态，可帮助开发者根据设备物理状态调整应用行为。

**起始版本：** 18

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

## 导入模块

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off](arkts-multimodalawareness-devicestatus-off-f.md#offsteadystandingdetect) | 取消订阅设备静止姿态感知（支架态）事件，用于应用在退出页面或不再需要监听支架态变化的场景。调用后释放相关资源。 |
| [on](arkts-multimodalawareness-devicestatus-on-f.md#onsteadystandingdetect) | 订阅设备静止姿态感知（支架态）事件。建议在不需要时调用off()取消订阅，释放资源。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDeviceRotationRadian](arkts-multimodalawareness-devicestatus-getdevicerotationradian-f-sys.md) | 获取设备的姿态数据。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceRotationRadian](arkts-multimodalawareness-devicestatus-devicerotationradian-i-sys.md) | 设备旋转弧度接口。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SteadyStandingStatus](arkts-multimodalawareness-devicestatus-steadystandingstatus-e.md) | 设备静止姿态感知状态（支架态）。 |
