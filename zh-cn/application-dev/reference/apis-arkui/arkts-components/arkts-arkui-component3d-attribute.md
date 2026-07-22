# Component3D属性/事件

**继承/实现关系：** Component3DAttribute extends [CommonMethod<Component3DAttribute>](CommonMethod<Component3DAttribute>)

**起始版本：** 12

<!--Device-unnamed-declare class Component3DAttribute extends CommonMethod<Component3DAttribute>--><!--Device-unnamed-declare class Component3DAttribute extends CommonMethod<Component3DAttribute>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## customRender

```TypeScript
customRender(uri: ResourceStr, selfRenderUpdate: boolean)
```

设置3D场景渲染的渲染管线.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Component3DAttribute-customRender(uri: ResourceStr, selfRenderUpdate: boolean): Component3DAttribute--><!--Device-Component3DAttribute-customRender(uri: ResourceStr, selfRenderUpdate: boolean): Component3DAttribute-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 渲染管线配置文件的路径 |
| selfRenderUpdate | boolean | 是 | 每帧触发动效渲染 |

## environment

```TypeScript
environment(uri: ResourceStr)
```

加载3D模型环境资源.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Component3DAttribute-environment(uri: ResourceStr): Component3DAttribute--><!--Device-Component3DAttribute-environment(uri: ResourceStr): Component3DAttribute-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 3D环境资源的路径 |

## renderHeight

```TypeScript
renderHeight(value: Dimension)
```

设置渲染高度分辨率.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Component3DAttribute-renderHeight(value: Dimension): Component3DAttribute--><!--Device-Component3DAttribute-renderHeight(value: Dimension): Component3DAttribute-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | GPU渲染目标的高度，目标将上采样或下采样到视图高度. |

## renderWidth

```TypeScript
renderWidth(value: Dimension)
```

设置渲染宽度分辨率.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Component3DAttribute-renderWidth(value: Dimension): Component3DAttribute--><!--Device-Component3DAttribute-renderWidth(value: Dimension): Component3DAttribute-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | GPU渲染目标的宽度，目标将上采样或下采样到视图宽度. |

## shader

```TypeScript
shader(uri: ResourceStr)
```

加载着色器URI.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Component3DAttribute-shader(uri: ResourceStr): Component3DAttribute--><!--Device-Component3DAttribute-shader(uri: ResourceStr): Component3DAttribute-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 自定义着色器的路径 |

## shaderImageTexture

```TypeScript
shaderImageTexture(uri: ResourceStr)
```

加载着色器纹理URI.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Component3DAttribute-shaderImageTexture(uri: ResourceStr): Component3DAttribute--><!--Device-Component3DAttribute-shaderImageTexture(uri: ResourceStr): Component3DAttribute-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 着色器所用纹理的路径 |

## shaderInputBuffer

```TypeScript
shaderInputBuffer(buffer: Array<number>)
```

着色器动画的缓冲区输入

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Component3DAttribute-shaderInputBuffer(buffer: Array<number>): Component3DAttribute--><!--Device-Component3DAttribute-shaderInputBuffer(buffer: Array<number>): Component3DAttribute-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | Array&lt;number&gt; | 是 | 着色器输入的统一缓冲区 |

