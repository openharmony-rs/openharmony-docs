# @ohos.multimedia.cameraPicker

本模块提供相机拍照与录制的能力。应用可选择媒体类型实现拍照和录制的功能。调用此类接口时，应用必须在界面UIAbility中调用，否则无法启动cameraPicker应用。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace cameraPicker--><!--Device-unnamed-declare namespace cameraPicker-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [pick](arkts-camera-camerapicker-pick-f.md#pick) | 拉起相机选择器，根据媒体类型进入相应的模式。使用Promise异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [PickerProfile](arkts-camera-camerapicker-pickerprofile-c.md) | 相机选择器的配置信息。 |
| [PickerResult](arkts-camera-camerapicker-pickerresult-c.md) | 相机选择器的处理结果。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PickerMediaType](arkts-camera-camerapicker-pickermediatype-e.md) | 枚举，相机选择器的媒体类型。 |

