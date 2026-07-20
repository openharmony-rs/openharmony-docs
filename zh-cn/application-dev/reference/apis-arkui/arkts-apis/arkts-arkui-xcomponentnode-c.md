# XComponentNode

定义XComponent Node。

**继承/实现关系：** XComponentNode extends [FrameNode](arkts-arkui-framenode-c.md)

**起始版本：** 11

**废弃版本：** 12

**替代接口：** XComponent

<!--Device-unnamed-export declare class XComponentNode extends FrameNode--><!--Device-unnamed-export declare class XComponentNode extends FrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="changerendertype"></a>
## changeRenderType

```TypeScript
changeRenderType(type: NodeRenderType): boolean
```

设置builderNode的渲染类型。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** appendChild

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentNode-changeRenderType(type: NodeRenderType): boolean--><!--Device-XComponentNode-changeRenderType(type: NodeRenderType): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | 是 | 渲染类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 返回是否成功修改渲染类型。 |

<a id="constructor"></a>
## constructor

```TypeScript
constructor(uiContext: UIContext, options: RenderOptions,
    id: string, type: XComponentType, libraryName?: string)
```

构造函数。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** createNode

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentNode-constructor(uiContext: UIContext, options: RenderOptions,
    id: string, type: XComponentType, libraryName?: string)--><!--Device-XComponentNode-constructor(uiContext: UIContext, options: RenderOptions,
    id: string, type: XComponentType, libraryName?: string)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 用于创建FrameNode的UIContext |
| options | [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 是 | Builder Node的渲染选项 |
| id | string | 是 | 应用定义的XComponent id |
| type | [XComponentType](arkts-arkui-xcomponenttype-e.md) | 是 | XComponent类型 |
| libraryName | string | 否 | XComponent要加载的库名称 |

<a id="oncreate"></a>
## onCreate

```TypeScript
onCreate(event?: Object): void
```

当XComponent的surface创建完成时回调。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** onLoad

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentNode-onCreate(event?: Object): void--><!--Device-XComponentNode-onCreate(event?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Object | 否 | 加载库时来自native的事件 |

<a id="ondestroy"></a>
## onDestroy

```TypeScript
onDestroy(): void
```

当XComponent的surface被销毁时回调。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** onDestroy

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentNode-onDestroy(): void--><!--Device-XComponentNode-onDestroy(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

