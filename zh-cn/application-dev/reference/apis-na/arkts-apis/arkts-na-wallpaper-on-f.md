# on

## on('colorChange')

```TypeScript
function on(type: 'colorChange', callback: (colors: Array<RgbaColor>, wallpaperType: WallpaperType) => void): void
```

订阅壁纸颜色变化结果上报事件。不支持多线程并发调用。

**起始版本：** 7

**废弃版本：** 9

<!--Device-wallpaper-function on(type: 'colorChange', callback: (colors: Array<RgbaColor>, wallpaperType: WallpaperType) => void): void--><!--Device-wallpaper-function on(type: 'colorChange', callback: (colors: Array<RgbaColor>, wallpaperType: WallpaperType) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'colorChange' | 是 |  |
| callback | (colors: Array<RgbaColor>, wallpaperType: WallpaperType) => void | 是 |  |

**示例：**

```TypeScript
try {
    let listener = (colors: Array<wallpaper.RgbaColor>, wallpaperType: wallpaper.WallpaperType): void => {
        console.info(`wallpaper color changed.`);
    };
    wallpaper.on('colorChange', listener);
} catch (error) {
    console.error(`failed to on because: ${JSON.stringify(error)}`);
}

```

