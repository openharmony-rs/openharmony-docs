# GifPropertyKey

表示GIF图片信息的枚举。

**起始版本：** 20

<!--Device-image-enum GifPropertyKey--><!--Device-image-enum GifPropertyKey-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## GIF_DELAY_TIME

```TypeScript
GIF_DELAY_TIME = 'GifDelayTime'
```

GIF图片钳制后的帧延迟时长。钳制范围为[100, 65535]。

单位：毫秒（ms）。

**起始版本：** 20

<!--Device-GifPropertyKey-GIF_DELAY_TIME = 'GifDelayTime'--><!--Device-GifPropertyKey-GIF_DELAY_TIME = 'GifDelayTime'-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## GIF_DISPOSAL_TYPE

```TypeScript
GIF_DISPOSAL_TYPE = 'GifDisposalType'
```

GIF图片的每帧处置方式。

- 0表示未指定。  
- 1表示不处置。  
- 2表示还原为背景色。  
- 3表示还原为前一帧。

该值为正整数。

**起始版本：** 20

<!--Device-GifPropertyKey-GIF_DISPOSAL_TYPE = 'GifDisposalType'--><!--Device-GifPropertyKey-GIF_DISPOSAL_TYPE = 'GifDisposalType'-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## GIF_HAS_GLOBAL_COLOR_MAP

```TypeScript
GIF_HAS_GLOBAL_COLOR_MAP = 'GifHasGlobalColorMap'
```

GIF图像是否包含全局调色板。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifPropertyKey-GIF_HAS_GLOBAL_COLOR_MAP = 'GifHasGlobalColorMap'--><!--Device-GifPropertyKey-GIF_HAS_GLOBAL_COLOR_MAP = 'GifHasGlobalColorMap'-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## GIF_CANVAS_WIDTH

```TypeScript
GIF_CANVAS_WIDTH = 'GifCanvasWidth'
```

GIF图像的画布宽度。

单位：像素（px）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifPropertyKey-GIF_CANVAS_WIDTH = 'GifCanvasWidth'--><!--Device-GifPropertyKey-GIF_CANVAS_WIDTH = 'GifCanvasWidth'-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## GIF_CANVAS_HEIGHT

```TypeScript
GIF_CANVAS_HEIGHT = 'GifCanvasHeight'
```

GIF图像的画布高度。

单位：像素（px）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifPropertyKey-GIF_CANVAS_HEIGHT = 'GifCanvasHeight'--><!--Device-GifPropertyKey-GIF_CANVAS_HEIGHT = 'GifCanvasHeight'-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## GIF_LOOP_COUNT

```TypeScript
GIF_LOOP_COUNT = 'GifLoopCount'
```

GIF图片循环次数。

取值为0或正整数。0表示无限循环，其他值表示实际循环次数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifPropertyKey-GIF_LOOP_COUNT = 'GifLoopCount'--><!--Device-GifPropertyKey-GIF_LOOP_COUNT = 'GifLoopCount'-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## GIF_UNCLAMPED_DELAY_TIME

```TypeScript
GIF_UNCLAMPED_DELAY_TIME = 'GifUnclampedDelayTime'
```

GIF图片未钳制的帧延迟时间。

单位：毫秒（ms）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GifPropertyKey-GIF_UNCLAMPED_DELAY_TIME = 'GifUnclampedDelayTime'--><!--Device-GifPropertyKey-GIF_UNCLAMPED_DELAY_TIME = 'GifUnclampedDelayTime'-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

