# @ohos.multimodalAwareness.deviceStatus

**deviceStatus**模块提供设备状态感知能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace deviceStatus--><!--Device-unnamed-declare namespace deviceStatus-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offSteadyStandingDetect](arkts-multimodalawareness-devicestatus-offsteadystandingdetect-f.md#offSteadyStandingDetect) | 取消订阅设备静止姿态感知（支架态）事件。 |
| off_steadyStandingDetect | 取消订阅设备静止姿态感知（支架态）事件，用于应用在退出页面或不再需要监听支架态变化的场景。调用后释放相关资源。 |
| [onSteadyStandingDetect](arkts-multimodalawareness-devicestatus-onsteadystandingdetect-f.md#onSteadyStandingDetect) | 订阅设备静止姿态感知（支架态）事件。 |
| on_steadyStandingDetect | 订阅设备静止姿态感知（支架态）事件。建议在不需要时调用off()取消订阅，释放资源。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDeviceRotationRadian](arkts-multimodalawareness-devicestatus-getdevicerotationradian-f-sys.md#getDeviceRotationRadian) | 获取设备的姿态数据。 姿态数据包含x、y、z三轴的姿态旋转角，即三轴的欧拉角，三轴定义与设备sensor定义相同，为右手系。姿态旋转角在ZXY旋转顺序、内旋下计算，通过传感器融合获取的四元数计算得到结果。 |
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
| [SteadyStandingStatus](arkts-multimodalawareness-devicestatus-steadystandingstatus-e.md) | 设备静止姿态感知状态（支架态）。 设备进入支架态指设备静止，且屏幕与水平面角度处于45度-135度。折叠屏手机需处于折叠状态或者完全展开状态。系统通过传感器检测设备的运动状态和角度变化，判断设备是否满足支架态条件。 |

