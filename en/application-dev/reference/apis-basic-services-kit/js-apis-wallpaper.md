# @ohos.wallpaper (Wallpaper)

<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @gcw_jQMboB9m-->
<!--Designer: @gcw_jQMboB9m-->
<!--Tester: @murphy84-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=46fd65bb731b0371fd6a258a08447359214d2b38 translatedAt=2026-11-10T04:20:47.789Z pushedAt=2026-11-10T07:09:54.459Z nl=1 -->

The **wallpaper** module provides APIs for switching between wallpapers. Since API version 9, the APIs of this module function as system APIs, and only system applications are allowed to switch between wallpapers. Applications that use the wallpaper, for example, the home screen, need to subscribe to wallpaper changes and update the wallpaper accordingly.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import


```ts
import { wallpaper } from '@kit.BasicServicesKit';
```

## WallpaperType

Enumerates the wallpaper types.

**System capability**: SystemCapability.MiscServices.Wallpaper

| Name| Value|Description|
| -------- | -------- |-------- |
| WALLPAPER_SYSTEM | 0 |Home screen wallpaper.|
| WALLPAPER_LOCKSCREEN | 1 |Lock screen wallpaper.|


## RgbaColor<sup>(deprecated)</sup>

Defines the RGBA color space for the wallpaper.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| red | number | No| No| Red color. The value ranges from 0 to 255.|
| green | number | No| No| Green color. The value ranges from 0 to 255.|
| blue | number | No| No| Blue color. The value ranges from 0 to 255.|
| alpha | number | No| No| Alpha value. The value ranges from 0 to 255.|


## wallpaper.on('colorChange')<sup>(deprecated)</sup>

on(type: 'colorChange', callback: (colors: Array&lt;RgbaColor&gt;, wallpaperType: WallpaperType) =&gt; void): void

Subscribes to the wallpaper color change event. Multi-thread concurrent calls are not supported.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the event to subscribe to. The value **'colorChange'** indicates subscribing to the wallpaper color change event.|
| callback | function | Yes| Callback triggered when the wallpaper color changes. The wallpaper type and main colors are returned.<br>- colors<br>  Main color of the wallpaper. For details, see [RgbaColor](#rgbacolordeprecated).<br>- wallpaperType<br>  Wallpaper type.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let listener = (colors: Array<wallpaper.RgbaColor>, wallpaperType: wallpaper.WallpaperType): void => {
        console.info(`wallpaper color changed.`);
    };
    wallpaper.on('colorChange', listener);
} catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to on. Code: ${err.code}, message: ${err.message}`);
}
```

## wallpaper.off('colorChange')<sup>(deprecated)</sup>

off(type: 'colorChange', callback?: (colors: Array&lt;RgbaColor&gt;, wallpaperType: WallpaperType) =&gt; void): void

Unsubscribes from the wallpaper color change event. Multi-thread concurrent calls are not supported.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the event to unsubscribe from. The value **'colorChange'** indicates unsubscribing from the wallpaper color change event.|
| callback | function | No|   Callback used for unsubscription. If this parameter is not set, this API unsubscribes from all callbacks of the specified event type.<br>- colors<br>  Main color of the wallpaper. For details, see [RgbaColor](#rgbacolordeprecated).<br>- wallpaperType<br>  Wallpaper type.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let listener = (colors: Array<wallpaper.RgbaColor>, wallpaperType: wallpaper.WallpaperType): void => {
    console.info(`wallpaper color changed.`);
};
try {
    wallpaper.on('colorChange', listener);
} catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to on. Code: ${error.code}, message: ${error.message}`);
}

try {
    // Unsubscribe from the listener.
    wallpaper.off('colorChange', listener);
} catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to off. Code: ${err.code}, message: ${err.message}`);
}

try {
    // Unsubscribe from all subscriptions of the colorChange type.
    wallpaper.off('colorChange');
} catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to off. Code: ${error.code}, message: ${error.message}`);
}
```

## wallpaper.getColors<sup>(deprecated)</sup>

getColors(wallpaperType: WallpaperType, callback: AsyncCallback&lt;Array&lt;RgbaColor&gt;&gt;): void

Obtains the dominant color information of the wallpaper of the specified type. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |
| callback | AsyncCallback&lt;Array&lt;[RgbaColor](#rgbacolordeprecated)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the dominant color information of the wallpaper obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getColors(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: Array<wallpaper.RgbaColor>) => {
    if (error) {
        console.error(`Failed to getColors. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to getColors: ${JSON.stringify(data)}`);
});
```

## wallpaper.getColors<sup>(deprecated)</sup>

getColors(wallpaperType: WallpaperType): Promise&lt;Array&lt;RgbaColor&gt;&gt;

Obtains the dominant color information of the wallpaper of the specified type. This API uses a promise to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[RgbaColor](#rgbacolordeprecated)&gt;&gt; | Promise used to return the dominant color information of the wallpaper. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getColors(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: Array<wallpaper.RgbaColor>) => {
    console.info(`success to getColors: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to getColors. Code: ${error.code}, message: ${error.message}`);
});
```

## wallpaper.getId<sup>(deprecated)</sup>

getId(wallpaperType: WallpaperType, callback: AsyncCallback&lt;number&gt;): void

Obtains the ID of the wallpaper of the specified type. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback used to return the result. If the wallpaper ID is obtained successfully, **err** is **undefined** and **data** is the wallpaper ID obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getId(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: number) => {
    if (error) {
        console.error(`Failed to getId. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to getId: ${JSON.stringify(data)}`);
});
```

## wallpaper.getId<sup>(deprecated)</sup>

getId(wallpaperType: WallpaperType): Promise&lt;number&gt;

Obtains the ID of the wallpaper of the specified type. This API uses a promise to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;number&gt; | Promise used to return the wallpaper ID. If wallpaper of this type is configured, a number greater than or equal to 0 is returned; otherwise, -1 is returned. The value ranges from -1 to (2^31-1). |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getId(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: number) => {
    console.info(`success to getId: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to getId. Code: ${error.code}, message: ${error.message}`);
});
```

## wallpaper.getMinHeight<sup>(deprecated)</sup>

getMinHeight(callback: AsyncCallback&lt;number&gt;): void

Obtains the minimum height of the wallpaper. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback function. When the minimum height of the wallpaper (in pixels) is obtained successfully, err is undefined and data is the obtained minimum height; otherwise, it is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getMinHeight((error: BusinessError, data: number) => {
    if (error) {
        console.error(`Failed to getMinHeight. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to getMinHeight: ${JSON.stringify(data)}`);
});
```

## wallpaper.getMinHeight<sup>(deprecated)</sup>

getMinHeight(): Promise&lt;number&gt;

Obtains the minimum height of the wallpaper. This API uses a promise to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;number&gt; | Promise used to return the minimum wallpaper height, in pixels. If the return value is 0, no wallpaper is set. In this case, the default height should be used instead. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getMinHeight().then((data: number) => {
    console.info(`success to getMinHeight: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
    console.error(`Failed to getMinHeight. Code: ${error.code}, message: ${error.message}`);
});
```

## wallpaper.getMinWidth<sup>(deprecated)</sup>

getMinWidth(callback: AsyncCallback&lt;number&gt;): void

Obtains the minimum width of the wallpaper. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback function. When the minimum width of the wallpaper (in pixels) is obtained successfully, err is undefined and data is the obtained minimum width of the wallpaper; otherwise, it is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getMinWidth((error: BusinessError, data: number) => {
    if (error) {
        console.error(`Failed to getMinWidth. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to getMinWidth: ${JSON.stringify(data)}`);
});
```

## wallpaper.getMinWidth<sup>(deprecated)</sup>

getMinWidth(): Promise&lt;number&gt;

Obtains the minimum width of the wallpaper. This API uses a promise to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;number&gt; | Promise used to return the minimum width of the wallpaper (in pixels). If the value returned is 0, no wallpaper is set, and the caller should use the default display width instead. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getMinWidth().then((data: number) => {
    console.info(`success to getMinWidth: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to getMinWidth. Code: ${error.code}, message: ${error.message}`);
});
```

## wallpaper.getFile<sup>(deprecated)</sup>

getFile(wallpaperType: WallpaperType, callback: AsyncCallback&lt;number&gt;): void

Obtains the wallpaper file of the specified type. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 8 and deprecated since API version 9.

**Required permissions**: ohos.permission.GET_WALLPAPER

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback function. When the wallpaper file is obtained successfully, err is undefined and data is the ID of the obtained wallpaper file descriptor; otherwise, it is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getFile(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: number) => {
    if (error) {
        console.error(`Failed to getFile. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to getFile: ${JSON.stringify(data)}`);
});
```

## wallpaper.getFile<sup>(deprecated)</sup>

getFile(wallpaperType: WallpaperType): Promise&lt;number&gt;

Obtains the wallpaper file of the specified type. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9.

**Required permissions**: ohos.permission.GET_WALLPAPER

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;number&gt; | Promise that returns the file descriptor ID of the wallpaper. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getFile(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: number) => {
    console.info(`success to getFile: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to getFile. Code: ${error.code}, message: ${error.message}`);
});
```

## wallpaper.isChangePermitted<sup>(deprecated)</sup>

isChangePermitted(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the application is allowed to change the wallpaper of the current user. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes | Callback function. Returns true to indicate that the application is allowed to change the wallpaper of the current user; returns false to indicate that it is not allowed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isChangePermitted((error: BusinessError, data: boolean) => {
    if (error) {
        console.error(`Failed to isChangePermitted. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to isChangePermitted: ${JSON.stringify(data)}`);
});
```

## wallpaper.isChangePermitted<sup>(deprecated)</sup>

isChangePermitted(): Promise&lt;boolean&gt;

Checks whether the application is allowed to change the wallpaper of the current user. This API uses a promise to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise object. Returns true to indicate that the application is allowed to change the wallpaper of the current user; returns false to indicate that it is not allowed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isChangePermitted().then((data: boolean) => {
    console.info(`success to isChangePermitted: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
    console.error(`Failed to isChangePermitted. Code: ${error.code}, message: ${error.message}`);
});
```

## wallpaper.isOperationAllowed<sup>(deprecated)</sup>

isOperationAllowed(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the user is allowed to set the wallpaper. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes | Callback function. Returns true to indicate that the user is allowed to set the wallpaper; returns false to indicate that it is not allowed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isOperationAllowed((error: BusinessError, data: boolean) => {
    if (error) {
        console.error(`Failed to isOperationAllowed. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to isOperationAllowed: ${JSON.stringify(data)}`);
});
```

## wallpaper.isOperationAllowed<sup>(deprecated)</sup>

isOperationAllowed(): Promise&lt;boolean&gt;

Checks whether the user is allowed to set the wallpaper. This API uses a promise to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**System capability**: SystemCapability.MiscServices.Wallpaper

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the user is allowed to set the wallpaper, and **false** indicates the opposite. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isOperationAllowed().then((data: boolean) => {
    console.info(`success to isOperationAllowed: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to isOperationAllowed. Code: ${error.code}, message: ${error.message}`);
});
```

## wallpaper.reset<sup>(deprecated)</sup>

reset(wallpaperType: WallpaperType, callback: AsyncCallback&lt;void&gt;): void

Resets the wallpaper of the specified type to the default wallpaper. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**Required permissions**: ohos.permission.SET_WALLPAPER

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the wallpaper is removed successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.reset(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to reset. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to reset.`);
});
```

## wallpaper.reset<sup>(deprecated)</sup>

reset(wallpaperType: WallpaperType): Promise&lt;void&gt;

Resets the wallpaper of the specified type to the default wallpaper. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9.

**Required permissions**: ohos.permission.SET_WALLPAPER

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.reset(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
    console.info(`success to reset.`);
}).catch((error: BusinessError) => {
    console.error(`Failed to reset. Code: ${error.code}, message: ${error.message}`);
});
```

## wallpaper.setWallpaper<sup>(deprecated)</sup>

setWallpaper(source: string | image.PixelMap, wallpaperType: WallpaperType, callback: AsyncCallback&lt;void&gt;): void

Sets a specified source as the wallpaper of a specified type. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**Required permissions**: ohos.permission.SET_WALLPAPER

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| source | string \| [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | Yes| URI of a JPEG or PNG file, or pixel map of a PNG file.|
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result.<br> If the wallpaper is set successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

// The source type is string.
let wallpaperPath = '/data/storage/el2/base/haps/entry/files/js.jpeg';
wallpaper.setWallpaper(wallpaperPath, wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to setWallpaper. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to setWallpaper.`);
});

// The source type is image.PixelMap.
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

## wallpaper.setWallpaper<sup>(deprecated)</sup>

setWallpaper(source: string | image.PixelMap, wallpaperType: WallpaperType): Promise&lt;void&gt;

Sets a specified source as the wallpaper of a specified type. This API uses a promise to return the result.

> **NOTE**
> 
> This API is supported since API version 7 and deprecated since API version 9.

**Required permissions**: ohos.permission.SET_WALLPAPER

**System capability**: SystemCapability.MiscServices.Wallpaper

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| source | string \| [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | Yes| URI of a JPEG or PNG file, or pixel map of a PNG file.|
| wallpaperType | [WallpaperType](#wallpapertype) | Yes | Wallpaper type. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

// The source type is string.
let wallpaperPath = '/data/storage/el2/base/haps/entry/files/js.jpeg';
wallpaper.setWallpaper(wallpaperPath, wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
    console.info(`success to setWallpaper.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to setWallpaper. Code: ${error.code}, message: ${error.message}`);
});
  
// The source type is image.PixelMap.
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