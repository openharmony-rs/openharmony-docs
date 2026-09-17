# getWallpaperByState（系统接口）

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## getWallpaperByState

```TypeScript
function getWallpaperByState(wallpaperType: WallpaperType, foldState: FoldState, rotateState: RotateState): Promise<image.PixelMap>
```

获取指定壁纸类型、折展态、横竖屏的壁纸图片的像素图，如果指定的壁纸不存在，会逐步降级匹配，unfolded-land -&gt; unfolded-port -&gt;normal-port。使用Promise异步回调。

**起始版本：** 14

**需要权限：** ohos.permission.GET_WALLPAPER

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-basicservices-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |
| foldState | [FoldState](arkts-basicservices-wallpaper-foldstate-e-sys.md) | 是 | 折展状态类型。 |
| rotateState | [RotateState](arkts-basicservices-wallpaper-rotatestate-e-sys.md) | 是 | 横竖屏状态类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise对象，返回壁纸图片的像素图对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.The type must be WallpaperType, parameter range must be WALLPAPER_LOCKSCREEN or WALLPAPER_SYSTEM. 3.The type must be FoldState, parameter range must be NORMAL or UNFOLD_ONCE_STATE or UNFOLD_TWICE_STATE. 4.The type must be RotateState, parameter range must be PORTRAIT or LANDSCAPE. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

wallpaper.getWallpaperByState(wallpaper.WallpaperType.WALLPAPER_SYSTEM,wallpaper.FoldState.NORMAL,wallpaper.RotateState.PORTRAIT).then((data:image.PixelMap) => {
  console.info(`success to getWallpaperByState: ${JSON.stringify(data.getImageInfoSync())}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to getWallpaperByState. Code: ${error.code}, Message: ${error.message}`);
});
```
