# CustomCursor

自定义光标资源。

**起始版本：** 15

<!--Device-pointer-interface CustomCursor--><!--Device-pointer-interface CustomCursor-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## focusX

```TypeScript
focusX?: number
```

自定义光标焦点的水平坐标。该坐标受自定义光标大小的限制。最小值为0，最大值为资源图的宽度最大值该参数缺省时默认为0，单位为像素（px）。

**类型：** number

**起始版本：** 15

<!--Device-CustomCursor-focusX?: int--><!--Device-CustomCursor-focusX?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

## focusY

```TypeScript
focusY?: number
```

自定义光标焦点的垂直坐标。该坐标受自定义光标大小的限制。最小值为0，最大值为资源图的高度最大值该参数缺省时默认为0，单位为像素（px）。

**类型：** number

**起始版本：** 15

<!--Device-CustomCursor-focusY?: int--><!--Device-CustomCursor-focusY?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

## pixelMap

```TypeScript
pixelMap: image.PixelMap
```

自定义光标。最小限制为资源图本身的最小限制。最大限制为256 x 256px。

**类型：** image.PixelMap

**起始版本：** 15

<!--Device-CustomCursor-pixelMap: image.PixelMap--><!--Device-CustomCursor-pixelMap: image.PixelMap-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

