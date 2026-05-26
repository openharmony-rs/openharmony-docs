# 智能帧保留视频解码

## 基础概念

从API version 26开始，系统引入了视频解码帧保留（Frame Retention）特性。这是一种深度结合硬件解码能力的系统级解码优化方案。

在传统的应用架构中，倍速播放时的丢帧通常在渲染层被动触发，这不仅意味着解码算力已经被浪费，且盲目丢帧极易刚好丢掉运动剧烈的关键画面，导致视觉撕裂或卡顿。本方案将倍速场景的丢帧或帧保留决策下移到底层系统层执行。通过在解码流水线中建立主动拦截与智能筛选机制，有效解决高分辨率、高帧率、高倍速（如3.0x甚至更高）等高负载场景下的性能瓶颈，为更高规格的视频倍速播放提供坚实的系统级支撑。

## 适用场景与核心优势

本方案适用于应用对系统负载有严格控制要求，或在非1.0x倍速下追求极致流畅度的播放场景。其核心优势在于**将复杂的帧干预逻辑完全托管给底层系统，应用层无需再为了丢帧策略而耗费精力**。

- **高负载倍速播放**：在1.5x、2.0x甚至3.0x倍速播放时，解码器每秒产生的解码帧数通常远大于屏幕实际能显示的帧数。传统的应用层被动丢帧或简单的均匀丢帧，极易破坏视觉连贯性。本方案通过底层感知引擎智能拦截，实现画面的平滑保留。
- **温控与节能降负载**：在设备触发高温预警或处于低电量模式时，通过平滑降低帧保留比例，有效控制解码与渲染频率，确保核心业务稳定不崩溃。

系统提供以下三种帧保留模式，开发者可按需灵活使用和切换：

| 模式 | 技术内涵与业务意图 |
| :--- | :--- |
| **全量直通（FULL）** | **设计初衷为关闭帧保留特性**。解码器处于透明直通状态，不干预任何输入输出，100%保留所有解码帧。算法层零开销。 |
| **感知自适应（ADAPTIVE）** | **更智能的托管保留策略**。动态分析视频运动特征（如运动矢量与复杂度），优先剔除视觉感知权重较低的帧。**在倍速场景下，它比简单的均匀抽帧更符合人眼视觉连贯性**，避免了顿挫感，应用层只需下发目标倍速，无需关心如何丢帧。 |
| **平滑定比（UNIFORM）** | 基于纯数学算法，按开发者指定的比例绝对均匀地抽帧。适合需要严格且固定控制输出帧率的物理降频场景。 |

## 推荐使用情况总结

为了帮助开发者快速进行架构决策，以下总结了不同业务痛点下最推荐的帧保留策略：

1. **日常倍速播放（1.25x ~ 3.0x等）**
   - **推荐**：感知自适应模式（ADAPTIVE）。
   - **痛点**：应用层无法获知画面内容，强行按比例丢帧会导致运动画面撕裂。
   - **收益**：应用只需将当前倍速值传给底层，将丢帧行为全权托管。系统会自动甄别并保留视觉关键帧，在大幅降低解码功耗的同时，获得远超应用层自行丢帧的流畅视觉体验。
2. **物理显示瓶颈（如60Hz屏幕播120fps视频）**
   - **推荐**：平滑定比模式（UNIFORM）。
   - **痛点**：解码器解出的高帧率画面超出了屏幕的物理刷新上限，多余算力被白白浪费。
   - **收益**：无需智能感知算法参与。上层精确计算出屏幕刷新率与视频帧率的比例（如60/120 = 0.5），下发UNIFORM模式，系统底层将绝对均匀地砍掉一半解码负载，画面表现与1.0x播放完全一致。
3. **系统温控与极限省电告警 **
   - **推荐**：平滑定比模式（UNIFORM）。
   - **痛点**：设备过热面临强制降频或关机风险，此时流畅度已不再是第一优先级，生存才是第一优先级。
   - **收益**：无视当前播放状态，直接下发UNIFORM模式和极低的比例（如0.3或更低）。强制约束解码与送显算力，快速遏制设备发热，提供最可靠的灾备降级。

## 约束和限制

- **API 范围**：本特性仅适用于视频解码场景，支持H.264、H.265及H.266格式的码流。
- **硬件依赖**：感知自适应模式（ADAPTIVE）依赖硬件解码器上报的运动矢量等底层特征。若设备硬件不支持，系统将自动降级为平滑定比抽帧或直通模式，确保播放不中断。

## 参数要求说明

开发者通过配置`OH_AVFormat`中的以下键值对来控制该特性：

1. **OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE（模式配置）**
   - **类型**：`int32_t`
   - **取值**：参考枚举`OH_FrameRetentionMode`（0: FULL, 1: ADAPTIVE, 2: UNIFORM）。
2. **OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_RATIO（保留比例）**
   - **类型**：`double`
   - **范围**：[0.01, 1.0]。（例如0.5表示保留50%的帧）
   - **说明**：仅在`UNIFORM`模式下强制生效；若在`UNIFORM`模式下未显式配置此值，系统默认以最高30fps为上限进行平滑限制。超出范围的值将被忽略。
3. **OH_MD_KEY_VIDEO_DECODER_SPEED（参考倍速）**
   - **类型**：`double`
   - **范围**：严格大于0.0。
   - **说明**：在`ADAPTIVE`模式下，**强烈建议**同步配置此参数。感知引擎需要依赖真实的播放倍速来精确校准人眼对丢帧的感知阈值。

## 基础使用：配置时机与模式设置

视频解码帧保留特性的参数生效极其灵活，支持在解码器生命周期的两个核心节点进行配置：**初始化阶段（Configure）**与**运行阶段（Running）**。

### 1. 初始化阶段配置

在解码器调用`OH_VideoDecoder_Configure`前，将模式与参数写入`OH_AVFormat`。此方式适用于在视频起播前就已经明确业务策略的场景。

```c++
#include <multimedia/player_framework/native_avcodec_videodecoder.h>
#include <multimedia/player_framework/native_avformat.h>

// 创建解码器与Format
OH_AVCodec *vdec = OH_VideoDecoder_CreateByMime(OH_AVCODEC_MIMETYPE_VIDEO_HEVC);
OH_AVFormat *format = OH_AVFormat_Create();

// ... 常规长宽等参数配置 ...

// 配置初始模式为感知自适应（ADAPTIVE），并下发初始参考倍速1.0
OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE, 
                        OH_FRAME_RETENTION_MODE_ADAPTIVE);
OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_VIDEO_DECODER_SPEED, 1.0);

OH_VideoDecoder_Configure(vdec, format);
OH_AVFormat_Destroy(format);
```

### 2. 运行阶段动态配置

当解码器处于`Running`状态时，可通过`OH_VideoDecoder_SetParameter`实时下发参数。底层支持无锁热更新，新参数将在下一帧解码前立即生效，不会中断或重置视频流。

```c++
OH_AVFormat *param = OH_AVFormat_Create();

// 动态切换为全量直通模式（FULL），关闭帧保留特性
OH_AVFormat_SetIntValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE, 
                        OH_FRAME_RETENTION_MODE_FULL);

OH_VideoDecoder_SetParameter(vdec, param);
OH_AVFormat_Destroy(param);
```

## 典型业务场景实践

为帮助开发者更好地将底层能力与上层业务结合，以下列举了四种典型的应用场景及组合策略。

### 场景一：全局开启感知自适应（ADAPTIVE），切倍速时仅更新参考倍速

**适用业务**：常规的长视频/短视频播放器，希望全程将功耗与流畅度的平衡交由底层系统接管。
**策略说明**：在`Configure`阶段即全局使能`ADAPTIVE`模式。后续用户每次点击切换倍速（如1.25x, 2.0x, 3.0x）时，应用无需干预丢帧逻辑，只需将新的倍速值下发给底层，感知引擎会自动重新校准丢帧阈值。

```c++
// 用户切换至2.0x倍速播放
OH_AVFormat *param = OH_AVFormat_Create();

// 模式已是ADAPTIVE，此处只需单纯更新参考倍速
OH_AVFormat_SetDoubleValue(param, OH_MD_KEY_VIDEO_DECODER_SPEED, 2.0);

OH_VideoDecoder_SetParameter(vdec, param);
OH_AVFormat_Destroy(param);
```

### 场景二：默认全量直通（FULL），仅高倍速时开启感知自适应（ADAPTIVE）

**适用业务**：对1.0x标准播放画质有极其严苛要求的应用（如本地超清播放器、影视级调色监看应用）。
**策略说明**：在`Configure`阶段或1.0x播放时，保持`FULL`模式（关闭特性）。当用户切换到大于1.0x的高倍速时，才动态唤醒`ADAPTIVE`模式并下发当前倍速。切回1.0x时再次切回`FULL`。

```c++
// 用户从1.0x切换至3.0x倍速播放
OH_AVFormat *param = OH_AVFormat_Create();

// 唤醒ADAPTIVE模式，并下发目标倍速
OH_AVFormat_SetIntValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE, 
                        OH_FRAME_RETENTION_MODE_ADAPTIVE);
OH_AVFormat_SetDoubleValue(param, OH_MD_KEY_VIDEO_DECODER_SPEED, 3.0);

OH_VideoDecoder_SetParameter(vdec, param);
OH_AVFormat_Destroy(param);
```

### 场景三：极致高负载场景，切倍速时由上层自主计算比例（UNIFORM）

**适用业务**：播放超高帧率视频（如60fps/120fps），且设备屏幕刷新率存在物理上限（如60Hz）。
**策略说明**：1.0x播放时使用`FULL`模式。当切换至高倍速（如2.0x）时，解码端每秒理论输出帧数将远超屏幕刷新率，多余的解码算力毫无意义。此时由上层计算精确的保留比例，使用`UNIFORM`模式强制底层平滑定比输出。当切回1.0x时，再次配置回`FULL`模式。

```c++
// 业务状态：原视频60fps，目标倍速2.0x，屏幕最高支持60Hz。
// 算力换算：2.0x下每秒需解码120帧，为匹配60Hz屏幕，仅需保留50% (60/120)。
double targetSpeed = 2.0;
double retentionRatio = 0.5; 

OH_AVFormat *param = OH_AVFormat_Create();

// 切换为UNIFORM平滑定比模式，精准控制输出负载
OH_AVFormat_SetIntValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE, 
                        OH_FRAME_RETENTION_MODE_UNIFORM);
// 下发计算好的保留比例
OH_AVFormat_SetDoubleValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_RATIO, retentionRatio);
// (可选) 同步告知倍速
OH_AVFormat_SetDoubleValue(param, OH_MD_KEY_VIDEO_DECODER_SPEED, targetSpeed);

// 实时下发生效，底层将执行绝对均匀的50%抽帧，避免连续卡顿
OH_VideoDecoder_SetParameter(vdec, param);
OH_AVFormat_Destroy(param);
```

### 场景四：响应系统温控与低功耗模式，强制降频（UNIFORM）

**适用业务**：所有涉及视频播放的应用，在接收到系统级高温预警（Thermal Warning）或用户开启超级省电模式时。
**策略说明**：无关乎当前用户处于何种播放倍速，首要任务是保障系统不因过热而宕机。直接通过`UNIFORM`模式下发一个较低的固定保留比例（如0.3或更低），强行折半砍掉解码与渲染的算力消耗，为系统降温提供最可靠的灾备降级。

```c++
// 接收到系统高温降频广播或极限省电信号
OH_AVFormat *param = OH_AVFormat_Create();

// 强制切换为UNIFORM模式，不再考虑视觉最优，优先保障生存
OH_AVFormat_SetIntValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE, 
                        OH_FRAME_RETENTION_MODE_UNIFORM);
// 强制仅保留30%的画面，大幅度降低整机负载
OH_AVFormat_SetDoubleValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_RATIO, 0.3);

OH_VideoDecoder_SetParameter(vdec, param);
OH_AVFormat_Destroy(param);
```