# 如何正确判断媒体资源
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @TristanMVP-->
<!--Designer: @AnakinJiang-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **注意：**
>
> [Media Library Kit](../photoAccessHelper-overview.md)仅提供图片和视频的管理能力，不涉及音频文件的管理。

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
    return 'unknown';
}
```

## 通过URI判断连拍图资源

未重命名连拍照片的URI中包含特定标识，开发者可以通过检查URI中的关键字来判断是否为连拍图资源：

- URI同时包含`burst`和`cover`时，表示该资源为连拍封面。
- URI仅包含`burst`时，表示该资源为连拍照片（非封面）。
- URI中不包含`burst`关键字时，表示该资源为非连拍图。

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