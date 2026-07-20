# DrawModifier

Defined the draw modifier of node. Provides draw callbacks for the associated Node.

**起始版本：** 12

<!--Device-unnamed-declare class DrawModifier--><!--Device-unnamed-declare class DrawModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="drawbehind"></a>
## drawBehind

```TypeScript
drawBehind?(drawContext: DrawContext): void
```

drawBehind Method. Executed before drawing associated Node.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawBehind?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawBehind?(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) | 是 | The drawContext used to draw. |

<a id="drawcontent"></a>
## drawContent

```TypeScript
drawContent?(drawContext: DrawContext): void
```

drawContent Method. Executed when associated Node is drawing, the default drawContent method will be replaced if this method is set.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawContent?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawContent?(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) | 是 | The drawContext used to draw. |

<a id="drawforeground"></a>
## drawForeground

```TypeScript
drawForeground(drawContext: DrawContext): void
```

前景绘制，在关联节点和其子节点绘制后执行

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawForeground(drawContext: DrawContext): void--><!--Device-DrawModifier-drawForeground(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) | 是 | 用来绘制的drawContext |

<a id="drawfront"></a>
## drawFront

```TypeScript
drawFront?(drawContext: DrawContext): void
```

drawFront Method. Executed after drawing associated Node.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawFront?(drawContext: DrawContext): void--><!--Device-DrawModifier-drawFront?(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) | 是 | The drawContext used to draw. |

<a id="drawoverlay"></a>
## drawOverlay

```TypeScript
drawOverlay(drawContext: DrawContext): void
```

在关联的Node及其所有子节点绘制完成后，在悬浮层中绘制内容。

自定义绘制包含五个层级：内容背景层、内容层、内容前景层、前景层和悬浮层。  
- 前景层和悬浮层在子节点之后绘制。  
- 悬浮层与前景层的区别在于：悬浮层可以在组件的边界范围外进行绘制。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-drawOverlay(drawContext: DrawContext): void--><!--Device-DrawModifier-drawOverlay(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | [DrawContext](../arkts-apis/arkts-arkui-graphics-drawcontext-c.md) | 是 | 用于绘制的drawContext |

<a id="invalidate"></a>
## invalidate

```TypeScript
invalidate(): void
```

Invalidate the component, which will cause a re-render of the component.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawModifier-invalidate(): void--><!--Device-DrawModifier-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

