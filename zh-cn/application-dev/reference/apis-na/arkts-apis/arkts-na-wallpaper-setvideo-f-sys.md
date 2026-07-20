# setVideo（系统接口）

<a id="setvideo"></a>
## setVideo

```TypeScript
function setVideo(source: string, wallpaperType: WallpaperType, callback: AsyncCallback<void>): void
```

将视频资源设置为桌面或锁屏的动态壁纸。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.SET_WALLPAPER

<!--Device-wallpaper-function setVideo(source: string, wallpaperType: WallpaperType, callback: AsyncCallback<void>): void--><!--Device-wallpaper-function setVideo(source: string, wallpaperType: WallpaperType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | string | 是 | mp4文件的Uri路径。 |
| wallpaperType | [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，设置壁纸成功，error为undefined，否则返回error信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let wallpaperPath = "/data/storage/el2/base/haps/entry/files/test.mp4";
try {
    wallpaper.setVideo(wallpaperPath, wallpaper.WallpaperType.WALLPAPER_SYSTEM, (error: BusinessError) => {
        if (error) {
            console.error(`failed to setVideo. Code: ${error.code}, Message: ${error.message}`);
            return;
        }
        console.info(`success to setVideo.`);
    });
} catch (error) {
    console.error(`failed to setVideo. Code: ${error.code}, Message: ${error.message}`);
}


```


<a id="setvideo-1"></a>
## setVideo

```TypeScript
function setVideo(source: string, wallpaperType: WallpaperType): Promise<void>
```

将视频资源设置为桌面或锁屏的动态壁纸。使用promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.SET_WALLPAPER

<!--Device-wallpaper-function setVideo(source: string, wallpaperType: WallpaperType): Promise<void>--><!--Device-wallpaper-function setVideo(source: string, wallpaperType: WallpaperType): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | string | 是 | mp4文件的Uri路径。 |
| wallpaperType | [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let wallpaperPath = "/data/storage/el2/base/haps/entry/files/test.mp4";
try {
    wallpaper.setVideo(wallpaperPath, wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
        console.info(`success to setVideo.`);
    }).catch((error: BusinessError) => {
        console.error(`failed to setVideo. Code: ${error.code}, Message: ${error.message}`);
    });
} catch (error) {
    console.error(`failed to setVideo. Code: ${error.code}, Message: ${error.message}`);
}

```

