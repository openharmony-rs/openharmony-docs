# 如何正确判断媒体资源
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @TristanMVP-->
<!--Designer: @AnakinJiang-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

[Media Library Kit](../photoAccessHelper-overview.md)（媒体文件管理服务）提供了媒体资源的管理能力，开发者可以访问和管理相册中的媒体信息。针对不同的媒体资源类型，系统提供了相应的判断方式，本文档提供了相关示例方法。

## 使用mimeType字段来判断资源类型

开发者可以通过判断mimeType的字符串前缀来区分媒体类型，具体判断方式如下：
- 当mimeType以'image/'开头时，表示该媒体文件为图片。
- 当mimeType以'video/'开头时，表示该媒体文件为视频。

**示例：**

<!-- @[PickerMediaLibrary_getMediaTypeByMimeType](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Picker/PickerMediaLibrarySample/entry/src/main/ets/common/utils/MediaLibraryPickerUtils.ets) -->

``` TypeScript
function getMediaTypeByMimeType(mimeType: string): string {
  if (mimeType.startsWith('video/')) {
    return 'video';
  } else if (mimeType.startsWith('image/')) {
    return 'image';
  }
  return 'unKnown';
}
```

## 通过URI判断连拍图资源

未重命名连拍照片的URI中包含特定标识，开发者可以通过检查URI中的关键字来判断是否为连拍图资源。

- 当URI同时包含`burst`和`cover`时，表示该资源为连拍封面。
- 当URI仅包含`burst`时，表示该资源为连拍照片（非封面）。
- 当URI中不包含`burst`关键字时，表示该资源为非连拍图。

**示例：**

<!-- @[PickerMediaLibrary_getBurstTypeByUri](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Picker/PickerMediaLibrarySample/entry/src/main/ets/common/utils/MediaLibraryPickerUtils.ets) -->

``` TypeScript
function getBurstTypeByUri(uri: string): string {
  const hasBurst = uri.includes('burst');
  const hasCover = uri.includes('cover');
        
  if (hasBurst && hasCover) {
    return '连拍封面';
  } else if (hasBurst) {
    return '连拍照片';
  }
  return '非连拍图';
}
```