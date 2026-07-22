# getId

## getId

```TypeScript
function getId(wallpaperType: WallpaperType, callback: AsyncCallback<number>): void
```

获取指定类型壁纸的ID。

**起始版本：** 7

**废弃版本：** 9

<!--Device-wallpaper-function getId(wallpaperType: WallpaperType, callback: AsyncCallback<number>): void--><!--Device-wallpaper-function getId(wallpaperType: WallpaperType, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 是 |  |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 |  |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getId(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: Number) => {
    if (error) {
        console.error(`failed to getId because: ${JSON.stringify(error)}`);
        return;
    }
    console.info(`success to getId: ${JSON.stringify(data)}`);
});

```


## getId

```TypeScript
function getId(wallpaperType: WallpaperType): Promise<number>
```

获取指定类型壁纸的ID。

**起始版本：** 7

**废弃版本：** 9

<!--Device-wallpaper-function getId(wallpaperType: WallpaperType): Promise<number>--><!--Device-wallpaper-function getId(wallpaperType: WallpaperType): Promise<number>-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 壁纸的ID。如果配置了这种壁纸类型的壁纸就返回一个大于等于0的数，否则返回-1。取值范围是-1到（2^31-1）。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getId(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: Number) => {
    console.info(`success to getId: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`failed to getId because: ${JSON.stringify(error)}`);
});

```

