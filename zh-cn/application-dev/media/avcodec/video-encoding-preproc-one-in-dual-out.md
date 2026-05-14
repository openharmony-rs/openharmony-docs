# 编码支持一入二出

从API version 26.0.0开始，支持编码一入二出编码，主副编码器分别支持前处理配置。


## 功能概述

**一入二出（One Input Dual Outputs）**是指通过同一份视频输入数据，同时驱动 **两个独立编码器** 产生两路不同编码码流的能力。

| 编码器角色 | 创建方式 | 说明 | 引入版本 |
|-----------|----------|------|----------|
| 主编码器（Primary） | `OH_VideoEncoder_CreatePrimaryWithPreproc` 创建 | 管理共享输入 Surface，负责前处理管线调度，可配置独立的编码参数和前处理参数 | 26.0.0 |
| 副编码器（Secondary） | `OH_VideoEncoder_CreateSecondaryFromPrimary` 从主编码器创建 | 共享主编码器的输入源，可配置独立的编码参数和前处理参数 | 26.0.0 |

### 架构图
以下为一入二出架构图：
![one input dual output](figures/video-encoding-one-in-dual-out.png)

## 使用场景
应用可依据自己的场景选择使用，场景使用举例见下表：
| 场景 | 主编码器（Primary） | 副编码器（Secondary） | 用途说明 |
|------|---------------------|----------------------|----------|
| 多码率直播（ABR） | 高码率主码流 | 降采样 + 丢帧的低码流 | 根据网络带宽自适应切换 |
| ROI 区域关注 | 全帧编码归档 | 裁剪感兴趣区域编码 | 监控全帧存储 + 局部区域分析 |
| 多人视频通话 | 全分辨率、高帧率（本地显示） | 降采样 + 丢帧、低码率（远端传输） | 本地高清预览 + 远端低带宽实时通话 |

## 约束与限制

### 创建与生命周期约束

| 序号 | 约束规则 |
|------|----------|
| 1 | Secondary 数量：每个 Primary 同时最多挂载 **1 个** Secondary |
| 2 | 创建顺序：必须先创建 Primary，再从 Primary 派生 Secondary |
| 3 | 生命周期关系：Primary 是 Secondary 的所有者（Owner），Secondary 不得脱离 Primary 独立存在。<br>- **推荐销毁顺序**：先 `Destroy(Secondary)` → 再 `Destroy(Primary)`，销毁后立即将对应指针赋值 `nullptr`<br>- **容错机制**：若违反顺序先 Destroy Primary，系统会级联释放关联的 Secondary，但仍应显式遵循正确顺序 |
| 4 | 重建能力：Secondary 销毁后，可以从同一个 Primary 重新创建新的 Secondary |

### 接口可用性约束

| 接口 | 主编码器 | 副编码器 | 备注 |
|------|:--------:|:--------:|------|
| `OH_VideoEncoder_CreatePrimaryWithPreproc` | √ | N/A | 创建主编码器入口 |
| `OH_VideoEncoder_CreateSecondaryFromPrimary` | √ | N/A | 创建副编码器入口，仅可以通过主编码器句柄创建 |
| `OH_VideoEncoder_RegisterCallback` | √ | √ | 各自独立注册 |
| `OH_VideoEncoder_RegisterParameterCallback` | × | × | 不支持随帧参数 |
| `OH_VideoEncoder_PushInputParameter` | × | × | 不支持随帧参数 |
| `OH_VideoEncoder_Configure` | √ | √ | 各自独立配置（分辨率、码率、前处理等均可不同） |
| `OH_VideoEncoder_GetSurface` | √ **仅限此调用者** | × | 副编码器调用返回错误 |
| `OH_VideoEncoder_Prepare` | √ | √ | 各自准备资源，参考普通编码器 |
| `OH_VideoEncoder_Start` | √ | √ | 各自独立控制，参考普通编码器 |
| `OH_VideoEncoder_Stop` | √ | √ | 各自独立控制，参考普通编码器 |
| `OH_VideoEncoder_Flush` | √ | √ | 各自独立控制，参考普通编码器 |
| `OH_VideoEncoder_Reset` | √ | √ | 各自独立控制，参考普通编码器 |
| `OH_VideoEncoder_SetParameter` | √ | √ | 运行时动态调整 |
| `OH_VideoEncoder_NotifyEndOfStream` | √ | √ | Surface 模式专用 |
| `OH_VideoEncoder_FreeOutputBuffer` | √ | √ | 各自释放各自的 output buffer |
| `OH_VideoEncoder_PushInputData` | × | × | 不支持 Buffer 模式 |
| `OH_VideoEncoder_PushInputBuffer` | × | × | 不支持 Buffer 模式 |
| `OH_VideoEncoder_QueryInputBuffer` | × | × | 不支持同步模式 |
| `OH_VideoEncoder_QueryOutputBuffer` | × | × | 不支持同步模式 |
| `OH_VideoEncoder_GetInputDescription` | √ | √ | 含前处理元数据信息 |
| `OH_VideoEncoder_GetOutputDescription` | √ | √ | |
| `OH_VideoEncoder_IsValid` | √ | √ | |
| `OH_VideoEncoder_Destroy` | √ | √ | 先销毁 Secondary，再销毁 Primary |

### 配置约束

| 约束项 | 说明 |
|--------|------|
| Surface 共享 | 主/副编码器共享同一个 Consumer Surface，仅需从 `GetSurface` 获取一次并绑定到数据源（Camera/XComponent）
| Window 生命周期 | `OH_VideoEncoder_GetSurface` 获取的 window 实例需由开发者负责释放，在所有编码器 Destroy 之后调用 `OH_NativeWindow_DestroyNativeWindow(window)` 销毁 |
| 前处理独立性 | 每个编码器可分别配置不同的降采样/裁剪/丢帧策略；但每个编码器内部降采样与裁剪仍然互斥 |
| 回调独立性 | 两路的 `onNewOutputBuffer` 回调在不同线程中触发，需各自释放 FreeOutputBuffer |


## 开发步骤

### 创建主编码器（Primary）

```cpp
static OH_AVCodec *g_primary = nullptr;
OH_AVErrCode ret = OH_VideoEncoder_CreatePrimaryWithPreproc(OH_AVCODEC_MIMETYPE_VIDEO_AVC, &g_primary);
if (ret != AV_ERR_OK || g_primary == nullptr) {
    // 异常处理。
    return -1;
}
```

### 注册主编码器回调

和普通编码器实现一致，参考[视频编码Surface模式](video-encoding.md#surface模式)的“步骤3-调用OH_VideoEncoder_RegisterCallback()设置回调函数”。

### 配置主编码器

编码器参数配置[视频编码Surface模式](video-encoding.md#surface模式)的“步骤5-调用OH_VideoEncoder_Configure()配置编码器”。以下内容重点说明基础参数与前处理参数的配置。

```cpp
OH_AVFormat *format = OH_AVFormat_Create();

// 基础编码参数（必填）。
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1920);         // 输入宽度（像素）
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1080);        // 输入高度（像素）
OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_FRAME_RATE, 30.0); // 原始帧率（丢帧功能的前置依赖）

// 前处理参数（按需选用）。
// 方案 A：降采样示例。
// 以下示例为将 1920x1080 缩放到 640x360 后编码。
// 注意：width 和 height 必须成对出现。
OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_WIDTH, 640);
OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_HEIGHT, 360);

// 方案 B：裁剪示例。
// 以下示例为从 1920x1080 中裁剪中心 1280x720 区域。
// 注意：left/top/right/bottom 必须全部同时出现。
// 举例：left = 320, top = 180, right = 1599, bottom = 899; 对应：宽=1599-320+1=1280, 高=899-180+1=720。
// OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT, 320);
// OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_TOP, 180);
// OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_RIGHT, 1599);
// OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_BOTTOM, 899);

// 方案 C：丢帧示例。
// 示例从 30fps 降到 15fps（可单独使用或与降采样/裁剪组合）。
// OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_VIDEO_ENCODER_PREPROC_DROP_TO_FRAME_RATE, 15.0);

// 执行配置。
ret = OH_VideoEncoder_Configure(encoder, format);
if (ret != AV_ERR_OK) {
    // 错误处理。
    OH_AVFormat_Destroy(format);
    return -1;
}
OH_AVFormat_Destroy(format);
```

> **注意**：Primary 的 WIDTH/HEIGHT 定义了共享输入 Surface 的尺寸，后续创建的 Secondary 在 Configure 时建议设置相同的输入尺寸值。

### 从主编码器派生创建副编码器（Secondary）

```cpp
static OH_AVCodec *g_secondary = nullptr;

// 必须在 Primary 成功创建之后才能创建 Secondary。
ret = OH_VideoEncoder_CreateSecondaryFromPrimary(g_primary, &g_secondary);
if (ret != AV_ERR_OK || g_secondary == nullptr) {
    // 异常处理。
    return -1;
}
```

### 注册副编码器回调

和普通编码器实现一致，参考[视频编码Surface模式](video-encoding.md#surface模式)的“步骤3-调用OH_VideoEncoder_RegisterCallback()设置回调函数”。
> **注意**：Primary 和 Secondary 的回调在**不同线程**中执行。两路都必须各自调用 `FreeOutputBuffer`，否则可能导致阻塞或饥饿。

### 配置副编码器（含差异化前处理）

```cpp
OH_AVFormat *secFmt = OH_AVFormat_Create();

// 输入尺寸与 Primary 一致（共享同一输入源）。
OH_AVFormat_SetIntValue(secFmt, OH_MD_KEY_WIDTH, 1920);           // 同 Primary
OH_AVFormat_SetIntValue(secFmt, OH_MD_KEY_HEIGHT, 1080);          // 同 Primary
OH_AVFormat_SetDoubleValue(secFmt, OH_MD_KEY_FRAME_RATE, 30.0);   // 同 Primary
OH_AVFormat_SetLongValue(secFmt, OH_MD_KEY_BITRATE, 1500000);     // 1.5Mbps（较低码率）

// 差异化前处理配置（Secondary 独立配置）。
// 模式 A：降采样（最常用）。
// 以下示例为将1080p缩放到480p用于预览。
// 注意：width和height必须成对出现。
OH_AVFormat_SetIntValue(secFmt,
    OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_WIDTH, 854);
OH_AVFormat_SetIntValue(secFmt,
    OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_HEIGHT, 480);

// 组合：降采样 + 丢帧，进一步降低预览路帧率。
OH_AVFormat_SetDoubleValue(secFmt,
    OH_MD_KEY_VIDEO_ENCODER_PREPROC_DROP_TO_FRAME_RATE, 15.0);

// 模式 B：ROI 裁剪（替代方案）。
// 以下示例为编码画面中心区域。
// 注意：left/top/right/bottom 必须全部同时出现。
// OH_AVFormat_SetIntValue(secFmt, OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_LEFT, 480);
// OH_AVFormat_SetIntValue(secFmt, OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_TOP, 270);
// OH_AVFormat_SetIntValue(secFmt, OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_RIGHT, 1439);
// OH_AVFormat_SetIntValue(secFmt, OH_MD_KEY_VIDEO_ENCODER_PREPROC_CROP_BOTTOM, 809);

ret = OH_VideoEncoder_Configure(g_secondary, secFmt);
OH_AVFormat_Destroy(secFmt);

if (ret != AV_ERR_OK) {
    // 异常处理。
    return -1;
}
```

### 获取共享 Surface 并绑定数据源

```cpp
// 关键规则：只能通过主编码器获取 Surface。
OHNativeWindow *window = nullptr;
ret = OH_VideoEncoder_GetSurface(g_primary, &window);
if (ret != AV_ERR_OK || window == nullptr) {
    // 异常处理。
    return -1;
}

// 将 window 绑定到 Camera / XComponent 数据源。
// cameraManager->SetPreviewSurface(window)
// nativeXComponent->SetSurface(window)
```

> **核心规则**：
> - **仅主编码器**可以合法调用 `GetSurface`
> - 副编码器调用将直接返回 `AV_ERR_OPERATE_NOT_PERMIT`
> - 主/副共享同一个 Consumer Surface，只需获取和绑定一次

### 完成编码器准备并启动两个编码器

```cpp
ret = OH_VideoEncoder_Prepare(g_primary);
if (ret != AV_ERR_OK) {
    // 异常处理。
}
ret = OH_VideoEncoder_Prepare(g_secondary);
if (ret != AV_ERR_OK) {
    // 异常处理。
}
ret = OH_VideoEncoder_Start(g_primary);
if (ret != AV_ERR_OK) {
    // 异常处理。
}

ret = OH_VideoEncoder_Start(g_secondary);
if (ret != AV_ERR_OK) {
    // 异常处理。
}
```

### 运行时动态调整（可选）

可在运行时通过 `SetParameter` 动态修改 Secondary 的前处理参数：

```cpp
// 动态调整副编码器的降采样目标分辨率。
void ChangeSecondaryResolution(int newWidth, int newHeight)
{
    OH_AVFormat *param = OH_AVFormat_Create();
    OH_AVFormat_SetIntValue(param,
        OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_WIDTH, newWidth);
    OH_AVFormat_SetIntValue(param,
        OH_MD_KEY_VIDEO_ENCODER_PREPROC_DOWNSAMPLING_HEIGHT, newHeight);
    OH_VideoEncoder_SetParameter(g_secondary, param);
    OH_AVFormat_Destroy(param);
}

// 根据网络状态动态调整丢帧力度。
void AdjustSecondaryDropRate(double targetFps)
{
    OH_AVFormat *param = OH_AVFormat_Create();
    if (targetFps > 0 && targetFps < 30.0) {
        OH_AVFormat_SetDoubleValue(param,
            OH_MD_KEY_VIDEO_ENCODER_PREPROC_DROP_TO_FRAME_RATE, targetFps);
    } else {
        // 设为 0.0 取消丢帧。
        OH_AVFormat_SetDoubleValue(param,
            OH_MD_KEY_VIDEO_ENCODER_PREPROC_DROP_TO_FRAME_RATE, 0.0);
    }
    OH_VideoEncoder_SetParameter(g_secondary, param);
    OH_AVFormat_Destroy(param);
}
```

### 停止与销毁

```cpp
// 停止编码器。
OH_VideoEncoder_Stop(g_secondary);
OH_VideoEncoder_Stop(g_primary);

// 发送结束标记（各发各的）。
OH_VideoEncoder_NotifyEndOfStream(g_primary);
OH_VideoEncoder_NotifyEndOfStream(g_secondary);

// 销毁：先Secondary后Primary。
if (g_secondary != nullptr)
{
    OH_VideoEncoder_Destroy(g_secondary);
    g_secondary = nullptr;
}

if (g_primary != nullptr)
{
    OH_VideoEncoder_Destroy(g_primary);
    g_primary = nullptr;
}

// 释放window实例。
if (window != nullptr){
    OH_NativeWindow_DestroyNativeWindow(window);
    window = nullptr;
}
```

> **销毁规则**：
> - **推荐顺序**：先 Destroy Secondary → 再 Destroy Primary
> - 若违反顺序先 Destroy Primary，系统会**自动**先销毁关联的 Secondary 再释放 Primary
> - 但仍建议显式遵循推荐顺序以确保代码清晰可控

---

## 推荐配置模式

### 模式 A：纯双分辨率（最常用）

- **Primary**：原始分辨率，无前处理或轻度丢帧 → 录制/归档
- **Secondary**：降采样到低分辨率 + 丢帧 → 预览/推流

```
输入: 1920x1080 @ 30fps
  ├── Primary:   1920x1080 @ 30fps → HEVC @ 8Mbps   （录制文件）
  └── Secondary: 854x480  @ 15fps → HEVC @ 1.5Mbps  （实时预览）
```

### 模式 B：全帧 + ROI 裁剪

- **Primary**：全帧编码 → 完整画面归档
- **Secondary**：裁剪指定区域 → 局部分析/特写

```
输入: 3840x2160 (4K) @ 30fps
  ├── Primary:   3840x2160 全帧 → HEVC @ 20Mbps  （完整归档）
  └── Secondary: 裁剪 1920x1080 → HEVC @ 4Mbps    （ROI 区域分析）
```

### 模式 C：多码率自适应（ABR）

- **Primary**：全帧 + 适度丢帧 → 主码流
- **Secondary**：大幅降采样 + 大幅丢帧 → 弱网备用码流

```
输入: 1920x1080 @ 30fps
  ├── Primary:   1920x1080 @ 25fps → AVC @ 6Mbps  （正常播放）
  └── Secondary: 854x480  @ 10fps → AVC @ 500Kbps （弱网降级）
```

---

## 常见问题排查

| 问题 | 可能原因 | 解决方法 |
|------|----------|----------|
| CreateSecondaryFromPrimary 返回 `AV_ERR_INVALID_VAL` | 传入的不是有效的 Primary 句柄 | 确保 Primary 由 `CreatePrimaryWithPreproc` 创建且已成功 Configure |
| CreateSecondaryFromPrimary 返回 `AV_ERR_OPERATE_NOT_PERMIT` | 该 Primary 已挂载了 Secondary | 先销毁旧的 Secondary，再创建新 Secondary；或检查是否有遗漏的 Destroy 调用 |
| Secondary Configure 报错 | 前处理参数不合法 | 检查降采样/裁剪参数完整性、范围合法性、Crop 与 Downsample 是否互斥设置 |
| Secondary 调用 GetSurface 报错 | 使用了副编码器句柄调用 | **只能通过主编码器句柄**调用 GetSurface，两者返回的是同一个共享 Surface |
| Secondary 无输出 | 未调用 Start / Surface 未绑定数据源 / 回调未正确注册 | 检查 Secondary 是否已 Start；确认 Primary 的 Surface 已绑定到 Camera/XComponent；确认回调函数非 null 且包含 FreeOutputBuffer |
| Primary 回调阻塞导致 Secondary 饥饿 | Primary 的 onNeedOutputData 中耗时过长 | 确保 Primary 回调中尽快 FreeOutputBuffer，避免长时间阻塞 |

