# RenderContext

定义了所有渲染资源的上下文。在同一渲染上下文中创建的多个场景之间，可以共享渲染资源。

**起始版本：** 23

<!--Device-unnamed-export interface RenderContext--><!--Device-unnamed-export interface RenderContext-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getRenderResourceFactory

```TypeScript
getRenderResourceFactory() : RenderResourceFactory
```

获取渲染资源工厂，提供创建不同渲染资源的功能。

**起始版本：** 23

<!--Device-RenderContext-getRenderResourceFactory() : RenderResourceFactory--><!--Device-RenderContext-getRenderResourceFactory() : RenderResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md) | 返回一个RenderResourceFactory实例，用于创建渲染资源。 |

**示例**

```TypeScript
import { Scene, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function getRenderResourceFactory(): void {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    console.error("Failed to get default render context");
    return;
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  console.info("TEST getRenderResourceFactory");
}
```

## loadPlugin

```TypeScript
loadPlugin(name: string): Promise<boolean>
```

用于加载指定名称的插件，通过插件名称查找并加载对应的插件资源，使用Promise异步回调。

**起始版本：** 23

<!--Device-RenderContext-loadPlugin(name: string): Promise<boolean>--><!--Device-RenderContext-loadPlugin(name: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要加载的插件名称，必须是系统预定义或已注册且可用的插件名称，且符合命名规范。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 返回一个Promise对象，解析结果为boolean类型，表示插件加载是否成功。true表示加载成功，false表示加载失败。 |

**示例**

```TypeScript
import { Scene, RenderContext } from '@kit.ArkGraphics3D';

function loadPlugin(): Promise<boolean> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    console.error("Failed to get default render context");
    return Promise.reject(new Error("RenderContext is null"));
  }
  return renderContext.loadPlugin("pluginName");
}
```

## registerResourcePath

```TypeScript
registerResourcePath(protocol: string, uri: string): boolean
```

注册shader等资产文件所在的路径目录及其检索名，通过检索名查找并替换shader内部关联文件的路径描述，找到对应的资产路径目录， 实现资产及其关联文件的正确加载。

**起始版本：** 23

<!--Device-RenderContext-registerResourcePath(protocol: string, uri: string): boolean--><!--Device-RenderContext-registerResourcePath(protocol: string, uri: string): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| protocol | string | 是 | 要注册的路径检索名，用作shader内部关联文件路径的前缀标识， 必须是系统未预定义或未注册且非空的检索名称。 |
| uri | string | 是 | 要注册的资产路径目录，与检索名对应，shader加载时会将路径中的检索名前缀替换为该目录， 必须是资产文件所在文件夹路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回资产文件路径是否注册成功。 true表示注册成功；false表示注册失败，可能原因为检索名已被注册或输入参数不可用。 |

**示例**

```TypeScript
import { Scene, RenderContext } from '@kit.ArkGraphics3D';

function registerResourcePath(): void {
  // 创建shader资源，路径和文件名可根据项目实际资源自定义
  Scene.load($rawfile("shaders/custom_shader/custom_material_sample.shader"))
    .then(() => {
      const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
      if (!renderContext) {
        console.error("Failed to get default render context");
        return false;
      }
      // 注册路径检索名"myproto"及其对应的资产路径目录"OhosRawFile://shaders/custom_shader/"
      // 当shader内部通过检索名引用关联文件，如路径为"myproto://textures/base.png"，
      // 系统会将"myproto://"替换为"OhosRawFile://shaders/custom_shader/"，
      // 最终从"OhosRawFile://shaders/custom_shader/textures/base.png"加载关联文件
      return renderContext.registerResourcePath("myproto", "OhosRawFile://shaders/custom_shader/");
    })
    .then(result => {
      if (result) {
        console.info("Succeeded in registering resource path");
      } else {
        console.error("Failed to register resource path");
      }
    });
}
```

