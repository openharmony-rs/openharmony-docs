# OH_PackingOptionsForSequence

```c
typedef struct OH_PackingOptionsForSequence OH_PackingOptionsForSequence
```

## 概述

OH_PackingOptionsForSequence是native层封装的GIF序列编码选项结构体，不可直接操作，而是采用函数调用方式创建、释放结构体以及操作具体字段。<br>使用 {@link OH_PackingOptionsForSequence_Create}函数创建OH_PackingOptionsForSequence对象。<br>使用<br>{@link OH_PackingOptionsForSequence_Release}函数释放OH_PackingOptionsForSequence对象。<br>使用约束：<br>OH_PackingOptionsForSequence用于配置PixelMap序列编码为GIF格式时的编码参数，需传入<br>{@link OH_ImagePackerNative_PackToDataFromPixelmapSequence}或<br>{@link OH_ImagePackerNative_PackToFileFromPixelmapSequence}使用。<br>资源管理：OH_PackingOptionsForSequence使用完成后，应调用<br>{@link OH_PackingOptionsForSequence_Release}释放。释放后不应继续传入图像序列编码接口或调用其字段获取和设置接口。通过<br>{@link OH_PackingOptionsForSequence_SetDelayTimeList}和{@link OH_PackingOptionsForSequence_SetDisposalTypes}<br>传入的数组不会被拷贝，调用方需保证OH_PackingOptionsForSequence对象使用期间数组数据有效。释放OH_PackingOptionsForSequence对象不会释放这些数组。<br><br>OH_PackingOptionsForSequence结构体内容和操作方式如下：<br>\| 字段类型 \| 字段名称 \| 字段描述 \| 字段获取函数 \| 字段设置函数 \|\| -- \| -- \| -- \| -- \| -- \|\|<br>uint32_t \| frameCount \| 编码时指定的帧数，编码时必须大于0。 \| {@link OH_PackingOptionsForSequence_GetFrameCount} \|<br>{@link OH_PackingOptionsForSequence_SetFrameCount} \|\| int32_t\| delayTimeList \| 编码时图片的延迟时间数组，<br>数组中的每个延迟时间必须大于0且不超过65535，单位为10毫秒（ms）。 \| {@link OH_PackingOptionsForSequence_GetDelayTimeList} \|<br>{@link OH_PackingOptionsForSequence_SetDelayTimeList} \|\| uint32_t\| disposalTypes \| 编码时图片的过渡帧模式数组，数组中的每个取值必须小于等于3，<br>取值含义见{@link OH_PackingOptionsForSequence_SetDisposalTypes}。 \| {@link OH_PackingOptionsForSequence_GetDisposalTypes} \|<br> {@link OH_PackingOptionsForSequence_SetDisposalTypes} \|\| uint32_t \| loopCount \| 编码时图片循环播放次数，取值范围为[0, 65535]。 \|<br>{@link OH_PackingOptionsForSequence_GetLoopCount} \| {@link OH_PackingOptionsForSequence_SetLoopCount} \|

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**起始版本：** 18

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_packer_native.h](capi-image-packer-native-h.md)

