# on (System API)

## Modules to Import

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## on('wallpaperChange')

```TypeScript
function on(
    type: 'wallpaperChange',
    callback: (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) => void
  ): void
```

Registers a listener for wallpaper changes to receive notifications about the changes.

**Since:** 10

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'wallpaperChange' | Yes | the incoming wallpaperChange table open receiver when the user modifies the wallpaper settings. |
| callback | (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) =&gt; void | Yes | wallpaperType indicates the wallpaper type. resourceType indicates the resource type of the wallpaper. uri indicates the wallpaper resource address. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | permission verification failed, application which is not a system application uses system API. |

**Examples**

```TypeScript
try {
    let listener = (wallpaperType: wallpaper.WallpaperType, resourceType: wallpaper.WallpaperResourceType): void => {
        console.info(`wallpaper color changed.`);
    };
    wallpaper.on('wallpaperChange', listener);
} catch (error) {
    console.error(`failed to on. Code: ${error.code}, Message: ${error.message}`);
}
```
