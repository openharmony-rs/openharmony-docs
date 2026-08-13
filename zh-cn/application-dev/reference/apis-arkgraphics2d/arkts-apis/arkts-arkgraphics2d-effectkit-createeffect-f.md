# createEffect

## createEffect

```TypeScript
function createEffect(source: image.PixelMap): Filter
```

通过传入的PixelMap创建Filter实例。后续可通过链式调用添加各种图像效果， 最终通过[getEffectPixelMap](arkts-arkgraphics2d-effectkit-filter-i.md#getEffectPixelMap)获取处理后的图像。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-effectKit-function createEffect(source: image.PixelMap): Filter--><!--Device-effectKit-function createEffect(source: image.PixelMap): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | image.PixelMap | 是 | image模块创建的PixelMap实例。可通过图片解码或直接创建获得，具体可见 [Image Kit简介](../../../media/image/image-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Filter | 返回一个未添加任何效果的Filter实例，失败时返回null。 |

## 示例

```TypeScript
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
image.createPixelMap(color, opts).then((pixelMap) => {
  let headFilter = effectKit.createEffect(pixelMap);
})
```

