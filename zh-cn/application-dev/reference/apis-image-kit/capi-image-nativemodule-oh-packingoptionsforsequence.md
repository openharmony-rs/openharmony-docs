# OH_PackingOptionsForSequence
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_PackingOptionsForSequence OH_PackingOptionsForSequence
```

## 概述

OH_PackingOptionsForSequence是native层封装的GIF序列编码选项结构体，不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。

使用[OH_PackingOptionsForSequence_Create](capi-image-packer-native-h.md#oh_packingoptionsforsequence_create)函数创建OH_PackingOptionsForSequence对象。

使用[OH_PackingOptionsForSequence_Release](capi-image-packer-native-h.md#oh_packingoptionsforsequence_release)函数释放OH_PackingOptionsForSequence对象。

使用约束：OH_PackingOptionsForSequence用于配置PixelMap序列编码为GIF格式时的编码参数，需传入[OH_ImagePackerNative_PackToDataFromPixelmapSequence](capi-image-packer-native-h.md#oh_imagepackernative_packtodatafrompixelmapsequence)或[OH_ImagePackerNative_PackToFileFromPixelmapSequence](capi-image-packer-native-h.md#oh_imagepackernative_packtofilefrompixelmapsequence)使用。

资源管理：OH_PackingOptionsForSequence使用完成后，应调用[OH_PackingOptionsForSequence_Release](capi-image-packer-native-h.md#oh_packingoptionsforsequence_release)释放。释放后不应继续传入图像序列编码接口或调用其字段获取和设置接口。通过[OH_PackingOptionsForSequence_SetDelayTimeList](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setdelaytimelist)和[OH_PackingOptionsForSequence_SetDisposalTypes](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setdisposaltypes)传入的数组不会被拷贝，调用方需保证OH_PackingOptionsForSequence对象使用期间数组数据有效。释放OH_PackingOptionsForSequence对象不会释放这些数组。

OH_PackingOptionsForSequence结构体内容和操作方式如下：

| 字段类型 | 字段名称 | 字段描述 | 字段获取函数 | 字段设置函数 |
| -- | -- | -- | -- | -- |
| uint32_t | frameCount | 编码时指定的帧数，编码时必须大于0。 | [OH_PackingOptionsForSequence_GetFrameCount](capi-image-packer-native-h.md#oh_packingoptionsforsequence_getframecount) | [OH_PackingOptionsForSequence_SetFrameCount](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setframecount) |
| int32_t * | delayTimeList | 编码时图片的延迟时间数组，数组中的每个延迟时间必须大于0且不超过65535，单位为10毫秒（ms）。 | [OH_PackingOptionsForSequence_GetDelayTimeList](capi-image-packer-native-h.md#oh_packingoptionsforsequence_getdelaytimelist) | [OH_PackingOptionsForSequence_SetDelayTimeList](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setdelaytimelist) |
| uint32_t * | disposalTypes | 编码时图片的过渡帧模式数组，数组中的每个取值必须小于等于3，取值含义见[OH_PackingOptionsForSequence_SetDisposalTypes](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setdisposaltypes)。 | [OH_PackingOptionsForSequence_GetDisposalTypes](capi-image-packer-native-h.md#oh_packingoptionsforsequence_getdisposaltypes) | [OH_PackingOptionsForSequence_SetDisposalTypes](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setdisposaltypes) |
| uint32_t | loopCount | 编码时图片循环播放次数，取值范围为[0, 65535]。 | [OH_PackingOptionsForSequence_GetLoopCount](capi-image-packer-native-h.md#oh_packingoptionsforsequence_getloopcount) | [OH_PackingOptionsForSequence_SetLoopCount](capi-image-packer-native-h.md#oh_packingoptionsforsequence_setloopcount) |

**起始版本：** 18

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_packer_native.h](capi-image-packer-native-h.md)
