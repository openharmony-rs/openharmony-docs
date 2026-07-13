# setCustomWallpaper（系统接口）

## setCustomWallpaper

```TypeScript
function setCustomWallpaper(source: string, wallpaperType: WallpaperType, callback: AsyncCallback<void>): void
```

将指定的zip资源包设置为桌面或锁屏的壁纸资源，仅当com.ohos.sceneboard存在时，支持使用该接口。且具有ohos.permission.GET_WALLPAPER权限的应用可以访问/data/wallpaper/目
录获取设置的资源。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.SET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | string | 是 | 指定的zip资源包。 |
| wallpaperType | WallpaperType | 是 | 壁纸类型。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，设置壁纸成功，error为undefined，否则返回error信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application usessystem API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let wallpaperPath = "/data/storage/el2/base/haps/entry/files/test.zip";
try {
    wallpaper.setCustomWallpaper(wallpaperPath, wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError) => {
        if (error) {
            console.error(`failed to setCustomWallpaper. Code: ${error.code}, Message: ${error.message}`);
            return;
        }
        console.info(`success to setCustomWallpaper.`);
    });
} catch (error) {
    console.error(`failed to setCustomWallpaper. Code: ${error.code}, Message: ${error.message}`);
}


```


## setCustomWallpaper

```TypeScript
function setCustomWallpaper(source: string, wallpaperType: WallpaperType): Promise<void>
```

将指定的zip资源包设置为桌面或锁屏的壁纸资源，仅当com.ohos.sceneboard存在时，支持使用该接口。且具有ohos.permission.GET_WALLPAPER权限的应用可以访问/data/wallpaper/目
录获取设置的资源。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.SET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | string | 是 | 指定的zip资源包。 |
| wallpaperType | WallpaperType | 是 | 壁纸类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application usessystem API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let wallpaperPath = "/data/storage/el2/base/haps/entry/files/test.zip";
try {
    wallpaper.setCustomWallpaper(wallpaperPath, wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
        console.info(`success to setCustomWallpaper.`);
    }).catch((error: BusinessError) => {
        console.error(`failed to setCustomWallpaper. Code: ${error.code}, Message: ${error.message}`);
    });
} catch (error) {
    console.error(`failed to setCustomWallpaper. Code: ${error.code}, Message: ${error.message}`);
}

```

