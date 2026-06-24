# PictureScanProgress

定义图片扫描进度的接口。

**起始版本：** 20

**系统能力：** SystemCapability.Print.PrintFramework

## isFinal

```TypeScript
isFinal: boolean
```

是否是本次扫描的最后一张图片。true表示是最后一张图片，false表示不是最后一张图片。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Print.PrintFramework

## pictureFd

```TypeScript
pictureFd: number
```

扫描图片的文件描述符。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Print.PrintFramework

## progress

```TypeScript
progress: number
```

当前进度百分比，范围从0~100。单位：百分比。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Print.PrintFramework

