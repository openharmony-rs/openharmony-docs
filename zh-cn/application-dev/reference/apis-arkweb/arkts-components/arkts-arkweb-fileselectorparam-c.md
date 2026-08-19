# FileSelectorParam

FileSelectorParam是ArkWeb组件中的文件选择器参数类，用于获取Web页面中`&lt;input type="file"&gt;`触发文件选择请求时的相关参数信息，包括文件选择模式、文件过滤类型、MIME类型、建议文件名、默认起 始路径等，帮助开发者高效构建符合HTML规范的自定义文件选择器。 当Web页面发起文件选择请求时，开发者通过FileSelectorParam获取前端传递的完整参数信息，据此构建与前端需求匹配的自定义文件选择器，确保文件选择的模式、类型过滤、命名等行为与HTML规范一致。 在Web组件中需要自定义处理文件上传请求的场景下使用。注册`onShowFileSelector`回调以拦截文件选择请求；从回调事件的`fileSelector`属性获取FileSelectorParam实例；读取参数后构建对应的系统 文件选择器（如DocumentViewPicker、PhotoViewPicker等）；通过FileSelectorResult返回选择结果至Web组件。 示例代码参考[onShowFileSelector](arkts-arkweb-web-attribute.md#onshowfileselector)。

**起始版本：** 9

<!--Device-unnamed-declare class FileSelectorParam--><!--Device-unnamed-declare class FileSelectorParam-End-->

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

FileSelectorParam的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-constructor()--><!--Device-FileSelectorParam-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getAcceptType

```TypeScript
getAcceptType(): Array<string>
```

获取文件过滤类型。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-getAcceptType(): Array<string>--><!--Device-FileSelectorParam-getAcceptType(): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回文件过滤类型数组，包含用于限制文件选择器可选文件范围的类型信息。元素为扩展名（如'.png'），对应HTML accept属性。 |

## getAcceptableFileTypes

```TypeScript
getAcceptableFileTypes(): Array<Array<AcceptableFileType>>
```

获取文件类型信息。对应HTML里[option](../../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的`types`。返回值为二维数组，每个子数组代表一组允许的文件类型。开发者应 在构建文件选择器时使用该返回值设置文件类型过滤规则，确保用户只能选择符合前端要求的文件。该参数与getAcceptType和getMimeTypes的区别在于types支持更精细的文件类型控制，可按MIME类型或扩展名分组设置。

**起始版本：** 23

<!--Device-FileSelectorParam-getAcceptableFileTypes(): Array<Array<AcceptableFileType>>--><!--Device-FileSelectorParam-getAcceptableFileTypes(): Array<Array<AcceptableFileType>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Array&lt;[AcceptableFileType](arkts-arkweb-acceptablefiletype-i.md)&gt;&gt; | 返回文件类型信息，为二维数组结构，包含多组可选文件类型的详细信息。对应HTML option的types属性。 |

## getDefaultPath

```TypeScript
getDefaultPath(): string
```

获取文件选择器默认起始路径。对应HTML里[option](../../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的`startIn`。

**起始版本：** 23

<!--Device-FileSelectorParam-getDefaultPath(): string--><!--Device-FileSelectorParam-getDefaultPath(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回默认起始路径。 <br>当前端startIn设置为公共目录`downloads`、`pictures`时，要注意应分别转化为OpenHarmony系统下的`download`和`images`，请参考 [获取并使用公共目录](../../../file-management/request-dir-permission.md)。 |

## getDescriptions

```TypeScript
getDescriptions(): Array<string>
```

获取允许的各组文件类型的可选描述。对应HTML里[option](../../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的`description`。返回的描述数组与 getAcceptableFileTypes返回的文件类型组一一对应。开发者可在构建文件选择器时使用这些描述作为每组文件类型的显示文本，帮助用户理解可选择的文件类型。若前端未设置description，返回空字符串。

**起始版本：** 23

<!--Device-FileSelectorParam-getDescriptions(): Array<string>--><!--Device-FileSelectorParam-getDescriptions(): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回文件类型的描述字符串数组，包含各组文件类型的可选描述文本。 |

## getMimeTypes

```TypeScript
getMimeTypes(): Array<string>
```

获取文件MIME类型。

**起始版本：** 18

<!--Device-FileSelectorParam-getMimeTypes(): Array<string>--><!--Device-FileSelectorParam-getMimeTypes(): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 原样返回HTML input标签的accept属性的值，包含指定允许选择的文件的MIME类型和扩展名信息。 |

## getMode

```TypeScript
getMode(): FileSelectorMode
```

获取文件选择器的模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-getMode(): FileSelectorMode--><!--Device-FileSelectorParam-getMode(): FileSelectorMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileSelectorMode](arkts-arkweb-fileselectormode-e.md) | 返回文件选择器的模式。 |

## getSuggestedName

```TypeScript
getSuggestedName(): string
```

获取建议选择的文件名。对应HTML里[option](../../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的`suggestedName`。若前端未设置suggestedName， 返回空字符串。开发者可在构建文件选择器时使用该返回值作为默认文件名，与[getDefaultPath](#getdefaultpath)配合使用可预设完整的文件路径和名称。

**起始版本：** 23

<!--Device-FileSelectorParam-getSuggestedName(): string--><!--Device-FileSelectorParam-getSuggestedName(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回建议选择的文件名字符串，表示建议用于文件选择器的默认文件名。 |

## getTitle

```TypeScript
getTitle(): string
```

获取文件选择器标题。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-getTitle(): string--><!--Device-FileSelectorParam-getTitle(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回文件选择器标题字符串，表示当前文件选择器在界面上显示的标题文本。 |

## isAcceptAllOptionExcluded

```TypeScript
isAcceptAllOptionExcluded(): boolean
```

获取文件选择器是否排除选项（\*\/\*），即所有文件。对应HTML里[option](../../../web/web-file-upload.md#自定义处理js接口拉起的文件请求)中的 `excludeAcceptAllOption`。

**起始版本：** 23

<!--Device-FileSelectorParam-isAcceptAllOptionExcluded(): boolean--><!--Device-FileSelectorParam-isAcceptAllOptionExcluded(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否排除“所有文件类型”选项。 <br>true表示排除（不包含“所有文件类型”选项），false表示包含（开发者应确保文件选择器中包含“所有文件类型”选项）。 |

## isCapture

```TypeScript
isCapture(): boolean
```

获取是否调用多媒体能力。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FileSelectorParam-isCapture(): boolean--><!--Device-FileSelectorParam-isCapture(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否调用多媒体能力。 <br>true表示需要调用摄像头或麦克风等多媒体设备来获取文件（如拍照或录音），false表示仅从存储设备中选择已有文件。对应HTML input标签的capture属性。 |

