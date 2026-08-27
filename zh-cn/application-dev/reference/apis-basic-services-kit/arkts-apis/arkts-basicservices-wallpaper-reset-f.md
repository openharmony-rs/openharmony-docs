# reset

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## reset

```TypeScript
function reset(wallpaperType: WallpaperType, callback: AsyncCallback<void>): void
```

移除指定类型的壁纸，恢复为默认显示的壁纸。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.SET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 |  |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，移除壁纸成功，error为undefined，否则返回error信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.reset(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to reset. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to reset.`);
});
```


## reset

```TypeScript
function reset(wallpaperType: WallpaperType): Promise<void>
```

移除指定类型的壁纸，恢复为默认显示的壁纸。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.SET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.reset(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
    console.info(`success to reset.`);
}).catch((error: BusinessError) => {
    console.error(`Failed to reset. Code: ${error.code}, message: ${error.message}`);
});
```
