# getFile

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## getFile

```TypeScript
function getFile(wallpaperType: WallpaperType, callback: AsyncCallback<number>): void
```

获取指定类型的壁纸文件。

**起始版本：** 8

**废弃版本：** 9

**需要权限：** ohos.permission.GET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 |  |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getFile(wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError, data: number) => {
    if (error) {
        console.error(`Failed to getFile. Code: ${error.code}, message: ${error.message}`);
        return;
    }
    console.info(`success to getFile: ${JSON.stringify(data)}`);
});
```


## getFile

```TypeScript
function getFile(wallpaperType: WallpaperType): Promise<number>
```

获取指定类型的壁纸文件。

**起始版本：** 8

**废弃版本：** 9

**需要权限：** ohos.permission.GET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | 调用成功则返回壁纸文件描述符ID，调用失败则返回error信息。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.getFile(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then((data: number) => {
    console.info(`success to getFile: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to getFile. Code: ${error.code}, message: ${error.message}`);
});
```
