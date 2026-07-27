# 媒体库变更说明

## cl.medialibrary.1 动态照片资源的PhotoKeys.DURATION字段值变更

**访问级别**

公共能力

**变更原因**

图库应用需获取动态照片中附带视频片段的时长，并根据该时长判断是否支持生成3D动态照片。因此动态照片PhotoKeys.DURATION字段的取值由图片资源的默认值0变更为动态照片附带视频片段的时长。

**变更影响**

变更前：动态照片（PhotoKeys.PHOTO_SUBTYPE=PhotoSubtype.MOVING_PHOTO）的PhotoKeys.DURATION字段值为0。

变更后：动态照片（PhotoKeys.PHOTO_SUBTYPE=PhotoSubtype.MOVING_PHOTO）的PhotoKeys.DURATION字段值为视频部分的时长；若无法解析则为-1。

如果应用使用PhotoKeys.DURATION字段进行业务逻辑判断，如判断图片和视频的分类，则需要进行适配，改为使用其他接口进行判断。

**起始 API Level**

14

**变更发生版本**

从OpenHarmony SDK 6.1.0.37开始。

**变更的接口/组件**

PhotoKeys.DURATION

**适配指导**

DURATION字段值仅可用于表示视频或动态照片中附带视频片段的时长，若需要判断图片和视频的分类，建议使用mimeType字段或PhotoKeys.PHOTO_TYPE字段进行判断。具体判断方法和示例代码如下：

- 使用mimeType字段判断图片和视频资源类型，具体判断方式如下：

    - 当mimeType以'image/'开头时，表示该媒体文件为图片。
    - 当mimeType以'video/'开头时，表示该媒体文件为视频。

    示例：
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

- 使用PhotoKeys.PHOTO_TYPE字段判断图片和视频资源类型，具体判断方式如下：

    - 当PhotoKeys.PHOTO_TYPE为PhotoType.IMAGE时，表示该媒体文件为图片。
    - 当PhotoKeys.PHOTO_TYPE为PhotoType.VIDEO时，表示该媒体文件为视频。

    调用getAssets接口查询指定URI对应的图片或视频的PhotoKeys.PHOTO_TYPE，以区分媒体类型，需要申请'ohos.permission.READ_IMAGEVIDEO'权限。

    通过picker的方式调用getAssets接口查询指定URI对应的图片或视频的PhotoKeys.PHOTO_TYPE，以区分媒体类型，则不需要申请此权限，详情请参考[指定URI获取图片或视频资源](../../../application-dev/media/medialibrary/photoAccessHelper-photoviewpicker.md#指定uri获取图片或视频资源)。

    示例：

    ``` TypeScript
    import { photoAccessHelper } from '@kit.MediaLibraryKit';
    import { dataSharePredicates } from '@kit.ArkData';

    async function getMediaTypeByPhotoType(phAccessHelper: photoAccessHelper.PhotoAccessHelper, uri: string): Promise<string> {
      let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
      predicates.equalTo(photoAccessHelper.PhotoKeys.URI, uri);
      let fetchOptions: photoAccessHelper.FetchOptions = {
        fetchColumns: [
          photoAccessHelper.PhotoKeys.PHOTO_TYPE
        ],
        predicates: predicates
      };
      try {
        let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
        if (fetchResult !== undefined) {
          console.info('fetchResult success');
          let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
          if (photoAsset !== undefined) {
            console.info('photoAsset.displayName :' + photoAsset.displayName);
            let photoType: photoAccessHelper.PhotoKeys = photoAccessHelper.PhotoKeys.PHOTO_TYPE;
            let photoAssetPhotoType : number = Number(photoAsset.get(photoType.toString()))
            if (photoAssetPhotoType === photoAccessHelper.PhotoType.VIDEO) {
              return 'video';
            } else if (photoAssetPhotoType === photoAccessHelper.PhotoType.IMAGE) {
              return 'image';
            }
            return 'unknown';
          }
        }
      } catch (err) {
        console.error(`getAssets failed, error: ${err.code}, ${err.message}`);
      }
      return 'undefined';
    }
    ```

> **说明：**
>
> - 如果应用需要判断媒体资源是否为动态照片，建议使用PhotoKeys.PHOTO_SUBTYPE字段进行判断。可参考上述判断图片和视频资源类型的示例，调用getAssets接口查询指定URI对应的图片或视频的PhotoKeys.PHOTO_SUBTYPE字段，当PhotoKeys.PHOTO_SUBTYPE为PhotoSubtype.MOVING_PHOTO时，表示该媒体文件为动态照片。