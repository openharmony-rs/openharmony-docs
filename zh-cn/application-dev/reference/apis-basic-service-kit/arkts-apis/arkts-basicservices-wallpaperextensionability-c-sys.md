# WallpaperExtensionAbility（系统接口）

class of wallpaper extension ability.

**起始版本：** 10

**废弃版本：** 23

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

## onCreate

```TypeScript
onCreate(want: object): void
```

初始化壁纸扩展应用。在拉起Extension壁纸扩展应用时触发回调，执行初始化应用操作。不支持多线程并发调用。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | object | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例：**

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

清理壁纸扩展应用资源。在销毁壁纸扩展应用时触发回调，执行资源清理。不支持多线程并发调用。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**示例：**

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

监听壁纸变化。在壁纸变化时触发回调。不支持多线程并发调用。

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | number | 是 | 壁纸类型。主屏幕壁纸为0，锁屏壁纸为1。 |

**示例：**

```TypeScript
import { WallpaperExtensionAbility } from '@kit.BasicServicesKit';
import { wallpaper } from '@kit.BasicServicesKit';

class WallpaperExt extends WallpaperExtensionAbility {
    onWallpaperChange(wallpaperType: wallpaper.WallpaperType): void {
        console.info('onWallpaperChange, wallpaperType:' + wallpaperType);
    }
}

```

