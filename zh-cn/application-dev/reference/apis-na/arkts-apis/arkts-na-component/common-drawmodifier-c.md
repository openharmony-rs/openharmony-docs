# DrawModifier

Defined the draw modifier of node. Provides draw callbacks for the associated Node. Each DrawModifier instance can be set for only one component. Repeated setting is not allowed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class DrawModifier--><!--Device-unnamed-export declare class DrawModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## drawBehind

```TypeScript
drawBehind(drawContext: DrawContext): void
```

drawBehind Method. Executed before drawing associated Node.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawModifier-drawBehind(drawContext: DrawContext): void--><!--Device-DrawModifier-drawBehind(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The drawContext used to draw. |

## drawContent

```TypeScript
drawContent(drawContext: DrawContext): void
```

drawContent Method. Executed when associated Node is drawing, the default drawContent method will be replaced if this method is set.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawModifier-drawContent(drawContext: DrawContext): void--><!--Device-DrawModifier-drawContent(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The drawContext used to draw. |

## drawForeground

```TypeScript
drawForeground(drawContext: DrawContext): void
```

drawForeground Method. This method is executed after drawing the associated Node and its children. It allows you to perform additional drawing operations on top of the already rendered content. This can be useful for adding visual elements that should appear above the main content.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawModifier-drawForeground(drawContext: DrawContext): void--><!--Device-DrawModifier-drawForeground(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The drawContext used to draw. |

## drawFront

```TypeScript
drawFront(drawContext: DrawContext): void
```

drawFront Method. Executed after drawing associated Node and its children.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawModifier-drawFront(drawContext: DrawContext): void--><!--Device-DrawModifier-drawFront(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The drawContext used to draw. |

## drawOverlay

```TypeScript
drawOverlay(drawContext: DrawContext): void
```

Draws content in the overlay layer after the associated Node and all its children have been drawn. Custom drawing consists of five layers: Behind, Content, Front, Foreground, and Overlay. - The Foreground and Overlay layers are drawn after child nodes. - The Overlay layer differs from Foreground in that it can draw outside the bounds of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawModifier-drawOverlay(drawContext: DrawContext): void--><!--Device-DrawModifier-drawOverlay(drawContext: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawContext | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The drawContext used to draw |

## invalidate

```TypeScript
invalidate(): void
```

Invalidate the component, which will cause a re-render of the component. No overloading is allowed or needed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawModifier-invalidate(): void--><!--Device-DrawModifier-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

