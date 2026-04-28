# 如何获取媒体图片中的地理位置信息
## 问题现象
```ts
async GetImageLatitude(context : Context) {
  let srcUri = '';
  try {
	  let fetchResult = await photoAccessHelper.getAssets(fetchOptions);
      if (fetchResult !== undefined) {
      	let asset = await fetchResult.getFirstObject();
        srcUri = assets.uri;
      }
  } catch (err) {
  	console.error('getAssets failed, error:${err.code}, ${err.message}')
  }
  
  let file = fs.openSync(srcUri, fs.OpenMode.READ_ONLY);

  const imageSourceObj = image.createImageSource(file.fd);
  console.info("getImagePropertySync");
  // 获取地理位置信息为空
  let latitude = imageSourceObj.getImagePropertySync(image.PropertyKey.GPS_LATITUDE);
  console.info("latitude : " + latitude);
}
```
使用只读模式打开图片后，解析图片无法获取图片中的地理位置信息

## 问题原因
为了保护用户图片中的隐私信息，应用在读取图片时，[Media Library Kit](../photoAccessHelper-overview.md)（媒体文件管理服务）会对图片进行了去隐私（抹除图片exif中敏感字段信息）处理，因此在图片使用过程中可能会出现地理位置丢失的情况。
> **注意：**
>
> 去隐私处理仅针对图片，视频不提供去隐私能力。

## 解决措施
应用申请[ohos.permissions.MEDIA_LOCATION](../../../security/AccessToken/permissions-for-all-user.md#ohospermissionmedia_location)权限后，应用的去隐私级别变为不脱敏，应用即可正常获取图片所有敏感信息。

## 附录
地理位置信息字段说明，具体字段说明和使用使用方式请参考[Image Kit](../../../reference/apis-image-kit/arkts-apis-image-e.md#propertykey7)
| 名称  |  说明 |
| ----- | ---- |
| GPSLatitude | 图片纬度。 |
| GPSLongitude | 图片经度。 |
| GPSTimeStamp | GPS时间戳。 |
| GPSDateStamp | GPS日期戳。 |
| GPSAltitude | 基于GPSAltitudeRef的高度。 |
| GPSVersionID | GPS信息版本号。 |

