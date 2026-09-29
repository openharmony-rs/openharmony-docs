# WallpaperInfo (System API)

```TypeScript
interface WallpaperInfo
```

WallpaperInfo definition including folding status, rotation status, and resource path.

@typedef WallpaperInfo

**Since:** 14

<!--Device-wallpaper-interface WallpaperInfo--><!--Device-wallpaper-interface WallpaperInfo-End-->

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## foldState

```TypeScript
foldState: FoldState
```

Indicates the folding status for wallpaper.

**Type:** [FoldState](arkts-basicservices-wallpaper-foldstate-e-sys.md)

**Since:** 14

<!--Device-WallpaperInfo-foldState: FoldState--><!--Device-WallpaperInfo-foldState: FoldState-End-->

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

## rotateState

```TypeScript
rotateState: RotateState
```

Indicates the rotation status for wallpaper.

**Type:** [RotateState](arkts-basicservices-wallpaper-rotatestate-e-sys.md)

**Since:** 14

<!--Device-WallpaperInfo-rotateState: RotateState--><!--Device-WallpaperInfo-rotateState: RotateState-End-->

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.

## source

```TypeScript
source: string
```

Indicates the resource path for wallpaper.

**Type:** string

**Since:** 14

<!--Device-WallpaperInfo-source: string--><!--Device-WallpaperInfo-source: string-End-->

**System capability:** SystemCapability.MiscServices.Wallpaper

**System API:** This is a system API.
