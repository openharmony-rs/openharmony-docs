# RenderTarget（系统接口）

```TypeScript
export interface RenderTarget extends Image
```

渲染目标类型，继承自[Image](arkts-arkgraphics3d-sceneresources-image-i.md)，用于离屏渲染。

**继承/实现关系：** RenderTarget extends [Image](arkts-arkgraphics3d-sceneresources-image-i.md)

**起始版本：** 26.1.0

<!--Device-unnamed-export interface RenderTarget extends Image--><!--Device-unnamed-export interface RenderTarget extends Image-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## getPixelMap

```TypeScript
getPixelMap(): Promise<image.PixelMap>
```

从渲染目标对象获取渲染结果的PixelMap，返回的PixelMap不可编辑，使用Promise异步回调。渲染目标对象已销毁时调用该接口抛出错误码25601006。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderTarget-getPixelMap(): Promise<image.PixelMap>--><!--Device-RenderTarget-getPixelMap(): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise对象，返回渲染结果对应的PixelMap。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 25601006 | Expired or invalid resource. |
