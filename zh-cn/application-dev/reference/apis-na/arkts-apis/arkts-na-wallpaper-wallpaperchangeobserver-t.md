# WallpaperChangeObserver

```TypeScript
type WallpaperChangeObserver = (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) => void
```

定义壁纸变化的监听回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-wallpaper-type WallpaperChangeObserver = (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) => void--><!--Device-wallpaper-type WallpaperChangeObserver = (wallpaperType: WallpaperType, resourceType: WallpaperResourceType, uri?: string) => void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 壁纸类型。  |
| resourceType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 壁纸资源类型。  |
| uri | string | 否 | 壁纸资源地址。  |

