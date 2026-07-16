# Core

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhanghongran-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

## 模块简介

Core 模块提供用于媒体系统的基础数据结构、内存管理、格式描述和错误处理等底层能力。作为多媒体框架的骨干支撑，本模块定义了媒体数据在内存中的组织形式、音视频参数的标准化描述方式以及统一的错误码规范，为上层音视频编解码、封装解封装等业务提供公共基础能力。

本模块提供的主要能力包括：

- **媒体格式描述**：创建和管理 OH_AVFormat 实例，以键值对形式存储音视频参数，支持 int、long、float、double、string、buffer 等多种数据类型，提供音频/视频格式的快速创建接口。
- **媒体缓冲区管理**：创建和管理 OH_AVBuffer 实例，承载音视频数据及相关元数据，支持缓冲区属性（时间戳、大小、偏移、标记）的读写操作，支持扩展参数的传递。
- **音频声道布局**：定义从单声道到 22.2 声道的完整声道布局方案，支持立体声、环绕声、Ambisonics 三维音频等多种配置。
- **Audio Vivid 元数据构建**：构建 Audio Vivid 三维音频编码所需的元数据，支持音频对象位置管理、增益控制、对象增删和元数据合并。
- **媒体类型定义**：定义 HDR 类型等常见媒体类型枚举。
- **错误码规范**：定义统一的媒体框架错误码，覆盖内存、IO、超时、DRM 解密、网络等各类错误场景。

适用场景包括：所有涉及音视频数据处理的场景，如配置编解码参数、管理输入输出缓冲区、处理三维音频、解析 HDR 视频信息、处理编解码异常等。

本模块包含头文件 `media_types.h`、`native_audio_channel_layout.h`、`native_audio_vivid.h`、`native_avbuffer.h`、`native_avbuffer_info.h`、`native_averrors.h`、`native_avformat.h` 和 `native_avmemory.h`，提供结构体 OH_AVBuffer、OH_AVFormat、OH_AVCodecBufferAttr、OH_AudioVividMetaBuilder 等，枚举 OH_AVErrCode、OH_AVPixelFormat、OH_AudioChannelLayout、OH_AVCodecBufferFlags 等，以及 40 余个函数。

## 关键术语

### 缓冲区术语

#### Buffer；缓冲区
用于存储音视频数据的内存区域，承载编码或解码过程中的原始数据、压缩数据和元数据，是编解码数据传递的基本单元。

#### Buffer Attribute；缓冲区属性
描述缓冲区元信息的结构，包括显示时间戳、数据大小、偏移量和帧标记等，用于标识和管理缓冲区中的数据内容。

#### PTS (Presentation Time Stamp)；显示时间戳
音视频帧在播放时应该显示的时间标记，单位为微秒，用于同步音视频流和维持正确的播放顺序。

#### Offset；偏移量
缓冲区中有效数据起始位置相对于缓冲区首地址的字节距离，用于定位数据在缓冲区中的具体位置。

#### Buffer Flags；缓冲区标记
标识缓冲区数据类型的标志位，包括关键帧、流结束帧、不完整帧、编解码特定数据等，用于指导数据处理流程。

#### EOS (End of Stream)；流结束帧
标识媒体流结束的特殊帧标记，通知解码器后续无更多输入数据，触发解码器的收尾处理流程。

#### Sync Frame；同步帧
可独立解码的帧类型，不依赖其他帧的信息，也称关键帧或I帧，用于随机访问和错误恢复。

#### Incomplete Frame；不完整帧
数据不完整的帧，仅包含部分帧数据，需要等待后续数据到达后才能完成解码处理。

#### Codec Specific Data；编解码特定数据
编解码器初始化所需的配置信息，如H.264的SPS/PPS、AAC的AudioSpecificConfig等，在解码开始前需要优先传递。

#### Discardable Frame；可丢弃帧
解码后可直接丢弃的帧，不用于显示输出，通常为解码过程中产生的中间参考帧。

#### Disposable Frame；可释放帧
不被其他帧参考的帧，解码后可立即释放缓冲区，不占用后续解码资源。

### 格式描述术语

#### Format Description；格式描述
以键值对形式存储的媒体参数信息，包括编解码参数、轨道信息、元数据等，用于配置编解码器和传递媒体属性。

#### Key-Value Pair；键值对
由键名和对应值组成的数据结构，用于灵活存储和查询媒体参数，支持多种数据类型如整数、浮点数、字符串等。

#### Media Metadata；媒体元数据
描述媒体文件属性的数据，包括标题、艺术家、专辑、时长、码率等信息，用于媒体管理和检索。

### 三维音频术语

#### Audio Vivid
中国自主知识产权的三维音频标准，支持声床和音频对象混合编码，可实现沉浸式三维声场效果，适用于影视、音乐、VR等场景。

#### Audio Object；音频对象
三维音频中的独立声音实体，具有确定的空间位置和运动轨迹，可在三维声场中自由移动，与声床共同构成完整的空间音频体验。

#### Soundbed；声床
三维音频中的基础声道布局，提供固定位置的背景声场，如环境音、背景音乐等，不随听众位置变化而移动。

#### Cartesian Coordinate System；笛卡尔坐标系
使用X、Y、Z三个坐标轴定义三维空间位置的坐标系统，X轴表示左右，Y轴表示前后，Z轴表示上下，取值范围为[-1.0, 1.0]。

#### Polar Coordinate System；极坐标系
使用方位角、俯仰角和距离定义三维空间位置的坐标系统，也称球坐标系，更符合人类对声音方向的感知习惯。

#### Azimuth；方位角
极坐标系中表示声音水平方向的角度，以正前方为0度，左侧为90度，右侧为-90度，正后方为±180度，范围为[-180.0, 180.0]。

#### Elevation；俯仰角
极坐标系中表示声音垂直方向的角度，以水平面为0度，正上方为90度，正下方为-90度，范围为[-90.0, 90.0]。

#### Normalization；归一化
将数值按比例转换到指定范围（如[-1.0, 1.0]或[0.0, 1.0]）的处理过程，便于不同尺度数据的统一处理和比较。

#### Metadata Builder；元数据构建器
用于构建和修改媒体元数据的工具对象，支持添加、删除、更新元数据项，常用于Audio Vivid等复杂元数据的生成。

### 内存管理术语

#### AVMemory；媒体内存
音视频数据的内存封装结构，提供内存地址、大小等基本信息，已废弃，建议使用AVBuffer替代以获得更完整的功能支持。

#### Native Object；原生对象
C/C++层的底层对象封装，为上层提供跨语言调用的统一接口，隐藏底层实现细节，实现模块间的解耦。

## 概述

Core模块提供用于媒体系统的基础能力，包含内存、错误码、媒体数据结构等相关函数。

**系统能力：** SystemCapability.Multimedia.Media.Core

**起始版本：** 9

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [media_types.h](capi-media-types-h.md) | 声明了常见媒体类型的定义。 |
| [native_audio_channel_layout.h](capi-native-audio-channel-layout-h.md) | 声明了录制和播放时的扬声器布局。 |
| [native_audio_vivid.h](capi-native-audio-vivid-h.md) | 声明Audio Vivid相关的函数和枚举。 |
| [native_avbuffer.h](capi-native-avbuffer-h.md) | 声明了媒体数据结构AVBuffer的函数接口。 |
| [native_avbuffer_info.h](capi-native-avbuffer-info-h.md) | 声明了媒体数据结构AVBuffer属性的定义。 |
| [native_averrors.h](capi-native-averrors-h.md) | 媒体框架错误码。 |
| [native_avformat.h](capi-native-avformat-h.md) | 声明了OH_AVFormat相关的函数和枚举。 |
| [native_avmemory.h](capi-native-avmemory-h.md) | 声明了媒体数据结构AVMemory的定义。 |
