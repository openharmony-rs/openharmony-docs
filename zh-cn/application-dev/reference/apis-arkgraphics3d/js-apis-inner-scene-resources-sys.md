# SceneResources (系统接口)
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

本模块提供ArkGraphics 3D中常用的基本资源类型。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 12开始支持，后续版本的新增接口，采用上角标标记接口的起始版本。
> - 页面仅包含本模块的系统接口，其他公开接口参见[SceneResources](js-apis-inner-scene-resources.md)。

## 导入模块

```ts
import { MaterialType, UnlitShadowAlphaMaterial, RenderTarget } from '@kit.ArkGraphics3D';
```

## MaterialType

场景中物体材质类型枚举，定义材质的渲染方式。

**系统能力：** SystemCapability.ArkUi.Graphics3D

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| UNLIT_SHADOW_ALPHA<sup>23+</sup> | 100 | 仅对阴影进行绘制，当材质开启[Blend](js-apis-inner-scene-resources.md#blend20)属性，与背景融合模拟透明材质效果。<br>**系统接口：** 此接口为系统接口。<br>**模型约束：** 此接口仅可在Stage模型下使用。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23|

## UnlitShadowAlphaMaterial<sup>23+</sup>

此材质继承自[Material](js-apis-inner-scene-resources.md#material)，仅绘制材质表面阴影。材质启用[Blend](js-apis-inner-scene-resources.md#blend20)属性时，可与背景融合模拟透明效果。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| baseColor | [MaterialProperty](js-apis-inner-scene-resources.md#materialproperty20) | 否 | 否 | 基础颜色属性，用于表示透明材质表面阴影的颜色信息。|

## RenderTarget

渲染目标类型，继承自[Image](js-apis-inner-scene-resources.md#image)，用于离屏渲染。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

### getPixelMap

getPixelMap(): Promise\<image.PixelMap\>

从渲染目标对象获取渲染结果的PixelMap，返回的PixelMap不可编辑，使用Promise异步回调。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)\> | Promise对象，返回渲染结果对应的PixelMap。 |

**错误码：**

以下错误码的详细介绍请参见[图形3D错误码](errorcode-graphics3d.md)。

| 错误码ID | 错误信息 |
| ---- | ---- |
| 25601006 | Expired or invalid resource. |

**示例：**

```ts
import { Scene, Camera, RenderTargetParameters } from '@kit.ArkGraphics3D';
import { image } from '@kit.ImageKit';

function getPixelMapFromRenderTarget(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), { offset: 0 })
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let sceneFactory = result.getResourceFactory();
      // 创建离屏渲染相机，用于离屏渲染，不能使用主相机
      let offscreenCamera: Camera = await sceneFactory.createCamera({ name: "offscreenCamera" });
      offscreenCamera.position = { x: 0, y: 0, z: 3 };
      // 配置渲染目标参数，设置渲染目标的尺寸为512*512像素
      let params: RenderTargetParameters = {
        name: "snapshotTarget",
        size: { x: 512, y: 512 }
      };
      // 对当前场景进行离屏渲染
      let renderTargets = await result.snapshot([offscreenCamera], [params]);
      if (renderTargets.length > 0) {
        // 从渲染目标对象获取PixelMap
        let pixelMap: image.PixelMap = await renderTargets[0].getPixelMap();
        let imageInfo = await pixelMap.getImageInfo();
        console.info("PixelMap width: " + imageInfo.size.width);
        // 释放PixelMap
        pixelMap.release();
      }
    }).catch((err: Error) => {
      console.error(`Failed to get pixel map. Message: ${err.message}`);
    });
}
```