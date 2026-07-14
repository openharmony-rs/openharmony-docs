# PositionArea

表示图片指定区域内的数据。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## offset

```TypeScript
offset: number
```

偏移量。单位：字节（Byte）。

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixels

```TypeScript
pixels: ArrayBuffer
```

像素数据缓冲区。仅支持BGRA_8888格式的像素数据。

**类型：** ArrayBuffer

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## region

```TypeScript
region: Region
```

区域信息，用于按区域进行图像数据的读写。写入的区域宽度加X坐标不能大于原图的宽度，写入的区域高度加Y坐标不能大于原图的高度。

**类型：** Region

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## stride

```TypeScript
stride: number
```

跨距，内存中每行像素所占的空间。单位：字节（Byte）。stride >= region.size.width * 4，不满足时数据读取异常。

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

