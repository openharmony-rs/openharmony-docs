# reset

## Modules to Import

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

<a id="reset1"></a>

## reset

```TypeScript
function reset(wallpaperType: WallpaperType, callback: AsyncCallback<void>): void
```

Removes a wallpaper of the specified type and restores the default one.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.SET_WALLPAPER

<!--Device-wallpaper-function reset(wallpaperType: WallpaperType, callback: AsyncCallback<void>): void--><!--Device-wallpaper-function reset(wallpaperType: WallpaperType, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.Wallpaper

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | Yes | indicates the wallpaper type. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback of reset. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.reset(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError) => {
    if (error) {
        console.error(`failed to reset because: ${JSON.stringify(error)}`);
        return;
    }
    console.info(`success to reset.`);
});
```


<a id="reset2"></a>

## reset

```TypeScript
function reset(wallpaperType: WallpaperType): Promise<void>
```

Removes a wallpaper of the specified type and restores the default one.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.SET_WALLPAPER

<!--Device-wallpaper-function reset(wallpaperType: WallpaperType): Promise<void>--><!--Device-wallpaper-function reset(wallpaperType: WallpaperType): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.Wallpaper

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | Yes | indicates the wallpaper type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.reset(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
    console.info(`success to reset.`);
}).catch((error: BusinessError) => {
    console.error(`failed to reset because: ${JSON.stringify(error)}`);
});
```
