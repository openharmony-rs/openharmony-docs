# DestHDRMode

```TypeScript
enum DestHDRMode
```

Defines the HDR format of the target file.

**Since:** 26.1.0

<!--Device-media-enum DestHDRMode--><!--Device-media-enum DestHDRMode-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder

## AUTO_HDR_VIVID

```TypeScript
AUTO_HDR_VIVID = 1
```

The target file format is HDR vivid only when the source file format is HDR vivid. In other cases, the target file format is SDR.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-DestHDRMode-AUTO_HDR_VIVID = 1--><!--Device-DestHDRMode-AUTO_HDR_VIVID = 1-End-->

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## SDR

```TypeScript
SDR = 0
```

The target file format is SDR.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-DestHDRMode-SDR = 0--><!--Device-DestHDRMode-SDR = 0-End-->

**System capability:** SystemCapability.Multimedia.Media.AVTranscoder
