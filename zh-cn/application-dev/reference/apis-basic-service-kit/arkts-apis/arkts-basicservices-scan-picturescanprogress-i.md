# PictureScanProgress

定义图片扫描进度的接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-scan-interface PictureScanProgress--><!--Device-scan-interface PictureScanProgress-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## isFinal

```TypeScript
isFinal: boolean
```

是否是本次扫描的最后一张图片。true表示是最后一张图片，false表示不是最后一张图片。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PictureScanProgress-isFinal: boolean--><!--Device-PictureScanProgress-isFinal: boolean-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## pictureFd

```TypeScript
pictureFd: int
```

扫描图片的文件描述符。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PictureScanProgress-pictureFd: int--><!--Device-PictureScanProgress-pictureFd: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## progress

```TypeScript
progress: int
```

当前进度百分比，范围从0~100。单位：百分比。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PictureScanProgress-progress: int--><!--Device-PictureScanProgress-progress: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

