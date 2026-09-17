# getPixelMap（系统接口）

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## getPixelMap

```TypeScript
function getPixelMap(wallpaperType: WallpaperType, callback: AsyncCallback<image.PixelMap>): void
```

获取壁纸图片的像素图。使用callback异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | 是 | 回调函数。当获取壁纸图片的像素图对象成功，err为undefined，data为获取到的像素图对象；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

wallpaper.getPixelMap(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: image.PixelMap) => {
  if (error) {
    console.error(`Failed to getPixelMap. Code: ${error.code}, message: ${error.message}`);
    return;
  }
  console.info(`success to getPixelMap: ${JSON.stringify(data.getImageInfoSync())}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

wallpaper.getPixelMap(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: image.PixelMap) => {
  console.info(`success to getPixelMap : ${JSON.stringify(data.getImageInfoSync())}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to getPixelMap. Code: ${error.code}, Message: ${error.message}`);
});
```


## getPixelMap

```TypeScript
function getPixelMap(wallpaperType: WallpaperType): Promise<image.PixelMap>
```

获取壁纸图片的像素图。使用Promise异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise对象，返回壁纸图片的像素图对象。 |

**示例**

参见 [getPixelMap](#getpixelmap)
