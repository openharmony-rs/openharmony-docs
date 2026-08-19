# WebContextMenuParam

WebContextMenuParam是ArkWeb组件中用于承载长按页面元素或鼠标右键弹出的上下文菜单信息的参数类，作为`onContextMenuShow`事件回调的数据载体，封装了菜单弹出位置、链接地址、媒体类型、选中文本、编辑 状态等关键信息。 自定义Web组件上下文菜单时，使用WebContextMenuParam获取用户长按/右击位置的网页元素详细信息（如链接URL、图片内容、媒体类型、输入框类型、编辑状态等），判断用户操作场景，决定是否拦截默认菜单并构建自定义菜单项。 自定义Web组件长按或右键菜单（如替换默认菜单、根据不同元素类型提供差异化菜单项、预览图片等）时，在`onContextMenuShow`事件回调中使用WebContextMenuParam获取上下文信息。 示例代码参考[onContextMenuShow](arkts-arkweb-web-attribute.md#oncontextmenushow)。

**起始版本：** 9

<!--Device-unnamed-declare class WebContextMenuParam--><!--Device-unnamed-declare class WebContextMenuParam-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

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

判断当前长按或右键位置是否存在图像内容，用于在自定义菜单中提供"保存图片"等图片相关功能。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-existsImageContents(): boolean--><!--Device-WebContextMenuParam-existsImageContents(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 长按位置存在图片返回true，否则返回false。 |

## getContextMenuMediaType

```TypeScript
getContextMenuMediaType(): ContextMenuDataMediaType
```

在上报上下文菜单事件时，获取用户长按或者右键点击的网页元素类型。

**起始版本：** 22

<!--Device-WebContextMenuParam-getContextMenuMediaType(): ContextMenuDataMediaType--><!--Device-WebContextMenuParam-getContextMenuMediaType(): ContextMenuDataMediaType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuDataMediaType](arkts-arkweb-contextmenudatamediatype-e.md) | 网页元素的媒体类型，包括图片、视频、音频等不同类型，用于区分用户点击的网页元素种类。 |

## getEditStateFlags

```TypeScript
getEditStateFlags(): number
```

获取网页元素的可编辑标识，用于精细控制自定义菜单选项的显示逻辑（如根据是否可复制、可粘贴、可撤销等显示对应的菜单项）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getEditStateFlags(): number--><!--Device-WebContextMenuParam-getEditStateFlags(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取网页元素可编辑标识，参照[ContextMenuEditStateFlags]{ |

## getInputFieldType

```TypeScript
getInputFieldType(): ContextMenuInputFieldType
```

获取网页元素的输入框类型（如文本框、密码框、搜索框等），用于根据输入框类型提供合适的编辑菜单选项（如文本框提供粘贴、全选，密码框只提供复制或隐藏密码等）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getInputFieldType(): ContextMenuInputFieldType--><!--Device-WebContextMenuParam-getInputFieldType(): ContextMenuInputFieldType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuInputFieldType](arkts-arkweb-contextmenuinputfieldtype-e.md) | 网页元素输入框的类型，包括文本框、密码框、邮箱框等不同类型，用于识别当前焦点所在的输入元素种类。 |

## getLinkUrl

```TypeScript
getLinkUrl(): string
```

获取经过安全检查的URL链接地址，可用于构建自定义菜单时提供"打开链接"、"分享链接"、"复制链接"等操作。 > **说明：** > > 与getUnfilteredLinkUrl()相比，该方法会对URL进行安全检查；与getSourceUrl()相比，该方法获取的是长按位置处的链接URL，而getSourceUrl()获取的是选中元素的src属性URL（如图 > 像、媒体等资源）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getLinkUrl(): string--><!--Device-WebContextMenuParam-getLinkUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 如果长按位置是链接，返回经过安全检查的URL链接，否则返回空字符串。 |

## getMediaType

```TypeScript
getMediaType(): ContextMenuMediaType
```

获取网页元素的媒体类型。 > **说明：** > > 从API version 22开始，[getContextMenuMediaType](#getcontextmenumediatype)提供更丰富的媒体类型识别能力。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getMediaType(): ContextMenuMediaType--><!--Device-WebContextMenuParam-getMediaType(): ContextMenuMediaType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuMediaType](arkts-arkweb-contextmenumediatype-e.md) | 网页元素媒体类型。 |

## getPreviewHeight

```TypeScript
getPreviewHeight(): number
```

获取预览图的高。

**起始版本：** 13

<!--Device-WebContextMenuParam-getPreviewHeight(): number--><!--Device-WebContextMenuParam-getPreviewHeight(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 预览图的高。 <br>单位：px（物理像素）。 |

## getPreviewWidth

```TypeScript
getPreviewWidth(): number
```

获取预览图的宽。

**起始版本：** 13

<!--Device-WebContextMenuParam-getPreviewWidth(): number--><!--Device-WebContextMenuParam-getPreviewWidth(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 预览图的宽。 <br>单位：px（物理像素）。 |

## getSelectionText

```TypeScript
getSelectionText(): string
```

获取右键单击已选中文本时的内容，用于在自定义菜单中提供"复制"、"分享"、"翻译"、"搜索"等文本操作功能。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getSelectionText(): string--><!--Device-WebContextMenuParam-getSelectionText(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 选中文本内容。如果右键单击位置存在选中的文本，返回选中的文本内容；不存在则返回空字符串。 |

## getSourceType

```TypeScript
getSourceType(): ContextMenuSourceType
```

获取上下文菜单事件的触发来源类型（如鼠标右键、长按操作等），用于根据不同来源调整菜单展示样式或提供差异化的菜单选项。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getSourceType(): ContextMenuSourceType--><!--Device-WebContextMenuParam-getSourceType(): ContextMenuSourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContextMenuSourceType](arkts-arkweb-contextmenusourcetype-e.md) | 菜单事件的触发来源类型，包括鼠标右键、长按等不同的触发方式。 |

## getSourceUrl

```TypeScript
getSourceUrl(): string
```

获取元素的src属性对应的URL链接地址。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getSourceUrl(): string--><!--Device-WebContextMenuParam-getSourceUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 如果选中的元素有src属性，返回src的URL。返回URL的最大上限为2MB，超出上限时返回空字符串。 |

## getUnfilteredLinkUrl

```TypeScript
getUnfilteredLinkUrl(): string
```

获取未经安全检查的原始URL链接地址。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-getUnfilteredLinkUrl(): string--><!--Device-WebContextMenuParam-getUnfilteredLinkUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 如果长按位置是链接，返回原始的URL链接，否则返回空字符串。 |

## isEditable

```TypeScript
isEditable(): boolean
```

判断网页元素是否可编辑。用于在自定义菜单中动态显示或隐藏编辑相关选项（如可编辑时显示粘贴、剪切、全选，不可编辑时隐藏这些选项）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-isEditable(): boolean--><!--Device-WebContextMenuParam-isEditable(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 网页元素可编辑返回true，否则返回false。 |

## x

```TypeScript
x(): number
```

弹出菜单的x坐标，相对于Web组件左上角的水平距离。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-x(): number--><!--Device-WebContextMenuParam-x(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取成功时返回非负整数，失败时返回-1。 <br>单位：px（物理像素）。 |

## y

```TypeScript
y(): number
```

弹出菜单的y坐标，相对于Web组件左上角的垂直距离。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuParam-y(): number--><!--Device-WebContextMenuParam-y(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取成功时返回非负整数，失败时返回-1。 <br>单位：px（物理像素）。 |

