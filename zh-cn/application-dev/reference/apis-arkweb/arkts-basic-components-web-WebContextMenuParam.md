# Class (WebContextMenuParam)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

WebContextMenuParam是ArkWeb组件中用于承载长按页面元素或鼠标右键弹出的上下文菜单信息的参数类，作为`onContextMenuShow`事件回调的数据载体，封装了菜单弹出位置、链接地址、媒体类型、选中文本、编辑状态等关键信息。

开发者在自定义Web组件的上下文菜单时，通过WebContextMenuParam获取用户长按/右击位置处的网页元素详细信息（如链接URL、图片内容、媒体类型、输入框类型、编辑状态等），据此判断用户操作场景，进而决定是否拦截默认菜单并构建自定义菜单项。

当需要在Web组件中自定义长按或右键弹出菜单的行为时（如替换默认菜单、根据不同元素类型提供差异化菜单项、预览图片等），在`onContextMenuShow`事件回调中使用WebContextMenuParam获取上下文信息。

示例代码参考[onContextMenuShow](./arkts-basic-components-web-events.md#oncontextmenushow9)。

> **说明：**
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 9开始支持。
>
> - 示例效果请以真机运行为准。

## constructor<sup>9+</sup>

constructor()

WebContextMenuParam的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

## x<sup>9+</sup>

x(): number

弹出菜单的x坐标，相对于Web组件左上角的水平距离。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明                                 |
| ------ |------------------------------------|
| number | 显示正常返回非负整数，否则返回-1。<br>单位：px（物理像素）。 |

## y<sup>9+</sup>

y(): number

弹出菜单的y坐标，相对于Web组件左上角的垂直距离。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明                 |
| ------ | ------------------ |
| number | 显示正常返回非负整数，否则返回-1。<br>单位：px（物理像素）。 |

## getLinkUrl<sup>9+</sup>

getLinkUrl(): string

获取经过安全检查的URL链接地址。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明                        |
| ------ | ------------------------- |
| string | 如果长按位置是链接，返回经过安全检查的URL链接。 |

## getUnfilteredLinkUrl<sup>9+</sup>

getUnfilteredLinkUrl(): string

获取原始URL链接地址。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明                    |
| ------ | --------------------- |
| string | 如果长按位置是链接，返回原始的URL链接。 |

## getSourceUrl<sup>9+</sup>

getSourceUrl(): string

获取元素的src属性对应的URL链接地址。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明                       |
| ------ | ------------------------ |
| string | 如果选中的元素有src属性，返回src的URL。返回URL的最大上限为2MB，超出上限时返回空字符串。 |

## existsImageContents<sup>9+</sup>

existsImageContents(): boolean

是否存在图像内容。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型      | 说明                        |
| ------- | ------------------------- |
| boolean | 长按位置中有图片返回true，否则返回false。 |

## getMediaType<sup>9+</sup>

getMediaType(): ContextMenuMediaType

获取网页元素媒体类型。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型                                       | 说明        |
| ---------------------------------------- | --------- |
| [ContextMenuMediaType](./arkts-basic-components-web-e.md#contextmenumediatype9) | 网页元素媒体类型。 |

## getSelectionText<sup>9+</sup>

getSelectionText(): string

获取选中文本。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明                   |
| ------ | -------------------- |
| string | 菜单上下文选中文本内容，不存在则返回空。 |

## getSourceType<sup>9+</sup>

getSourceType(): ContextMenuSourceType

获取菜单事件来源。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
| [ContextMenuSourceType](./arkts-basic-components-web-e.md#contextmenusourcetype9) | 菜单事件来源。 |

## getInputFieldType<sup>9+</sup>

getInputFieldType(): ContextMenuInputFieldType

获取网页元素输入框类型。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型                                       | 说明     |
| ---------------------------------------- | ------ |
| [ContextMenuInputFieldType](./arkts-basic-components-web-e.md#contextmenuinputfieldtype9) | 输入框类型。 |

## isEditable<sup>9+</sup>

isEditable(): boolean

判断网页元素是否可编辑。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型      | 说明                         |
| ------- | -------------------------- |
| boolean | 网页元素可编辑返回true，不可编辑返回false。 |

## getEditStateFlags<sup>9+</sup>

getEditStateFlags(): number

获取网页元素可编辑标识。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明                                       |
| ------ | ---------------------------------------- |
| number | 网页元素可编辑标识，参照[ContextMenuEditStateFlags](./arkts-basic-components-web-e.md#contextmenueditstateflags9)。 |

## getPreviewWidth<sup>13+</sup>

getPreviewWidth(): number

获取预览图的宽。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明       |
| ------ | ----------- |
| number | 预览图的宽。<br>单位：px（物理像素）。 |

## getPreviewHeight<sup>13+</sup>

getPreviewHeight(): number

获取预览图的高。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明       |
| ------ | ----------  |
| number | 预览图的高。<br>单位：px（物理像素）。 |

## getContextMenuMediaType<sup>22+</sup>

getContextMenuMediaType(): ContextMenuDataMediaType

在上报上下文菜单事件时，获取用户点击的网页元素类型。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明       |
| ------ | ----------  |
| [ContextMenuDataMediaType](./arkts-basic-components-web-e.md#contextmenudatamediatype22) | 网页元素媒体类型。 |