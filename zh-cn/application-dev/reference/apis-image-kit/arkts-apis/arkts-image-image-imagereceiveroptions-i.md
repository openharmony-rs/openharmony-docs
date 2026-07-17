# ImageReceiverOptions

ImageReceiver的初始化选项。

**起始版本：** 23

<!--Device-image-interface ImageReceiverOptions--><!--Device-image-interface ImageReceiverOptions-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## capacity

```TypeScript
capacity?: number
```

可同时访问的最大图像数量。该值必须为正整数，且小于或等于64张。

该参数仅作为期望值，实际capacity由设备硬件决定。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageReceiverOptions-capacity?: int--><!--Device-ImageReceiverOptions-capacity?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

## size

```TypeScript
size?: Size
```

图像的大小，包括宽与高，且值都大于0。单位：像素（px）。

该参数不会影响接收到的图片大小，实际返回大小由生产者决定，如相机。

**类型：** Size

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageReceiverOptions-size?: Size--><!--Device-ImageReceiverOptions-size?: Size-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

