# Video Codec Width, Height, Stride, and Crop Information

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhanghongran-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:19:28.539Z pushedAt=2026-07-20T07:55:12.752Z -->

## Overview

In video codec development, **width** and **height** are represented in multiple forms. Additionally, hardware processing typically requires memory alignment (stride), and decoding output may involve a **crop region**. This section systematically organizes the dimension-related parameters in video codec APIs and their relationships, helping you correctly understand and use these parameters.

## Parameter Overview

**Table 1** Overview of dimension parameters

| Parameter | Key Name | Type | Description| Encoder Usage Scenario | Decoder Usage Scenario | Calling API |
|------|------|------|------|--------|--------|----------|
| width/height | `OH_MD_KEY_WIDTH`/`OH_MD_KEY_HEIGHT` | int32_t | Configured video width/height. | Configure the target encoding resolution. | Configure the pre-allocated buffer. | Configure |
| stride | `OH_MD_KEY_VIDEO_STRIDE` | int32_t | Width stride (number of bytes per row after row alignment). | Obtain the memory-aligned width of the buffer. | Obtain the memory-aligned width of the buffer. |GetInputDescription/GetOutputDescription/OnStreamChanged |
| sliceHeight | `OH_MD_KEY_VIDEO_SLICE_HEIGHT` | int32_t | Height stride (total number of rows after column alignment). | Obtain the memory-aligned height of the buffer. | Obtain the memory-aligned height of the buffer. |GetInputDescription/GetOutputDescription/OnStreamChanged |
| picWidth/picHeight | `OH_MD_KEY_VIDEO_PIC_WIDTH`/`OH_MD_KEY_VIDEO_PIC_HEIGHT` | int32_t | Actual valid width/height of the image. | — | Obtain the valid width/height of the decoded output.|GetOutputDescription/OnStreamChanged |
| cropTop | `OH_MD_KEY_VIDEO_CROP_TOP` | int32_t | Top row coordinate (y) of the crop rectangle, including the top row of the crop frame. Row index starts from 0. | — | Obtain the upper boundary of the decoded crop.|GetOutputDescription/OnStreamChanged |
| cropBottom | `OH_MD_KEY_VIDEO_CROP_BOTTOM` | int32_t | Bottom row coordinate (y) of the crop rectangle, including the bottom row of the crop frame. Row index starts from 0. | — | Obtain the lower boundary of the decoded crop. |GetOutputDescription/OnStreamChanged |
| cropLeft | `OH_MD_KEY_VIDEO_CROP_LEFT` | int32_t | Left column coordinate (x) of the crop rectangle, including the leftmost column of the crop frame. Column index starts from 0. | — | Obtain the left boundary of the decoded crop. |GetOutputDescription/OnStreamChanged |
| cropRight | `OH_MD_KEY_VIDEO_CROP_RIGHT` | int32_t | Right column coordinate (x) of the crop rectangle, including the rightmost column of the crop frame. Column index starts from 0. | — | Obtain the right boundary of the decoded crop. |GetOutputDescription/OnStreamChanged |

> **NOTE**
>
> For the definitions of the keys in the table, refer to [native_avcodec_base.h](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md).

## Core Concepts

### Difference Between width/height and picWidth/picHeight

**width/height (Configured Dimensions)**

The encoder's `OH_MD_KEY_WIDTH` and `OH_MD_KEY_HEIGHT` are the target encoding resolution configured through the `Configure` API. This is the **expected size** of the encoder input data, and also the **encoding resolution** in the bitstream.

```c++
// Encoder configuration example.
OH_AVFormat *format = OH_AVFormat_Create();
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1920);  // Target encoding width.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1080);  // Target encoding height.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12);
// Destroy the format after use.
OH_AVFormat_Destroy(format);
```

The decoder's `OH_MD_KEY_WIDTH` and `OH_MD_KEY_HEIGHT` serve as decoding resolution hints configured through the `Configure` API. Based on these parameters, the decoder **pre-allocates internal buffers** to ensure that the encoded frame size in the bitstream can be accommodated.

> **NOTE**
>
> - The decoder's `width`/`height` are **expected values** during the configuration phase. The actual valid image size of the decoded output is determined by `OH_MD_KEY_VIDEO_PIC_WIDTH`/`OH_MD_KEY_VIDEO_PIC_HEIGHT` (see below).
> - You are advised to set `width`/`height` to match the actual bitstream resolution or slightly larger.
> - The decoder supports dynamic changes in bitstream resolution (e.g., adaptive bitrate scenarios), in which case the decoder outputs the corresponding `picWidth`/`picHeight` based on the actual frame size.

```c++
// Decoder configuration example.
OH_AVFormat *format = OH_AVFormat_Create();
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1920);   // Decoding width (mandatory).
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1080);  // Decoding height (mandatory).
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12);
// Destroy the format after use.
OH_AVFormat_Destroy(format);
```

**picWidth/picHeight (Valid Image Dimensions)**

The decoder's `OH_MD_KEY_VIDEO_PIC_WIDTH` and `OH_MD_KEY_VIDEO_PIC_HEIGHT` represent the width and height of the **actual valid pixel region** in the decoded output.

Since video bitstream standards (such as H.264/H.265) support the crop mechanism, the size of an encoded frame in the bitstream is not equivalent to the **actual valid pixel region**.

```txt
picWidth  = cropRight - cropLeft + 1     (Width: difference between the left and right column coordinates plus 1.)
picHeight = cropBottom - cropTop + 1     (Height: difference between the top and bottom row coordinates plus 1.)
```

### stride/sliceHeight (Memory Stride)

**Definition of Stride**

Video codec hardware typically requires **memory alignment to specific bytes or pixels** to improve access efficiency. When the configured image width/height does not meet the alignment requirements, the hardware allocates a larger buffer, and the excess portion is referred to as **padding**.

Stride has two dimensions:

- **Stride**: The actual number of bytes per row in memory, typically greater than or equal to the valid image width.

- **sliceHeight**: The total number of rows allocated in memory, typically greater than or equal to the valid image height.

The relationship between the two and the valid dimensions is as follows:

```txt
stride      = width + padding_width          (Horizontal direction)
sliceHeight = height + padding_height        (Vertical direction)
```

**Memory Layout on the Encoder Side**

Taking the NV12 format as an example, the memory layout of the encoder input buffer is shown in Figure 1.

**Figure 1** Memory layout of an NV12 format image
![encoder stride](figures/copy-by-line-encoder.png)

The following table describes the parameters in Figure 1.

| Parameter | Key Name | Description |
|------|------|------|
| width | `OH_MD_KEY_WIDTH` | The valid image width configured by the developer. |
| height | `OH_MD_KEY_HEIGHT` | The valid image height configured by the developer. |
| stride | `OH_MD_KEY_VIDEO_STRIDE` | The actual number of pixels per row in the buffer (including right-side padding). |
| sliceHeight | `OH_MD_KEY_VIDEO_SLICE_HEIGHT` | The actual number of rows in the Y-plane region (including bottom padding). |

**Memory Layout on the Decoder Side**

The memory layout of the decoder output buffer is similar, but different key names are used to identify the valid region.

**Figure 2** Memory layout of the decoder output buffer 
![decoder stride](figures/copy-by-line-decoder.png)

The following table describes the parameters in Figure 2.

| Name | Key Name | Description |
|------|------|------|
| picWidth | `OH_MD_KEY_VIDEO_PIC_WIDTH` | Actual valid width of the decoded image. |
| picHeight | `OH_MD_KEY_VIDEO_PIC_HEIGHT` | Actual valid height of the decoded image. |
| stride | `OH_MD_KEY_VIDEO_STRIDE` | Actual number of pixels per row in the buffer (including right-side padding). |
| sliceHeight | `OH_MD_KEY_VIDEO_SLICE_HEIGHT` | Actual number of rows in the Y-component region (including bottom padding). |

### Crop Rectangle

**Memory Layout on the Decoder Side with Crop Information**

In most cases, the left and top crop offsets in the bitstream parameter set are 0. Therefore, the valid display area of the decoded output usually starts from the beginning of the memory buffer, meaning that both `cropLeft` and `cropTop` are 0.

**Figure 3** Memory layout on the decoder side with crop information
![crop](figures/crop_display.png)

The four decoder-specific crop parameters define the rectangular region of the **valid display area**.

| Name | Key Name | Description |
|------|--------|--------|
| cropLeft | `OH_MD_KEY_VIDEO_CROP_LEFT` | The column coordinate (x) of the left edge of the valid area. The coordinate starts from 0, and the specified column is included. |
| cropRight | `OH_MD_KEY_VIDEO_CROP_RIGHT` | The column coordinate (x) of the right edge of the valid area. The coordinate starts from 0, and the specified column is included. |
| cropTop | `OH_MD_KEY_VIDEO_CROP_TOP` | The row coordinate (y) of the top edge of the valid area. The coordinate starts from 0, and the specified row is included. |
| cropBottom | `OH_MD_KEY_VIDEO_CROP_BOTTOM` | The row coordinate (y) of the bottom edge of the valid area. The coordinate starts from 0, and the specified row is included. |

## Relationship Between picWidth/picHeight and Bitstream Standards (H.264/H.265)

### H.264/AVC Standard

In the H.264 standard, the image size relationship is defined by the following fields in the Sequence Parameter Set (SPS).

| H.264 SPS Field | Description |
|----------------|------|
| `pic_width_in_mbs_minus1` | Encoded frame width in units of macroblocks. |
| `pic_height_in_map_units_minus1` | Encoded frame height in units of macroblock rows. |
| `frame_cropping_flag` | Whether cropping is enabled. |
| `frame_crop_left_offset` | Left crop offset (number of pixels from the left edge). |
| `frame_crop_right_offset` | Right crop offset (number of pixels from the right edge). |
| `frame_crop_top_offset` | Top crop offset (number of pixels from the top edge). |
| `frame_crop_bottom_offset` | Bottom crop offset (number of pixels from the bottom edge). |

For common formats such as YUV420 and H.264 videos with `frame_mbs_only_flag = 1`, the valid image size can be calculated using the following formulas.

```txt
// Method 1: Calculate directly using SPS offsets.
picWidth  = (pic_width_in_mbs_minus1 + 1) * 16 - 2 * frame_crop_left_offset - 2 * frame_crop_right_offset
picHeight = (pic_height_in_map_units_minus1 + 1) * 16 - 2 * frame_crop_top_offset - 2 * frame_crop_bottom_offset

// Method 2: Calculate using API coordinate values (equivalent).
picWidth  = cropRight - cropLeft + 1
picHeight = cropBottom - cropTop + 1
```

### H.265 HEVC Standard

The H.265 standard uses Coding Tree Unit (CTU) instead of macroblocks. The following table lists the corresponding fields in the SPS.

| H.265 SPS Field | Description |
|----------------|------|
| `pic_width_in_luma_samples` | Width of the encoded frame in luma samples (in pixels). |
| `pic_height_in_luma_samples` | Height of the encoded frame in luma samples (in pixels). |
| `conformance_window_flag` | Whether the conformance window (crop) is enabled. |
| `conf_win_left_offset` | Left offset of the conformance window (number of pixels from the left edge). |
| `conf_win_right_offset` | Right offset of the conformance window (number of pixels from the right edge). |
| `conf_win_top_offset` | Top offset of the conformance window (number of pixels from the top edge). |
| `conf_win_bottom_offset` | Bottom offset of the conformance window (number of pixels from the bottom edge). |

For common YUV420 H.265 videos, the valid image size can be calculated using the following formulas.

```txt
// Method 1: Calculate directly using SPS offsets.
picWidth  = pic_width_in_luma_samples - 2 * conf_win_right_offset - 2 * conf_win_left_offset
picHeight = pic_height_in_luma_samples - 2 * conf_win_bottom_offset - 2 * conf_win_top_offset

// Method 2: Calculated using API coordinate values (equivalent).
picWidth  = cropRight - cropLeft + 1
picHeight = cropBottom - cropTop + 1
```

> **NOTE**
>
> Stride (stride/sliceHeight) is a **platform/hardware implementation-related memory management attribute** and does not belong to any video codec standard. Therefore, different chip platforms have different alignment rules.
>
> 1. General-purpose CPU (software codec) platform: stride is usually equal to width (no additional alignment required).
> 2. ARM GPU (Mali) platform: row alignment to 64 or 128 bytes.
> 3. DSP/NPU platform: row alignment to 16 or 32 pixels.
> 4. Specific SoC: may require stricter alignment.
> You should obtain the actual stride value through `GetInputDescription`/`GetOutputDescription` or the `OnStreamChanged` callback, rather than assuming a fixed value.

## Code Example

### Scenario 1: Writing Data to the Encoder Input Buffer

In encoder buffer mode, the encoder provides an available input buffer through the `OnNeedInputBuffer` callback. You need to copy the raw image data into the `OH_AVBuffer`. When the buffer memory stride is greater than the configured width and height, the valid data must be copied row by row while skipping the padding area; otherwise, the image will be misaligned.

Reference code: step 3 in [Buffer Mode](video-encoding.md#buffer-mode) of the video encoding development guide, and step 8 in [Buffer Mode](video-encoding.md#buffer-mode) of the video encoding development guide

### Scenario 2: Reading Data from the Decoder Output Buffer

In decoder buffer mode, when reading data, it is necessary to read row by row based on the valid image dimensions and stride, and to skip padding and invalid edges in combination with the crop information.

Reference code: step 3 in [Buffer Mode](video-decoding.md#buffer-mode) of the video decoding development guide, and step 11 in [Buffer Mode](video-decoding.md#buffer-mode) of the video decoding development guide

### Scenario 3: Surface Mode

When surface mode is used, the system automatically handles stride and memory alignment. You do not need to manage padding.

| Mode | Party Responsible for Stride Handling | Need to Consider Stride |
|------|-------------------------------|-----------------------------|
| Surface mode | System (automatically handled by the underlying graphics stack). | No |
| Buffer mode | Developer (data must be copied row by row). | Yes |

## Dimension Relationship Quick Reference

### Encoder Parameter Relationship Diagram

```txt
Configure phase (set by developers):
  OH_MD_KEY_WIDTH                -> Target encoding width
  OH_MD_KEY_HEIGHT               -> Target encoding height

Runtime (obtained through GetInputDescription):
  OH_MD_KEY_VIDEO_STRIDE         -> Buffer stride in width direction (>= width)
  OH_MD_KEY_VIDEO_SLICE_HEIGHT   -> Buffer stride in height direction (>= height)

Relationship:
  stride      >= width (no stride offset is required when they are equal)
  sliceHeight >= height (no vertical padding is required when they are equal)
```

### Decoder Parameter Relationship Diagram

```txt
Configure parameters:
  OH_MD_KEY_WIDTH                -> Configured width (used for decoder buffer allocation)
  OH_MD_KEY_HEIGHT               -> Configured height (used for decoder buffer allocation)

Bitstream parsing results (GetOutputDescription/OnStreamChanged):
  OH_MD_KEY_VIDEO_PIC_WIDTH      -> cropRight - cropLeft + 1 (valid display width)
  OH_MD_KEY_VIDEO_PIC_HEIGHT     -> cropBottom - cropTop + 1 (valid display height)
  OH_MD_KEY_VIDEO_CROP_*         -> Crop coordinates (optional. When cropLeft = 0, cropTop = 0, cropRight = encoded frame width - 1, and cropBottom = encoded frame height - 1, no cropping is applied.)

  OH_MD_KEY_VIDEO_STRIDE         -> Buffer stride in width direction (>= encoded frame width)
  OH_MD_KEY_VIDEO_SLICE_HEIGHT   -> Buffer stride in height direction (>= encoded frame height)

Relationship (typical case, with cropping and alignment):
  width/height  ≥ cropRight+1/cropBottom+1 (configured values must cover the actual coordinate range in the bitstream)
  stride        ≥ cropRight + 1
  sliceHeight   ≥ cropBottom + 1
```

## FAQs

### Q1: Why Do Green Edges or Corrupted Frames Appear in the Encoded Output?

**Answer**: When writing input data to the encoder buffer, the data is not copied according to the stride alignment requirements. As a result, the padding area may contain invalid data or out-of-bounds writes may occur.

**Solution**: Use the row-by-row copy method described in Scenario 1. Ensure that the length of each `memcpy` operation is the valid width and that the pointer is advanced by the stride.

### Q2: Why Does the Decoded Image Appear Stretched or Compressed?

**Answer**: When processing decoded output, the `stride` is used as the image width and height instead of `picWidth` and `picHeight`.

**Solution**: Use `picWidth` and `picHeight` as the actual image resolution for display or saving, and use `stride` only for memory operations.

### When Do I Need to Consider Crop Information?

**Answer**: You only need to consider crop information when using a decoder and the bitstream contains non-zero crop values. This is commonly seen in the following scenarios:

- Bitstreams output by some network cameras. (The encoded frame is padded to a multiple of 16 and then cropped back to the original size.)

- Bitstreams generated by some transcoding tools.

For most common bitstreams, such as videos recorded by mobile phones, the crop values usually cover the entire coded frame. In this case, `LEFT = 0`, `TOP = 0`, `RIGHT = encoded frame width - 1`, and `BOTTOM = encoded frame height - 1`. Therefore, `picWidth` equals the coded frame width and `picHeight` equals the coded frame height, and no additional crop offset processing is required.

### What Are the Differences Between Surface Mode and Buffer Mode?

**Answer**: The differences are shown in the following table.

| Aspect | Surface Mode | Buffer Mode |
|------|-------------|-------------|
| Stride handling | Handled automatically by the system/driver layer. | Must be handled manually by the developer. |
| Applicable scenarios | Camera preview and playback rendering. | Transcoding, AI processing, file saving, etc. |

### Q5: Are Stride Values Always Fixed?

**Answer**: Not necessarily. The stride depends on:

- Platform: Different SoCs have different alignment requirements.

- Pixel format: The alignment rules for YUV420P and RGBA may differ.

Therefore, query the stride again each time in `OnStreamChanged` or during the first call to `GetInputDescription`/`GetOutputDescription`. Do not cache the stride value.

### Q6: What Do the Width and Height Parameters in Capability Query APIs Such as `OH_AVCapability_IsVideoSizeSupported` Refer To?

**Answer**: The width and height parameters in these APIs generally refer to the **encoded frame width and height** defined in the bitstream parameter set (such as SPS), and they do not directly correspond to any of the width/height keys used in the `avcodec` APIs (such as `OH_MD_KEY_WIDTH`, `OH_MD_KEY_VIDEO_PIC_WIDTH`, etc.). During decoding, the decoder determines whether decoding at that resolution is supported based on the **encoded frame width and height** read from the bitstream parameter set. If the width and height queried earlier do not match the actual parameters in the bitstream, the actual decoding capability may differ from the query result.

## References

- [Video Encoding](video-encoding.md): complete workflow for surface mode and buffer mode

- [Video Decoding](video-decoding.md): complete workflow for surface mode and buffer mode.

- [native_avcodec_base.h](../../reference/apis-avcodec-kit/capi-native-avcodec-base-h.md): definitions of all key names

- [native_avcodec_videoencoder.h](../../reference/apis-avcodec-kit/capi-native-avcodec-videoencoder-h.md): encoder APIs

- [native_avcodec_videodecoder.h](../../reference/apis-avcodec-kit/capi-native-avcodec-videodecoder-h.md): decoder APIs