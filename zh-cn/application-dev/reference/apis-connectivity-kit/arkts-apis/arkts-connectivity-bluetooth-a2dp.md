# @ohos.bluetooth.a2dp(蓝牙a2dp模块)

本模块提供基于增强音频分发协议（Advanced Audio Distribution Profile，A2DP）的蓝牙媒体音频能力，支持获取媒体播放状态和连接状态等方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { a2dp } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createA2dpSnkProfile](arkts-connectivity-a2dp-createa2dpsnkprofile-f.md) | 创建a2dp sink实例。 |
| [createA2dpSrcProfile](arkts-connectivity-a2dp-createa2dpsrcprofile-f.md) | 创建蓝牙媒体A2DP Source实例。通过该实例，可以使用本端作为A2DP Source设备时提供的各项方法，如：获取和其他设备间的蓝牙媒体音频播放状态。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [A2dpSourceProfile](arkts-connectivity-a2dp-a2dpsourceprofile-i.md) | 该实例表示蓝牙媒体音频中的A2DP Source角色。 |
| [CodecInfo](arkts-connectivity-a2dp-codecinfo-i.md) | 蓝牙媒体音频使用的编解码器。 |
| [CodecInfoList](arkts-connectivity-a2dp-codecinfolist-i.md) | 蓝牙媒体音频编解码器支持的能力集合。不同编解码器支持的位深、声道模式、采样率、码率和帧长类型与音频接收器设备端能力有关。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [A2dpSinkProfile](arkts-connectivity-a2dp-a2dpsinkprofile-i-sys.md) | 管理a2dp sink业务。 |
| [A2dpSourceProfile](arkts-connectivity-a2dp-a2dpsourceprofile-i-sys.md) | 该实例表示蓝牙媒体音频中的A2DP Source角色。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-a2dp-baseprofile-t.md) | 基础Profile接口定义，提供监听和获取连接状态等公共能力。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CodecBitRate](arkts-connectivity-a2dp-codecbitrate-e.md) | 枚举，蓝牙媒体音频编解码器的码率，表示单位时间内音频数据的传输量，单位为kbps。码率影响音频音质和传输带宽。 |
| [CodecBitsPerSample](arkts-connectivity-a2dp-codecbitspersample-e.md) | 枚举，蓝牙媒体音频编解码器的位深，表示蓝牙音频信号在数字表示中使用的位数，单位为bit。位深决定每个采样点可以表示的动态范围和精度。 |
| [CodecChannelMode](arkts-connectivity-a2dp-codecchannelmode-e.md) | 枚举，蓝牙媒体音频编解码器的声道模式，表示音频播放时独立的空间信号路径数量。声道模式影响声音的立体感和空间定位‌。 |
| [CodecFrameLength](arkts-connectivity-a2dp-codecframelength-e.md) | 枚举，蓝牙媒体音频编解码器的帧长，表示一帧音频数据播放的时长，单位为ms。帧长影响音频传输的延迟和效率。 |
| [CodecSampleRate](arkts-connectivity-a2dp-codecsamplerate-e.md) | 枚举，蓝牙媒体音频编解码器的采样率，表示每秒对蓝牙音频采样的次数，单位为Hz。采样率的选择会影响音质和传输效率。 |
| [CodecType](arkts-connectivity-a2dp-codectype-e.md) | 枚举，蓝牙媒体音频编解码器类型。 |
| [PlayingState](arkts-connectivity-a2dp-playingstate-e.md) | 枚举，蓝牙媒体音频播放状态。 |
