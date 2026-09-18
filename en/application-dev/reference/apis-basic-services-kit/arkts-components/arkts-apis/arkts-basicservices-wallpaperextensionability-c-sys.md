# WallpaperExtensionAbility (System API)

class of wallpaper extension ability.

**Since:** 10

**Deprecated since:** 23

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';
```

## onCreate

```TypeScript
onCreate(want: object): void
```

Called once to initialize the extension ability.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | object | Yes | Indicates connection information about the wallpaper extension ability. |

**Examples**

```TypeScript
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

class WallpaperExt extends WallpaperExtensionAbility {
    onCreate(want: Want): void {
        console.info('onCreate, want:' + want.abilityName);
    }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Called once to destroy the extension ability.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

**Examples**

```TypeScript
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';

class WallpaperExt extends WallpaperExtensionAbility {
    onDestroy(): void {
        console.info('onDestroy');
    }
}
```

## onWallpaperChange

```TypeScript
onWallpaperChange(wallpaperType: number): void
```

The onWallpaperChange callback is triggered when the user modifies the wallpaper settings.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wallpaperType | number | Yes | Indicates the wallpaper type. |

**Examples**

```TypeScript
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';
import { wallpaper } from '@kit.BasicServicesKit';

class WallpaperExt extends WallpaperExtensionAbility {
    onWallpaperChange(wallpaperType: wallpaper.WallpaperType): void {
        console.info('onWallpaperChange, wallpaperType:' + wallpaperType);
    }
}
```
