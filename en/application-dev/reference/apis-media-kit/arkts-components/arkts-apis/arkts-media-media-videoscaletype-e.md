# VideoScaleType

Enumerates the video scale modes.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## VIDEO_SCALE_TYPE_FIT

```TypeScript
VIDEO_SCALE_TYPE_FIT = 0
```

Default mode. The video will be stretched to fit the window.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## VIDEO_SCALE_TYPE_FIT_CROP

```TypeScript
VIDEO_SCALE_TYPE_FIT_CROP = 1
```

Maintains the video's aspect ratio, and scales to fill the shortest side of the window, with the longer side cropped.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer

## VIDEO_SCALE_TYPE_SCALED_ASPECT

```TypeScript
VIDEO_SCALE_TYPE_SCALED_ASPECT = 2
```

Maintains the video's aspect ratio, and scales to fill the longer side of the window, with the shorter side centered and unfilled parts left black.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Media.VideoPlayer
