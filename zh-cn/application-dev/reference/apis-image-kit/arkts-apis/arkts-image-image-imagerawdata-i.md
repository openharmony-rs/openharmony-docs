# ImageRawData

图像的RAW数据。

**起始版本：** 24

<!--Device-image-interface ImageRawData--><!--Device-image-interface ImageRawData-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## bitsPerPixel

```TypeScript
bitsPerPixel: number
```

每个像素在缓冲区数据中实际占用的位数。单位：比特（bit）。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRawData-bitsPerPixel: int--><!--Device-ImageRawData-bitsPerPixel: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## buffer

```TypeScript
buffer: ArrayBuffer
```

图像缓冲区。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageRawData-buffer: ArrayBuffer--><!--Device-ImageRawData-buffer: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

