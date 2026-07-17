# setAllWallpapers（系统接口）

## setAllWallpapers

```TypeScript
function setAllWallpapers(wallpaperInfos: Array<WallpaperInfo>, wallpaperType: WallpaperType): Promise<void>
```

设置设备所有形态的壁纸。使用promise异步回调。（包括折展状态、横竖屏状态、资源路径，其中NORMAL-PORT为必选）

**起始版本：** 14

**需要权限：** ohos.permission.SET_WALLPAPER

<!--Device-wallpaper-function setAllWallpapers(wallpaperInfos: Array<WallpaperInfo>, wallpaperType: WallpaperType): Promise<void>--><!--Device-wallpaper-function setAllWallpapers(wallpaperInfos: Array<WallpaperInfo>, wallpaperType: WallpaperType): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperInfos | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<WallpaperInfo> | 是 | 所有壁纸的信息结构。 |
| wallpaperType | [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 是 | 壁纸类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified.2.The first parameter type must be Array&lt;WallpaperInfo&gt;. The second type must be WallpaperType.3.The first parameter type must be Array&lt;WallpaperInfo&gt;, must include wallpaper with FoldState NORMAL and RotateState PORTRAIT. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { wallpaper } from '@kit.BasicServicesKit';

let wallpaperInfos: Array<wallpaper.WallpaperInfo>
wallpaperInfos = [
  {
    foldState: wallpaper.FoldState.NORMAL,
    rotateState: wallpaper.RotateState.PORTRAIT,
    source: '/data/storage/el2/base/haps/entry/files/normal.jpeg'
  },
  {
    foldState: wallpaper.FoldState.UNFOLD_ONCE_STATE,
    rotateState: wallpaper.RotateState.LANDSCAPE,
    source: '/data/storage/el2/base/haps/entry/files/unfold_once_state.jpeg'
  },
  {
    foldState: wallpaper.FoldState.UNFOLD_TWICE_STATE,
    rotateState: wallpaper.RotateState.PORTRAIT,
    source: '/data/storage/el2/base/haps/entry/files/unfold_twice_state.jpeg'
  }
];
wallpaper.setAllWallpapers(wallpaperInfos, wallpaper.WallpaperType.WALLPAPER_SYSTEM).then(() => {
  console.info(`success to setAllWallpapers.`);
}).catch((error: BusinessError) => {
  console.error(`failed to setAllWallpapers. Code: ${error.code}, Message: ${error.message}`);
});

```

