# getColorsSync (System API)

## Modules to Import

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## getColorsSync

```TypeScript
function getColorsSync(wallpaperType: WallpaperType): Array<RgbaColor>
```

Obtains the wallpaper colors for the wallpaper of the specified type. Returns rgbaColor type of array callback function.

**Since:** 9

**Deprecated since:** 23

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | Yes | indicates the wallpaper type. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[RgbaColor](arkts-basicservices-wallpaper-rgbacolor-i.md)&gt; | the Array&lt;RgbaColor&gt; returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | permission verification failed, application which is not a system application uses system API. |

**Examples**

```TypeScript
try {
    let colors = wallpaper.getColorsSync(wallpaper.WallpaperType.WALLPAPER_SYSTEM);
    console.info(`success to getColorsSync: ${JSON.stringify(colors)}`);
} catch (error) {
    console.error(`failed to getColorsSync. Code: ${error.code}, Message: ${error.message}`);
}
```
