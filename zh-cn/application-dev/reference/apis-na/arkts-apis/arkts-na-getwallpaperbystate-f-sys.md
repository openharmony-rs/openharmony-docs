# getWallpaperByState（系统接口）

## getWallpaperByState

```TypeScript
function getWallpaperByState(wallpaperType: WallpaperType, foldState: FoldState, rotateState: RotateState): Promise<image.PixelMap>
```

获取指定壁纸类型、折展态、横竖屏的壁纸图片的像素图，如果指定的壁纸不存在，会逐步降级匹配，unfolded-land -> unfolded-port ->normal-port。使用promise异步回调。

**起始版本：** 14

**需要权限：** ohos.permission.GET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | WallpaperType | 是 | 壁纸类型。 |
| foldState | FoldState | 是 | 折展状态类型。 |
| rotateState | RotateState | 是 | 横竖屏状态类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | 调用成功则返回壁纸图片的像素图对象，调用失败则返回error信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified.2.The type must be WallpaperType, parameter range must be WALLPAPER_LOCKSCREEN or WALLPAPER_SYSTEM.3.The type must be FoldState, parameter range must be NORMAL or UNFOLD_ONCE_STATE or UNFOLD_TWICE_STATE.4.The type must be RotateState, parameter range must be PORTRAIT or LANDSCAPE. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application usessystem API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { wallpaper } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

wallpaper.getWallpaperByState(wallpaper.WallpaperType.WALLPAPER_SYSTEM,wallpaper.FoldState.NORMAL,wallpaper.RotateState.PORTRAIT).then((data:image.PixelMap) => {
  console.info(`success to getWallpaperByState: ${JSON.stringify(data.getImageInfoSync())}`);
}).catch((error: BusinessError) => {
  console.error(`failed to getWallpaperByState. Code: ${error.code}, Message: ${error.message}`);
});

```

