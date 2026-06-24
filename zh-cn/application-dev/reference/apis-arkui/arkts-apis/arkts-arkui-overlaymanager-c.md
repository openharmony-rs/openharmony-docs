# OverlayManager

提供绘制浮层的能力。

> **说明：**
>
> - 本Class首批接口从API version 12开始支持。

> - 以下API需先使用UIContext中的[getOverlayManager()](arkts-arkui-uicontext-c.md#getOverlayManager-1)方法获取到OverlayManager对象，再通过该对象调用对应方法。
>
> - OverlayManager上节点的层级在Page页面层级之上，在Dialog、Popup、Menu、BindSheet、BindContentCover和Toast等之下。
>
> - OverlayManager上节点安全区域内外的绘制方式与Page一致，键盘避让方式与Page一致。
>
> - 与OverlayManager相关的属性推荐采用AppStorage来进行应用全局存储，以免切换页面后属性值发生变化从而导致业务错误。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addComponentContent

```TypeScript
addComponentContent(content: ComponentContent, index?: number): void
```

在OverlayManager上新增指定节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent | 是 | 在OverlayManager的指定节点上添加此content。<br/>**说明：**<br/><br/>新增的节点默认处于页面居中，按层级堆叠。 |
| index | number | 否 |  |

## addComponentContentWithOrder

```TypeScript
addComponentContentWithOrder(content: ComponentContent, levelOrder?: LevelOrder): void
```

创建浮层节点时，指定显示顺序。
支持在浮层节点创建时指定显示的顺序。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent | 是 | 在OverlayManager的指定节点上添加此content。<br/><br/>**说明：**<br/><br/>新增的节点默认处于页面居中位置，按层级堆叠。 |
| levelOrder | LevelOrder | 否 |  |

## hideAllComponentContents

```TypeScript
hideAllComponentContents(): void
```

隐藏OverlayManager上的所有ComponentContent。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hideComponentContent

```TypeScript
hideComponentContent(content: ComponentContent): void
```

隐藏OverlayManager上的指定节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent | 是 | 在OverlayManager上隐藏此content。 |

## openOrderOverlay

```TypeScript
openOrderOverlay(content: ComponentContent, options?: OrderOverlayOptions): Promise<void>
```

打开一个支持层级配置的浮层，浮层中的内容由开发者传入的组件内容（content字段）决定。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent | 是 | 浮层的显示内容，在OverlayManager的新节点上添加此内容节点。<br/>**说明：**<br/>新增的节点默认处于页面居中位置，按层级堆叠。 |
| options | OrderOverlayOptions | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103307](../../errorcode-universal.md#103307-The) | The overlay cannot be opened due to the system pop-up window. |

## removeComponentContent

```TypeScript
removeComponentContent(content: ComponentContent): void
```

删除overlay上的指定节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent | 是 | 在OverlayManager上删除此content。 |

## showAllComponentContents

```TypeScript
showAllComponentContents(): void
```

显示OverlayManager上所有的ComponentContent。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showComponentContent

```TypeScript
showComponentContent(content: ComponentContent): void
```

在OverlayManager上显示指定节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent | 是 | 在OverlayManager上显示此content。 |

