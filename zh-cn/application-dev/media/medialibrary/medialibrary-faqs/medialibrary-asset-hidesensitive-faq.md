# 如何获取媒体图片中的地理位置信息
为了保护用户图片中的隐私信息，应用在读取图片时，[Media Library Kit](../photoAccessHelper-overview.md)（媒体文件管理服务）对图片进行了去隐私（抹除图片exif中敏感字段信息）处理，因此在消费者使用过程中可能会出现地理位置丢失的情况。
## 查看媒体图片时，图片中未包含地理位置信息
**示例：**

```ts
function GetImageLatitude(context : Context) {
  let file = fs.openSync(uri, fs.OpenMode.READ_ONLY);

  const imageSourceObj = image.createImageSource(file.fd);
  console.info("getImagePropertySync");
  let latitude = imageSourceObj.getImagePropertySync(image.PropertyKey.GPS_LATITUDE);
  console.info("latitude : " + latitude);
}
```
打开图片后，解析图片无法获取图片中的地理位置信息

## 图片去隐私
[Media Library Kit](../photoAccessHelper-overview.md)（媒体文件管理服务）提供了四档图片去隐私级别；用户分享图片时可以根据需要手动选择去隐私级别，而在默认状态下，系统会使用脱敏地理位置信息级别对图片进行去隐私处理。
| 名称  |  说明 |
| ----- | ---- |
| HIDE_LOCATION_AND_SHOOTING_PARAM | 脱敏地理位置和拍摄参数。 |
| HIDE_LOCATION_ONLY | 脱敏地理位置信息。 |
| HIDE_SHOOTING_PARAM_ONLY | 脱敏拍摄参数。 |
| NO_HIDE_SENSITIVE_TYPE |  不脱敏。 |

## 申请ohos.permissions.MEDIA_LOCATION权限
应用申请ohos.permissions.MEDIA_LOCATION权限后，应用的去隐私级别变为不脱敏，应用即可正常获取图片所有敏感信息

## 附录
敏感信息字段说明，具体参考[Image Kit](../../../reference/apis-image-kit/arkts-apis-image-e.md#propertykey7)
### 地理位置信息字段
| 名称  |  说明 |
| ----- | ---- |
| GPSLatitude | 图片纬度。 |
| GPSLongitude | 图片经度。 |
| GPSTimeStamp | GPS时间戳。 |
| GPSDateStamp | GPS日期戳。 |
| GPSAltitude | 基于GPSAltitudeRef的高度。 |
| GPSVersionID | GPS信息版本号。 |
### 拍摄参数字段
| 名称  |  说明 |
| ----- | ---- |
|Make|生产商。|
| Model | 设备型号。 |
| Software | 用于生成图像的软件名称和版本。 |
| DateTime | 日期时间。 |
| ExposureTime |曝光时间。  |
| FNumber | 	光圈值。|
| ExposureProgram | 拍照时相机用来设置曝光的程序的类别。|
| PhotographicSensitivity | 用于表示图像拍摄时所用的感光度值（ISO 值），也叫ISO Speed。 |
| DateTimeOriginal | 	拍摄时间。|
| DateTimeDigitized | 图像作为数字数据存储的日期和时间 |
| ExposureBiasValue | 曝光偏差值。 |
| MeteringMode | 测光模式。 |
| LightSource | 光源。 |
| Flash | 	闪光灯，记录闪光灯状态。 |
| FocalLength | 焦距。 |
| ExposureMode | 	拍摄时设置的曝光模式。 |
| WhiteBalance | 	白平衡。 |
| DigitalZoomRatio | 捕获时的数字变焦比率。 |
| FocalLengthIn35mmFilm | 	换算成35mm等效焦距。 |

