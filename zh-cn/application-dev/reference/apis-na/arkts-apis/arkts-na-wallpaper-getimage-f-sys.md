# getImage（系统接口）

## getImage

```TypeScript
function getImage(wallpaperType: WallpaperType, callback: AsyncCallback<image.PixelMap>): void
```

获取壁纸图片的像素图，且只能获取使用setImage设置的静态壁纸。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WALLPAPER

<!--Device-wallpaper-function getImage(wallpaperType: WallpaperType, callback: AsyncCallback<image.PixelMap>): void--><!--Device-wallpaper-function getImage(wallpaperType: WallpaperType, callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<image.PixelMap> | 是 | 回调函数，调用成功则返回壁纸图片的像素图对象，调用失败则返回error信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

wallpaper.getImage(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: image.PixelMap) => {
  if (error) {
    console.error(`failed to getImage. Code: ${error.code}, Message: ${error.message}`);
    return;
  }
  console.info(`success to getImage: ${JSON.stringify(data.getImageInfoSync())}`);
});

```


## getImage

```TypeScript
function getImage(wallpaperType: WallpaperType): Promise<image.PixelMap>
```

获取壁纸图片的像素图，且只能获取使用setImage设置的静态壁纸。使用promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WALLPAPER

<!--Device-wallpaper-function getImage(wallpaperType: WallpaperType): Promise<image.PixelMap>--><!--Device-wallpaper-function getImage(wallpaperType: WallpaperType): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<image.PixelMap> | 调用成功则返回壁纸图片的像素图对象，调用失败则返回error信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

wallpaper.getImage(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: image.PixelMap) => {
  console.info(`success to getImage: ${JSON.stringify(data.getImageInfoSync())}`);
}).catch((error: BusinessError) => {
  console.error(`failed to getImage. Code: ${error.code}, Message: ${error.message}`);
});

```

