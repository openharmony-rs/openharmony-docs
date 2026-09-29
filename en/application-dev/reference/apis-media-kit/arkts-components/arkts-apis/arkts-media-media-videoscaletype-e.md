# VideoScaleType

```TypeScript
enum VideoScaleType
```

Enumerates the video scale modes.

**Since:** 9

<!--Device-media-enum VideoScaleType--><!--Device-media-enum VideoScaleType-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## VIDEO_SCALE_TYPE_FIT

```TypeScript
VIDEO_SCALE_TYPE_FIT = 0
```

Default mode. The video will be stretched to fit the window.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-VideoScaleType-VIDEO_SCALE_TYPE_FIT = 0--><!--Device-VideoScaleType-VIDEO_SCALE_TYPE_FIT = 0-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## VIDEO_SCALE_TYPE_FIT_CROP

```TypeScript
VIDEO_SCALE_TYPE_FIT_CROP = 1
```

Maintains the video's aspect ratio, and scales to fill the shortest side of the window, with the longer side cropped.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-VideoScaleType-VIDEO_SCALE_TYPE_FIT_CROP = 1--><!--Device-VideoScaleType-VIDEO_SCALE_TYPE_FIT_CROP = 1-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## VIDEO_SCALE_TYPE_SCALED_ASPECT

```TypeScript
VIDEO_SCALE_TYPE_SCALED_ASPECT = 2
```

Maintains the video's aspect ratio, and scales to fill the longer side of the window, with the shorter side centered and unfilled parts left black.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-VideoScaleType-VIDEO_SCALE_TYPE_SCALED_ASPECT = 2--><!--Device-VideoScaleType-VIDEO_SCALE_TYPE_SCALED_ASPECT = 2-End-->

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer
