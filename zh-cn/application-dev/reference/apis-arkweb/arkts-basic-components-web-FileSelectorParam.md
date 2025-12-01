# Class (FileSelectorParam)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

Web组件获取文件对象。示例代码参考[onShowFileSelector事件](./arkts-basic-components-web-events.md#onshowfileselector9)。

> **说明：**
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 9开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## constructor<sup>9+</sup>

constructor()

FileSelectorParam的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

## getTitle<sup>9+</sup>

getTitle(): string

获取文件选择器标题。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明         |
| ------ | ---------- |
| string | 返回文件选择器标题。 |

## getMode<sup>9+</sup>

getMode(): FileSelectorMode

获取文件选择器的模式。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型                                       | 说明          |
| ---------------------------------------- | ----------- |
| [FileSelectorMode](./arkts-basic-components-web-e.md#fileselectormode9) | 返回文件选择器的模式。 |

## getAcceptType<sup>9+</sup>

getAcceptType(): Array\<string\>

获取文件过滤类型。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型              | 说明        |
| --------------- | --------- |
| Array\<string\> | 返回文件过滤类型。 |

## isCapture<sup>9+</sup>

isCapture(): boolean

获取是否调用多媒体能力。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型      | 说明           |
| ------- | ------------ |
| boolean | 返回是否调用多媒体能力。<br>true表示返回调用多媒体能力，false表示返回未调用多媒体能力。 |

## getMimeTypes<sup>18+</sup>

getMimeTypes(): Array\<string\>

获取文件MIME类型。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型              | 说明        |
| --------------- | --------- |
| Array\<string\> | 返回文件MIME类型。 |

## getSuggestedName<sup>23+</sup>

getSuggestedName(): string

获取建议选择的文件名。对应HTML里[option](../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的`suggestedName`。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明         |
| ------ | ---------- |
| string | 返回建议文件名。 |

## getDefaultPath<sup>23+</sup>

getDefaultPath(): string

获取文件选择器默认起始路径。对应HTML里[option](../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的`startIn`。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型     | 说明         |
| ------ | ---------- |
| string | 返回默认路径。<br>当前端startIn设置为公共目录`downloads`、`pictures`时，要注意应分别转化为鸿蒙系统下的`download`和`images`。 |

## getDescriptions<sup>23+</sup>

getDescriptions(): Array\<string\>

获取各组文件类型的描述。为允许的文件类型类别的可选描述。对应HTML里[option](../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的`description`。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型              | 说明        |
| --------------- | --------- |
| Array\<string\> | 返回文件类型的描述数组。 |

## isAcceptAllOptionExcluded<sup>23+</sup>

isAcceptAllOptionExcluded(): boolean

获取文件选择器是否支持选项（\*\/\*），即所有文件。对应HTML里[option](../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的`excludeAcceptAllOption`。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型      | 说明           |
| ------- | ------------ |
| boolean | 返回是否包含一个不应用任何文件类型过滤器的选项。<br>true表示不包含，false表示包含，默认为false。 |