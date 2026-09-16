# XComponentNode

提供XComponent节点XComponentNode，表示组件树中的XComponent组件，用于EGL/OpenGL ES渲染和媒体数据写入，并支持动态修改节点渲染类型，适用于需要在ArkUI组件树中嵌入Native自渲染内容的场景。

@extends FrameNode

**继承/实现关系：** XComponentNode extends [FrameNode](arkts-arkui-framenode-c.md)

**起始版本：** 11

**废弃版本：** 12

**替代接口：** XComponent

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## changeRenderType

```TypeScript
changeRenderType(type: NodeRenderType): boolean
```

动态修改XComponentNode的渲染类型。可在运行时动态切换渲染策略，适用于根据内容渲染需求选择不同渲染类型的场景。例如，当需要在组件上进行EGL/OpenGL ES直接绘制时可使用RENDER_TYPE_DISPLAY类型；当需要将渲染内容作为纹理参与合成（如实现半透明叠加效果或离屏渲染）时可切换为RENDER_TYPE_TEXTURE类型。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** appendChild

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | 是 | 需要修改的目标渲染类型，取值为NodeRenderType枚举定义的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 修改渲染类型是否成功。<br>true：修改渲染类型成功；false：修改渲染类型失败。 |

## constructor

```TypeScript
constructor(uiContext: UIContext, options: RenderOptions,
    id: string, type: XComponentType, libraryName?: string)
```

XComponentNode的构造函数。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** createNode

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | UI上下文，获取方式可参考UIContext获取方法。 |
| options | [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 是 | XComponentNode的渲染配置选项，用于设置节点渲染相关参数，如理想尺寸（selfIdealSize）等。 |
| id | string | 是 | XComponent的唯一标识，最大支持字符串长度128，超出长度时无效。详见XComponent组件。 |
| type | [XComponentType](arkts-arkui-xcomponenttype-e.md) | 是 | 用于指定XComponent组件类型，取值为XComponentType枚举定义的值。详见XComponent组件。 |
| libraryName | string | 否 | Native层编译输出动态库名称。不传该参数时，默认不加载Native动态库。详见XComponent组件。 |

## onCreate

```TypeScript
onCreate(event?: Object): void
```

XComponentNode加载完成时触发该回调。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** onLoad

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Object | 否 | XComponent实例对象的事件参数，用于获取XComponent实例的context。context上挂载的方法由开发者在Native层定义，开发者可通过该context调用Native层注册的方法。 |

## onDestroy

```TypeScript
onDestroy(): void
```

XComponentNode销毁时触发该回调。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** onDestroy

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
