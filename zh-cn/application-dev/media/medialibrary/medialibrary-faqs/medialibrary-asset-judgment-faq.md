# 如何正确判断媒体资源
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @TristanMVP-->
<!--Designer: @AnakinJiang-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

[Media Library Kit](../photoAccessHelper-overview.md)（媒体文件管理服务）提供了媒体资源的管理能力，开发者可以访问和修改相册中的媒体信息。

> **注意：**
>
> Media Library Kit仅提供图片和视频的管理能力，不涉及音频文件的管理。

## 使用mimeType字段来判断资源类型

开发者可以通过判断mimeType的字符串前缀来区分媒体类型，具体判断方式如下：
- 当mimeType以'image/'开头时，表示该媒体文件为图片。
- 当mimeType以'video/'开头时，表示该媒体文件为视频。

**示例：**

```ts

function getMediaTypeByMimeType(mimeType: string): string {
  if (mimeType.startsWith('video/')) {
    return '视频';
  } else if (mimeType.startsWith('image/')) {
    return '图片';
  }
  return '未知';
}
```