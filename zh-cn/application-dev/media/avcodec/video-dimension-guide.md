# 视频编解码宽高、跨距与裁剪信息说明

## 概述

在视频编解码（Video Codec）开发中，图像的**宽度**和**高度**存在多种表示形式，同时硬件处理通常需要内存对齐（跨距），解码输出还可能涉及**裁剪区域**。本文档系统梳理视频编解码 API 中涉及的尺寸相关参数及其关系，帮助开发者正确理解和使用这些参数。

## 1. 参数总览

### 1.1 尺寸参数一览表

| 参数 | 键名 | 类型 | 含义 | 编码器使用场景 | 解码器使用场景 | 调用接口 |
|------|------|------|------|--------|--------|----------|
| width / height | `OH_MD_KEY_WIDTH` / `OH_MD_KEY_HEIGHT` | int32_t | 配置的视频宽/高 | Configure 输入（目标编码分辨率） | Configure 输入（解码分辨率提示，用于预分配缓冲区） | 开发者配置Configure |
| stride | `OH_MD_KEY_VIDEO_STRIDE` | int32_t | 宽跨距（行对齐后每行字节数） | 获取Buffer内存对齐宽 | 获取Buffer内存对齐宽 | GetInputDescription / GetOutputDescription / OnStreamChanged |
| sliceHeight | `OH_MD_KEY_VIDEO_SLICE_HEIGHT` | int32_t | 高跨距（列对齐后总行数） | 获取Buffer内存对齐高 | 获取Buffer内存对齐高 | GetInputDescription / GetOutputDescription / OnStreamChanged |
| picWidth / picHeight | `OH_MD_KEY_VIDEO_PIC_WIDTH` / `OH_MD_KEY_VIDEO_PIC_HEIGHT` | int32_t | 图像真实有效宽/高 | — | 解码输出有效宽/高 | GetOutputDescription / OnStreamChanged |
| cropTop | `OH_MD_KEY_VIDEO_CROP_TOP` | int32_t | 裁剪矩形顶部行坐标(y)，包含裁剪框顶部的行，行索引从0开始 | — | 解码裁剪上边界 | GetOutputDescription / OnStreamChanged |
| cropBottom | `OH_MD_KEY_VIDEO_CROP_BOTTOM` | int32_t | 裁剪矩形底部行坐标(y)，包含裁剪框底部的行，行索引从0开始 | — | 解码裁剪下边界 | GetOutputDescription / OnStreamChanged |
| cropLeft | `OH_MD_KEY_VIDEO_CROP_LEFT` | int32_t | 裁剪矩形左列坐标(x)，包含裁剪框最左边的列，列索引从0开始 | — | 解码裁剪左边界 | GetOutputDescription / OnStreamChanged |
| cropRight | `OH_MD_KEY_VIDEO_CROP_RIGHT` | int32_t | 裁剪矩形右列坐标(x)，包含裁剪框最右边的列，列索引从0开始 | — | 解码裁剪右边界 | GetOutputDescription / OnStreamChanged |

> 以上键均定义于 [capi-codecbase.md](../reference/apis-avcodec-kit/capi-codecbase.md)。

---

## 2. 核心概念详解

### 2.1 width / height vs picWidth / picHeight —— 配置尺寸 vs 有效图像尺寸

#### 编码器：width / height（配置尺寸）

编码器的 `OH_MD_KEY_WIDTH` 和 `OH_MD_KEY_HEIGHT` 是开发者通过 `Configure` 接口配置的目标编码分辨率。这是编码器输入数据的**期望尺寸**，同时也是码流中的**编码分辨率**。

```c++
// 编码器配置示例
OH_AVFormat *format = OH_AVFormat_Create();
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1920);   // 目标编码宽度
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1080);  // 目标编码高度
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12);
// 使用 format 完成后需销毁
OH_AVFormat_Destroy(format);
```

#### 解码器：width / height（配置尺寸）

解码器的 `OH_MD_KEY_WIDTH` 和 `OH_MD_KEY_HEIGHT` 是开发者通过 `Configure` 接口配置的解码分辨率提示。解码器根据此参数**预分配内部缓冲区**，确保能够容纳码流中的编码帧尺寸。

> **注意**：解码器的 width/height 是配置阶段的**期望值**，实际解码输出的有效图像尺寸由 `OH_MD_KEY_VIDEO_PIC_WIDTH/VIDEO_PIC_HEIGHT`（见下文）决定。通常建议将 width/height 设置为与码流实际分辨率一致或略大。解码器支持码流分辨率的动态变化（如自适应码流场景），此时解码器会根据实际帧尺寸输出对应的 picWidth/picHeight。

```c++
// 解码器配置示例
OH_AVFormat *format = OH_AVFormat_Create();
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1920);   // 解码宽度（必须配置）
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1080);  // 解码高度（必须配置）
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12);
// 使用 format 完成后需销毁
OH_AVFormat_Destroy(format);
```

#### 解码器：picWidth / picHeight（有效图像尺寸）

解码器的 `OH_MD_KEY_VIDEO_PIC_WIDTH` 和 `OH_MD_KEY_VIDEO_PIC_HEIGHT` 表示解码输出的**实际有效像素区域**的宽度和高度。

由于视频码流标准（如 H.264/H.265）支持**裁剪**机制，码流中编码帧的大小可能不等于最终显示的有效图像大小：

```
picWidth  = cropRight - cropLeft + 1     （宽度方向：左右列坐标差+1）
picHeight = cropBottom - cropTop + 1      （高度方向：上下行坐标差+1）
```

### 2.2 stride / sliceHeight —— 内存跨距（对齐）

#### 什么是跨距？

**跨距（Stride）** 是指内存缓冲区中**相邻两行数据起始位置之间的字节距离**。

视频编解码硬件通常要求**内存按特定字节或像素对齐**以提高存取效率。当配置的图像宽/高不满足对齐要求时，硬件会分配更大的缓冲区，多余的部分称为 **padding（填充区）**。

跨距包含两个维度：

- **宽跨距（stride）：** 内存中每一行的**实际字节数**，通常 ≥ 图像有效宽度
- **高跨距（sliceHeight）：** 内存中分配的总**行数**，通常 ≥ 图像有效高度

两者与有效尺寸的关系为：

```
stride      = width + padding_width          （水平方向）
sliceHeight = height + padding_height        （垂直方向）
```

#### 编码器侧内存布局

以 NV12 格式为例，编码器输入 Buffer 的内存布局如下：

![encoder stride](figures/copy-by-line-encoder.png)

图中各参数含义：

| 参数 | 键名 | 说明 |
|------|------|------|
| width | `OH_MD_KEY_WIDTH` | 开发者配置的图像有效宽度 |
| height | `OH_MD_KEY_HEIGHT` | 开发者配置的图像有效高度 |
| stride | `OH_MD_KEY_VIDEO_STRIDE` | Buffer 中每行的实际像素数（含右侧 padding） |
| sliceHeight | `OH_MD_KEY_VIDEO_SLICE_HEIGHT` | Y 分量区域的实际行数（含底部 padding） |

> **注意：** 编码器使用 `width`/`height` 作为有效区域标识。

#### 解码器侧内存布局

解码器输出 Buffer 的内存布局类似，但使用不同的键名来标识有效区域：

![decoder stride](figures/copy-by-line-decoder.png)

图中各参数含义：

| 参数 | 键名 | 说明 |
|------|------|------|
| picWidth | `OH_MD_KEY_VIDEO_PIC_WIDTH` | 解码后图像的实际有效宽度 |
| picHeight | `OH_MD_KEY_VIDEO_PIC_HEIGHT` | 解码后图像的实际有效高度 |
| stride | `OH_MD_KEY_VIDEO_STRIDE` | Buffer 中每行的实际像素数（含右侧 padding） |
| sliceHeight | `OH_MD_KEY_VIDEO_SLICE_HEIGHT` | Y 分量区域的实际行数（含底部 padding） |

### 2.3 Crop —— 裁剪矩形（仅解码器）

#### 含crop信息时解码器侧内存布局

一般情况下，`crop_left`与`crop_top`通常为0。

![crop](figures/crop_display.png)

解码器特有的 4 个裁剪参数定义了**有效显示区域**的矩形范围：

| 参数 | 键名 | 说明 |
|------|--------|--------|
| cropLeft | `OH_MD_KEY_VIDEO_CROP_LEFT` | 有效区域左边缘的列坐标(x)，从0开始计数，包含该列 |
| cropRight | `OH_MD_KEY_VIDEO_CROP_RIGHT` | 有效区域右边缘的列坐标(x)，从0开始计数，包含该列 |
| cropTop | `OH_MD_KEY_VIDEO_CROP_TOP` | 有效区域顶部的行坐标(y)，从0开始计数，包含该行 |
| cropBottom | `OH_MD_KEY_VIDEO_CROP_BOTTOM` | 有效区域底部的行坐标(y)，从0开始计数，包含该行 |

---

## 3. picWidth / picHeight 与码流标准的关系（H.264 / H.265）

### 3.1 H.264 AVC 标准

H.264 标准中通过 SPS（Sequence Parameter Set）中的以下字段定义图像尺寸关系：

| H.264 SPS 字段 | 含义 | 对应 API 键 |
|----------------|------|-------------|
| `pic_width_in_mbs_minus1` | 以宏块为单位的编码帧宽度 | 编码帧宽 = `(值+1) * 16` |
| `pic_height_in_map_units_minus1` | 以宏块行为单位的编码帧高度 | 编码帧高 = `(值+1) * 16` |
| `frame_cropping_flag` | 是否启用裁剪标志 | — |
| `frame_crop_left_offset` | 左裁剪偏移（距左边缘的像素数） | → cropLeft（坐标=偏移值） |
| `frame_crop_right_offset` | 右裁剪偏移（距右边缘的像素数） | → cropRight（坐标=编码帧宽-1-偏移值） |
| `frame_crop_top_offset` | 上裁剪偏移（距顶部的像素数） | → cropTop（坐标=偏移值） |
| `frame_crop_bottom_offset` | 下裁剪偏移（距底部的像素数） | → cropBottom（坐标=编码帧高-1-偏移值） |


**对于常见的 yuv420 , frame_mbs_only_flag = 1 的 H.264 视频来说，有效图像尺寸计算公式：**

```
// 方式一：通过SPS偏移量直接计算
picWidth  = (pic_width_in_mbs_minus1 + 1) * 16 - 2 * frame_crop_left_offset - 2 * frame_crop_right_offset
picHeight = (pic_height_in_map_units_minus1 + 1) * 16 - 2 * frame_crop_top_offset – 2 * frame_crop_bottom_offset

// 方式二：通过API坐标值计算（等价）
picWidth  = cropRight - cropLeft + 1
picHeight = cropBottom - cropTop + 1
```

### 3.2 H.265 HEVC 标准

H.265 标准使用 CTU（Coding Tree Unit）替代宏块，SPS 中的对应字段：

| H.265 SPS 字段 | 含义 | 对应 API 键 |
|----------------|------|-------------|
| `pic_width_in_luma_samples` | 亮度分量的编码帧宽度（像素） | 编码帧宽 |
| `pic_height_in_luma_samples` | 亮度分量的编码帧高度（像素） | 编码帧高 |
| `conformance_window_flag` | 是否启用一致性窗口（裁剪）标志 | — |
| `conf_win_left_offset` | 一致性窗口左偏移（距左边缘的像素数） | → cropLeft（坐标=偏移值） |
| `conf_win_right_offset` | 一致性窗口右偏移（距右边缘的像素数） | → cropRight（坐标=编码帧宽-1-偏移值） |
| `conf_win_top_offset` | 一致性窗口上偏移（距顶部的像素数） | → cropTop（坐标=偏移值） |
| `conf_win_bottom_offset` | 一致性窗口下偏移（距底部的像素数） | → cropBottom（坐标=编码帧高-1-偏移值） |

**对于常见的 yuv420 的 H.265 视频来说，有效图像尺寸计算公式：**
```
// 方式一：通过SPS偏移量直接计算
picWidth  = pic_width_in_luma_samples - 2 * conf_win_right_offset - 2 * conf_win_left_offset
picHeight = pic_height_in_luma_samples - 2 * conf_win_bottom_offset - 2 * conf_win_top_offset

// 方式二：通过API坐标值计算（等价）
picWidth  = cropRight - cropLeft + 1
picHeight = cropBottom - cropTop + 1
```

### 3.3 跨距与标准的无关性

**跨距（stride/sliceHeight）不属于任何视频码流标准**，它是**平台/硬件实现相关的内存管理属性**。不同芯片平台可能有不同的对齐规则：

| 平台类型 | 典型对齐要求 |
|---------|-------------|
| 通用 CPU（软件编解码） | stride 通常等于 width（无需额外对齐） |
| ARM GPU (Mali) | 行对齐至 64 或 128 字节 |
| DSP / NPU | 行对齐至 16 或 32 像素 |
| 特定 SoC | 可能需要更严格的对齐 |

开发者应始终通过 `GetInputDescription` / `GetOutputDescription` 或 `OnStreamChanged` 回调获取实际跨距值，而非假设固定值。

---

## 4. 使用场景与代码指南

### 4.1 场景一：编码器 —— 向输入 Buffer 写入数据（需考虑跨距）

当使用编码器 **Buffer 模式**时，编码器通过 `OnNeedInputBuffer` 回调提供可用的输入 Buffer。开发者需要将原始图像数据拷贝到 `OH_AVBuffer` 中。如果**跨距不等于宽/高**，必须按行拷贝并进行跨距偏移。

```c++
// 假设从编码器回调获取到 buffer 和 index
static void FillInputBuffer(OH_AVCodec *codec, uint32_t index,
                            OH_AVBuffer *buffer,
                            const uint8_t *srcData,
                            int32_t width, int32_t height,
                            int32_t srcStride)
{
    // 1. 首次帧：获取编码器的 stride 和 sliceHeight
    static bool firstFrame = true;
    static int32_t dstStride = 0, dstSliceHeight = 0;
    if (firstFrame) {
        auto format = OH_VideoEncoder_GetInputDescription(codec);
        OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_STRIDE, &dstStride);
        OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_SLICE_HEIGHT, &dstSliceHeight);
        firstFrame = false;
    }

    // 2. 获取 Buffer 地址
    uint8_t *dst = OH_AVBuffer_GetAddr(buffer);
    if (dst == nullptr) return;

    // 3. 按行拷贝数据
    const uint8_t *srcY  = srcData;
    const uint8_t *srcUV = srcData + height * srcStride;
    uint8_t *dstY  = dst;
    uint8_t *dstUV = dst + dstSliceHeight * dstStride;

    // 拷贝 Y 分量
    for (int32_t i = 0; i < height; ++i) {
        memcpy_s(dstY, dstStride, srcY, width);
        dstY += dstStride;
        srcY += srcStride;
    }
    // 拷贝 UV 分量（高度为 Y 的一半）
    int32_t uvHeight = height / 2;
    for (int32_t i = 0; i < uvHeight; ++i) {
        memcpy_s(dstUV, dstStride, srcUV, width);
        dstUV += dstStride;
        srcUV += srcStride;
    }

    // 4. 设置 Buffer 属性
    OH_AVCodecBufferAttr attr = {};
    attr.size   = frameSize;
    attr.offset = 0;
    attr.pts    = frameIndex * 1000000 / 30;  // 30fps，单位：微秒
    attr.flags  = 0;  // 最后一帧设为 AVCODEC_BUFFER_FLAGS_EOS
    OH_AVBuffer_SetBufferAttr(buffer, &attr);

    // 5. 送入编码器
    OH_VideoEncoder_PushInputBuffer(codec, index);
}
```

### 4.2 场景二：解码器 —— 从输出 Buffer 读取数据（需考虑跨距 + 裁剪）

当使用解码器 **Buffer 模式**时，需要从解码器输出的 AVBuffer 中读取数据。解码器输出同时涉及**跨距**和**可能的裁剪**：

```c++
// 在 OnStreamChanged 回调或首次调用 GetOutputDescription 时获取参数
static void OnStreamChanged(OH_AVCodec *codec, OH_AVFormat *format, void *userData)
{
    (void)codec;
    (void)userData;

    int32_t picWidth = 0, picHeight = 0;
    int32_t stride = 0, sliceHeight = 0;
    int32_t cropTop = 0, cropBottom = 0, cropLeft = 0, cropRight = 0;

    bool ret = OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_PIC_WIDTH, &picWidth) &&
               OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_PIC_HEIGHT, &picHeight) &&
               OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_STRIDE, &stride) &&
               OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_SLICE_HEIGHT, &sliceHeight) &&
               // 裁剪信息可选（某些码流可能无裁剪）
               OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_CROP_TOP, &cropTop) &&
               OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_CROP_BOTTOM, &cropBottom) &&
               OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_CROP_LEFT, &cropLeft) &&
               OH_AVFormat_GetIntValue(format, OH_MD_KEY_VIDEO_CROP_RIGHT, &cropRight);

    if (!ret) {
        // 异常处理
        return;
    }
    
    printf("有效图像: %d x %d, 跨距: %d x %d\n",
           picWidth, picHeight, stride, sliceHeight);
    if (cropTop || cropBottom || cropLeft || cropRight) {
        printf("裁剪: top=%d bottom=%d left=%d right=%d\n",
               cropTop, cropBottom, cropLeft, cropRight);
    }
}
```

**读取解码输出并按行拷贝的代码模式与编码器相同**（参考场景一的 memcpy 循环），但使用 `picWidth`/`picHeight` 替代 `width`/`height` 作为有效区域尺寸。

### 4.3 场景三：Surface 模式（无需手动处理跨距）

使用 **Surface 模式**时，系统自动处理跨距和内存对齐，开发者无需关心 padding：

| 模式 | 跨距处理责任方 | 需要关注跨距？ |
|------|---------------|--------------|
| **Surface 模式** | 系统（底层图形栈自动处理） | 否 |
| **Buffer 模式** | 开发者（需自行按行拷贝） | 是 |

---

## 5. 尺寸关系速查表

### 5.1 编码器参数关系图

```
Configure 阶段（开发者设置）：
  OH_MD_KEY_WIDTH ──────────→ 编码目标宽度
  OH_MD_KEY_HEIGHT ─────────→ 编码目标高度

运行时（GetInputDescription 获取）：
  OH_MD_KEY_VIDEO_STRIDE ──→ Buffer 行对齐宽（≥ width）
  OH_MD_KEY_VIDEO_SLICE_HEIGHT → Buffer 行对齐高（≥ height）

关系：
  stride ≥ width      （相等时无需跨距偏移）
  sliceHeight ≥ height （相等时无垂直 padding）
```

### 5.2 解码器参数关系图

```
Configure 配置参数：
  OH_MD_KEY_WIDTH            ──→ 配置宽度（解码器缓冲区分配依据）
  OH_MD_KEY_HEIGHT           ──→ 配置高度（解码器缓冲区分配依据）

码流解析结果（GetOutputDescription / OnStreamChanged）：
  picWidth  = cropRight - cropLeft + 1       （有效显示宽）
  picHeight = cropBottom - cropTop + 1        （有效显示高）

  OH_MD_KEY_VIDEO_PIC_WIDTH  ──→ 有效显示宽
  OH_MD_KEY_VIDEO_PIC_HEIGHT ──→ 有效显示高
  OH_MD_KEY_VIDEO_CROP_*     ──→ 裁剪坐标（可选，cropLeft=0/cropTop=0/cropRight=编码帧宽-1/cropBottom=编码帧高-1 时表示无裁剪）

  OH_MD_KEY_VIDEO_STRIDE      ──→ Buffer 行对齐宽（≥ 编码帧宽）
  OH_MD_KEY_VIDEO_SLICE_HEIGHT → Buffer 行对齐高（≥ 编码帧高）

关系（典型情况，有裁剪且有对齐）：
  width/height ≥ cropRight+1 / cropBottom+1  （配置值应覆盖实际码流坐标范围）
  stride ≥ cropRight + 1
  sliceHeight ≥ cropBottom + 1
```

---

## 6. 常见问题 FAQ

### Q1：为什么我的编码输出画面有绿边或花屏？

**原因：** 写入编码器输入 Buffer 时未按跨距对齐拷贝，导致 padding 区域包含脏数据或越界写入。

**解决：** 使用场景一的按行拷贝代码，确保每次 memcpy 的长度为有效宽度，指针步进为跨距。

### Q2：为什么解码后的图片看起来被拉伸或压缩？

**原因：** 读取解码输出时使用了 `stride` 而非 `picWidth`/`picHeight` 作为图像尺寸进行后续处理。

**解决：** 显示或保存时应使用 `picWidth`/`picHeight` 作为图像的实际分辨率；仅在内存操作时使用跨距。

### Q3：何时需要关注裁剪（Crop）信息？

**回答：** 仅在使用解码器且码流中存在非零裁剪值时需要关注。常见于：
- 某些网络摄像头输出的码流（编码帧填充到 16 的倍数后 crop 回原始尺寸）
- 部分转码工具生成的码流

大多数常规码流（如手机拍摄的视频）裁剪值通常覆盖整个编码帧（即 `LEFT=0, TOP=0, RIGHT=编码帧宽-1, BOTTOM=编码帧高-1`），此时 `picWidth=编码帧宽, picHeight=编码帧高`，无需额外处理裁剪偏移。

### Q4：Surface 模式和 Buffer 模式的区别？

| 维度 | Surface 模式 | Buffer 模式 |
|------|-------------|-------------|
| 跨距处理 | 系统/驱动层自动处理 | **开发者必须手动处理** |
| 适用场景 | 摄像头预览、播放渲染 | 转码、AI 处理、文件保存等 |

### Q5：跨距值一定是固定的吗？

**不一定。** 跨距取决于：
- **硬件平台**：不同 SoC 有不同的对齐要求
- **像素格式**：YUV420P 和 RGBA 的对齐规则可能不同
- **运行时条件**：某些情况下（如低延迟模式），跨距可能变化

因此建议**每次在 OnStreamChanged 或首次 GetInputDescription/GetOutputDescription 时重新查询**，不要缓存跨距值。

### Q6：`OH_AVCapability_IsVideoSizeSupported` 等能力查询接口中的宽高参数是指什么？

**回答：** 这些接口中的宽高参数通常指的是码流参数集（如 SPS）中定义的**编码帧宽高**，与 `avcodec` 接口中使用的各种宽高 Key（如 `OH_MD_KEY_WIDTH`、`OH_MD_KEY_VIDEO_PIC_WIDTH` 等）均无直接对标关系。

---

## 参考文档

- [视频编码开发指导](video-encoding.md) —— Surface 模式 / Buffer 模式完整流程
- [视频解码开发指导](video-decoding.md) —— Surface 模式 / Buffer 模式完整流程
- [Codec Base API 参考](../reference/apis-avcodec-kit/capi-codecbase.md) —— 所有键名定义
- [AVCodec Kit API Reference - VideoEncoder](../reference/apis-avcodec-kit/capi-native-avcodec-videoencoder-h.md) —— 编码器接口
- [AVCodec Kit API Reference - VideoDecoder](../reference/apis-avcodec-kit/capi-native-avcodec-videodecoder-h.md) —— 解码器接口
