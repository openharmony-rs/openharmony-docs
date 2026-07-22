# WebContextMenuParam

定义上下文菜单参数，关联{@link WebContextMenuParam}方法。

**起始版本：** 9

<!--Device-unnamed-declare class WebContextMenuParam--><!--Device-unnamed-declare class WebContextMenuParam-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

WebContextMenuParam的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-constructor()--><!--Device-WebContextMenuParam-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## existsImageContents

```TypeScript
existsImageContents(): boolean
```

长按菜单所在位置是否包含图片内容。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-existsImageContents(): boolean--><!--Device-WebContextMenuParam-existsImageContents(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前上下文菜单位置是否存在图片内容。 |

## getContextMenuMediaType

```TypeScript
getContextMenuMediaType(): ContextMenuDataMediaType
```

返回上下文节点的类型。

**起始版本：** 22

<!--Device-WebContextMenuParam-getContextMenuMediaType(): ContextMenuDataMediaType--><!--Device-WebContextMenuParam-getContextMenuMediaType(): ContextMenuDataMediaType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuDataMediaType](arkts-arkweb-contextmenudatamediatype-e.md) | 返回上下文节点的类型。 |

## getEditStateFlags

```TypeScript
getEditStateFlags(): number
```

返回上下文可编辑状态标记 {@link ContextMenuEditStateFlags}。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getEditStateFlags(): number--><!--Device-WebContextMenuParam-getEditStateFlags(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | @syscap SystemCapability.Web.Webview.Core@atomicservice |

## getInputFieldType

```TypeScript
getInputFieldType(): ContextMenuInputFieldType
```

若上下文菜单在输入框上触发，则返回输入框类型。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getInputFieldType(): ContextMenuInputFieldType--><!--Device-WebContextMenuParam-getInputFieldType(): ContextMenuInputFieldType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuInputFieldType](arkts-arkweb-contextmenuinputfieldtype-e.md) | 输入框上触发菜单时返回输入框类型。 |

## getLinkUrl

```TypeScript
getLinkUrl(): string
```

若长按位置为链接，则返回经过安全校验的链接 URL。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getLinkUrl(): string--><!--Device-WebContextMenuParam-getLinkUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 关联链接时返回链接地址，否则返回 null。 |

## getMediaType

```TypeScript
getMediaType(): ContextMenuMediaType
```

返回上下文节点的类型。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getMediaType(): ContextMenuMediaType--><!--Device-WebContextMenuParam-getMediaType(): ContextMenuMediaType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuMediaType](arkts-arkweb-contextmenumediatype-e.md) | 返回上下文节点的类型。 |

## getPreviewHeight

```TypeScript
getPreviewHeight(): number
```

返回选择菜单预览高度。

**起始版本：** 13

<!--Device-WebContextMenuParam-getPreviewHeight(): number--><!--Device-WebContextMenuParam-getPreviewHeight(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 预览菜单高度。单位：像素。 |

## getPreviewWidth

```TypeScript
getPreviewWidth(): number
```

返回选择菜单预览宽度。

**起始版本：** 13

<!--Device-WebContextMenuParam-getPreviewWidth(): number--><!--Device-WebContextMenuParam-getPreviewWidth(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 菜单预览宽度。单位：像素。 |

## getSelectionText

```TypeScript
getSelectionText(): string
```

返回选中的文本内容。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getSelectionText(): string--><!--Device-WebContextMenuParam-getSelectionText(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回选中文本，未选中任何文本时返回 null。 |

## getSourceType

```TypeScript
getSourceType(): ContextMenuSourceType
```

* 返回上下文菜单的来源类型。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getSourceType(): ContextMenuSourceType--><!--Device-WebContextMenuParam-getSourceType(): ContextMenuSourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuSourceType](arkts-arkweb-contextmenusourcetype-e.md) | @syscap SystemCapability.Web.Webview.Core@atomicservice |

## getSourceUrl

```TypeScript
getSourceUrl(): string
```

若选中元素包含 SRC 属性，则返回其资源地址 URL。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getSourceUrl(): string--><!--Device-WebContextMenuParam-getSourceUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 若当前上下文菜单源自元素 src 属性，则返回资源链接地址，否则返回 null。 |

## getUnfilteredLinkUrl

```TypeScript
getUnfilteredLinkUrl(): string
```

若长按位置为链接，则返回该链接的原始 URL。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getUnfilteredLinkUrl(): string--><!--Device-WebContextMenuParam-getUnfilteredLinkUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 关联链接时返回未过滤的链接地址，否则返回 null。 |

## isEditable

```TypeScript
isEditable(): boolean
```

* 返回当前上下文是否可编辑。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-isEditable(): boolean--><!--Device-WebContextMenuParam-isEditable(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | @syscap SystemCapability.Web.Webview.Core@atomicservice |

## x

```TypeScript
x(): number
```

菜单在Web组件内的水平偏移坐标。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-x(): number--><!--Device-WebContextMenuParam-x(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 上下文菜单X坐标。正常情况下返回非负整数，否则返回 -1。单位：像素。 |

## y

```TypeScript
y(): number
```

菜单在Web组件内的垂直偏移坐标。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-y(): number--><!--Device-WebContextMenuParam-y(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 上下文菜单Y坐标。正常情况下返回非负整数，否则返回 -1。单位：像素。 |

