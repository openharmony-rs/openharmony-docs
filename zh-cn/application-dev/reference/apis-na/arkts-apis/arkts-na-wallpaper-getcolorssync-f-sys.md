# getColorsSync（系统接口）

<a id="getcolorssync"></a>
## getColorsSync

```TypeScript
function getColorsSync(wallpaperType: WallpaperType): Array<RgbaColor>
```

获取指定类型壁纸的主要颜色信息。

> **说明：**  
>  
> 从 API version 9开始支持，从API version 23开始废弃。

**起始版本：** 9

**废弃版本：** 23

<!--Device-wallpaper-function getColorsSync(wallpaperType: WallpaperType): Array<RgbaColor>--><!--Device-wallpaper-function getColorsSync(wallpaperType: WallpaperType): Array<RgbaColor>-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wallpaperType | [WallpaperType](arkts-na-wallpaper-wallpapertype-e.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;RgbaColor&gt; | 返回壁纸的主要颜色信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | permission verification failed, application which is not a system application uses system API. |

**示例：**

```TypeScript
try {
    let colors = wallpaper.getColorsSync(wallpaper.WallpaperType.WALLPAPER_SYSTEM);
    console.info(`success to getColorsSync: ${JSON.stringify(colors)}`);
} catch (error) {
    console.error(`failed to getColorsSync. Code: ${error.code}, Message: ${error.message}`);
}

```

