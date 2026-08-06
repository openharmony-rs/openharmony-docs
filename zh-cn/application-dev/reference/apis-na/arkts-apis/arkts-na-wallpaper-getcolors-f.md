# getColors

## getColors

```TypeScript
function getColors(wallpaperType: WallpaperType, callback: AsyncCallback<Array<RgbaColor>>): void
```

获取指定类型壁纸的主要颜色信息。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-wallpaper-function getColors(wallpaperType: WallpaperType, callback: AsyncCallback<Array<RgbaColor>>): void--><!--Device-wallpaper-function getColors(wallpaperType: WallpaperType, callback: AsyncCallback<Array<RgbaColor>>): void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;RgbaColor&gt;&gt; | 是 | 回调函数，返回壁纸的主要颜色信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getColors(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: Array<wallpaper.RgbaColor>) => {
    if (error) {
        console.error(`failed to getColors because: ${JSON.stringify(error)}`);
        return;
    }
    console.info(`success to getColors: ${JSON.stringify(data)}`);
});
```


## getColors

```TypeScript
function getColors(wallpaperType: WallpaperType): Promise<Array<RgbaColor>>
```

获取指定类型壁纸的主要颜色信息。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-wallpaper-function getColors(wallpaperType: WallpaperType): Promise<Array<RgbaColor>>--><!--Device-wallpaper-function getColors(wallpaperType: WallpaperType): Promise<Array<RgbaColor>>-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;RgbaColor&gt;&gt; | 返回壁纸的主要颜色信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getColors(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: Array<wallpaper.RgbaColor>) => {
    console.info(`success to getColors: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`failed to getColors because: ${JSON.stringify(error)}`);
});
```

