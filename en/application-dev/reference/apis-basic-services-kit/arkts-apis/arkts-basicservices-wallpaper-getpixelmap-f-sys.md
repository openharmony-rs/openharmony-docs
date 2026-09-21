# getPixelMap (System API)

## Modules to Import

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## getPixelMap

```TypeScript
function getPixelMap(wallpaperType: WallpaperType, callback: AsyncCallback<image.PixelMap>): void
```

Obtains the default pixel map of a wallpaper of the specified type. Returns the default pixel map.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.GET_WALLPAPER

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | Yes | indicates the wallpaper type. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | the callback of getPixelMap. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

wallpaper.getPixelMap(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: image.PixelMap) => {
  if (error) {
    console.error(`failed to getPixelMap. Code: ${error.code}, Message: ${error.message}`);
    return;
  }
  console.info(`success to getPixelMap : ${JSON.stringify(data.getImageInfoSync())}`);
});
```


<a id="getpixelmap-1"></a>

## getPixelMap

```TypeScript
function getPixelMap(wallpaperType: WallpaperType): Promise<image.PixelMap>
```

Obtains the default pixel map of a wallpaper of the specified type. Returns the default pixel map.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.GET_WALLPAPER

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | Yes | indicates the wallpaper type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | the promise returned by the function. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

wallpaper.getPixelMap(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: image.PixelMap) => {
  console.info(`success to getPixelMap : ${JSON.stringify(data.getImageInfoSync())}`);
}).catch((error: BusinessError) => {
  console.error(`failed to getPixelMap. Code: ${error.code}, Message: ${error.message}`);
});
```
