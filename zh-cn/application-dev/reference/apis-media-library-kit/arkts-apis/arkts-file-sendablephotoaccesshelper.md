# @ohos.file.sendablePhotoAccessHelper

该模块基于[Sendable](../../../arkts-utils/arkts-sendable.md)对象，提供相册管理功能，包括创建相册和访问、修改相册中的媒体 数据。

**起始版本：** 12

<!--Device-unnamed-declare namespace sendablePhotoAccessHelper--><!--Device-unnamed-declare namespace sendablePhotoAccessHelper-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getPhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-getphotoaccesshelper-f.md) | 获取相册管理模块的实例，用于访问和修改相册中的媒体文件。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-getphotoaccesshelper-f-sys.md) | 支持跨用户获取相册管理模块的实例，用于访问和修改相册中的媒体文件。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AbsAlbum](arkts-medialibrary-sendablephotoaccesshelper-absalbum-i.md) | 定义相册的抽象接口。 |
| [Album](arkts-medialibrary-sendablephotoaccesshelper-album-i.md) | 实体相册 |
| [FetchResult](arkts-medialibrary-sendablephotoaccesshelper-fetchresult-i.md) | 文件检索结果集。 |
| [PhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-photoaccesshelper-i.md) | 提供操作系统媒体资源能力的接口。 |
| [PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md) | 提供封装文件属性的方法。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AbsAlbum](arkts-medialibrary-sendablephotoaccesshelper-absalbum-i-sys.md) | 定义相册的抽象接口。 |
| [Album](arkts-medialibrary-sendablephotoaccesshelper-album-i-sys.md) | 实体相册 |
| [PhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-photoaccesshelper-i-sys.md) | 提供操作系统媒体资源能力的接口。 |
| [PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i-sys.md) | 提供封装文件属性的方法。 |
| [SharedPhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-sharedphotoasset-i-sys.md) | Defines the shared photo asset |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AlbumSubtype](arkts-medialibrary-sendablephotoaccesshelper-albumsubtype-e.md) | 枚举，相册子类型，表示具体的相册类型。 |
| [AlbumType](arkts-medialibrary-sendablephotoaccesshelper-albumtype-e.md) | 枚举，相册类型，表示是用户相册还是系统预置相册。 |
| [DynamicRangeType](arkts-medialibrary-sendablephotoaccesshelper-dynamicrangetype-e.md) | 枚举，媒体文件的动态范围类型。 |
| [PhotoSubtype](arkts-medialibrary-sendablephotoaccesshelper-photosubtype-e.md) | 枚举，不同[PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md)的类型。 |
| [PhotoType](arkts-medialibrary-sendablephotoaccesshelper-phototype-e.md) | 枚举，媒体文件类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AlbumSubtype](arkts-medialibrary-sendablephotoaccesshelper-albumsubtype-e-sys.md) | 枚举，相册子类型，表示具体的相册类型。 |
| [AlbumType](arkts-medialibrary-sendablephotoaccesshelper-albumtype-e-sys.md) | 枚举，相册类型，表示是用户相册还是系统预置相册。 |
| [MovingPhotoEffectMode](arkts-medialibrary-sendablephotoaccesshelper-movingphotoeffectmode-e-sys.md) | Enumeration of moving photo effect mode. |
| [PhotoSubtype](arkts-medialibrary-sendablephotoaccesshelper-photosubtype-e-sys.md) | 枚举，不同[PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md)的类型。 |
| [PositionType](arkts-medialibrary-sendablephotoaccesshelper-positiontype-e-sys.md) | Photo asset position |
| [ThumbnailVisibility](arkts-medialibrary-sendablephotoaccesshelper-thumbnailvisibility-e-sys.md) | Ability to access thumbnail |
<!--DelEnd-->

