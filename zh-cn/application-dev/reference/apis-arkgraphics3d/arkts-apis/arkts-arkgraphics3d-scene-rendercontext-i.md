# RenderContext

渲染上下文，定义所有渲染资源的上下文。同一渲染上下文中的资源可在该上下文内创建的场景间共享。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface RenderContext--><!--Device-unnamed-export interface RenderContext-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getRenderResourceFactory

```TypeScript
getRenderResourceFactory() : RenderResourceFactory
```

获取资源工厂.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RenderContext-getRenderResourceFactory() : RenderResourceFactory--><!--Device-RenderContext-getRenderResourceFactory() : RenderResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md) | RenderResourceFactory实例 |

## 示例

```TypeScript
import { Scene, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function getRenderResourceFactory(): void {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    console.error("RenderContext is null");
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

加载外部插件

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RenderContext-loadPlugin(name: string): Promise<boolean>--><!--Device-RenderContext-loadPlugin(name: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 插件名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 返回表示插件加载是否成功的Promise |

## 示例

```TypeScript
import { Scene, RenderContext } from '@kit.ArkGraphics3D';

function loadPlugin(): Promise<boolean> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    console.error("RenderContext is null");
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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

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
| boolean | 返回资产文件路径是否注册成功。true表示注册成功； false表示注册失败，可能原因为检索名已被注册或输入参数不可用。 |

## 示例

```TypeScript
import { Scene, RenderContext } from '@kit.ArkGraphics3D';

function registerResourcePath(): void {
  // 创建shader资源，路径和文件名可根据项目实际资源自定义
  Scene.load($rawfile("shaders/custom_shader/custom_material_sample.shader"))
    .then(() => {
      const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
      if (!renderContext) {
        console.error("RenderContext is null");
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
        console.info("resource path registration success");
      } else {
        console.error("resource path registration failed");
      }
    });
}
```

