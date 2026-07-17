# Web属性/事件

Defines the Web attribute functions.

**继承/实现关系：** WebAttribute extends [CommonMethod<WebAttribute>](CommonMethod<WebAttribute>)

**起始版本：** 11

<!--Device-unnamed-declare class WebAttribute extends CommonMethod<WebAttribute>--><!--Device-unnamed-declare class WebAttribute extends CommonMethod<WebAttribute>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## aiSessionOptions

```TypeScript
aiSessionOptions(aiSessions: Array<AISessionEvent>)
```

Web组件的自定义AI会话配置。用于注册多个自定义AI会话。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-aiSessionOptions(aiSessions: Array<AISessionEvent>): WebAttribute--><!--Device-WebAttribute-aiSessionOptions(aiSessions: Array<AISessionEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aiSessions | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<AISessionEvent> | 是 | AISessionOptions对象的数组。 |

## allowWindowOpenMethod

```TypeScript
allowWindowOpenMethod(flag : boolean)
```

Whether the window can be open automatically through JavaScript.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-allowWindowOpenMethod(flag : boolean): WebAttribute--><!--Device-WebAttribute-allowWindowOpenMethod(flag : boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | boolean | 是 | If it is true, the window can be opened automatically through JavaScript. |

## backToTop

```TypeScript
backToTop(backToTop: boolean)
```

Set whether to enable the back-to-top feature for web component when the status bar is touched.

**起始版本：** 22

<!--Device-WebAttribute-backToTop(backToTop: boolean): WebAttribute--><!--Device-WebAttribute-backToTop(backToTop: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| backToTop | boolean | 是 | { |

## bindSelectionMenu

```TypeScript
bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType,
    options?: SelectionMenuOptionsExt)
```

绑定到选择菜单。

**起始版本：** 13

<!--Device-WebAttribute-bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType,
    options?: SelectionMenuOptionsExt): WebAttribute--><!--Device-WebAttribute-bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType,
    options?: SelectionMenuOptionsExt): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementType | [WebElementType](arkts-arkweb-web-webelementtype-e.md) | 是 | 表示选择菜单的类型。 |
| content | [CustomBuilder](../../apis-arkui/arkts-components/arkts-arkui-custombuilder-t.md) | 是 | 表示选择菜单的内容。 |
| responseType | [WebResponseType](arkts-arkweb-web-webresponsetype-e.md) | 是 | 表示选择菜单的响应类型。 |
| options | [SelectionMenuOptionsExt](arkts-arkweb-web-selectionmenuoptionsext-i.md) | 否 | 表示选择菜单的配置项。 |

## blankScreenDetectionConfig

```TypeScript
blankScreenDetectionConfig(detectConfig: BlankScreenDetectionConfig)
```

设置白屏检测的策略配置，如使能开关、检测时间和检测策略等。当属性没有显式调用时，默认关闭白屏检测。

> **说明：**  
>  
> - 根据detectConfig的配置，在网页加载后检测到白屏或者近似白屏现象，可触发回调  
> [onDetectedBlankScreen](web:WebAttribute.onDetectedBlankScreen)。  
>  
> - 设置后下次导航生效。  
>  
> - 当用户与网页发生交互后，不再会继续检查是否白屏。  
>  
> - 不支持layoutMode为WebLayoutMode.FIT_CONTENT的场景。

**起始版本：** 22

<!--Device-WebAttribute-blankScreenDetectionConfig(detectConfig: BlankScreenDetectionConfig): WebAttribute--><!--Device-WebAttribute-blankScreenDetectionConfig(detectConfig: BlankScreenDetectionConfig): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detectConfig | [BlankScreenDetectionConfig](arkts-arkweb-web-blankscreendetectionconfig-i.md) | 是 | 白屏检测的策略配置。 |

## blockNetwork

```TypeScript
blockNetwork(block: boolean)
```

设置Web组件是否阻止从网络加载资源。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-blockNetwork(block: boolean): WebAttribute--><!--Device-WebAttribute-blockNetwork(block: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| block | boolean | 是 | { |

## blurOnKeyboardHideMode

```TypeScript
blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode)
```

Sets the blur on for elements on webview when soft keyboard is hidden manually.

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode): WebAttribute--><!--Device-WebAttribute-blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [BlurOnKeyboardHideMode](arkts-arkweb-web-bluronkeyboardhidemode-e.md) | 是 | Default value is SILENT. Set BLUR to enable the blur on keyboard hide mode, which can be {@link BlurOnKeyboardHideMode}. |

## bypassVsyncCondition

```TypeScript
bypassVsyncCondition(condition: WebBypassVsyncCondition)
```

当开发者调用scrollBy接口进行页面滚动时，可以通过bypassVsyncCondition接口设置渲染流程跳过vsync（垂直同步）调度，直接触发绘制。该属性没有显式调用时，默认不跳过vsync调度。

**起始版本：** 20

<!--Device-WebAttribute-bypassVsyncCondition(condition: WebBypassVsyncCondition): WebAttribute--><!--Device-WebAttribute-bypassVsyncCondition(condition: WebBypassVsyncCondition): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | [WebBypassVsyncCondition](arkts-arkweb-web-webbypassvsynccondition-e.md) | 是 | 触发渲染流程跳过vsync调度的条件。 <br> 传入undefined或null时为NONE。 |

## cacheMode

```TypeScript
cacheMode(cacheMode: CacheMode)
```

设置缓存模式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-cacheMode(cacheMode: CacheMode): WebAttribute--><!--Device-WebAttribute-cacheMode(cacheMode: CacheMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cacheMode | [CacheMode](arkts-arkweb-web-cachemode-e.md) | 是 | 要设置的缓存模式。 |

## copyOptions

```TypeScript
copyOptions(value: CopyOptions)
```

调用以设置复制选项

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-copyOptions(value: CopyOptions): WebAttribute--><!--Device-WebAttribute-copyOptions(value: CopyOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CopyOptions](../../apis-arkui/arkts-apis/arkts-arkui-enums-copyoptions-e.md) | 是 | 复制选项。 |

## darkMode

```TypeScript
darkMode(mode: WebDarkMode)
```

设置Web深色模式。当属性没有显式调用时，默认Web深色模式关闭。

当深色模式开启时，Web将启用媒体查询prefers-color-scheme中网页所定义的深色样式，若网页未定义深色样式，则保持原状。如需开启强制深色模式，建议配合[forceDarkAccess](WebAttribute.forceDarkAccess)使用。深色模式具体用法可参考[Web深色模式适配](../../../../web/web-set-dark-mode.md)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-darkMode(mode: WebDarkMode): WebAttribute--><!--Device-WebAttribute-darkMode(mode: WebDarkMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebDarkMode](arkts-arkweb-web-webdarkmode-e.md) | 是 | 设置Web的深色模式为关闭、开启或跟随系统。<br>传入null或undefined时为`WebDarkMode.Off`。 |

## dataDetectorConfig

```TypeScript
dataDetectorConfig(config: TextDataDetectorConfig)
```

实体识词配置

**起始版本：** 20

<!--Device-WebAttribute-dataDetectorConfig(config: TextDataDetectorConfig): WebAttribute--><!--Device-WebAttribute-dataDetectorConfig(config: TextDataDetectorConfig): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [TextDataDetectorConfig](../../apis-arkui/arkts-apis/arkts-arkui-text-common-textdatadetectorconfig-i.md) | 是 | 实体识词配置 |

## databaseAccess

```TypeScript
databaseAccess(databaseAccess: boolean)
```

Sets whether the Web access the database.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-databaseAccess(databaseAccess: boolean): WebAttribute--><!--Device-WebAttribute-databaseAccess(databaseAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| databaseAccess | boolean | 是 | { |

## defaultFixedFontSize

```TypeScript
defaultFixedFontSize(size: number)
```

Sets the default font size for the web page.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-defaultFixedFontSize(size: number): WebAttribute--><!--Device-WebAttribute-defaultFixedFontSize(size: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置网页的默认等宽字体大小，单位px。<br>输入值的范围为[-2^31, 2^31-1]，实际渲染时超过72px的值按照72px进行渲染，低于1px的值按照1px进行渲染。<br  ><br>传入null或undefined时为13。 |

## defaultFontSize

```TypeScript
defaultFontSize(size: number)
```

Sets the default font size for the web page.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-defaultFontSize(size: number): WebAttribute--><!--Device-WebAttribute-defaultFontSize(size: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置网页的默认字体大小，单位px。<br>输入值的范围为[-2^31, 2^31-1]，实际渲染时超过72px的值按照72px进行渲染，低于1px的值按照1px进行渲染。<br>传入null或undefined时为16。 |

## defaultTextEncodingFormat

```TypeScript
defaultTextEncodingFormat(textEncodingFormat: string)
```

设置网页的默认字符编码。当属性没有显式调用时，网页的默认字符编码为"UTF-8"。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-defaultTextEncodingFormat(textEncodingFormat: string): WebAttribute--><!--Device-WebAttribute-defaultTextEncodingFormat(textEncodingFormat: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textEncodingFormat | string | 是 | 默认字符编码。<br>传入null或undefined时为"UTF-8"。 |

## domStorageAccess

```TypeScript
domStorageAccess(domStorageAccess: boolean)
```

Sets whether to enable the DOM Storage API permission.The default value is false.

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-domStorageAccess(domStorageAccess: boolean): WebAttribute--><!--Device-WebAttribute-domStorageAccess(domStorageAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domStorageAccess | boolean | 是 | {@code true} means enable the DOM Storage API permission in Web; {@code false} otherwise. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

设置自定义文本菜单。

**起始版本：** 12

<!--Device-WebAttribute-editMenuOptions(editMenu: EditMenuOptions): WebAttribute--><!--Device-WebAttribute-editMenuOptions(editMenu: EditMenuOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [EditMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-text-common-editmenuoptions-i.md) | 是 | 自定义文本菜单选项。菜单项数量、菜单内容尺寸和图标尺寸需与 ArkUI Menu 组件保持一致。菜单中仅支持使用系统提供的 id 枚举值（TextMenuItemId），包括剪切、复制、粘贴、全选、翻译、搜索以及网页中的部分 AI 菜单。onMenuItemClick 函数中的 textRange 参数在网页场景下无意义，传入值为 -1。 |

## enableAutoFill

```TypeScript
enableAutoFill(value: boolean)
```

设置是否启用自动填充功能。

**起始版本：** 23

<!--Device-WebAttribute-enableAutoFill(value: boolean): WebAttribute--><!--Device-WebAttribute-enableAutoFill(value: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 表示是否启用自动填充的标识。默认值为 true。true：启用，false：禁用。 |

## enableDataDetector

```TypeScript
enableDataDetector(enable: boolean)
```

开启实体识词

**起始版本：** 20

<!--Device-WebAttribute-enableDataDetector(enable: boolean): WebAttribute--><!--Device-WebAttribute-enableDataDetector(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | true为开启实体识词，false关闭，默认值关闭 |

## enableDefaultContextMenu

```TypeScript
enableDefaultContextMenu(enable: boolean)
```

设置是否使能默认右键菜单

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-enableDefaultContextMenu(enable: boolean): WebAttribute--><!--Device-WebAttribute-enableDefaultContextMenu(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | {@code true} means the Web enable the default right-click context menu,{@code false} otherwise.The default value is false. |

## enableDrag

```TypeScript
enableDrag(value: boolean)
```

启用或禁用此组件的拖动。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-enableDrag(value: boolean): WebAttribute--><!--Device-WebAttribute-enableDrag(value: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | {@code true}启用拖动，{@code false}禁用拖动。默认值为true。 |

## enableFollowSystemFontWeight

```TypeScript
enableFollowSystemFontWeight(follow: boolean)
```

设置Web组件是否开启字重跟随系统设置变化。当属性没有显式调用时，Web组件默认开启字重跟随系统设置变化。

> **说明：**  
>  
> 目前该能力只支持前端文本元素跟随变化，暂不支持canvas元素、内嵌docx和pdf格式中的文本跟随变化。

**起始版本：** 18

<!--Device-WebAttribute-enableFollowSystemFontWeight(follow: boolean): WebAttribute--><!--Device-WebAttribute-enableFollowSystemFontWeight(follow: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| follow | boolean | 是 | 设置Web组件是否开启字重跟随系统设置变化。<br>true表示字重跟随系统设置中的字体粗细变化，系统设置改变时字重跟随变化。false表示字重不再跟随系统设置中的字体粗细变化，系统设置改变时维持当前字重不变。<br>传入undefined或null时为true。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enabled: boolean)
```

启用或禁用触觉反馈。

**起始版本：** 13

<!--Device-WebAttribute-enableHapticFeedback(enabled: boolean): WebAttribute--><!--Device-WebAttribute-enableHapticFeedback(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 默认值为 true，设置为 false 可禁用触觉反馈。 |

## enableImageAnalyzer

```TypeScript
enableImageAnalyzer(enable: boolean)
```

设置 Web 组件支持 AI 图像识别能力。

**起始版本：** 23

<!--Device-WebAttribute-enableImageAnalyzer(enable: boolean): WebAttribute--><!--Device-WebAttribute-enableImageAnalyzer(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | {@code true} 表示启用 Web AI 图像识别能力，{@code false} 表示禁用。默认值为 true。 |

## enableNativeEmbedMode

```TypeScript
enableNativeEmbedMode(enabled: boolean)
```

Sets the enable native embed mode for web.

<p><strong>API Note</strong>:<strong>Performance Note</strong>:<p>For details about how to rendering native components on the Web using same-layer rendering,see [Rendering Native Components on the Web Using Same-Layer Rendering](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-render-web-using-same-layer-render)</p>

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-enableNativeEmbedMode(enabled: boolean): WebAttribute--><!--Device-WebAttribute-enableNativeEmbedMode(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Whether to enable the same-layer rendering feature.The value true means to enable the same-layer rendering feature, and false means the opposite. |

## enableNativeMediaPlayer

```TypeScript
enableNativeMediaPlayer(config: NativeMediaPlayerConfig)
```

开启[应用接管网页媒体播放功能](../../../../web/app-takeovers-web-media.md)。当属性没有显式调用时，默认不开启接管网页媒体播放功能。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-enableNativeMediaPlayer(config: NativeMediaPlayerConfig): WebAttribute--><!--Device-WebAttribute-enableNativeMediaPlayer(config: NativeMediaPlayerConfig): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [NativeMediaPlayerConfig](arkts-arkweb-web-nativemediaplayerconfig-i.md) | 是 | enable: 是否开启该功能。<br/> shouldOverlay: 该功能开启后， 应用接管网页视频的播放器画面是否覆盖网页内容。<br  >传入undefined或null时为`{enable: false, shouldOverlay: false}`。 |

## enableScrollDirectionalLock

```TypeScript
enableScrollDirectionalLock(value: boolean, type: ScrollDirectionalLockType)
```

在WebView组件中启用或禁用滚动手势的方向锁定。

当启用方向锁定时，滚动轴将根据初始滑动向量方向。此行为有助于防止意外的滚动方向更改在触摸交互过程中，特别是在嵌套滚动场景中。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-enableScrollDirectionalLock(value: boolean, type: ScrollDirectionalLockType): WebAttribute--><!--Device-WebAttribute-enableScrollDirectionalLock(value: boolean, type: ScrollDirectionalLockType): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否使能定向锁定。  - `true`：为对应的类型类别启用方向锁定。  - `false`：禁用对应类型类别的方向锁定。 |
| type | [ScrollDirectionalLockType](arkts-arkweb-web-scrolldirectionallocktype-e.md) | 是 | 指定方向锁的应用场景。 |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean)
```

设置是否启用文本选择的AI菜单功能，启用后可识别选区中的邮件、电话、网址、日期、地址等，并在文本选择菜单中展示对应的AI菜单项。默认启用AI菜单功能。

AI菜单功能启用时，在网页中选中文本后，文本选择菜单能够展示对应的AI菜单项，包括[TextMenuItemId](../../apis-arkui/arkts-apis/arkts-arkui-text-common-textmenuitemid-c.md)中的url（打开链接）、email（新建邮件）、phoneNumber（呼叫）、address（导航前往）、dateTime（新建日程）。

AI菜单生效时，需在选中范围内，包括一个完整的AI实体，才能展示对应的选项。该菜单项与[TextMenuItemId](../../apis-arkui/arkts-apis/arkts-arkui-text-common-textmenuitemid-c.md)中的askAI菜单项不同时出现。

示例使用场景详见[使用Web组件的智能分词能力](../../../../web/web-data-detector.md)。

> **说明：**  
>  
> 当enableSelectedDataDetector未配置或设置为true时，将遵循  
> [dataDetectorConfig](../../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#datadetectorconfig20)  
> 中types的配置；若  
> [dataDetectorConfig](../../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#datadetectorconfig20)  
> 也未配置，则默认识别所有类型。  
>  
> 当enableSelectedDataDetector设置为false时，不激活实体文本选择AI菜单项。

**起始版本：** 22

<!--Device-WebAttribute-enableSelectedDataDetector(enable: boolean): WebAttribute--><!--Device-WebAttribute-enableSelectedDataDetector(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用Web文本识别，true表示启用，false表示不启用。<br>传入undefined或null时属性重置为默认值。 |

## enableWebAVSession

```TypeScript
enableWebAVSession(enabled: boolean)
```

设置是否对接播控

**起始版本：** 18

<!--Device-WebAttribute-enableWebAVSession(enabled: boolean): WebAttribute--><!--Device-WebAttribute-enableWebAVSession(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | true为开启，false为关闭 |

## fileAccess

```TypeScript
fileAccess(fileAccess: boolean)
```

Sets whether to enable access to the file system in the application.This setting dose not affect the access to the files specified though $rawfile(filepath/filename).<p><strong>API Note</strong>:<br>fileAccess is disabled by default since API version 12.When fileAccess is set to false, files in the read-only /data/storage/el1/bundle/entry/resources/resfile<br>directory can still be accessed through the file protocol.</p>

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-fileAccess(fileAccess: boolean): WebAttribute--><!--Device-WebAttribute-fileAccess(fileAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileAccess | boolean | 是 | {@code true} means enable local file system access in Web; {@code false} otherwise.The default value is false. |

## forceDarkAccess

```TypeScript
forceDarkAccess(access: boolean)
```

设置网页是否开启强制深色模式。该属性仅在[darkMode](WebAttribute.darkMode)开启深色模式时生效。当属性没有显式调用时，默认网页不开启强制深色模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-forceDarkAccess(access: boolean): WebAttribute--><!--Device-WebAttribute-forceDarkAccess(access: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access | boolean | 是 | 设置网页是否开启强制深色模式。<br>true表示设置网页开启强制深色模式，false表示设置网页不开启强制深色模式。<br>传入null或undefined时为false。 |

## forceDisplayScrollBar

```TypeScript
forceDisplayScrollBar(enabled: boolean)
```

是否强制显示滚动条。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-forceDisplayScrollBar(enabled: boolean): WebAttribute--><!--Device-WebAttribute-forceDisplayScrollBar(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | { |

## forceEnableZoom

```TypeScript
forceEnableZoom(enable: boolean)
```

设置是否遵守网页中 <meta name="viewport"> 标签设置的缩放限制。

**起始版本：** 21

<!--Device-WebAttribute-forceEnableZoom(enable: boolean): WebAttribute--><!--Device-WebAttribute-forceEnableZoom(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | { |

## geolocationAccess

```TypeScript
geolocationAccess(geolocationAccess: boolean)
```

Sets whether to allow access to geographical locations.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-geolocationAccess(geolocationAccess: boolean): WebAttribute--><!--Device-WebAttribute-geolocationAccess(geolocationAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| geolocationAccess | boolean | 是 | Whether to enable geolocation access. {@code true} means the Web allows access to geographical locations; {@code false} means the Web disallows access to geographical locations. The default value is true. |

## gestureFocusMode

```TypeScript
gestureFocusMode(mode: GestureFocusMode)
```

设置手势获焦的模式。当用户使用不同手势操作web时，根据所设置的模式决定是否获焦和获焦时机。默认值DEFAULT，所有手势均会在touchDown时获焦。

**起始版本：** 20

<!--Device-WebAttribute-gestureFocusMode(mode: GestureFocusMode): WebAttribute--><!--Device-WebAttribute-gestureFocusMode(mode: GestureFocusMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [GestureFocusMode](arkts-arkweb-web-gesturefocusmode-e.md) | 是 | The gesture focus mode, which can be {@link GestureFocusMode}.The default value is FocusMode.DEFAULT. |

## horizontalScrollBarAccess

```TypeScript
horizontalScrollBarAccess(horizontalScrollBar: boolean)
```

设置是否绘制水平滚动条。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-horizontalScrollBarAccess(horizontalScrollBar: boolean): WebAttribute--><!--Device-WebAttribute-horizontalScrollBarAccess(horizontalScrollBar: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontalScrollBar | boolean | 是 | 若需要绘制水平滚动条则为 true。 |

## imageAccess

```TypeScript
imageAccess(imageAccess: boolean)
```

设置是否允许自动加载图片资源。当属性没有显式调用时，允许自动加载图片资源。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-imageAccess(imageAccess: boolean): WebAttribute--><!--Device-WebAttribute-imageAccess(imageAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageAccess | boolean | 是 | 设置是否允许自动加载图片资源。<br>true表示设置允许自动加载图片资源，false表示设置不允许自动加载图片资源。<br>传入undefined或null时为false。 |

## initialScale

```TypeScript
initialScale(percent: number)
```

设置网页的初始缩放比例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-initialScale(percent: number): WebAttribute--><!--Device-WebAttribute-initialScale(percent: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| percent | number | 是 | 网页初始缩放比例。 |

## javaScriptAccess

```TypeScript
javaScriptAccess(javaScriptAccess: boolean)
```

设置是否允许执行JavaScript脚本。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-javaScriptAccess(javaScriptAccess: boolean): WebAttribute--><!--Device-WebAttribute-javaScriptAccess(javaScriptAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| javaScriptAccess | boolean | 是 | {@code true} true表示允许执行JavaScript脚本，false表示不允许执行JavaScript脚本。默认值为true. |

## javaScriptOnDocumentEnd

```TypeScript
javaScriptOnDocumentEnd(scripts: Array<ScriptItem>)
```

Injects the JavaScripts script into the Web component. When the specified page or document has been loaded,the script is executed on any page whose source matches scriptRules.<p><strong>API NOTE</strong>:<br>The script runs before any Javascript code of the page, when the DOM tree has been loaded and rendered.The script is excuted in the lexicographic order, not the array order.You are not advised to use this API together with runJavaScriptOnDocumentEnd.<p>

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-javaScriptOnDocumentEnd(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-javaScriptOnDocumentEnd(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<ScriptItem> | 是 | The array of the JavaScripts to be injected. |

## javaScriptOnDocumentStart

```TypeScript
javaScriptOnDocumentStart(scripts: Array<ScriptItem>)
```

Injects the JavaScripts script into the Web component.When the specified page or document starts to be loaded, the script is executed on any page whose source matches scriptRules.<p><strong>API Note</strong>:<br>The script runs before any JavaScript code of the page, when the DOM tree may not have been loaded or rendered.The script is executed in the lexicographic order instead of array sequence.if the array sequemce is required, you are advised to use the runJavaScriptOnDocumentStart interface.You are not advised to use this API together with runJavaScriptOnDocumentStart.</p>

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-javaScriptOnDocumentStart(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-javaScriptOnDocumentStart(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<ScriptItem> | 是 | The array of the JavaScripts to be injected. |

## javaScriptProxy

```TypeScript
javaScriptProxy(javaScriptProxy: JavaScriptProxy)
```

Injects the JavaScript object into window and invoke the function in window.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-javaScriptProxy(javaScriptProxy: JavaScriptProxy): WebAttribute--><!--Device-WebAttribute-javaScriptProxy(javaScriptProxy: JavaScriptProxy): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| javaScriptProxy | [JavaScriptProxy](arkts-arkweb-web-javascriptproxy-i.md) | 是 | The ArkTs object in javaScriptProxy will be registered into this Web component,and the methods within the methodList of the injected ArkTs object declared in javaScriptProxy can be accessed by JavaScript.<br>**起始版本：** 12 |

## keyboardAppearance

```TypeScript
keyboardAppearance(mode: WebKeyboardAppearanceMode)
```

设置WebKeyboardAppearanceMode以决定软键盘的沉浸式模式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-keyboardAppearance(mode: WebKeyboardAppearanceMode): WebAttribute--><!--Device-WebAttribute-keyboardAppearance(mode: WebKeyboardAppearanceMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebKeyboardAppearanceMode](arkts-arkweb-web-webkeyboardappearancemode-e.md) | 是 | 此网站的WebKeyboardAppearanceMode。 |

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode(mode: WebKeyboardAvoidMode)
```

Set web avoidance keyboard mode. The default value is WebKeyboardAvoidMode.RESIZE_CONTENT.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-keyboardAvoidMode(mode: WebKeyboardAvoidMode): WebAttribute--><!--Device-WebAttribute-keyboardAvoidMode(mode: WebKeyboardAvoidMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebKeyboardAvoidMode](arkts-arkweb-web-webkeyboardavoidmode-e.md) | 是 | The web keyboard avoid mode, which can be {@link WebKeyboardAvoidMode}. |

## layoutMode

```TypeScript
layoutMode(mode: WebLayoutMode)
```

设置Web布局模式。当属性没有显式调用时，默认Web布局跟随系统模式。常见问题请参考[Web组件大小自适应页面内容布局](../../../../web/web-fit-content.md)。

> **说明：**  
>  
> 目前只支持两种Web布局模式，分别为Web布局跟随系统（`WebLayoutMode.NONE`）和Web组件高度基于前端页面高度的自适应网页布局（`WebLayoutMode.FIT_CONTENT`）。  
>  
> Web组件高度基于前端页面自适应布局有如下限制：  
>  
> - 如果Web组件宽或长度超过7680px，请在Web组件创建的时候指定`RenderMode.SYNC_RENDER`模式，否则会整个白屏。  
>  
> - Web组件创建后不支持动态切换layoutMode模式。  
>  
> - Web组件宽高规格：指定`RenderMode.ASYNC_RENDER`模式时，分别不超过7680px。  
>  
> - 频繁更改页面宽高会触发Web组件重新布局，影响体验。  
>  
> - 不支持瀑布流网页（下拉到底部加载更多）。  
>  
> - 不支持宽度自适应，仅支持高度自适应。  
>  
> - 由于高度自适应网页高度，您无法通过修改组件高度属性来修改组件高度。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-layoutMode(mode: WebLayoutMode): WebAttribute--><!--Device-WebAttribute-layoutMode(mode: WebLayoutMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebLayoutMode](arkts-arkweb-web-weblayoutmode-e.md) | 是 | 设置web布局模式，跟随系统或自适应布局。<br>传入null或undefined时为`WebLayoutMode.NONE` |

## mediaOptions

```TypeScript
mediaOptions(options: WebMediaOptions)
```

设置Web媒体播放的策略，其中包括：Web中的音频在重新获焦后能够自动续播的有效期、应用内多个Web实例的音频是否独占。当该属性未显式设置时，默认Web中的音频重新获焦后无法自动续播、应用内多个Web实例的音频是独占的。

> **说明：**  
>  
> - 同一Web实例中的多个音频均视为同一音频。  
>  
> - 该媒体播放策略将同时管控有声视频。  
>  
> - 建议为所有Web组件设置相同的[audioExclusive](arkts-arkweb-web-webmediaoptions-i.md)值。  
>  
> - 音视频互相打断在应用内和应用间生效，续播只在应用间生效。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-mediaOptions(options: WebMediaOptions): WebAttribute--><!--Device-WebAttribute-mediaOptions(options: WebMediaOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [WebMediaOptions](arkts-arkweb-web-webmediaoptions-i.md) | 是 | 设置Web的媒体策略。<br>属性参数更新后需重新播放音频方可生效。<br>传入undefined或null时为`{resumeInterval: 0,audioExclusive: true}` |

## mediaPlayGestureAccess

```TypeScript
mediaPlayGestureAccess(access: boolean)
```

设置有声视频的自动播放是否需要用户手动点击，静音视频播放不受该接口管控。当该属性未显式设置时，默认有声视频的自动播放需要用户手动点击。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-mediaPlayGestureAccess(access: boolean): WebAttribute--><!--Device-WebAttribute-mediaPlayGestureAccess(access: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access | boolean | 是 | 设置有声视频的自动播放是否需要用户手动点击。<br>true表示设置有声视频的自动播放需要用户手动点击，false表示设置有声视频的自动播放不需要用户手动点击，能自动播放。<br>传入undefined或null时为false。 |

## metaViewport

```TypeScript
metaViewport(enabled: boolean)
```

设置meta标签的viewport属性是否可用。当属性没有显式调用时，默认支持meta标签的viewport属性。

> **说明：**  
>  
> - 当前通过User-Agent中是否含有"Mobile"字段来判断是否开启前端HTML页面中meta标签的viewport属性。当User-Agent中不含有"Mobile"字段时，meta标签中viewport属性默认关闭  
> ，此时可通过显性设置metaViewport属性为true来覆盖关闭状态。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-metaViewport(enabled: boolean): WebAttribute--><!--Device-WebAttribute-metaViewport(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否支持meta标签的viewport属性。<br>true表示支持meta标签的viewport属性，将解析viewport属性，并根据viewport属性布局。<br>false表示不支持meta标签的viewport属性，将不解析viewport属性，进行默认布局。<br>传入null或undefined时为true。 |

## minFontSize

```TypeScript
minFontSize(size: number)
```

Sets the minimum font size for the web page.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-minFontSize(size: number): WebAttribute--><!--Device-WebAttribute-minFontSize(size: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置网页字体大小最小值，单位px。<br>输入值的范围为[-2^31, 2^31-1]，实际渲染时超过72px的值按照72px进行渲染，低于1px的值按照1px进行渲染。<br>传入null或undefined时为8。 |

## minLogicalFontSize

```TypeScript
minLogicalFontSize(size: number)
```

Sets the minimum logical font size for the web page.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-minLogicalFontSize(size: number): WebAttribute--><!--Device-WebAttribute-minLogicalFontSize(size: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置网页逻辑字体大小最小值，单位px。<br>输入值的范围为[-2^31, 2^31-1]，实际渲染时超过72px的值按照72px进行渲染，低于1px的值按照1px进行渲染。<br  >传入null或undefined时为18。 |

## mixedMode

```TypeScript
mixedMode(mixedMode: MixedMode)
```

设定当安全源尝试从非安全源加载资源时的行为。当属性没有显式调用时，默认值为MixedMode.None，即禁止安全源从非安全源加载内容。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-mixedMode(mixedMode: MixedMode): WebAttribute--><!--Device-WebAttribute-mixedMode(mixedMode: MixedMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mixedMode | [MixedMode](arkts-arkweb-web-mixedmode-e.md) | 是 | 要设置的混合内容模式。 |

## multiWindowAccess

```TypeScript
multiWindowAccess(multiWindow: boolean)
```

Set whether multiple windows are supported.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-multiWindowAccess(multiWindow: boolean): WebAttribute--><!--Device-WebAttribute-multiWindowAccess(multiWindow: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| multiWindow | boolean | 是 | True if it needs to be triggered manually by the user else false. |

## nativeEmbedOptions

```TypeScript
nativeEmbedOptions(options?: EmbedOptions)
```

设置同层渲染相关配置，该属性仅在[enableNativeEmbedMode](WebAttribute.enableNativeEmbedMode)开启时生效，不支持动态修改。当属性没有显式调用时，默认为`{supportDefaultIntrinsicSize: false}`。

**起始版本：** 16

<!--Device-WebAttribute-nativeEmbedOptions(options?: EmbedOptions): WebAttribute--><!--Device-WebAttribute-nativeEmbedOptions(options?: EmbedOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EmbedOptions](arkts-arkweb-web-embedoptions-i.md) | 否 | 同层渲染相关配置。<br>传入undefined或null时为`{supportDefaultIntrinsicSize: false}`。 |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions | NestedScrollOptionsExt)
```

调用以设置嵌套滚动选项。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-nestedScroll(value: NestedScrollOptions | NestedScrollOptionsExt): WebAttribute--><!--Device-WebAttribute-nestedScroll(value: NestedScrollOptions | NestedScrollOptionsExt): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | NestedScrollOptions \| NestedScrollOptionsExt | 是 | 嵌套滚动选项。<br>**起始版本：** 14 |

## onActivateContent

```TypeScript
onActivateContent(callback: Callback<void>)
```

设置绕过vsync的条件。如果条件匹配，则绘制不依赖于Vsync信号，直接绘制

**起始版本：** 20

<!--Device-WebAttribute-onActivateContent(callback: Callback<void>): WebAttribute--><!--Device-WebAttribute-onActivateContent(callback: Callback<void>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<void> | 是 | The triggered function when the web page is active for window.open called by other web component. |

## onAdsBlocked

```TypeScript
onAdsBlocked(callback: OnAdsBlockedCallback)
```

Called when received Ads blocked results.If blocked results exist at the end of page loading, the first call will be triggered.To avoid performance issues, subsequent results will be periodically reported through this api.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onAdsBlocked(callback: OnAdsBlockedCallback): WebAttribute--><!--Device-WebAttribute-onAdsBlocked(callback: OnAdsBlockedCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAdsBlockedCallback](arkts-arkweb-onadsblockedcallback-t.md) | 是 | The callback for OnAdsBlockedCallback. |

## onAlert

```TypeScript
onAlert(callback: Callback<OnAlertEvent, boolean>)
```

Web 想要显示 JavaScript alert() 弹窗时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onAlert(callback: Callback<OnAlertEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onAlert(callback: Callback<OnAlertEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnAlertEvent, boolean> | 是 | 网页中调用 alert() 显示警告弹窗时使用的回调函数。[since 8 - 11] |

## onAudioStateChanged

```TypeScript
onAudioStateChanged(callback: Callback<OnAudioStateChangedEvent>)
```

设置网页上的音频播放状态发生改变时的回调函数。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onAudioStateChanged(callback: Callback<OnAudioStateChangedEvent>): WebAttribute--><!--Device-WebAttribute-onAudioStateChanged(callback: Callback<OnAudioStateChangedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnAudioStateChangedEvent> | 是 | 网页上的音频播放状态发生改变时触发。在API 12之前，使用 { function } 作为参数类型。 |

## onBeforeUnload

```TypeScript
onBeforeUnload(callback: Callback<OnBeforeUnloadEvent, boolean>)
```

Triggered when the Web wants to confirm navigation from JavaScript onbeforeunload.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onBeforeUnload(callback: Callback<OnBeforeUnloadEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onBeforeUnload(callback: Callback<OnBeforeUnloadEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnBeforeUnloadEvent, boolean> | 是 | The triggered function when the web page wants to confirm navigation from JavaScript |

## onCameraCaptureStateChange

```TypeScript
onCameraCaptureStateChange(callback: OnCameraCaptureStateChangeCallback)
```

通知用户当前网页的摄像头状态，摄像头有三个状态，无状态（None），捕获中（Active），暂停中（Paused）。使用callback异步回调。

可以通过startCamera，stopCamera，closeCamera这三个接口来切换摄像头的状态。这三个接口分别对应开启，暂停，停止摄像头功能。示例使用场景详见[startCamera](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#startcamera-1)。

> **说明：**  
>  
> 当前网页正在使用摄像头时，返回在捕获中状态。  
>  
> 当前网页暂停使用摄像头时，返回暂停中状态。  
>  
> 当前网页完全没有使用摄像头时，返回无状态。

**起始版本：** 23

<!--Device-WebAttribute-onCameraCaptureStateChange(callback: OnCameraCaptureStateChangeCallback): WebAttribute--><!--Device-WebAttribute-onCameraCaptureStateChange(callback: OnCameraCaptureStateChangeCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnCameraCaptureStateChangeCallback](arkts-arkweb-oncameracapturestatechangecallback-t.md) | 是 | 回调函数。当摄像头捕获状态改变时触发该回调，返回原来的状态和改变后的状态。 |

## onClientAuthenticationRequest

```TypeScript
onClientAuthenticationRequest(callback: Callback<OnClientAuthenticationEvent>)
```

通知用户收到SSL客户端证书请求事件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onClientAuthenticationRequest(callback: Callback<OnClientAuthenticationEvent>): WebAttribute--><!--Device-WebAttribute-onClientAuthenticationRequest(callback: Callback<OnClientAuthenticationEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnClientAuthenticationEvent> | 是 | The triggered callback when needs ssl client certificate from the user. [since 9 - 11] |

## onConfirm

```TypeScript
onConfirm(callback: Callback<OnConfirmEvent, boolean>)
```

网页需要显示 JavaScript confirm() 确认弹窗时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onConfirm(callback: Callback<OnConfirmEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onConfirm(callback: Callback<OnConfirmEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnConfirmEvent, boolean> | 是 | 网页调用 confirm() 时触发的回调函数。[since 8 - 11] |

## onConsole

```TypeScript
onConsole(callback: Callback<OnConsoleEvent, boolean>)
```

通知宿主应用JavaScript console消息。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onConsole(callback: Callback<OnConsoleEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onConsole(callback: Callback<OnConsoleEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnConsoleEvent, boolean> | 是 | The triggered function when the web page receives a JavaScript console |

## onContextMenuHide

```TypeScript
onContextMenuHide(callback: OnContextMenuHideCallback)
```

调用时触发，允许自定义隐藏上下文菜单。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onContextMenuHide(callback: OnContextMenuHideCallback): WebAttribute--><!--Device-WebAttribute-onContextMenuHide(callback: OnContextMenuHideCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnContextMenuHideCallback](arkts-arkweb-oncontextmenuhidecallback-t.md) | 是 | 调用以允许自定义隐藏上下文菜单时触发的函数。 |

## onContextMenuShow

```TypeScript
onContextMenuShow(callback: Callback<OnContextMenuShowEvent, boolean>)
```

调用时触发，允许自定义显示上下文菜单。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onContextMenuShow(callback: Callback<OnContextMenuShowEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onContextMenuShow(callback: Callback<OnContextMenuShowEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnContextMenuShowEvent, boolean> | 是 | 调用以允许自定义显示上下文菜单时触发的回调。[9 - 11 版本起支持] |

## onControllerAttached

```TypeScript
onControllerAttached(callback: () => void)
```

Triggered when The controller is bound to the web component, this controller must be a WebviewController.This callback can not use the interface about manipulating web pages.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onControllerAttached(callback: () => void): WebAttribute--><!--Device-WebAttribute-onControllerAttached(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () => void | 是 | The triggered callback when web controller initialization success. |

## onDataResubmitted

```TypeScript
onDataResubmitted(callback: Callback<OnDataResubmittedEvent>)
```

Triggered when the form could be resubmitted.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onDataResubmitted(callback: Callback<OnDataResubmittedEvent>): WebAttribute--><!--Device-WebAttribute-onDataResubmitted(callback: Callback<OnDataResubmittedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnDataResubmittedEvent> | 是 | The triggered callback to decision whether resend form data or not. |

## onDetectedBlankScreen

```TypeScript
onDetectedBlankScreen(callback: OnDetectBlankScreenCallback)
```

Web组件检测到白屏时触发此回调。

> **说明：**  
>  
> - 需配合[blankScreenDetectionConfig](web:WebAttribute.blankScreenDetectionConfig)使用。否则，默认关闭白屏检测功能，不会返回检测到白屏时的回  
> 调函数。

**起始版本：** 22

<!--Device-WebAttribute-onDetectedBlankScreen(callback: OnDetectBlankScreenCallback): WebAttribute--><!--Device-WebAttribute-onDetectedBlankScreen(callback: OnDetectBlankScreenCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnDetectBlankScreenCallback](arkts-arkweb-ondetectblankscreencallback-t.md) | 是 | Web组件检测到白屏时的回调函数。 |

## onDownloadStart

```TypeScript
onDownloadStart(callback: Callback<OnDownloadStartEvent>)
```

通知主应用开始下载一个文件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onDownloadStart(callback: Callback<OnDownloadStartEvent>): WebAttribute--><!--Device-WebAttribute-onDownloadStart(callback: Callback<OnDownloadStartEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnDownloadStartEvent> | 是 | The triggered function when starting to download. [since 8 - 11] |

## onErrorReceive

```TypeScript
onErrorReceive(callback: Callback<OnErrorReceiveEvent>)
```

网页加载遇到错误时触发该回调。主资源与子资源出错都会回调该接口，可以通过[isMainFrame](arkts-arkweb-web-webresourcerequest-c.md#ismainframe-1)来判断是否是主资源报错。出于性能考虑，建议此回调中尽量执行简单逻辑。在无网络的情况下，触发此回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onErrorReceive(callback: Callback<OnErrorReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onErrorReceive(callback: Callback<OnErrorReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnErrorReceiveEvent> | 是 | The triggered function when the web page receives a web resource loading |

## onFaviconReceived

```TypeScript
onFaviconReceived(callback: Callback<OnFaviconReceivedEvent>)
```

设置应用为当前页面接收到新的favicon时的回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFaviconReceived(callback: Callback<OnFaviconReceivedEvent>): WebAttribute--><!--Device-WebAttribute-onFaviconReceived(callback: Callback<OnFaviconReceivedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnFaviconReceivedEvent> | 是 | The triggered callback when the application receive a new favicon for the |

## onFileSelectorShow

```TypeScript
onFileSelectorShow(callback: (event?: { callback: Function, fileSelector: object }) => void)
```

Triggered when the file selector shows.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onShowFileSelector

<!--Device-WebAttribute-onFileSelectorShow(callback: (event?: { callback: Function, fileSelector: object }) => void): WebAttribute--><!--Device-WebAttribute-onFileSelectorShow(callback: (event?: { callback: Function, fileSelector: object }) => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: { callback: Function, fileSelector: object }) => void | 是 | The triggered when the file selector shows. |

## onFirstContentfulPaint

```TypeScript
onFirstContentfulPaint(callback: Callback<OnFirstContentfulPaintEvent>)
```

设置网页首次内容绘制回调函数。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFirstContentfulPaint(callback: Callback<OnFirstContentfulPaintEvent>): WebAttribute--><!--Device-WebAttribute-onFirstContentfulPaint(callback: Callback<OnFirstContentfulPaintEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnFirstContentfulPaintEvent> | 是 | 网页首次内容绘制回调函数。<br>**起始版本：** 12 |

## onFirstMeaningfulPaint

```TypeScript
onFirstMeaningfulPaint(callback: OnFirstMeaningfulPaintCallback)
```

设置网页绘制页面主要内容回调函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFirstMeaningfulPaint(callback: OnFirstMeaningfulPaintCallback): WebAttribute--><!--Device-WebAttribute-onFirstMeaningfulPaint(callback: OnFirstMeaningfulPaintCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnFirstMeaningfulPaintCallback](arkts-arkweb-onfirstmeaningfulpaintcallback-t.md) | 是 | 网页绘制页面主要内容度量信息的回调。 |

## onFirstScreenPaint

```TypeScript
onFirstScreenPaint(callback: OnFirstScreenPaintCallback)
```

网页首屏渲染结束时触发此回调，使用callback异步回调。

> **说明：**  
>  
> - 首屏渲染（First Screen Paint，FSP），记录了视口内图片、文本或视频元素完成渲染所需的时间，是衡量页面首次加载到渲染完成的核心性能指标。当一定时间内视口内没有可见元素超出历史绘制区域时，将视口内元素绘制的  
> 历史最大的时刻视为首屏渲染完成时刻。  
>  
> - 接口在首屏绘制完成后，需要等待一定时间没有新的渲染信息需要处理后，才会上报回调。接口回调时刻和首屏渲染完成时刻不同。  
>  
> - 渲染未完成时，若用户输入或滚动页面，将会立即上报回调函数。  
>  
> - 该接口适用于在即时加载场景下获取首屏渲染时间，在预加载或预渲染场景下使用无法达到预期。

**起始版本：** 23

<!--Device-WebAttribute-onFirstScreenPaint(callback: OnFirstScreenPaintCallback): WebAttribute--><!--Device-WebAttribute-onFirstScreenPaint(callback: OnFirstScreenPaintCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnFirstScreenPaintCallback](arkts-arkweb-onfirstscreenpaintcallback-t.md) | 是 | 回调函数，设置Web组件的检测到首屏渲染。 |

## onFullScreenEnter

```TypeScript
onFullScreenEnter(callback: OnFullScreenEnterCallback)
```

通知开发者Web组件进入全屏模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFullScreenEnter(callback: OnFullScreenEnterCallback): WebAttribute--><!--Device-WebAttribute-onFullScreenEnter(callback: OnFullScreenEnterCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnFullScreenEnterCallback](arkts-arkweb-onfullscreenentercallback-t.md) | 是 | Web组件进入全屏时的回调信息。在API 12之前，使用 { function } 作为参数类型。 |

## onFullScreenExit

```TypeScript
onFullScreenExit(callback: () => void)
```

通知开发者Web组件退出全屏模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFullScreenExit(callback: () => void): WebAttribute--><!--Device-WebAttribute-onFullScreenExit(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () => void | 是 | 退出全屏模式时的回调函数。 |

## onGeolocationHide

```TypeScript
onGeolocationHide(callback: () => void)
```

Triggered when requesting to hide the geolocation.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onGeolocationHide(callback: () => void): WebAttribute--><!--Device-WebAttribute-onGeolocationHide(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () => void | 是 | Callback invoked when the request for obtaining geolocation information has been |

## onGeolocationShow

```TypeScript
onGeolocationShow(callback: Callback<OnGeolocationShowEvent>)
```

Triggered when requesting to show the geolocation permission.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onGeolocationShow(callback: Callback<OnGeolocationShowEvent>): WebAttribute--><!--Device-WebAttribute-onGeolocationShow(callback: Callback<OnGeolocationShowEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnGeolocationShowEvent> | 是 | Callback invoked when a request to obtain the geolocation information is received.<br>**起始版本：** 12 |

## onHttpAuthRequest

```TypeScript
onHttpAuthRequest(callback: Callback<OnHttpAuthRequestEvent, boolean>)
```

通知收到http auth认证请求。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onHttpAuthRequest(callback: Callback<OnHttpAuthRequestEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onHttpAuthRequest(callback: Callback<OnHttpAuthRequestEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnHttpAuthRequestEvent, boolean> | 是 | The triggered when the browser needs credentials from the user. [since 9 - 11] |

## onHttpErrorReceive

```TypeScript
onHttpErrorReceive(callback: Callback<OnHttpErrorReceiveEvent>)
```

网页加载资源遇到的HTTP错误（响应码>=400）时触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onHttpErrorReceive(callback: Callback<OnHttpErrorReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onHttpErrorReceive(callback: Callback<OnHttpErrorReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnHttpErrorReceiveEvent> | 是 | The triggered function when the web page receives a web resource loading HTTP |

## onInputmethodAttached

```TypeScript
onInputmethodAttached(callback: OnInputmethodAttachedCallback)
```

当inputmethod被附加到IMF时，会触发回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-onInputmethodAttached(callback: OnInputmethodAttachedCallback): WebAttribute--><!--Device-WebAttribute-onInputmethodAttached(callback: OnInputmethodAttachedCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnInputmethodAttachedCallback](arkts-arkweb-oninputmethodattachedcallback-t.md) | 是 | 当inputmethod被附加到IMF时触发的回调。 |

## onIntelligentTrackingPreventionResult

```TypeScript
onIntelligentTrackingPreventionResult(callback: OnIntelligentTrackingPreventionCallback)
```

Called when tracker's cookie is prevented.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onIntelligentTrackingPreventionResult(callback: OnIntelligentTrackingPreventionCallback): WebAttribute--><!--Device-WebAttribute-onIntelligentTrackingPreventionResult(callback: OnIntelligentTrackingPreventionCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnIntelligentTrackingPreventionCallback](arkts-arkweb-onintelligenttrackingpreventioncallback-t.md) | 是 | Callback triggered when tracker's cookie is prevented. |

## onInterceptKeyEvent

```TypeScript
onInterceptKeyEvent(callback: (event: KeyEvent) => boolean)
```

Key events notify the application before the WebView consumes them.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onInterceptKeyEvent(callback: (event: KeyEvent) => boolean): WebAttribute--><!--Device-WebAttribute-onInterceptKeyEvent(callback: (event: KeyEvent) => boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event: KeyEvent) => boolean | 是 | Key event info. |

## onInterceptKeyboardAttach

```TypeScript
onInterceptKeyboardAttach(callback: WebKeyboardCallback)
```

When the soft keyboard is about to be displayed on the current Web,it gives the application the opportunity to intercept the system keyboard attachment.The application can return the keyboard options to control the web to pull up the soft keyboard of the different type.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onInterceptKeyboardAttach(callback: WebKeyboardCallback): WebAttribute--><!--Device-WebAttribute-onInterceptKeyboardAttach(callback: WebKeyboardCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [WebKeyboardCallback](arkts-arkweb-webkeyboardcallback-t.md) | 是 | The callback for onInterceptKeyboardAttach. |

## onInterceptRequest

```TypeScript
onInterceptRequest(callback: Callback<OnInterceptRequestEvent, WebResourceResponse>)
```

当Web组件加载URL之前触发该回调，用于拦截URL并返回响应数据。`onInterceptRequest`可拦截所有跳转请求并返回响应数据，但无法访问POST请求体（Body）内容。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onInterceptRequest(callback: Callback<OnInterceptRequestEvent, WebResourceResponse>): WebAttribute--><!--Device-WebAttribute-onInterceptRequest(callback: Callback<OnInterceptRequestEvent, WebResourceResponse>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnInterceptRequestEvent, WebResourceResponse> | 是 | The triggered callback when the resources loading is intercepted. [since 9 - 11] |

## onLargestContentfulPaint

```TypeScript
onLargestContentfulPaint(callback: OnLargestContentfulPaintCallback)
```

设置网页绘制页面最大内容回调函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onLargestContentfulPaint(callback: OnLargestContentfulPaintCallback): WebAttribute--><!--Device-WebAttribute-onLargestContentfulPaint(callback: OnLargestContentfulPaintCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnLargestContentfulPaintCallback](arkts-arkweb-onlargestcontentfulpaintcallback-t.md) | 是 | 网页绘制页面最大内容度量信息的回调。 |

## onLoadFinished

```TypeScript
onLoadFinished(callback: Callback<OnLoadFinishedEvent>)
```

通知宿主应用程序页面已加载完成。此方法仅为主框架调用。与 onPageEnd 不同，fragment导航也会触发 onLoadFinished

**起始版本：** 20

<!--Device-WebAttribute-onLoadFinished(callback: Callback<OnLoadFinishedEvent>): WebAttribute--><!--Device-WebAttribute-onLoadFinished(callback: Callback<OnLoadFinishedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnLoadFinishedEvent> | 是 | 网页加载结束时触发的函数。 |

## onLoadIntercept

```TypeScript
onLoadIntercept(callback: Callback<OnLoadInterceptEvent, boolean>)
```

当Web组件加载url之前触发该回调，用于判断是否阻止此次访问。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onLoadIntercept(callback: Callback<OnLoadInterceptEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onLoadIntercept(callback: Callback<OnLoadInterceptEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnLoadInterceptEvent, boolean> | 是 | The triggered callback when the navigation is intercepted. [since 10 - 11] |

## onLoadStarted

```TypeScript
onLoadStarted(callback: Callback<OnLoadStartedEvent>)
```

在页面加载开始时触发。此方法每次主框架加载时调用一次。嵌入框架的更改，例如点击目标为 iframe 的链接和片段导航（导航到 #fragment_id）不会触发此回调。与 onPageBegin 不同，onLoadStarted 仅在页面完全加载之前自动重定向时触发一次。OnPageBegin 每次导航时都会触发。

**起始版本：** 20

<!--Device-WebAttribute-onLoadStarted(callback: Callback<OnLoadStartedEvent>): WebAttribute--><!--Device-WebAttribute-onLoadStarted(callback: Callback<OnLoadStartedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnLoadStartedEvent> | 是 | 网页加载开始时触发的函数。 |

## onMicrophoneCaptureStateChange

```TypeScript
onMicrophoneCaptureStateChange(callback: OnMicrophoneCaptureStateChangeCallback)
```

通知用户当前网页中麦克风状态，麦克风有三个状态，未工作（None），捕获中（Active），暂停中（Paused）。使用callback异步回调。

可以通过resumeMicrophone，pauseMicrophone，stopMicrophone这三个接口来切换麦克风的状态。这三个接口功能分别对应解除暂停，暂停，停止麦克风。示例使用场景详见[网页中麦克风的使用](../../../../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#resumemicrophone23)。

> **说明：**  
>  
> 当前网页正在使用麦克风时，返回捕获中状态；当前网页暂停使用麦克风时，返回暂停中状态；当前网页完全没有使用麦克风时，返回未工作状态。  
>  
> 当前麦克风处于捕获中状态时，设置暂停使用，当前麦克风变为暂停中状态。可通过ArkWeb设置麦克风开始使用状态进行恢复捕捉。  
>  
> 当前麦克风处于捕获中状态时，设置停止使用，当前麦克风停止捕捉，麦克风变为未工作状态。除非重新前端开始捕捉，否则无法恢复。  
>  
> 当前麦克风处于暂停中状态时，设置开始使用，当前麦克风继续捕捉，变为捕获中状态。  
>  
> 当前麦克风处于暂停中状态时，设置停止使用，当前麦克风停止捕捉，变为未工作状态。除非重新前端开始捕捉，否则无法恢复。  
>  
> 当前麦克风处于未工作状态时，设置开始使用以及暂停使用，麦克风状态均不发生变化。

**起始版本：** 23

<!--Device-WebAttribute-onMicrophoneCaptureStateChange(callback: OnMicrophoneCaptureStateChangeCallback): WebAttribute--><!--Device-WebAttribute-onMicrophoneCaptureStateChange(callback: OnMicrophoneCaptureStateChangeCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnMicrophoneCaptureStateChangeCallback](arkts-arkweb-onmicrophonecapturestatechangecallback-t.md) | 是 | 回调函数。当麦克风捕获状态改变时触发该回调，返回原来的状态和改变后的状态。 |

## onNativeEmbedGestureEvent

```TypeScript
onNativeEmbedGestureEvent(callback: (event: NativeEmbedTouchInfo) => void)
```

当手指触摸到同层标签时触发该回调。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onNativeEmbedGestureEvent(callback: (event: NativeEmbedTouchInfo) => void): WebAttribute--><!--Device-WebAttribute-onNativeEmbedGestureEvent(callback: (event: NativeEmbedTouchInfo) => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event: NativeEmbedTouchInfo) => void | 是 | 手指触摸到同层标签时触发该回调。 |

## onNativeEmbedLifecycleChange

```TypeScript
onNativeEmbedLifecycleChange(callback: (event: NativeEmbedDataInfo) => void)
```

当同层标签生命周期变化时触发该回调。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onNativeEmbedLifecycleChange(callback: (event: NativeEmbedDataInfo) => void): WebAttribute--><!--Device-WebAttribute-onNativeEmbedLifecycleChange(callback: (event: NativeEmbedDataInfo) => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event: NativeEmbedDataInfo) => void | 是 | 同层标签生命周期变化时触发该回调。 |

## onNativeEmbedMouseEvent

```TypeScript
onNativeEmbedMouseEvent(callback: MouseInfoCallback)
```

在同层标签上执行以下行为时触发该回调：

- 使用鼠标左键、中键、右键进行点击或长按。  
- 使用触摸板进行对应鼠标左键、中键、右键点击长按的操作。

**起始版本：** 20

<!--Device-WebAttribute-onNativeEmbedMouseEvent(callback: MouseInfoCallback): WebAttribute--><!--Device-WebAttribute-onNativeEmbedMouseEvent(callback: MouseInfoCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [MouseInfoCallback](arkts-arkweb-mouseinfocallback-t.md) | 是 | 当鼠标/触摸板点击到同层标签时触发该回调。 |

## onNativeEmbedObjectParamChange

```TypeScript
onNativeEmbedObjectParamChange(callback: OnNativeEmbedObjectParamChangeCallback)
```

当同层渲染object标签内嵌param元素变化时触发此回调。

**起始版本：** 21

<!--Device-WebAttribute-onNativeEmbedObjectParamChange(callback: OnNativeEmbedObjectParamChangeCallback): WebAttribute--><!--Device-WebAttribute-onNativeEmbedObjectParamChange(callback: OnNativeEmbedObjectParamChangeCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnNativeEmbedObjectParamChangeCallback](arkts-arkweb-onnativeembedobjectparamchangecallback-t.md) | 是 | 增加、修改或删除同层渲染object标签内嵌param元素时触发此回调。 |

## onNativeEmbedVisibilityChange

```TypeScript
onNativeEmbedVisibilityChange(callback: OnNativeEmbedVisibilityChangeCallback)
```

当网页中同层标签（例如<embed\>标签或<object\>标签）在视口内的可见性发生变化时，将触发该回调。同层标签默认不可见，若在页面首次加载时已可见，则会上报；若不可见，则不会上报。同层标签全部不可见才视为不可见，部分可见或全部可见则视为可见。若要获取因同层标签CSS属性（包括visibility、display以及尺寸变化）导致的可见状态变化，需配置[nativeEmbedOptions](web:WebAttribute.nativeEmbedOptions)，并将[EmbedOptions](arkts-arkweb-web-embedoptions-i.md)中的supportCssDisplayChange参数设为true。

**起始版本：** 12

<!--Device-WebAttribute-onNativeEmbedVisibilityChange(callback: OnNativeEmbedVisibilityChangeCallback): WebAttribute--><!--Device-WebAttribute-onNativeEmbedVisibilityChange(callback: OnNativeEmbedVisibilityChangeCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnNativeEmbedVisibilityChangeCallback](arkts-arkweb-onnativeembedvisibilitychangecallback-t.md) | 是 | 同层标签可见性变化时触发该回调。 |

## onNavigationEntryCommitted

```TypeScript
onNavigationEntryCommitted(callback: OnNavigationEntryCommittedCallback)
```

Called when the load committed.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onNavigationEntryCommitted(callback: OnNavigationEntryCommittedCallback): WebAttribute--><!--Device-WebAttribute-onNavigationEntryCommitted(callback: OnNavigationEntryCommittedCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnNavigationEntryCommittedCallback](arkts-arkweb-onnavigationentrycommittedcallback-t.md) | 是 | Function Triggered when a load committed. |

## onOverScroll

```TypeScript
onOverScroll(callback: Callback<OnOverScrollEvent>)
```

过度滚动时触发。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onOverScroll(callback: Callback<OnOverScrollEvent>): WebAttribute--><!--Device-WebAttribute-onOverScroll(callback: Callback<OnOverScrollEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnOverScrollEvent> | 是 | 发生过度滚动时触发的函数。[since 10 - 11] |

## onOverrideErrorPage

```TypeScript
onOverrideErrorPage(callback: OnOverrideErrorPageCallback)
```

页面文档资源发生错误的时候触发，只有主frame会触发

**起始版本：** 20

<!--Device-WebAttribute-onOverrideErrorPage(callback: OnOverrideErrorPageCallback): WebAttribute--><!--Device-WebAttribute-onOverrideErrorPage(callback: OnOverrideErrorPageCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnOverrideErrorPageCallback](arkts-arkweb-onoverrideerrorpagecallback-t.md) | 是 | The triggered function when the |

## onOverrideUrlLoading

```TypeScript
onOverrideUrlLoading(callback: OnOverrideUrlLoadingCallback)
```

When the URL is about to be loaded into the current Web, it gives the application the opportunity to take control.This will not called for POST requests, may be called for subframes and with non-HTTP(S) schemes.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onOverrideUrlLoading(callback: OnOverrideUrlLoadingCallback): WebAttribute--><!--Device-WebAttribute-onOverrideUrlLoading(callback: OnOverrideUrlLoadingCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnOverrideUrlLoadingCallback](arkts-arkweb-onoverrideurlloadingcallback-t.md) | 是 | The callback for onOverrideUrlLoading. |

## onPageBegin

```TypeScript
onPageBegin(callback: Callback<OnPageBeginEvent>)
```

Called when the web page starts to be loaded.This API is called only for the main frame, and not for the iframe or frameset content.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPageBegin(callback: Callback<OnPageBeginEvent>): WebAttribute--><!--Device-WebAttribute-onPageBegin(callback: Callback<OnPageBeginEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnPageBeginEvent> | 是 | The triggered function at the begin of web page loading. |

## onPageEnd

```TypeScript
onPageEnd(callback: Callback<OnPageEndEvent>)
```

网页加载完成时触发该回调，且只在主frame触发，iframe或者frameset的内容加载时不会触发此回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPageEnd(callback: Callback<OnPageEndEvent>): WebAttribute--><!--Device-WebAttribute-onPageEnd(callback: Callback<OnPageEndEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnPageEndEvent> | 是 | The triggered function at the end of web page loading. [since 8 - 11] |

## onPageVisible

```TypeScript
onPageVisible(callback: Callback<OnPageVisibleEvent>)
```

Triggered when previous page will no longer be drawn and next page begin to draw.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPageVisible(callback: Callback<OnPageVisibleEvent>): WebAttribute--><!--Device-WebAttribute-onPageVisible(callback: Callback<OnPageVisibleEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnPageVisibleEvent> | 是 | The triggered callback when previous page will no longer be drawn and next |

## onPdfLoadEvent

```TypeScript
onPdfLoadEvent(callback: Callback<OnPdfLoadEvent>)
```

通知用户PDF页面加载状态，包括成功或失败。

**起始版本：** 20

<!--Device-WebAttribute-onPdfLoadEvent(callback: Callback<OnPdfLoadEvent>): WebAttribute--><!--Device-WebAttribute-onPdfLoadEvent(callback: Callback<OnPdfLoadEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnPdfLoadEvent> | 是 | 当PDF加载成功或失败时，会触发回调，通知用户PDF页面加载状态。 |

## onPdfScrollAtBottom

```TypeScript
onPdfScrollAtBottom(callback: Callback<OnPdfScrollEvent>)
```

通知用户PDF页面已滚动到底。

**起始版本：** 20

<!--Device-WebAttribute-onPdfScrollAtBottom(callback: Callback<OnPdfScrollEvent>): WebAttribute--><!--Device-WebAttribute-onPdfScrollAtBottom(callback: Callback<OnPdfScrollEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnPdfScrollEvent> | 是 | 当PDF滚动到垂直方向底部时，会触发回调，通知用户PDF页面已滚动到底。 |

## onPermissionRequest

```TypeScript
onPermissionRequest(callback: Callback<OnPermissionRequestEvent>)
```

Triggered when the host application that web content from the specified origin is attempting to access the resources.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPermissionRequest(callback: Callback<OnPermissionRequestEvent>): WebAttribute--><!--Device-WebAttribute-onPermissionRequest(callback: Callback<OnPermissionRequestEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnPermissionRequestEvent> | 是 | The triggered callback when the host application that web content from the specified origin is |

## onProgressChange

```TypeScript
onProgressChange(callback: Callback<OnProgressChangeEvent>)
```

网页加载进度变化时触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onProgressChange(callback: Callback<OnProgressChangeEvent>): WebAttribute--><!--Device-WebAttribute-onProgressChange(callback: Callback<OnProgressChangeEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnProgressChangeEvent> | 是 | The triggered function when the page loading progress changes. [since 8 - 11] |

## onPrompt

```TypeScript
onPrompt(callback: Callback<OnPromptEvent, boolean>)
```

网页需要显示 JavaScript prompt() 输入弹窗时触发。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPrompt(callback: Callback<OnPromptEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onPrompt(callback: Callback<OnPromptEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnPromptEvent, boolean> | 是 | 网页调用 prompt() 时使用的回调函数。[since 9 - 11] |

## onRefreshAccessedHistory

```TypeScript
onRefreshAccessedHistory(callback: Callback<OnRefreshAccessedHistoryEvent>)
```

Triggered when the Web page refreshes accessed history.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onRefreshAccessedHistory(callback: Callback<OnRefreshAccessedHistoryEvent>): WebAttribute--><!--Device-WebAttribute-onRefreshAccessedHistory(callback: Callback<OnRefreshAccessedHistoryEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnRefreshAccessedHistoryEvent> | 是 | The triggered callback when the Web page refreshes accessed history. [since 8 - 11] |

## onRenderExited

```TypeScript
onRenderExited(callback: Callback<OnRenderExitedEvent>)
```

Triggered when the render process exits.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onRenderExited(callback: Callback<OnRenderExitedEvent>): WebAttribute--><!--Device-WebAttribute-onRenderExited(callback: Callback<OnRenderExitedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnRenderExitedEvent> | 是 | The triggered when the render process exits. |

## onRenderExited

```TypeScript
onRenderExited(callback: (event?: { detail: object }) => boolean)
```

Triggered when the render process exits.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onRenderExited

<!--Device-WebAttribute-onRenderExited(callback: (event?: { detail: object }) => boolean): WebAttribute--><!--Device-WebAttribute-onRenderExited(callback: (event?: { detail: object }) => boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: { detail: object }) => boolean | 是 | The triggered when the render process exits. |

## onRenderProcessNotResponding

```TypeScript
onRenderProcessNotResponding(callback: OnRenderProcessNotRespondingCallback)
```

Triggered when render process not responding.

**起始版本：** 12

<!--Device-WebAttribute-onRenderProcessNotResponding(callback: OnRenderProcessNotRespondingCallback): WebAttribute--><!--Device-WebAttribute-onRenderProcessNotResponding(callback: OnRenderProcessNotRespondingCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnRenderProcessNotRespondingCallback](arkts-arkweb-onrenderprocessnotrespondingcallback-t.md) | 是 | The triggered function when render process not responding. |

## onRenderProcessResponding

```TypeScript
onRenderProcessResponding(callback: OnRenderProcessRespondingCallback)
```

Triggered when the unresponsive render process becomes responsive.

**起始版本：** 12

<!--Device-WebAttribute-onRenderProcessResponding(callback: OnRenderProcessRespondingCallback): WebAttribute--><!--Device-WebAttribute-onRenderProcessResponding(callback: OnRenderProcessRespondingCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnRenderProcessRespondingCallback](arkts-arkweb-onrenderprocessrespondingcallback-t.md) | 是 | The triggered function when the unresponsive render process becomes responsive. |

## onRequestSelected

```TypeScript
onRequestSelected(callback: () => void)
```

Web 获取焦点时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onRequestSelected(callback: () => void): WebAttribute--><!--Device-WebAttribute-onRequestSelected(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () => void | 是 | Web 获取焦点时触发的函数。 |

## onResourceLoad

```TypeScript
onResourceLoad(callback: Callback<OnResourceLoadEvent>)
```

通知Web组件所加载的资源文件url信息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onResourceLoad(callback: Callback<OnResourceLoadEvent>): WebAttribute--><!--Device-WebAttribute-onResourceLoad(callback: Callback<OnResourceLoadEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnResourceLoadEvent> | 是 | The triggered when the url loading. [since 9 - 11] |

## onSafeBrowsingCheckFinish

```TypeScript
onSafeBrowsingCheckFinish(callback: OnSafeBrowsingCheckResultCallback)
```

Triggered when the website security risk check is completed.<p><strong>API Note</strong>:<br>Unlike onSafeBrowsingCheckResult, which is only triggered when a URL has security risks, onSafeBrowsingCheckFinish is also triggered when the website security risk check is not performed or no risks are found.

**起始版本：** 21

<!--Device-WebAttribute-onSafeBrowsingCheckFinish(callback: OnSafeBrowsingCheckResultCallback): WebAttribute--><!--Device-WebAttribute-onSafeBrowsingCheckFinish(callback: OnSafeBrowsingCheckResultCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnSafeBrowsingCheckResultCallback](arkts-arkweb-onsafebrowsingcheckresultcallback-t.md) | 是 | Triggered when received website security risk check result. |

## onSafeBrowsingCheckResult

```TypeScript
onSafeBrowsingCheckResult(callback: OnSafeBrowsingCheckResultCallback)
```

Called when received website security risk check result.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onSafeBrowsingCheckResult(callback: OnSafeBrowsingCheckResultCallback): WebAttribute--><!--Device-WebAttribute-onSafeBrowsingCheckResult(callback: OnSafeBrowsingCheckResultCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnSafeBrowsingCheckResultCallback](arkts-arkweb-onsafebrowsingcheckresultcallback-t.md) | 是 | Function triggered when received website security risk check result. |

## onScaleChange

```TypeScript
onScaleChange(callback: Callback<OnScaleChangeEvent>)
```

WebView 缩放比例变化时触发。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onScaleChange(callback: Callback<OnScaleChangeEvent>): WebAttribute--><!--Device-WebAttribute-onScaleChange(callback: Callback<OnScaleChangeEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnScaleChangeEvent> | 是 | 缩放比例变化时触发的回调。[9 - 11 版本起支持] |

## onScreenCaptureRequest

```TypeScript
onScreenCaptureRequest(callback: Callback<OnScreenCaptureRequestEvent>)
```

Triggered when the host application that web content from the specified origin is requesting to capture screen.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onScreenCaptureRequest(callback: Callback<OnScreenCaptureRequestEvent>): WebAttribute--><!--Device-WebAttribute-onScreenCaptureRequest(callback: Callback<OnScreenCaptureRequestEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnScreenCaptureRequestEvent> | 是 | The triggered callback when the host application that web content from the specified origin is |

## onScroll

```TypeScript
onScroll(callback: Callback<OnScrollEvent>)
```

滚动条滑动到指定位置时触发。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onScroll(callback: Callback<OnScrollEvent>): WebAttribute--><!--Device-WebAttribute-onScroll(callback: Callback<OnScrollEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnScrollEvent> | 是 | 网页滚动到指定位置时触发的函数。[since 9 - 11] |

## onSearchResultReceive

```TypeScript
onSearchResultReceive(callback: Callback<OnSearchResultReceiveEvent>)
```

Notify search result to host application through onSearchResultReceive.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onSearchResultReceive(callback: Callback<OnSearchResultReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onSearchResultReceive(callback: Callback<OnSearchResultReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnSearchResultReceiveEvent> | 是 | Function Triggered when the host application call searchAllAsync. |

## onShowFileSelector

```TypeScript
onShowFileSelector(callback: Callback<OnShowFileSelectorEvent, boolean>)
```

文件选择器显示时触发。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onShowFileSelector(callback: Callback<OnShowFileSelectorEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onShowFileSelector(callback: Callback<OnShowFileSelectorEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnShowFileSelectorEvent, boolean> | 是 | 文件选择器显示时触发的回调函数。[since 9 - 11] |

## onSslErrorEvent

```TypeScript
onSslErrorEvent(callback: OnSslErrorEventCallback)
```

通知用户加载资源（主资源+子资源）时发生SSL错误，如果只想处理主资源的SSL错误，请用 isMainFrame 字段进行区分。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onSslErrorEvent(callback: OnSslErrorEventCallback): WebAttribute--><!--Device-WebAttribute-onSslErrorEvent(callback: OnSslErrorEventCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnSslErrorEventCallback](arkts-arkweb-onsslerroreventcallback-t.md) | 是 | The triggered callback when the Web page receives an ssl Error. |

## onSslErrorEventReceive

```TypeScript
onSslErrorEventReceive(callback: Callback<OnSslErrorEventReceiveEvent>)
```

通知用户加载资源时发生SSL错误，只支持主资源。如果需要支持子资源，请使用 OnSslErrorEvent 接口。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onSslErrorEventReceive(callback: Callback<OnSslErrorEventReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onSslErrorEventReceive(callback: Callback<OnSslErrorEventReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnSslErrorEventReceiveEvent> | 是 | The triggered callback when the Web page receives an ssl Error. [since 9 - 11] |

## onSslErrorReceive

```TypeScript
onSslErrorReceive(callback: (event?: { handler: Function, error: object }) => void)
```

Triggered when the Web page receives an ssl Error.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onSslErrorEventReceive

<!--Device-WebAttribute-onSslErrorReceive(callback: (event?: { handler: Function, error: object }) => void): WebAttribute--><!--Device-WebAttribute-onSslErrorReceive(callback: (event?: { handler: Function, error: object }) => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: { handler: Function, error: object }) => void | 是 | The triggered callback when the Web page receives an ssl Error. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: TextSelectionChangeCallback)
```

文本选择发生变化时调用。

**起始版本：** 23

<!--Device-WebAttribute-onTextSelectionChange(callback: TextSelectionChangeCallback): WebAttribute--><!--Device-WebAttribute-onTextSelectionChange(callback: TextSelectionChangeCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextSelectionChangeCallback](arkts-arkweb-textselectionchangecallback-t.md) | 是 | 文本选择变化时的回调函数。 |

## onTitleReceive

```TypeScript
onTitleReceive(callback: Callback<OnTitleReceiveEvent>)
```

当页面文档标题`<title>`元素发生变更时，触发回调。若当前页面未显示设置标题，ArkWeb将在加载完成前基于页面的URL生成标题并返回给应用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onTitleReceive(callback: Callback<OnTitleReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onTitleReceive(callback: Callback<OnTitleReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnTitleReceiveEvent> | 是 | The triggered function when the title of the main application document |

## onTouchIconUrlReceived

```TypeScript
onTouchIconUrlReceived(callback: Callback<OnTouchIconUrlReceivedEvent>)
```

设置接收到apple-touch-icon url地址时的回调函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onTouchIconUrlReceived(callback: Callback<OnTouchIconUrlReceivedEvent>): WebAttribute--><!--Device-WebAttribute-onTouchIconUrlReceived(callback: Callback<OnTouchIconUrlReceivedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnTouchIconUrlReceivedEvent> | 是 | The triggered callback when the application receive an new url of an |

## onUrlLoadIntercept

```TypeScript
onUrlLoadIntercept(callback: (event?: { data: string | WebResourceRequest }) => boolean)
```

Triggered when the URL loading is intercepted.

**起始版本：** 8

**废弃版本：** 10

**替代接口：** onLoadIntercept

<!--Device-WebAttribute-onUrlLoadIntercept(callback: (event?: { data: string | WebResourceRequest }) => boolean): WebAttribute--><!--Device-WebAttribute-onUrlLoadIntercept(callback: (event?: { data: string | WebResourceRequest }) => boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: { data: string \| WebResourceRequest }) => boolean | 是 | The triggered callback when the URL loading is intercepted. |

## onVerifyPin

```TypeScript
onVerifyPin(callback: OnVerifyPinCallback)
```

Triggered when the Web page needs verify pin from the user.

**起始版本：** 22

<!--Device-WebAttribute-onVerifyPin(callback: OnVerifyPinCallback): WebAttribute--><!--Device-WebAttribute-onVerifyPin(callback: OnVerifyPinCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnVerifyPinCallback](arkts-arkweb-onverifypincallback-t.md) | 是 | The triggered callback when needs verify pin from the user. |

## onViewportFitChanged

```TypeScript
onViewportFitChanged(callback: OnViewportFitChangedCallback)
```

网页meta中viewport-fit配置项更改时触发该回调，应用可在此回调中自适应布局视口。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onViewportFitChanged(callback: OnViewportFitChangedCallback): WebAttribute--><!--Device-WebAttribute-onViewportFitChanged(callback: OnViewportFitChangedCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnViewportFitChangedCallback](arkts-arkweb-onviewportfitchangedcallback-t.md) | 是 | 网页meta中viewport-fit配置项更改时触发的回调。 |

## onWindowExit

```TypeScript
onWindowExit(callback: () => void)
```

Triggered when web page requires the user to close a window.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onWindowExit(callback: () => void): WebAttribute--><!--Device-WebAttribute-onWindowExit(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () => void | 是 | The triggered callback when web page requires the user to close a window. |

## onWindowNew

```TypeScript
onWindowNew(callback: Callback<OnWindowNewEvent>)
```

Triggered when web page requires the user to create a window.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onWindowNew(callback: Callback<OnWindowNewEvent>): WebAttribute--><!--Device-WebAttribute-onWindowNew(callback: Callback<OnWindowNewEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnWindowNewEvent> | 是 | The triggered callback when web page requires the user to create a window. |

## onWindowNewExt

```TypeScript
onWindowNewExt(callback: Callback<OnWindowNewExtEvent>)
```

Triggered when web page requires to create a new window.If the {@link setWebController} interface is not called, the render process will be blocked.If no new window is created, it is set to null when calling the {@link setWebController} interface,informing the Web that no new window is created.New windows must not be placed to directly cover the original Web component. Additionally,their URLs?specifically the content shown in the address bar?should follow the same display format as the main page, ensuring clarity for users and avoiding confusion. In cases where reliable visual management of URLs is not feasible, restricting the creation of new windows should be considered. It is also important to note that the origin of new window requests cannot be tracked with certainty; such requests may even be triggered by third-party iframes.For this reason, applications must implement default defensive measures like sandbox isolation and permission controls to safeguard security.

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onWindowNewExt(callback: Callback<OnWindowNewExtEvent>): WebAttribute--><!--Device-WebAttribute-onWindowNewExt(callback: Callback<OnWindowNewExtEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<OnWindowNewExtEvent> | 是 | The triggered callback when web page requires the user |

## onlineImageAccess

```TypeScript
onlineImageAccess(onlineImageAccess: boolean)
```

设置是否允许从网络加载图片资源（通过HTTP和HTTPS访问的资源）。当属性没有显式调用时，默认允许从网络加载图片资源。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onlineImageAccess(onlineImageAccess: boolean): WebAttribute--><!--Device-WebAttribute-onlineImageAccess(onlineImageAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onlineImageAccess | boolean | 是 | 设置是否允许从网络加载图片资源。<br>true表示设置允许从网络加载图片资源，false表示设置不允许从网络加载图片资源。<br>传入undefined或null时为false。 |

## optimizeParserBudget

```TypeScript
optimizeParserBudget(optimizeParserBudget: boolean)
```

设置是否开启分段解析HTML优化。当属性没有显式调用时，默认使用解析时间作为HTML分段解析的分段点。ArkWeb内核在解析HTML文档结构时采取分段解析策略，旨在避免过多占用主线程资源，并使网页具有渐进式加载能力。ArkWeb内核默认使用解析时间作为分段点，当单次解析时间超过阈值时，会中断解析，随后进行布局和渲染操作。开启优化后，ArkWeb内核将不仅检查解析时间是否超出限制，还会额外判断解析的Token（HTML文档的最小解析单位，例如`<div>`、`attr="xxx"`等）数量是否超过内核规定的阈值，并下调此阈值。当页面的FCP（First Contentful Paint 首次内容绘制）触发时会恢复成默认的中断判断逻辑。这将使得网页在FCP到来之前的解析操作更频繁，从而提高首帧内容被提前解析完成并进入渲染阶段的可能性，同时有效缩减首帧渲染的工作量，最终实现FCP时间提前。由于页面的FCP触发时会恢复成默认分段解析逻辑，因此分段解析HTML优化仅对每个Web组件加载的首个页面生效。

**起始版本：** 15

<!--Device-WebAttribute-optimizeParserBudget(optimizeParserBudget: boolean): WebAttribute--><!--Device-WebAttribute-optimizeParserBudget(optimizeParserBudget: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| optimizeParserBudget | boolean | 是 | 设置开启分段解析HTML优化。<br>true表示使用解析个数代替解析时间作为HTML分段解析的分段点，并减少每段解析的个数上限。false表示使用解析时间作为HTML分段解析的分段点。<br>传入undefined或null时为false。 |

## overScrollMode

```TypeScript
overScrollMode(mode: OverScrollMode)
```

设置网页的过度滚动模式

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-overScrollMode(mode: OverScrollMode): WebAttribute--><!--Device-WebAttribute-overScrollMode(mode: OverScrollMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [OverScrollMode](arkts-arkweb-web-overscrollmode-e.md) | 是 | 过度滚动模式，可参考 {@link OverScrollMode}。默认值为 OverScrollMode.NEVER。 |

## overviewModeAccess

```TypeScript
overviewModeAccess(overviewModeAccess: boolean)
```

设置是否使用概览模式加载网页，即缩小内容以适应屏幕宽度。当属性没有显式调用时，默认允许使用概览模式加载网页。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-overviewModeAccess(overviewModeAccess: boolean): WebAttribute--><!--Device-WebAttribute-overviewModeAccess(overviewModeAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| overviewModeAccess | boolean | 是 | 设置是否使用概览模式加载网页。<br>true表示设置使用概览模式加载网页，false表示设置不使用概览模式加载网页。<br>传入undefined或null时为false。 |

## password

```TypeScript
password(password: boolean)
```

设置网页是否允许保存密码。

**起始版本：** 8

**废弃版本：** 10

**替代接口：** enableAutofill

<!--Device-WebAttribute-password(password: boolean): WebAttribute--><!--Device-WebAttribute-password(password: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| password | boolean | 是 | {@code true} 表示允许网页保存密码；{@code false} 表示不允许。 |

## pinchSmooth

```TypeScript
pinchSmooth(isEnabled: boolean)
```

设置网页是否开启捏合流畅模式。该属性没有显式调用时，默认不开启捏合流畅模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-pinchSmooth(isEnabled: boolean): WebAttribute--><!--Device-WebAttribute-pinchSmooth(isEnabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 网页是否开启捏合流畅模式。<br>true表示设置网页开启捏合流畅模式，false表示设置网页不开启捏合流畅模式。<br>传入undefined或null时为false。 |

## registerNativeEmbedRule

```TypeScript
registerNativeEmbedRule(tag: string, type:string)
```

注册使用同层渲染的HTML标签名和类型。标签名仅支持使用<object\>和<embed\>。标签类型只能使用ASCII可显示字符。

若指定类型与W3C定义的<object\>或<embed\>标准类型重合，ArkWeb内核将其识别为非同层标签。

本接口同样受enableNativeEmbedMode接口控制，在未使能同层渲染时本接口无效。在不使用本接口的情况下，ArkWeb内核默认将"native/"前缀类型的<embed\>标签识别为同层标签。

具体使用详情请参考[同层渲染](../../../../web/web-same-layer.md#web页面中同层渲染输入框)指南。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-registerNativeEmbedRule(tag: string, type:string): WebAttribute--><!--Device-WebAttribute-registerNativeEmbedRule(tag: string, type:string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tag | string | 是 | 标签名。 |
| type | string | 是 | 标签类型，内核使用前缀匹配此参数。 |

## rotateRenderEffect

```TypeScript
rotateRenderEffect(effect: WebRotateEffect)
```

设置Web组件旋转时，宽高动画过程中组件内容的填充方式。若未显式调用属性，默认保持动画终态的内容大小，内容始终与组件左上角对齐。

**起始版本：** 22

<!--Device-WebAttribute-rotateRenderEffect(effect: WebRotateEffect): WebAttribute--><!--Device-WebAttribute-rotateRenderEffect(effect: WebRotateEffect): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [WebRotateEffect](arkts-arkweb-web-webrotateeffect-e.md) | 是 | 设置Web组件旋转时，宽高动画过程中组件内容的填充方式。 |

## runJavaScriptOnDocumentEnd

```TypeScript
runJavaScriptOnDocumentEnd(scripts: Array<ScriptItem>)
```

Injects the JavaScripts that will be run after document has been parsed finished.

> **说明：**  
>  
> - 网页文档根元素（HTML Element）创建后、但尚未加载任何其他内容之前注入脚本。  
>  
> - 该脚本按照数组本身顺序执行。  
>  
> - 不建议与[javaScriptOnDocumentStart](WebAttribute.javaScriptOnDocumentStart)同时使用。  
>  
> - 内容相同的脚本多次注入时将被静默去重，不展示，不提醒，使用首次注入时的scriptRules。

**起始版本：** 15

<!--Device-WebAttribute-runJavaScriptOnDocumentEnd(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-runJavaScriptOnDocumentEnd(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<ScriptItem> | 是 | The JavaScripts executed in array order. |

## runJavaScriptOnDocumentStart

```TypeScript
runJavaScriptOnDocumentStart(scripts: Array<ScriptItem>)
```

Injects the JavaScripts that will be run just after document object has been created.

> **说明：**  
>  
> - 网页文档根元素（HTML Element）创建后、但尚未加载任何其他内容之前注入脚本。  
>  
> - 该脚本按照数组本身顺序执行。  
>  
> - 不建议与[javaScriptOnDocumentStart](WebAttribute.javaScriptOnDocumentStart)同时使用。  
>  
> - 内容相同的脚本多次注入时将被静默去重，不展示，不提醒，使用首次注入时的scriptRules。

**起始版本：** 15

<!--Device-WebAttribute-runJavaScriptOnDocumentStart(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-runJavaScriptOnDocumentStart(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<ScriptItem> | 是 | The JavaScripts executed in array order. |

## runJavaScriptOnHeadEnd

```TypeScript
runJavaScriptOnHeadEnd(scripts: Array<ScriptItem>)
```

Injects the JavaScripts that will be run after head element has been parsed finished.

> **说明：**  
>  
> - 该脚本按照数组本身顺序执行。  
>  
> - 内容相同的脚本多次注入时将被静默去重，不展示，不提醒，使用首次注入时的scriptRules。

**起始版本：** 15

<!--Device-WebAttribute-runJavaScriptOnHeadEnd(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-runJavaScriptOnHeadEnd(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<ScriptItem> | 是 | The JavaScripts executed in array order. |

## scrollbarLayoutPolicy

```TypeScript
scrollbarLayoutPolicy(policy: ScrollbarLayoutPolicy)
```

设置滚动条布局策略。控制滚动条在容器中的布局方式——要么遵循W3C标准，要么遵循系统默认值。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-scrollbarLayoutPolicy(policy: ScrollbarLayoutPolicy): WebAttribute--><!--Device-WebAttribute-scrollbarLayoutPolicy(policy: ScrollbarLayoutPolicy): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [ScrollbarLayoutPolicy](arkts-arkweb-web-scrollbarlayoutpolicy-e.md) | 是 | 要应用的布局策略。 |

## selectionMenuOptions

```TypeScript
selectionMenuOptions(expandedMenuOptions: Array<ExpandedMenuItemOptions>)
```

设置自定义文本菜单。

**起始版本：** 12

**废弃版本：** 20

**替代接口：** editMenuOptions

<!--Device-WebAttribute-selectionMenuOptions(expandedMenuOptions: Array<ExpandedMenuItemOptions>): WebAttribute--><!--Device-WebAttribute-selectionMenuOptions(expandedMenuOptions: Array<ExpandedMenuItemOptions>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expandedMenuOptions | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<ExpandedMenuItemOptions> | 是 | 自定义文本菜单配置项。菜单项数量、菜单内容尺寸、startIcon 图标尺寸均与 ArkUI Menu 组件保持一致。 |

## tableData

```TypeScript
tableData(tableData: boolean)
```

设置网页是否保存表格数据。

**起始版本：** 8

**废弃版本：** 10

**替代接口：** enableAutofill

<!--Device-WebAttribute-tableData(tableData: boolean): WebAttribute--><!--Device-WebAttribute-tableData(tableData: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tableData | boolean | 是 | { |

## textAutosizing

```TypeScript
textAutosizing(textAutosizing: boolean)
```

设置Web组件是否开启文本字体大小自动调整。当属性没有显式调用时，Web组件默认开启文本字体大小自动调整。

文本字体大小自动调整生效后，对于字号过小的文本将自动加大字号至16px~32px，避免屏幕较小（默认视口宽度 < 980px）的设备因为缺少移动端适配出现字体过小的可读性问题。

> **说明：**  
>  
> - 文本字体大小自动调整生效需要满足的前置条件：  
> > - 设备形态为：Phone、Tablet、Wearable、TV。  
> > - Web组件视口宽度 < 980px。  
> > - 页面文本量大，页面文本的字号*字符数 ≥ 3920。  
> > - 前端无metaViewport设置，或metaViewport设置中无"width"和"initial-scale"属性。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-textAutosizing(textAutosizing: boolean): WebAttribute--><!--Device-WebAttribute-textAutosizing(textAutosizing: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textAutosizing | boolean | 是 | 文本自动调整大小。<br>true表示文本自动调整大小，false表示文本不自动调整大小。<br>传入undefined或null时为true。 |

## textZoomAtio

```TypeScript
textZoomAtio(textZoomAtio: number)
```

设置页面的文本缩放百分比。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用[textZoomRatio<sup>9+</sup>](WebAttribute.textZoomRatio)代替。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** textZoomRatio

<!--Device-WebAttribute-textZoomAtio(textZoomAtio: number): WebAttribute--><!--Device-WebAttribute-textZoomAtio(textZoomAtio: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textZoomAtio | number | 是 | 要设置的页面的文本缩放百分比。<br>取值范围为正整数。<br>默认值：100。 |

## textZoomRatio

```TypeScript
textZoomRatio(textZoomRatio: number)
```

设置页面的文本缩放百分比。当属性没有显式调用时，默认缩放百分比为100%。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-textZoomRatio(textZoomRatio: number): WebAttribute--><!--Device-WebAttribute-textZoomRatio(textZoomRatio: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textZoomRatio | number | 是 | 要设置的页面的文本缩放百分比。<br>取值为整数，范围为(0, 2147483647]。 |

## userAgent

```TypeScript
userAgent(userAgent: string)
```

Sets the Web's user agent.

**起始版本：** 8

**废弃版本：** 10

**替代接口：** setCustomUserAgent

<!--Device-WebAttribute-userAgent(userAgent: string): WebAttribute--><!--Device-WebAttribute-userAgent(userAgent: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | The Web's user agent. |

## verticalScrollBarAccess

```TypeScript
verticalScrollBarAccess(verticalScrollBar: boolean)
```

设置是否绘制垂直滚动条。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-verticalScrollBarAccess(verticalScrollBar: boolean): WebAttribute--><!--Device-WebAttribute-verticalScrollBarAccess(verticalScrollBar: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| verticalScrollBar | boolean | 是 | 若需要绘制垂直滚动条则为 true。 |

## webCursiveFont

```TypeScript
webCursiveFont(family: string)
```

设置网页的cursive font字体库，用于渲染html前端使用cursive字体的元素。

当属性没有显式调用时，默认网页的cursive font字体库为cursive。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webCursiveFont(family: string): WebAttribute--><!--Device-WebAttribute-webCursiveFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的cursive font字体库。<br>传入null或undefined时为cursive。 |

## webFantasyFont

```TypeScript
webFantasyFont(family: string)
```

设置网页的fantasy font字体库，用于渲染html前端使用fantasy字体的元素。

当属性没有显式调用时，默认网页的fantasy font字体库为fantasy。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webFantasyFont(family: string): WebAttribute--><!--Device-WebAttribute-webFantasyFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的fantasy font字体库。<br>传入null或undefined时为fantasy。 |

## webFixedFont

```TypeScript
webFixedFont(family: string)
```

设置网页的fixed font字体库，用于渲染html前端使用monospace字体的元素。

当属性没有显式调用时，默认网页的fixed font字体库为monospace。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webFixedFont(family: string): WebAttribute--><!--Device-WebAttribute-webFixedFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的fixed font字体库。<br>传入null或undefined时为monospace。 |

## webSansSerifFont

```TypeScript
webSansSerifFont(family: string)
```

设置网页的sans-serif font字体库，用于渲染html前端使用sans-serif字体的元素。

当属性没有显式调用时，默认网页的sans-serif font字体库为sans-serif。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webSansSerifFont(family: string): WebAttribute--><!--Device-WebAttribute-webSansSerifFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的sans-serif font字体库。<br>传入null或undefined时为sans-serif。 |

## webSerifFont

```TypeScript
webSerifFont(family: string)
```

设置网页的serif font字体库，用于渲染html前端使用serif字体的元素。

当属性没有显式调用时，默认网页的serif font字体库为serif。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webSerifFont(family: string): WebAttribute--><!--Device-WebAttribute-webSerifFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的serif font字体库。<br>传入null或undefined时为serif。 |

## webStandardFont

```TypeScript
webStandardFont(family: string)
```

设置网页的standard font字体库，用于渲染html前端未指定字体样式的元素。

当属性没有显式调用时，默认网页的standard font字体库为sans-serif。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webStandardFont(family: string): WebAttribute--><!--Device-WebAttribute-webStandardFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的standard font字体库。<br>传入null或undefined时为sans-serif。 |

## wideViewModeAccess

```TypeScript
wideViewModeAccess(wideViewModeAccess: boolean)
```

设置Web是否支持html中meta标签的viewport属性。该接口为空接口。

> **说明：**  
>  
> 从API version 8开始支持，从API version 10开始废弃，建议使用[metaViewport<sup>12+</sup>](WebAttribute.metaViewport)替代。

**起始版本：** 8

**废弃版本：** 10

**替代接口：** metaViewport

<!--Device-WebAttribute-wideViewModeAccess(wideViewModeAccess: boolean): WebAttribute--><!--Device-WebAttribute-wideViewModeAccess(wideViewModeAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wideViewModeAccess | boolean | 是 | 设置Web是否支持html中meta标签的viewport属性。<br/>true表示支持html中meta标签的viewport属性，false表示不支持html中meta标签的viewport属性。 |

## zoomAccess

```TypeScript
zoomAccess(zoomAccess: boolean)
```

设置网页是否支持手势缩放。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-zoomAccess(zoomAccess: boolean): WebAttribute--><!--Device-WebAttribute-zoomAccess(zoomAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoomAccess | boolean | 是 | { |

## zoomControlAccess

```TypeScript
zoomControlAccess(zoomControlAccess: boolean)
```

设置网页是否支持使用 Ctrl 键进行缩放。

**起始版本：** 22

<!--Device-WebAttribute-zoomControlAccess(zoomControlAccess: boolean): WebAttribute--><!--Device-WebAttribute-zoomControlAccess(zoomControlAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoomControlAccess | boolean | 是 | {@code true} 表示网页支持使用 Ctrl 键缩放，{@code false} 表示不支持。默认值为 true。 |

