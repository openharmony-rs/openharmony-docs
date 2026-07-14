# DecodingDynamicRange

描述解码时期望的图像动态范围。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## AUTO

```TypeScript
AUTO = 0
```

自适应，根据图片信息处理。即如果图片本身为HDR图片，则会按照HDR内容解码；反之按照SDR内容解码。通过
[CreateIncrementalSource](arkts-image-createincrementalsource-f.md#createincrementalsource-1)创建的ImageSource会解码为SDR内容。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SDR

```TypeScript
SDR = 1
```

按照标准动态范围处理图片。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## HDR

```TypeScript
HDR = 2
```

按照高动态范围处理图片。通过[CreateIncrementalSource](arkts-image-createincrementalsource-f.md#createincrementalsource-1)创建的ImageSource会解码为SDR内容。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

