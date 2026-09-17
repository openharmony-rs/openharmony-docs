# on

## 导入模块

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## on('colorChange')

```TypeScript
function on(type: 'colorChange', callback: (colors: Array<RgbaColor>, wallpaperType: WallpaperType) => void): void
```

订阅壁纸颜色变化结果上报事件。不支持多线程并发调用。<br>  
> **说明：** 
> 
> 从 API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.MiscServices.Wallpaper

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'colorChange' | 是 | 取值为'colorChange'，表示壁纸颜色变化结果上报事件。 |
| callback | (colors: Array&lt;[RgbaColor](arkts-basicservices-wallpaper-rgbacolor-i.md)&gt;, wallpaperType: WallpaperType) =&gt; void | 是 | 壁纸颜色变化触发该回调方法，返回壁纸类型和壁纸的主要颜色信息。<br>- colors<br> 壁纸的主要颜色信息，其类型见[RgbaColor](arkts-basicservices-wallpaper-rgbacolor-i.md)。<br>- wallpaperType<br> 壁纸类型。 |
