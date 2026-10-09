# How to Correctly Identify Media Asset Types
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @TristanMVP-->
<!--Designer: @AnakinJiang-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

[Media Library Kit](../photoAccessHelper-overview.md) provides media asset management capabilities, allowing you to access and manage media information in albums. Different media asset types can be identified in different ways. This section provides examples of how to identify them.

## Identifying Asset Types Using the mimeType Field

You can distinguish media asset types by checking the string prefix of **mimeType**. The rules are as follows:
- If **mimeType** starts with **'image/'**, the media asset is an image.
- If **mimeType** starts with **'video/'**, the media asset is a video.

**Example:**

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

## Identifying Burst Photo Assets by URI

The URI of an unrenamed burst photo contains specific identifiers. You can determine whether an asset is a burst photo by checking keywords in the URI.

- If the URI contains both **burst** and **cover**, the asset is a burst cover.
- If the URI contains only **burst**, the asset is a burst photo (non-cover).
- If the URI does not contain the **burst** keyword, the asset is not a burst photo.

**Example:**

<!-- @[PickerMediaLibrary_getBurstTypeByUri](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Picker/PickerMediaLibrarySample/entry/src/main/ets/common/utils/MediaLibraryPickerUtils.ets) -->

``` TypeScript
function getBurstTypeByUri(uri: string): string {
  const hasBurst = uri.includes('burst');
  const hasCover = uri.includes('cover');
        
  if (hasBurst && hasCover) {
    return 'Burst photo cover'
  } else if (hasBurst) {
    return 'Burst shot photo'
  }
  return 'Non-burst photo'
}
```
