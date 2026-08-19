# @ohos.multimodalAwareness.deviceStatus

**deviceStatus**本模块提供对设备状态的感知能力，通过传感器实时感知设备物理状态，可帮助开发者根据设备物理状态调整应用行为。

**起始版本：** 23

<!--Device-unnamed-declare namespace deviceStatus--><!--Device-unnamed-declare namespace deviceStatus-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

## 导入模块

```TypeScript
import { deviceStatus } from '@kit.MultimodalAwarenessKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offSteadyStandingDetect](arkts-multimodalawareness-devicestatus-offsteadystandingdetect-f.md) | 取消订阅设备静止姿态感知（支架态）事件。 |
| [off_steadyStandingDetect](arkts-multimodalawareness-devicestatus-offsteadystandingdetect-f.md) | 取消订阅设备静止姿态感知（支架态）事件，用于应用在退出页面或不再需要监听支架态变化的场景。调用后释放相关资源。 |
| [onSteadyStandingDetect](arkts-multimodalawareness-devicestatus-onsteadystandingdetect-f.md) | 订阅设备静止姿态感知（支架态）事件。 |
| [on_steadyStandingDetect](arkts-multimodalawareness-devicestatus-onsteadystandingdetect-f.md) | 订阅设备静止姿态感知（支架态）事件。建议在不需要时调用off()取消订阅，释放资源。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDeviceRotationRadian](arkts-multimodalawareness-devicestatus-getdevicerotationradian-f-sys.md) | 获取设备的姿态数据。 姿态数据包含x、y、z三轴的姿态旋转角，即三轴的欧拉角，三轴定义与设备sensor定义相同，为右手系。姿态旋转角在ZXY旋转顺序、内旋下计算， <br>通过传感器融合获取的四元数计算得到结果。 |
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
| [SteadyStandingStatus](arkts-multimodalawareness-devicestatus-steadystandingstatus-e.md) | 设备静止姿态感知状态（支架态）。 设备进入支架态指设备静止，且屏幕与水平面角度处于45度-135度。折叠屏手机需处于折叠状态或者完全展开状态。系统通过传感器检测设备的运动状态和角度变化， <br>判断设备是否满足支架态条件。 |

