# offWallpaperChange（系统接口）

## offWallpaperChange

```TypeScript
function offWallpaperChange(callback?: WallpaperChangeObserver): void
```

取消订阅壁纸变化通知事件。不支持多线程并发调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-wallpaper-function offWallpaperChange(callback?: WallpaperChangeObserver): void--><!--Device-wallpaper-function offWallpaperChange(callback?: WallpaperChangeObserver): void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

