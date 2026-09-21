# reset

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## reset

```TypeScript
function reset(wallpaperType: WallpaperType, callback: AsyncCallback<void>): void
```

移除指定类型的壁纸，恢复为默认显示的壁纸。使用callback异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.SET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当移除壁纸成功，err为undefined，否则为错误对象。 |

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


<a id="reset-1"></a>

## reset

```TypeScript
function reset(wallpaperType: WallpaperType): Promise<void>
```

移除指定类型的壁纸，恢复为默认显示的壁纸。使用Promise异步回调。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.SET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.reset(wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
    console.info(`success to reset.`);
}).catch((error: BusinessError) => {
    console.error(`Failed to reset. Code: ${error.code}, message: ${error.message}`);
});
```
