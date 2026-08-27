# off

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## off('colorChange')

```TypeScript
function off(type: 'colorChange', callback?: (colors: Array<RgbaColor>, wallpaperType: WallpaperType) => void): void
```

取消订阅壁纸颜色变化结果上报事件。不支持多线程并发调用。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'colorChange' | 是 |  |
| callback | (colors: Array&lt;[RgbaColor](arkts-basicservices-wallpaper-rgbacolor-i.md)&gt;, wallpaperType: WallpaperType) =&gt; void | 否 |  |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let listener = (colors: Array<wallpaper.RgbaColor>, wallpaperType: wallpaper.WallpaperType): void => {
    console.info(`wallpaper color changed.`);
};
try {
    wallpaper.on('colorChange', listener);
} catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to on. Code: ${error.code}, message: ${error.message}`);
}

try {
    // 取消订阅listener
    wallpaper.off('colorChange', listener);
} catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to off. Code: ${err.code}, message: ${err.message}`);
}

try {
    // 取消所有'colorChange'类型的订阅
    wallpaper.off('colorChange');
} catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to off. Code: ${error.code}, message: ${error.message}`);
}
```
