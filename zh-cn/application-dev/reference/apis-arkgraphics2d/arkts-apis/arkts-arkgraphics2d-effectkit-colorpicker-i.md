# ColorPicker

取色类，用于从一张图像数据中获取它的主要颜色，适用于UI主题色提取、图片配色分析、智能配色推荐等场景， 可帮助开发者基于图片内容动态生成和谐的配色方案。在调用ColorPicker的方法前，需要先通过 [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md)创建一个ColorPicker实例。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## getAverageColor

```TypeScript
getAverageColor(): Color
```

读取图像平均的颜色值，结果写入[Color](arkts-arkgraphics2d-effectkit-color-i.md)里，使用同步方式返回。 常用于获取图片整体色调，如图片色调统计、背景色自适应等场景。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Color | Color实例，即图像平均的颜色值，失败时返回null。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
      // 获取图像平均颜色
      let averageColor = colorPicker.getAverageColor();
      console.info('get average color =' + averageColor);
    }
  });
});
```

## getHighestSaturationColor

```TypeScript
getHighestSaturationColor(): Color
```

读取图像饱和度最高的颜色值，结果写入[Color](arkts-arkgraphics2d-effectkit-color-i.md)里，使用同步方式返回。 常用于提取图像中最鲜艳的颜色，如UI主题强调色提取、图标高亮色选择等场景。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Color | Color实例，即图像饱和度最高的颜色值，失败时返回null。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
      // 获取图像饱和度最高的颜色
      let saturationColor = colorPicker.getHighestSaturationColor();
      console.info('get highest saturation color =' + saturationColor);
    }
  });
});
```

## getLargestProportionColor

```TypeScript
getLargestProportionColor(): Color
```

读取图像中占比最多的颜色值，结果写入[Color](arkts-arkgraphics2d-effectkit-color-i.md)里，使用同步方式返回。 该接口使用中位切分算法划分颜色空间，获取占比最多的颜色空间的平均颜色。 常用于识别图片中面积最大的颜色区域，如图标背景色提取、图片内容分析等场景。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Color | Color实例，即图像占比最多的颜色值，失败时返回null。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
      // 获取图像占比最多的颜色
      let largestColor = colorPicker.getLargestProportionColor();
      console.info('get largest proportion color =' + largestColor);
    }
  });
});
```

## getMainColor

```TypeScript
getMainColor(): Promise<Color>
```

读取图像主色的颜色值，结果写入[Color](arkts-arkgraphics2d-effectkit-color-i.md)里，使用Promise异步回调。 该接口通过图像缩放算法，根据周围像素的加权计算，将原图缩小到1个像素以得到主色。 常用于应用主题色自动提取、UI界面根据图片自动配色、音乐播放器根据专辑封面动态调整背景色等场景。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Color&gt; | Promise对象。返回图像主色对应的颜色值，失败时返回错误信息。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
      // 获取图像主色
      colorPicker.getMainColor().then(mainColor => {
        console.info('Succeeded in getting main color.');
        console.info(`color[ARGB]=${mainColor.alpha},${mainColor.red},${mainColor.green},${mainColor.blue}`);
      });
    }
  });
});
```

## getMainColorSync

```TypeScript
getMainColorSync(): Color
```

读取图像主色的颜色值，结果写入[Color](arkts-arkgraphics2d-effectkit-color-i.md)里，使用同步方式返回。 该接口通过图像缩放算法，根据周围像素的加权计算，将原图缩小到1个像素以得到主色。 常用于应用主题色自动提取、UI界面根据图片自动配色、音乐播放器根据专辑封面动态调整背景色等场景。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Color | Color实例，即图像主色对应的颜色值，失败时返回null。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
      // 同步获取图像主色
      let mainColor = colorPicker.getMainColorSync();
      console.info('get main color =' + mainColor);
    }
  });
});
```

## getTopProportionColors

```TypeScript
getTopProportionColors(colorCount: number): Array<Color | null>
```

读取图像占比靠前的颜色值，个数由`colorCount`指定，结果写入[Color](arkts-arkgraphics2d-effectkit-color-i.md)的数组里，使用同步方式返回。 常用于提取图片中占比最高的多个颜色，如多色调配色方案生成、图片色彩分布分析等场景。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorCount | number | 是 | 需要获取的颜色个数，向下取整。在OpenHarmony 6.1之前，取值范围为[1, 10]， 取色个数大于10视为取前10个；从OpenHarmony 6.1开始，取值范围为[1, 20]，取色个数大于20视为取前20个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array &lt;Color \ | null&gt; | Color数组，即图像占比前`colorCount`的颜色值数组，按占比排序。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
      // 获取图像占比前2位的颜色
      let colors = colorPicker.getTopProportionColors(2);
      for (let index = 0; index < colors.length; index++) {
        if (colors[index]) {
          console.info('get top proportion colors: index ' + index + ', color ' + colors[index]);
        }
      }
    }
  });
});
```

## isBlackOrWhiteOrGrayColor

```TypeScript
isBlackOrWhiteOrGrayColor(color: number): boolean
```

判断指定颜色值是否为黑白灰颜色，返回true或false。 常用于判断颜色是否属于无彩色系，如智能配色过滤、图片颜色分类等场景。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | number | 是 | 需要判断是否黑白灰色的颜色值，格式为0xAARRGGBB，取值范围为[0x0, 0xFFFFFFFF]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示颜色为黑白灰色，false表示颜色不是黑白灰色。 |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建ColorPicker实例
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error(`Failed to create color picker. Code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('Succeeded in creating color picker.');
      // 判断颜色是否为黑白灰色
      let isBlackOrWhiteOrGray = colorPicker.isBlackOrWhiteOrGrayColor(0xFFFFFFFF);
      console.info('is black or white or gray color[bool](white) =' + isBlackOrWhiteOrGray);
    }
  });
});
```
