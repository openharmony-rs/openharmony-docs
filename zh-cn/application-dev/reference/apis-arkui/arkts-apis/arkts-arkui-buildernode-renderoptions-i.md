# RenderOptions

创建BuilderNode时的可选参数。

**起始版本：** 11

<!--Device-unnamed-export interface RenderOptions--><!--Device-unnamed-export interface RenderOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selfIdealSize

```TypeScript
selfIdealSize?: Size
```

节点的理想大小。

默认值：{ width: 0, height: 0 }

**类型：** Size

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderOptions-selfIdealSize?: Size--><!--Device-RenderOptions-selfIdealSize?: Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## surfaceId

```TypeScript
surfaceId?: string
```

纹理接收方的surfaceId。纹理接收方一般为[OH_NativeImage](../../../../reference/apis-arkgraphics2d/capi-oh-nativeimage-oh-nativeimage.md)。

surfaceId仅当type为NodeRenderType.RENDER_TYPE_TEXTURE时生效。

默认值：""

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderOptions-surfaceId?: string--><!--Device-RenderOptions-surfaceId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: NodeRenderType
```

节点的渲染类型。

默认值：NodeRenderType.RENDER_TYPE_DISPLAY

**类型：** NodeRenderType

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderOptions-type?: NodeRenderType--><!--Device-RenderOptions-type?: NodeRenderType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

