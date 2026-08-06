# RenderOptions

创建BuilderNode时的可选参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface RenderOptions--><!--Device-unnamed-export interface RenderOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableMinimized

```TypeScript
enableMinimized?: boolean
```

控制BuilderNode持有的FrameNode的类型，当此开关设置为true时，BuilderNode持有的FrameNode为轻量化的FrameNode，内存更小，但是不支持FrameNode的部分接口，具体信息请参见 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderOptions-enableMinimized?: boolean--><!--Device-RenderOptions-enableMinimized?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selfIdealSize

```TypeScript
selfIdealSize?: Size
```

节点的理想大小。 默认值：{ width: 0, height: 0 }

**类型：** Size

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderOptions-selfIdealSize?: Size--><!--Device-RenderOptions-selfIdealSize?: Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## surfaceId

```TypeScript
surfaceId?: string
```

纹理接收方的surfaceId。纹理接收方一般为 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 surfaceId仅当type为NodeRenderType.RENDER\_TYPE\_TEXTURE时生效。 默认值：""

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderOptions-surfaceId?: string--><!--Device-RenderOptions-surfaceId?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: NodeRenderType
```

节点的渲染类型。 默认值：NodeRenderType.RENDER\_TYPE\_DISPLAY

**类型：** NodeRenderType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderOptions-type?: NodeRenderType--><!--Device-RenderOptions-type?: NodeRenderType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

