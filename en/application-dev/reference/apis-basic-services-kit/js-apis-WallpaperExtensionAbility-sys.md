# @ohos.WallpaperExtensionAbility (WallpaperExtensionAbility) (System APIs)

<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @gcw_jQMboB9m-->
<!--Designer: @gcw_jQMboB9m-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=531db22a21215c0121639101d61b4ccd5426a88b translatedAt=2026-06-08T07:57:10.662Z pushedAt=2026-06-09T10:12:44.329Z -->

The **WallpaperExtensionAbility** module provides lifecycle callbacks for wallpaper extension abilities and APIs for listening for wallpaper changes.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';
```

## WallpaperExtensionAbility.onCreate<sup>(deprecated)</sup>

onCreate(want: object): void

Initializes a wallpaper extension application. Multi-thread concurrent calls are not supported.

> **NOTE:**
> 
> This API is supported since API version 10 and deprecated since API version 23.

**System capability**: SystemCapability.MiscServices.Wallpaper

**System API**: This is a system API.

**Parameters**

| Name| Type         | Mandatory| Description                            |
| ------ | ----------- | ---- | ------------------------------- |
| want   | object | Yes   | Want information related to the **WallpaperExtensionAbility** instance, including the ability name and bundle name. |

**Example**

```ts
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

class WallpaperExt extends WallpaperExtensionAbility {
    onCreate(want: Want): void {
        console.info('onCreate, want:' + want.abilityName);
    }
}
```

## WallpaperExtensionAbility.onWallpaperChange<sup>(deprecated)</sup>

onWallpaperChange(wallpaperType: number): void

Defines an API called when the wallpaper changes. Multi-thread concurrent calls are not supported.

> **NOTE:**
> 
> This API is supported since API version 10 and deprecated since API version 23.

**System capability**: SystemCapability.MiscServices.Wallpaper

**System API**: This is a system API.

**Parameters**

| Name| Type       | Mandatory| Description                  |
| ------ | --------- | --- |----------------------|
| wallpaperType  | number | Yes | Wallpaper type.<br> **0**: home screen wallpaper.<br>**1**: lock screen wallpaper.|

**Example**

```ts
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';
import { wallpaper } from '@kit.BasicServicesKit';

class WallpaperExt extends WallpaperExtensionAbility {
    onWallpaperChange(wallpaperType: wallpaper.WallpaperType): void {
        console.info('onWallpaperChange, wallpaperType:' + wallpaperType);
    }
}
```

## WallpaperExtensionAbility.onDestroy<sup>(deprecated)</sup>

onDestroy(): void

Defines an API called when this wallpaper extension ability is destroyed to clear resources. Multi-thread concurrent calls are not supported.

> **NOTE:**
> 
> This API is supported since API version 10 and deprecated since API version 23.

**System capability**: SystemCapability.MiscServices.Wallpaper

**System API**: This is a system API.

**Example**

```ts
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';

class WallpaperExt extends WallpaperExtensionAbility {
    onDestroy(): void {
        console.info('onDestroy');
    }
}
```