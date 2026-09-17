# setWallpaper

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## setWallpaper

```TypeScript
function setWallpaper(
    source: string | image.PixelMap,
    wallpaperType: WallpaperType,
    callback: AsyncCallback<void>
  ): void
```

将指定资源设置为指定类型的壁纸。使用callback异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.SET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | string &#124; [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | 是 | JPEG或PNG文件的Uri路径，或者PNG格式文件的位图。 |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置壁纸成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

// source类型为string
let wallpaperPath = '/data/storage/el2/base/haps/entry/files/js.jpeg';
wallpaper.setWallpaper(wallpaperPath, wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to setWallpaper. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to setWallpaper.`);
});

// source类型为image.PixelMap
let imageSource = image.createImageSource('file://' + wallpaperPath);
let opts: image.DecodingOptions = {
    desiredSize: {
        height: 3648,
        width: 2736
    }
};
imageSource.createPixelMap(opts).then((pixelMap: image.PixelMap) => {
    wallpaper.setWallpaper(pixelMap, wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError) => {
        if (error) {
            console.error(`Failed to setWallpaper. Code: ${error.code}, message: ${error.message}`);
            return;
        }
        console.info(`success to setWallpaper.`);
    });
}).catch((error: BusinessError) => {
    console.error(`Failed to createPixelMap. Code: ${error.code}, message: ${error.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

// source类型为string
let wallpaperPath = '/data/storage/el2/base/haps/entry/files/js.jpeg';
wallpaper.setWallpaper(wallpaperPath, wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
    console.info(`success to setWallpaper.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to setWallpaper. Code: ${error.code}, message: ${error.message}`);
});
  
// source类型为image.PixelMap
let imageSource = image.createImageSource('file://' + wallpaperPath);
let opts: image.DecodingOptions = {
    desiredSize: {
        height: 3648,
        width: 2736
    }
};
imageSource.createPixelMap(opts).then((pixelMap: image.PixelMap) => {
    wallpaper.setWallpaper(pixelMap, wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
        console.info(`success to setWallpaper.`);
    }).catch((error: BusinessError) => {
        console.error(`Failed to setWallpaper. Code: ${error.code}, message: ${error.message}`);
    });
  }).catch((error: BusinessError) => {
    console.error(`Failed to createPixelMap. Code: ${error.code}, message: ${error.message}`);
});
```


## setWallpaper

```TypeScript
function setWallpaper(source: string | image.PixelMap, wallpaperType: WallpaperType): Promise<void>
```

将指定资源设置为指定类型的壁纸。使用Promise异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.SET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | string &#124; [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | 是 | JPEG或PNG文件的Uri路径，或者PNG格式文件的位图。 |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例**

参见 [setWallpaper](#setwallpaper)
