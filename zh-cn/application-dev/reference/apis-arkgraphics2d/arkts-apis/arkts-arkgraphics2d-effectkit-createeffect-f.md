# createEffect

## 导入模块

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

<a id="createeffect"></a>
## createEffect

```TypeScript
function createEffect(source: image.PixelMap): Filter
```

通过传入的PixelMap创建Filter实例。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-effectKit-function createEffect(source: image.PixelMap): Filter--><!--Device-effectKit-function createEffect(source: image.PixelMap): Filter-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | image.PixelMap | 是 | image模块创建的PixelMap实例。可通过图片解码或直接创建获得，具体可见[Image Kit简介](docroot://media/image/image-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 返回不带任何效果的Filter链表头节点，失败时返回null。 |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// 创建用于图像效果的buffer
const colorBuffer = new ArrayBuffer(96);
// 设置图像初始化选项
let opts : image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// 创建PixelMap实例
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // 创建Filter实例
  let headFilter = effectKit.createEffect(pixelMap);
});

```

