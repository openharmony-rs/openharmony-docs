# 如何获取媒体图片中的地理位置信息
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

## 媒体去隐私
