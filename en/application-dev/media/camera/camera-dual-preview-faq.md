# Image Data Processing Issues in Dual-Channel Preview
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d264fdc9993bcb3eda088083c9376480dd641e58 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

## Symptom

In dual-channel preview, the preview image data received through [ImageReceiver](../../reference/apis-image-kit/arkts-apis-image-ImageReceiver.md) is unusable, cannot be processed, or produces visual corruption such as misaligned images or incorrect colors.

## Possible Causes

In dual-channel preview, the first preview stream obtains image data for processing through the [ImageReceiver](../../reference/apis-image-kit/arkts-apis-image-ImageReceiver.md) Surface. The correct pixel format and row alignment must be used to parse this data. Possible causes are as follows:

1. After registering the ImageReceiver [on](../../reference/apis-image-kit/arkts-apis-image-ImageReceiver.md#on9) callback and receiving [Image](../../reference/apis-image-kit/arkts-apis-image-Image.md) data, the app calls [createPixelMap](../../reference/apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmap8) without correctly mapping the Image format to PixelMapFormat. The pixel format mismatch prevents correct parsing.

2. The app does not correctly handle row padding in [Component](../../reference/apis-image-kit/arkts-apis-image-i.md#component9).byteBuffer. Each row of camera output may contain extra bytes for memory alignment. Using this data directly can cause misalignment or visual corruption.

## Solution

1. Register the ImageReceiver [on](../../reference/apis-image-kit/arkts-apis-image-ImageReceiver.md#on9) callback. After receiving [Image](../../reference/apis-image-kit/arkts-apis-image-Image.md) data, map its format to the corresponding [PixelMapFormat](../../reference/apis-image-kit/arkts-apis-image-e.md#pixelmapformat7), then call [createPixelMap](../../reference/apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmap8). For the mapping, see step 3 in [First Preview Stream for Image Processing](camera-dual-channel-preview.md#first-preview-stream-used-for-image-processing) in Dual-Channel Preview (ArkTS).

2. Handle row alignment to ensure that the image data contains no extra row padding bytes.

   Obtain the row stride through rowStride in [Component](../../reference/apis-image-kit/arkts-apis-image-i.md#component9) and compare it with the image width. If stride differs from width, remove the extra padding bytes using either of the following methods:

   - Method 1: Copy the valid pixel data row by row into a new buffer, removing row padding, then call [createPixelMap](../../reference/apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmap8).
   - Method 2: Create a PixelMap of stride x height and call [cropSync](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md#cropsync12) to crop out the extra pixels.
