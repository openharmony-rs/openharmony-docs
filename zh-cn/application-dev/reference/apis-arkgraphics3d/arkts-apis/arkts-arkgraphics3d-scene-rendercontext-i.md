# RenderContext

渲染上下文，定义所有渲染资源的上下文。同一渲染上下文中的资源可在该上下文内创建的场景间共享。

**起始版本：** 20

<!--Device-unnamed-export interface RenderContext--><!--Device-unnamed-export interface RenderContext-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getRenderResourceFactory

```TypeScript
getRenderResourceFactory() : RenderResourceFactory
```

获取资源工厂.

**起始版本：** 20

<!--Device-RenderContext-getRenderResourceFactory() : RenderResourceFactory--><!--Device-RenderContext-getRenderResourceFactory() : RenderResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md) | -- RenderResourceFactory实例 |

## loadPlugin

```TypeScript
loadPlugin(name: string): Promise<boolean>
```

加载外部插件

**起始版本：** 20

<!--Device-RenderContext-loadPlugin(name: string): Promise<boolean>--><!--Device-RenderContext-loadPlugin(name: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 插件名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | - 返回表示插件加载是否成功的Promise |

## registerResourcePath

```TypeScript
registerResourcePath(protocol: string, uri: string): boolean
```

注册资源路径

**起始版本：** 20

<!--Device-RenderContext-registerResourcePath(protocol: string, uri: string): boolean--><!--Device-RenderContext-registerResourcePath(protocol: string, uri: string): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| protocol | string | 是 | uri的协议 |
| uri | string | 是 | 要注册的路径 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 注册成功返回true，false表示协议已被注册 |

