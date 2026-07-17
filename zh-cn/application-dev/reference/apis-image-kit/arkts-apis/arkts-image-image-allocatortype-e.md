# AllocatorType

表示用于图像解码的内存类型的枚举。开发者可根据场景选择合适的内存申请类型。

**起始版本：** 15

<!--Device-image-enum AllocatorType--><!--Device-image-enum AllocatorType-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## AUTO

```TypeScript
AUTO = 0
```

系统决定内存申请类型。

**起始版本：** 15

<!--Device-AllocatorType-AUTO = 0--><!--Device-AllocatorType-AUTO = 0-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## DMA

```TypeScript
DMA = 1
```

使用DMA（Direct Memory Access，直接内存访问）的内存类型，适用于对解码及渲染性能有较高要求的场景。根据设备硬件的差异可能会在每行像素的末尾产生用于内存对齐的空白填充字节。

**起始版本：** 15

<!--Device-AllocatorType-DMA = 1--><!--Device-AllocatorType-DMA = 1-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## SHARE_MEMORY

```TypeScript
SHARE_MEMORY = 2
```

使用共享内存（Share Memory）的内存类型。

**起始版本：** 15

<!--Device-AllocatorType-SHARE_MEMORY = 2--><!--Device-AllocatorType-SHARE_MEMORY = 2-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

