# Web属性/事件

定义了Web属性函数。

**继承/实现关系：** WebAttribute extends CommonMethod<WebAttribute>

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

<!--Device-unnamed-declare class WebAttribute--><!--Device-unnamed-declare class WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## aiSessionOptions

```TypeScript
aiSessionOptions(aiSessions: Array<AISessionEvent>)
```

自定义Web组件的前端AI会话配置，用于注册多个自定义AI会话。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-aiSessionOptions(aiSessions: Array<AISessionEvent>): WebAttribute--><!--Device-WebAttribute-aiSessionOptions(aiSessions: Array<AISessionEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aiSessions | Array&lt;[AISessionEvent](arkts-arkweb-aisessionevent-i.md)&gt; | 是 | 前端AI会话配置对象数组，每个对象包含AI会话类型及对应的生命周期回调方法。当前仅支持 [AISessionType](arkts-arkweb-aisessiontype-e.md#aisessiontype)中包含的模型。 |

## allowWindowOpenMethod

```TypeScript
allowWindowOpenMethod(flag : boolean)
```

设置网页是否可以通过JavaScript自动打开新窗口。 > **说明：** > > - 该属性仅在[javaScriptAccess](#javascriptaccess)开启时生效。 > > - 该属性在[multiWindowAccess](#multiwindowaccess)开启时打开新窗口，关闭时打开本地窗口。 > > - 该属性的默认值与系统属性`persist.web.allowWindowOpenMethod.enabled`保持一致，如果未设置系统属性则默认值为false。 > > - 通过`hdc shell param get persist.web.allowWindowOpenMethod.enabled` 检查是否开启系统属性 > `persist.web.allowWindowOpenMethod.enabled`。若属性值为1代表开启系统属性；若属性值为0或不存在，代表未开启系统属性，可通过命令 > `hdc shell param set persist.web.allowWindowOpenMethod.enabled 1` 开启系统属性。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-allowWindowOpenMethod(flag : boolean): WebAttribute--><!--Device-WebAttribute-allowWindowOpenMethod(flag : boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | boolean | 是 | <br>true表示网页可以通过JavaScript自动打开新窗口，该属性为false时，用户行为仍可通过JavaScript自动打开新窗口，但非用户行为不能通过JavaScript自动打开新窗口。 <br>此处的用户行为是指，在用户对Web组件进行点击等操作后，同时在5秒内请求打开新窗口（window.open）的行为。 <br>默认值与系统属性关联，当系统属性`persist.web.allowWindowOpenMethod.enabled`为true时，默认值为true，如果未设置系统属性则默认值为false。 |

## backToTop

```TypeScript
backToTop(backToTop: boolean)
```

设置Web组件是否启用点击状态栏网页回到顶部功能。当属性没有显式调用时，默认开启状态栏网页回到顶部功能。

**起始版本：** 22

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-WebAttribute-backToTop(backToTop: boolean): WebAttribute--><!--Device-WebAttribute-backToTop(backToTop: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| backToTop | boolean | 是 | 是否启用Web点击状态栏回顶，true表示启用，false表示不启用。 <br>传入undefined或null时为true。 |

## bindSelectionMenu

```TypeScript
bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType,
      options?: SelectionMenuOptionsExt)
```

设置自定义选择菜单。

**起始版本：** 13

**ArkTS模式：** 起始版本为13。

**废弃版本：** -1

<!--Device-WebAttribute-bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType,      options?: SelectionMenuOptionsExt): WebAttribute--><!--Device-WebAttribute-bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType,      options?: SelectionMenuOptionsExt): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementType | [WebElementType](arkts-arkweb-webelementtype-e.md) | 是 | 菜单的类型。 |
| content | CustomBuilder | 是 | 菜单的内容。 |
| responseType | [WebResponseType](arkts-arkweb-webresponsetype-e.md) | 是 | 菜单的响应类型。 |
| options | [SelectionMenuOptionsExt](arkts-arkweb-selectionmenuoptionsext-i.md) | 否 | 菜单的选项。传入undefined或null时使用默认配置。 |

## blankScreenDetectionConfig

```TypeScript
blankScreenDetectionConfig(detectConfig: BlankScreenDetectionConfig)
```

设置白屏检测的策略配置，如使能开关、检测时间和检测策略等。当属性没有显式调用时，默认关闭白屏检测。 > **说明：** > > - 根据detectConfig的配置，在网页加载后检测到白屏或者近似白屏现象，可触发回调[onDetectedBlankScreen](#ondetectedblankscreen)。 > > - 设置后下次导航生效。 > > - 当用户与网页发生交互后，不再会继续检查是否白屏。 > > - 不支持layoutMode为WebLayoutMode.FIT_CONTENT的场景。

**起始版本：** 22

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-WebAttribute-blankScreenDetectionConfig(detectConfig: BlankScreenDetectionConfig): WebAttribute--><!--Device-WebAttribute-blankScreenDetectionConfig(detectConfig: BlankScreenDetectionConfig): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| detectConfig | [BlankScreenDetectionConfig](arkts-arkweb-blankscreendetectionconfig-i.md) | 是 | 白屏检测的策略配置。 |

## blockNetwork

```TypeScript
blockNetwork(block: boolean)
```

设置Web组件是否阻止从网络加载资源。当属性没有显式调用时，默认允许从网络加载资源。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-blockNetwork(block: boolean): WebAttribute--><!--Device-WebAttribute-blockNetwork(block: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| block | boolean | 是 | 设置Web组件是否允许从网络加载资源。 <br>true表示不允许从网络加载资源，false表示允许从网络加载资源。 <br>传入undefined或null时为false。 |

## blurOnKeyboardHideMode

```TypeScript
blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode)
```

设置当软键盘收起时Web元素失焦模式。当属性没有显式调用时，默认按[BlurOnKeyboardHideMode.SILENT](arkts-arkweb-bluronkeyboardhidemode-e.md#bluronkeyboardhidemode)模式处理。

**起始版本：** 14

**ArkTS模式：** 起始版本为14。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode): WebAttribute--><!--Device-WebAttribute-blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [BlurOnKeyboardHideMode](arkts-arkweb-bluronkeyboardhidemode-e.md) | 是 | 设置当软键盘收起时Web元素失焦关闭或开启。默认值：`BlurOnKeyboardHideMode.SILENT`。 |

## bypassVsyncCondition

```TypeScript
bypassVsyncCondition(condition: WebBypassVsyncCondition)
```

当开发者调用scrollBy接口进行页面滚动时，可以通过bypassVsyncCondition接口设置渲染流程跳过vsync（垂直同步）调度，直接触发绘制。该属性没有显式调用时，默认不跳过vsync调度。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-bypassVsyncCondition(condition: WebBypassVsyncCondition): WebAttribute--><!--Device-WebAttribute-bypassVsyncCondition(condition: WebBypassVsyncCondition): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | [WebBypassVsyncCondition](arkts-arkweb-webbypassvsynccondition-e.md) | 是 | 触发渲染流程跳过vsync调度的条件。 <br> 传入undefined或null时为NONE。 |

## cacheMode

```TypeScript
cacheMode(cacheMode: CacheMode)
```

设置缓存模式。当属性没有显式调用时，默认为`CacheMode.Default`。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-cacheMode(cacheMode: CacheMode): WebAttribute--><!--Device-WebAttribute-cacheMode(cacheMode: CacheMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cacheMode | [CacheMode](arkts-arkweb-cachemode-e.md) | 是 | 要设置的缓存模式。 <br>传入undefined或null时为CacheMode.Default。 |

## copyOptions

```TypeScript
copyOptions(value: CopyOptions)
```

设置剪贴板复制范围选项。该属性没有显式调用时，默认支持复制后在当前设备所有应用内粘贴。 > **说明：** > > 当设置为CopyOptions.None时，[dataDetectorConfig](#datadetectorconfig)中的enablePreviewMenu配置项无效。当 > [enableDataDetector](#enabledatadetector)设置为true且此属性设置为CopyOptions.LocalDevice时，AI菜单功能将被激活。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-copyOptions(value: CopyOptions): WebAttribute--><!--Device-WebAttribute-copyOptions(value: CopyOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CopyOptions | 是 | 要设置的剪贴板复制范围选项。 <br>传入undefined或null时为CopyOptions.None。 |

## darkMode

```TypeScript
darkMode(mode: WebDarkMode)
```

设置Web深色模式。当属性没有显式调用时，默认关闭。 当深色模式开启时，Web将启用媒体查询prefers-color-scheme中网页所定义的深色样式，若网页未定义深色样式，则保持原状。如需开启强制深色模式，建议配合 [forceDarkAccess](#forcedarkaccess)使用。深色模式具体用法可参考[Web深色模式适配](../../../web/web-set-dark-mode.md)。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-darkMode(mode: WebDarkMode): WebAttribute--><!--Device-WebAttribute-darkMode(mode: WebDarkMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebDarkMode](arkts-arkweb-webdarkmode-e.md) | 是 | 设置Web的深色模式为关闭、开启或跟随系统。 <br>传入null或undefined时为`WebDarkMode.Off`。 |

## dataDetectorConfig

```TypeScript
dataDetectorConfig(config: TextDataDetectorConfig)
```

设置文本识别配置。 需配合[enableDataDetector](#enabledatadetector)一起使用，设置enableDataDetector为true时，dataDetectorConfig的配置 才能生效。 当两个实体A、B重叠时，按以下规则保留实体： 1. 若A&nbsp;⊂&nbsp;B，则保留B，反之则保留A。 2. 当A&nbsp;⊄&nbsp;B且B&nbsp;⊄&nbsp;A时，若A.start&nbsp;&lt;&nbsp;B.start，则保留A，反之则保留B。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-dataDetectorConfig(config: TextDataDetectorConfig): WebAttribute--><!--Device-WebAttribute-dataDetectorConfig(config: TextDataDetectorConfig): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | TextDataDetectorConfig | 是 | 文本识别配置。 |

## databaseAccess

```TypeScript
databaseAccess(databaseAccess: boolean)
```

设置Web SQL数据库存储API权限，若未显式调用，此权限默认关闭。 > **说明：** > > - 本接口在ArkWeb内核升级到M132版本后因内核废弃Web SQL，对Web SQL数据库的控制失效。ArkWeb内核版本参考ArkWeb简介 > [约束与限制](../../../web/web-component-overview.md#约束与限制)。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-databaseAccess(databaseAccess: boolean): WebAttribute--><!--Device-WebAttribute-databaseAccess(databaseAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| databaseAccess | boolean | 是 | 设置是否开启Web SQL数据库存储API权限。 <br>true表示开启，false表示关闭。 <br>传入undefined或null时为false。 |

## defaultFixedFontSize

```TypeScript
defaultFixedFontSize(size: number)
```

设置网页的默认等宽字体大小。对于html前端使用monospace字体且未指定font-size样式的元素，将按此值渲染字体大小。 当属性没有显式调用时，默认等宽字体大小为13。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-defaultFixedFontSize(size: number): WebAttribute--><!--Device-WebAttribute-defaultFixedFontSize(size: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置网页的默认等宽字体大小，单位px。 <br>输入值的范围为[-2^31, 2^31-1]，实际渲染时超过72px的值按照72px进行渲染，低于1px的值按照1px进行渲染。 <br>传入null或undefined时为13。 |

## defaultFontSize

```TypeScript
defaultFontSize(size: number)
```

设置网页的默认字体大小。对于html前端使用非monospace字体且未指定font-size样式的元素，将按此值渲染字体大小。 当属性没有显式调用时，网页的默认字体大小为16。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-defaultFontSize(size: number): WebAttribute--><!--Device-WebAttribute-defaultFontSize(size: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置网页的默认字体大小，单位px。 <br>输入值的范围为[-2^31, 2^31-1]，实际渲染时超过72px的值按照72px进行渲染，低于1px的值按照1px进行渲染。 <br>传入null或undefined时为16。 |

## defaultTextEncodingFormat

```TypeScript
defaultTextEncodingFormat(textEncodingFormat: string)
```

设置网页的默认字符编码。当属性没有显式调用时，网页的默认字符编码为"UTF-8"。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-defaultTextEncodingFormat(textEncodingFormat: string): WebAttribute--><!--Device-WebAttribute-defaultTextEncodingFormat(textEncodingFormat: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textEncodingFormat | string | 是 | 默认字符编码。 <br>传入null或undefined时为"UTF-8"。 |

## domStorageAccess

```TypeScript
domStorageAccess(domStorageAccess: boolean)
```

设置是否开启文档对象模型存储接口（DOM Storage API）权限，当属性没有显式调用时，默认不开启文档对象模型存储接口（DOM Storage API）权限。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-domStorageAccess(domStorageAccess: boolean): WebAttribute--><!--Device-WebAttribute-domStorageAccess(domStorageAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domStorageAccess | boolean | 是 | 设置是否开启文档对象模型存储接口（DOM Storage API）权限。 <br>true表示开启，false表示不开启。 <br>传入undefined或null时为false。 |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: EditMenuOptions)
```

设置Web组件自定义文本选择菜单。 > **说明：** > > 本接口与bindSelectionMenu功能类似，差异如下： > > - editMenuOptions：在系统默认菜单风格基础上添加扩展项，触发条件不变。 > > - [bindSelectionMenu](#bindselectionmenu)：完全自定义菜单风格和触发条件，由开发者定义。 > > 两者不宜同时使用，建议根据自定义程度需求选择。 > 用户可以通过该属性设置自定义的文本菜单。 在onCreateMenu中，可以修改、增加、删除菜单选项，如果希望不显示文本菜单，需要返回空数组。 在onMenuItemClick中，可以自定义菜单选项的回调函数。该函数在菜单选项被点击后触发，并根据返回值决定是否执行系统默认的回调。返回true 不执行系统回调，返回false继续执行系统回调。 在[onPrepareMenu&lt;sup&gt;20+&lt;/sup&gt;](../../../reference/apis-arkui/arkui-ts/ts-text-common.md#属性-1)中，当文本选择区域变化后显示菜单之前触发该 回调，可在该回调中进行修改、增加、删除菜单选项，实现动态更新菜单。 本接口在与[selectionMenuOptions&lt;sup&gt;(deprecated)&lt;/sup&gt;](#selectionmenuoptions)同时使用时，会使 selectionMenuOptions&lt;sup&gt;(deprecated)&lt;/sup&gt;不生效。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

<!--Device-WebAttribute-editMenuOptions(editMenu: EditMenuOptions): WebAttribute--><!--Device-WebAttribute-editMenuOptions(editMenu: EditMenuOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | EditMenuOptions | 是 | Web自定义文本菜单选项。 <br>菜单项数量，及菜单的content大小、icon图标尺寸，与ArkUI Menu组件保持一致。 <br>菜单中系统自带的id枚举值（TextMenuItemId）在Web中仅支持CUT、COPY、PASTE、SELECT_ALL、TRANSLATE、SEARCH、 AI_WRITER七项。 <br>onMenuItemClick函数中textRange参数在Web中无意义，传入值为-1。 |

## enableAutoFill

```TypeScript
enableAutoFill(value: boolean)
```

设置是否启用网页自动填充，默认开启。 &lt;!--RP1--&gt; > **说明：** > > 本接口的自动填充功能，依赖“智能填充服务”和“密码填充服务”的支持。 &lt;!--RP1End--&gt;

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-WebAttribute-enableAutoFill(value: boolean): WebAttribute--><!--Device-WebAttribute-enableAutoFill(value: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否启用网页自动填充，true表示启用，false表示不启用。 <br>传入undefined或null时为true。 |

## enableDataDetector

```TypeScript
enableDataDetector(enable: boolean)
```

设置是否识别网页文本特殊实体，如邮件、电话、网址等。该接口依赖设备底层具备文本识别能力，否则设置无效。该属性没有显式调用时，默认不启用。 > **说明：** > > [dataDetectorConfig](#datadetectorconfig)和 > [enableSelectedDataDetector](#enableselecteddatadetector)等属性依赖此属性开启时才能正常生效。 > 当enableDataDetector设置为true，同时不设置[dataDetectorConfig](#datadetectorconfig)属性时，默认识别所有类型的实体，所识别实体的 > color和decoration会被更改为如下样式： &lt;!--code_no_check--&gt; 当enableDataDetector设置为true且[copyOptions](#copyoptions)设置为CopyOptions.LocalDevice时，AI菜单功能将被激活。此时，在 网页中选中文本后，文本选择菜单能够展示对应的AI菜单项，包括TextMenuItemId中的url（打开链接）、email（新建邮件）、phoneNumber（呼叫）、address （导航至该位置）、dateTime（新建日程提醒）。 AI菜单生效时，需在选中范围内，包括一个完整的AI实体，才能展示对应的选项。该菜单项与TextMenuItemId中的askAI菜单项不同时出现。 示例使用场景详见[使用Web组件的智能分词能力](../../../web/web-data-detector.md)。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-enableDataDetector(enable: boolean): WebAttribute--><!--Device-WebAttribute-enableDataDetector(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用Web文本识别，true表示启用，false表示不启用。 <br>传入undefined或null时属性设置不生效。 |

## enableDefaultContextMenu

```TypeScript
enableDefaultContextMenu(enable: boolean)
```

设置是否启用默认右键上下文菜单。不调用该方法时，默认不启用。默认菜单仅支持CUT、COPY、PASTE、SELECT_ALL菜单项。 > **说明：** > > - 当设置了[onContextMenuShow](#oncontextmenushow)回调并在回调中返回true时，本接口的设置不生效。 > > - 默认菜单项会受[editMenuOptions](#editmenuoptions)控制，通过该属性可以自定义菜单选项。

**起始版本：** 24

**ArkTS模式：** 起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-enableDefaultContextMenu(enable: boolean): WebAttribute--><!--Device-WebAttribute-enableDefaultContextMenu(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用默认右键上下文菜单，true表示启用，false表示不启用。 <br>传入undefined或null时为false。 |

## enableDrag

```TypeScript
enableDrag(value: boolean)
```

设置是否启用拖拽功能。不调用该属性时，默认启用网页拖拽功能。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-enableDrag(value: boolean): WebAttribute--><!--Device-WebAttribute-enableDrag(value: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否启用网页拖拽功能，true表示启用，false表示不启用。传入undefined或null时为true。 |

## enableFollowSystemFontWeight

```TypeScript
enableFollowSystemFontWeight(follow: boolean)
```

设置Web组件是否开启字重跟随系统设置变化。当属性没有显式调用时，Web组件默认字重不跟随系统设置变化。 > **说明：** > > 目前该能力只支持前端文本元素跟随变化，暂不支持canvas元素、内嵌docx和pdf格式中的文本跟随变化。

**起始版本：** 18

**ArkTS模式：** 起始版本为18。

**废弃版本：** -1

<!--Device-WebAttribute-enableFollowSystemFontWeight(follow: boolean): WebAttribute--><!--Device-WebAttribute-enableFollowSystemFontWeight(follow: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| follow | boolean | 是 | 设置Web组件是否开启字重跟随系统设置变化。 <br>true表示字重跟随系统设置中的字体粗细变化，系统设置改变时字重跟随变化。false表示字重不再跟随系统设置中的字体粗细变化，系统设置改变时维持当前字重不变。 <br>传入undefined或null时为false。 |

## enableFullscreenVideoOverlay

```TypeScript
enableFullscreenVideoOverlay(enabled: boolean)
```

设置 Web 组件是否开启覆盖式全屏播放功能。当属性没有显式调用时，默认不开启该能力。 > **说明：** > > - 当前只支持H264、H265解码格式的视频。 > > - 只有视频元素发出的全屏请求才会响应。 > 26.0.0

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-enableFullscreenVideoOverlay(enabled: boolean): WebAttribute--><!--Device-WebAttribute-enableFullscreenVideoOverlay(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置 Web 组件是否开启覆盖式全屏播放功能。 <br>true 表示开启该功能。 <br>false 表示不开启。 <br>传入 undefined 或 null 时为 false。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enabled: boolean)
```

设置Web组件长按文本选择是否开启振动。需配置"ohos.permission.VIBRATE"。该属性没有显式调用时，默认开启振动。

**起始版本：** 13

**ArkTS模式：** 起始版本为13。

**废弃版本：** -1

<!--Device-WebAttribute-enableHapticFeedback(enabled: boolean): WebAttribute--><!--Device-WebAttribute-enableHapticFeedback(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否开启振动。 <br>true表示开启振动，false表示不开启振动。 <br>传入undefined或null时保持默认值，即开启振动。 |

## enableImageAnalyzer

```TypeScript
enableImageAnalyzer(enable: boolean)
```

设置是否启用网页图片AI分析，当前支持图片文字识别功能。属性未显式调用时，该功能默认开启。 > **说明：** > > 长按或鼠标悬停在图片文字上时，触发图片AI分析，可以选中图片中的文字。能够触发分析的图片规格如下。 > > - 图片的原始长宽均不小于100px。 > > - 在[设备类型](../../../quick-start/module-configuration-file.md#devicetypes标签)不为2in1的设备上，需要图片渲染宽度超过网页宽度的80%。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-WebAttribute-enableImageAnalyzer(enable: boolean): WebAttribute--><!--Device-WebAttribute-enableImageAnalyzer(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用网页图片AI分析，true表示启用，false表示不启用。 <br>传入undefined或null时重置为true。 |

## enableMediaNetworkProxy

```TypeScript
enableMediaNetworkProxy(enabled: boolean)
```

设置Web组件是否开启媒体资源网络请求代理功能。当属性没有显式调用时，默认不开启该能力。 > **说明：** > > - 当前只支持HLS流媒体视频。 > 26.0.0

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-enableMediaNetworkProxy(enabled: boolean): WebAttribute--><!--Device-WebAttribute-enableMediaNetworkProxy(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置Web组件是否开启媒体资源网络请求代理功能。 <br>true表示开启该功能。 <br>false表示不开启。 |

## enableNativeEmbedMode

```TypeScript
enableNativeEmbedMode(enabled: boolean)
```

设置是否开启同层渲染功能。当该方法没有显式调用时，默认不开启同层渲染功能。 > **说明：** > > [registerNativeEmbedRule](#registernativeembedrule)和 > [nativeEmbedOptions](#nativeembedoptions)等接口依赖此属性开启时才生效。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-enableNativeEmbedMode(enabled: boolean): WebAttribute--><!--Device-WebAttribute-enableNativeEmbedMode(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否开启同层渲染功能。 <br>true表示开启同层渲染功能，false表示不开启同层渲染功能。 <br>传入undefined或null时为false。 |

## enableNativeMediaPlayer

```TypeScript
enableNativeMediaPlayer(config: NativeMediaPlayerConfig)
```

开启[应用接管网页媒体播放功能](../../../web/app-takeovers-web-media.md)。当属性没有显式调用时，默认不开启接管网页媒体播放功能。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-enableNativeMediaPlayer(config: NativeMediaPlayerConfig): WebAttribute--><!--Device-WebAttribute-enableNativeMediaPlayer(config: NativeMediaPlayerConfig): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [NativeMediaPlayerConfig](arkts-arkweb-nativemediaplayerconfig-i.md) | 是 | 应用接管网页媒体播放功能的配置对象。包含以下属性：enable（boolean 类型，是否开启该功能，默认为 false）， shouldOverlay（boolean 类型，当功能开启后，应用接管网页视频的播放器画面是否覆盖网页内容，默认为 false）。 <br>传入 undefined 或 null 时为`{enable: false, shouldOverlay: false}`。 |

## enableScrollDirectionalLock

```TypeScript
enableScrollDirectionalLock(value: boolean, type: ScrollDirectionalLockType)
```

设置Web组件滑动方向锁定，防止用户在斜向滑动时同时触发水平和垂直滚动，提升滚动体验。不调用该方法设置时，默认在嵌套滚动场景下支持滑动方向锁定。ALL模式适用于所有需要锁定滑动的场景，NESTED_SCROLL模式仅适用于嵌套滚动 场景。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-enableScrollDirectionalLock(value: boolean, type: ScrollDirectionalLockType): WebAttribute--><!--Device-WebAttribute-enableScrollDirectionalLock(value: boolean, type: ScrollDirectionalLockType): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持滑动方向锁定。`true` 表示滑动方向锁定，滚动视图会根据用户初始滑动的方向来锁定滚动轴，`false` 表示不锁定。 |
| type | [ScrollDirectionalLockType](arkts-arkweb-scrolldirectionallocktype-e.md) | 是 | 设置Web组件在哪些场景下希望滑动方向锁定。ALL表示所有场景都支持滑动锁定，NESTED_SCROLL表示在嵌套滚动场景下支持滑动锁定。 |

## enableSelectedDataDetector

```TypeScript
enableSelectedDataDetector(enable: boolean)
```

设置是否启用文本选择的AI菜单功能，启用后可识别选区中的邮件、电话、网址、日期、地址等，并在文本选择菜单中展示对应的AI菜单项。默认启用AI菜单功能。 AI菜单功能启用时，在网页中选中文本后，文本选择菜单能够展示对应的AI菜单项，包括TextMenuItemId中的url（打开链接）、email（新建邮件）、phoneNumber（ 呼叫）、address（导航前往）、dateTime（新建日程）。 AI菜单生效时，需在选中范围内，包括一个完整的AI实体，才能展示对应的选项。该菜单项与TextMenuItemId中的askAI菜单项不同时出现。 示例使用场景详见[使用Web组件的智能分词能力](../../../web/web-data-detector.md)。

**起始版本：** 22

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-WebAttribute-enableSelectedDataDetector(enable: boolean): WebAttribute--><!--Device-WebAttribute-enableSelectedDataDetector(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用Web文本识别，true表示启用，false表示不启用。 <br>传入undefined或null时属性重置为默认值。 |

## enableWebAVSession

```TypeScript
enableWebAVSession(enabled: boolean)
```

设置是否支持应用对接到播控中心。当属性没有显式设置时，默认支持应用对接到播控中心。

**起始版本：** 18

**ArkTS模式：** 起始版本为18。

**废弃版本：** -1

<!--Device-WebAttribute-enableWebAVSession(enabled: boolean): WebAttribute--><!--Device-WebAttribute-enableWebAVSession(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置是否支持应用对接到播控中心。 <br>true表示支持应用对接到播控中心，false表示不支持应用对接到播控中心。 <br>传入undefined或null时为true。 |

## fileAccess

```TypeScript
fileAccess(fileAccess: boolean)
```

设置是否开启应用中文件系统的访问。[\$rawfile(filepath/filename)](../../../quick-start/resource-categories-and-access.md#资源访问)中的文件不受该 属性影响而被限制访问。API version 11及以前，当属性没有显式调用时，默认开启应用中文件系统的访问。API version 12及以后，当属性没有显式调用时，默认不开启应用中文件系统的访问。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-fileAccess(fileAccess: boolean): WebAttribute--><!--Device-WebAttribute-fileAccess(fileAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fileAccess | boolean | 是 | 设置是否开启应用中文件系统的访问。 <br>true表示开启，false表示不开启。 <br>同时，当fileAccess为false的时候，仅只读资源目录`/data/storage/el1/bundle/entry/resources/resfile`里面的资源依然可以通过file协议访问，不受 fileAccess管控。 <br>API version 11及以前，传入undefined或null时为true，API version 12及以后传入undefined或null时为false。 |

## forceDarkAccess

```TypeScript
forceDarkAccess(access: boolean)
```

设置网页是否开启强制深色模式。该属性仅在[darkMode](#darkmode)开启深色模式时生效。当属性没有显式调用时，默认网页不开启强制深色模式。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-forceDarkAccess(access: boolean): WebAttribute--><!--Device-WebAttribute-forceDarkAccess(access: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access | boolean | 是 | 设置网页是否开启强制深色模式。 <br>true表示开启，false表示设置不开启。 <br>传入null或undefined时为false。 |

## forceDisplayScrollBar

```TypeScript
forceDisplayScrollBar(enabled: boolean)
```

设置滚动条是否常驻。在常驻状态下，当页面大小超过一页时，滚动条出现且不消失。该属性没有显式调用时，默认设置滚动条不常驻。 全量展开模式下不支持滚动条常驻，即layoutMode为WebLayoutMode.FIT_CONTENT模式时，参数enabled为false。 > **说明：** > > - 该接口在当前应用的所有Web组件中全局生效。多个Web组件设置不同值时，以首次设置的值为准。 > > - 若同时调用[setScrollbarMode](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#setscrollbarmode)，该接口设置不生效。

**起始版本：** 14

**ArkTS模式：** 起始版本为14。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-forceDisplayScrollBar(enabled: boolean): WebAttribute--><!--Device-WebAttribute-forceDisplayScrollBar(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 滚动条是否常驻。 <br>true表示滚动条常驻，false表示滚动条不常驻。 <br>当layoutMode为WebLayoutMode.FIT_CONTENT模式时，enabled参数强制为false，设置true也不生效。 <br>传入undefined或null时属性设置不生效。 |

## forceEnableZoom

```TypeScript
forceEnableZoom(enable: boolean)
```

设置Web组件是否启用强制缩放功能。

**起始版本：** 21

**ArkTS模式：** 起始版本为21。

**废弃版本：** -1

<!--Device-WebAttribute-forceEnableZoom(enable: boolean): WebAttribute--><!--Device-WebAttribute-forceEnableZoom(enable: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 设置是否遵从网页中`&lt;meta name="viewport"&gt;`标签设置的缩放限制。 <br>设置为`true`时，不遵从网页缩放限制；设置为`false`时，遵从网页缩放限制。 <br>传入`undefined`与`null`时属性设置不生效。 |

## geolocationAccess

```TypeScript
geolocationAccess(geolocationAccess: boolean)
```

设置是否开启获取地理位置权限。当属性没有显式调用时，默认开启。具体使用方式参考[管理位置权限](../../../web/web-geolocation-permission.md)。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-geolocationAccess(geolocationAccess: boolean): WebAttribute--><!--Device-WebAttribute-geolocationAccess(geolocationAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| geolocationAccess | boolean | 是 | 设置是否开启获取地理位置权限。 <br>true表示开启，false表示不开启。 <br>传入undefined或null时为false。 |

## gestureFocusMode

```TypeScript
gestureFocusMode(mode: GestureFocusMode)
```

设置Web组件手势获焦模式，用于控制Web组件的焦点响应行为。该属性没有显式调用时，默认表示手势按下时，任何手势均会使Web组件获焦。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-gestureFocusMode(mode: GestureFocusMode): WebAttribute--><!--Device-WebAttribute-gestureFocusMode(mode: GestureFocusMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [GestureFocusMode](arkts-arkweb-gesturefocusmode-e.md) | 是 | 设置Web组件手势获焦模式。传入undefined或null时为GestureFocusMode.DEFAULT。 |

## horizontalScrollBarAccess

```TypeScript
horizontalScrollBarAccess(horizontalScrollBar: boolean)
```

设置是否显示横向滚动条，包括系统默认滚动条和用户自定义滚动条。该属性没有显式调用时，默认显示。 > **说明：** > > - 通过[@State](../../../ui/state-management/arkts-state.md)变量控制横向滚动条的隐藏/显示后，需要调用 > [controller.refresh()](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#refresh)生效。 > > - 通过[@State](../../../ui/state-management/arkts-state.md)变量频繁动态改变时，建议切换开关变量和Web组件一一对应。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-horizontalScrollBarAccess(horizontalScrollBar: boolean): WebAttribute--><!--Device-WebAttribute-horizontalScrollBarAccess(horizontalScrollBar: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| horizontalScrollBar | boolean | 是 | 设置是否显示横向滚动条。 <br>true表示显示，false表示不显示。 <br>传入undefined或null时为false。 |

## imageAccess

```TypeScript
imageAccess(imageAccess: boolean)
```

设置是否允许自动加载图片资源。当属性没有显式调用时，默认允许。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-imageAccess(imageAccess: boolean): WebAttribute--><!--Device-WebAttribute-imageAccess(imageAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageAccess | boolean | 是 | 设置是否允许自动加载图片资源。 <br>true 表示允许，false 表示不允许。 <br>传入 undefined 或 null 时为 false。 |

## initialScale

```TypeScript
initialScale(percent: number)
```

设置整体页面的缩放百分比。该属性没有显式调用时，默认为100。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-initialScale(percent: number): WebAttribute--><!--Device-WebAttribute-initialScale(percent: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| percent | number | 是 | 要设置的整体页面的缩放百分比。 <br>取值范围：(0, 1000]。 <br>传入undefined或null时属性设置不生效。 |

## javaScriptAccess

```TypeScript
javaScriptAccess(javaScriptAccess: boolean)
```

设置是否允许执行JavaScript脚本。当属性没有显式调用时，默认允许。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-javaScriptAccess(javaScriptAccess: boolean): WebAttribute--><!--Device-WebAttribute-javaScriptAccess(javaScriptAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| javaScriptAccess | boolean | 是 | 是否允许执行JavaScript脚本。 <br>true表示允许，false表示不允许。 <br>传入undefined或null时为false。 |

## javaScriptOnDocumentEnd

```TypeScript
javaScriptOnDocumentEnd(scripts: Array<ScriptItem>)
```

将JavaScript脚本注入到Web组件中，当指定页面或者文档加载完成时，该脚本将在其来源与scriptRules匹配的任何页面中执行。当属性没有显式调用时，默认不将JavaScript脚本注入到Web组件中。 > **说明：** > > - 该脚本将在页面的任何JavaScript代码之后运行，并且DOM树此时已经加载、渲染完毕。 > > - 该脚本按照字典序执行，非数组本身顺序。 > > - 内容相同的脚本多次注入时将被静默去重，不展示，不提醒，使用首次注入时的scriptRules。 > > - 本接口不支持[UrlRegexRule](arkts-arkweb-urlregexrule-i.md#urlregexrule)。 > > - 建议使用[runJavaScriptOnDocumentEnd](#runjavascriptondocumentend)代替。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-javaScriptOnDocumentEnd(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-javaScriptOnDocumentEnd(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | Array&lt;[ScriptItem](arkts-arkweb-scriptitem-i.md)&gt; | 是 | 需要注入的ScriptItem数组。 <br>传入undefined或null时不将JavaScript脚本注入到Web组件中。 |

## javaScriptOnDocumentStart

```TypeScript
javaScriptOnDocumentStart(scripts: Array<ScriptItem>)
```

将JavaScript脚本注入到Web组件中，当指定页面或者文档开始加载时，该脚本将在其来源与scriptRules匹配的任何页面中执行。当属性没有显式调用时，默认不将JavaScript脚本注入到Web组件中。 > **说明：** > > - 网页文档根元素（HTML Element）创建后、但尚未加载任何其他内容之前注入脚本。 > > - 该脚本按照字典序执行，非数组本身顺序，若需数组本身顺序，建议使用[runJavaScriptOnDocumentStart](#runjavascriptondocumentstart) > 接口。 > > - 内容相同的脚本多次注入时将被静默去重，不展示，不提醒，使用首次注入时的scriptRules。 > > - 本接口不支持[UrlRegexRule](arkts-arkweb-urlregexrule-i.md#urlregexrule)。 > > - 建议使用[runJavaScriptOnDocumentStart](#runjavascriptondocumentstart)代替。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-javaScriptOnDocumentStart(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-javaScriptOnDocumentStart(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | Array&lt;[ScriptItem](arkts-arkweb-scriptitem-i.md)&gt; | 是 | 需要注入的ScriptItem数组。 <br>传入undefined或null时不将JavaScript脚本注入到Web组件中。 |

## javaScriptProxy

```TypeScript
javaScriptProxy(javaScriptProxy: JavaScriptProxy)
```

将javaScriptProxy中的ArkTS对象注册到Web组件中，该对象将使用JavaScriptProxy中指定的名称注册到网页的所有框架中，包括所有iframe，这使得JavaScript可以调用 javaScriptProxy中ArkTS对象的方法。 > **说明：** > > javaScriptProxy接口需要和 > [deleteJavaScriptRegister&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#deletejavascriptregister) > 接口配合使用，防止内存泄漏。 > > javaScriptProxy对象的所有参数不支持更新。 > > 注册javaScriptProxy对象时，同步与异步列表请至少选择一项不为空，可同时注册两类方法。 > > 此接口只支持注册一个对象，若需要注册多个对象请使用 > [registerJavaScriptProxy&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#registerjavascriptproxy) > 。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-javaScriptProxy(javaScriptProxy: JavaScriptProxy): WebAttribute--><!--Device-WebAttribute-javaScriptProxy(javaScriptProxy: JavaScriptProxy): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| javaScriptProxy | [JavaScriptProxy](arkts-arkweb-javascriptproxy-i.md) | 是 | 参与注册的对象。只能声明方法，不能声明属性。 <br>传入undefined或null时不将javaScriptProxy中的ArkTS对象注册到Web组件中。<br>**起始版本：** 12 |

## keyboardAppearance

```TypeScript
keyboardAppearance(mode: WebKeyboardAppearanceMode)
```

设置键盘外观模式，用于控制Web组件内输入框弹出键盘的外观样式，包括沉浸式和非沉浸式模式。不调用该方法时，默认跟随系统的沉浸式模式。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-keyboardAppearance(mode: WebKeyboardAppearanceMode): WebAttribute--><!--Device-WebAttribute-keyboardAppearance(mode: WebKeyboardAppearanceMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebKeyboardAppearanceMode](arkts-arkweb-webkeyboardappearancemode-e.md) | 是 | 键盘外观。传入undefined或null时，跟随系统的沉浸式模式。 |

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode(mode: WebKeyboardAvoidMode)
```

Web组件自定义软件键盘避让模式。 当UIContext设置的键盘避让模式为[KeyboardAvoidMode.RESIZE](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-keyboardavoidmode-e.md#keyboardavoidmode)模式时，该接口功能不生效。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-keyboardAvoidMode(mode: WebKeyboardAvoidMode): WebAttribute--><!--Device-WebAttribute-keyboardAvoidMode(mode: WebKeyboardAvoidMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebKeyboardAvoidMode](arkts-arkweb-webkeyboardavoidmode-e.md) | 是 | Web软键盘避让模式。 <br>嵌套滚动场景下不推荐使用web软键盘避让，包括RESIZE_VISUAL与RESIZE_CONTENT。 <br>默认值：`WebKeyboardAvoidMode.RESIZE_CONTENT`避让行为。 |

## layoutMode

```TypeScript
layoutMode(mode: WebLayoutMode)
```

设置Web布局模式。当属性没有显式调用时，默认Web布局跟随系统模式（WebLayoutMode.NONE）。常见问题请参考[Web组件大小自适应页面内容布局](../../../web/web-fit-content.md)。 > **说明：** > > 目前只支持两种Web布局模式，分别为 > > - Web布局跟随系统（`WebLayoutMode.NONE`）。 > > - Web组件高度基于前端页面高度的自适应网页布局（`WebLayoutMode.FIT_CONTENT`）。 > > Web组件高度基于前端页面自适应布局有如下限制： > > - 当layoutMode设置为WebLayoutMode.FIT_CONTENT > > - [forceDisplayScrollBar](#forcedisplayscrollbar)不支持常驻 > > - [blankScreenDetectionConfig](#blankscreendetectionconfig)不生效 > > - 如果Web组件宽或长度超过7680px，请在Web组件创建的时候指定`RenderMode.SYNC_RENDER`模式，否则会整个白屏。 > > - Web组件创建后不支持动态切换layoutMode模式。 > > - Web组件宽高规格：指定`RenderMode.ASYNC_RENDER`模式时，分别不超过7680px。 > > - 频繁更改页面宽高会触发Web组件重新布局，影响体验。 > > - 不支持瀑布流网页（下拉到底部加载更多）。 > > - 不支持宽度自适应，仅支持高度自适应。 > > - 由于高度自适应网页高度，您无法通过修改组件高度属性来修改组件高度。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-layoutMode(mode: WebLayoutMode): WebAttribute--><!--Device-WebAttribute-layoutMode(mode: WebLayoutMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [WebLayoutMode](arkts-arkweb-weblayoutmode-e.md) | 是 | 设置Web布局模式，跟随系统或自适应布局。 <br>传入null或undefined时为`WebLayoutMode.NONE` |

## mediaOptions

```TypeScript
mediaOptions(options: WebMediaOptions)
```

设置Web媒体播放的策略，其中包括：Web中的音频在重新获焦后能够自动续播的有效期、应用内多个Web实例的音频是否独占。当该属性未显式设置时，默认Web中的音频重新获焦后无法自动续播、应用内多个Web实例的音频是独占的。 > **说明：** > > - 同一Web实例中的多个音频均视为同一音频。 > > - 该媒体播放策略将同时管控有声视频。 > > - 建议为所有Web组件设置相同的[audioExclusive](arkts-arkweb-webmediaoptions-i.md#webmediaoptions)值。 > > - 音视频互相打断在应用内和应用间生效，续播只在应用间生效。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-mediaOptions(options: WebMediaOptions): WebAttribute--><!--Device-WebAttribute-mediaOptions(options: WebMediaOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [WebMediaOptions](arkts-arkweb-webmediaoptions-i.md) | 是 | 设置Web的媒体策略。 <br>属性参数更新后需重新播放音频方可生效。 <br>传入undefined或null时为`{resumeInterval: 0, audioExclusive: true}` |

## mediaPlayGestureAccess

```TypeScript
mediaPlayGestureAccess(access: boolean)
```

设置有声视频的自动播放是否需要用户手动点击，静音视频播放不受该接口管控。当该属性未显式设置时，默认需要用户手动点击。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-mediaPlayGestureAccess(access: boolean): WebAttribute--><!--Device-WebAttribute-mediaPlayGestureAccess(access: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| access | boolean | 是 | 设置有声视频的自动播放是否需要用户手动点击。 <br>true 表示需要用户手动点击，false 表示不需要，能自动播放。 <br>传入 undefined 或 null 时为 false。 |

## metaViewport

```TypeScript
metaViewport(enabled: boolean)
```

设置meta标签的viewport属性是否可用。当属性没有显式调用时，默认支持meta标签的viewport属性。 > **说明：** > > - 当前通过User-Agent中是否含有"Mobile"字段来判断是否开启前端HTML页面中meta标签的viewport属性。当User-Agent中不含有"Mobile"字段时，meta标签中viewport属性默认关 > 闭，此时可通过显式设置metaViewport属性为true来覆盖关闭状态。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-metaViewport(enabled: boolean): WebAttribute--><!--Device-WebAttribute-metaViewport(enabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否支持meta标签的viewport属性。 <br>true表示支持meta标签的viewport属性，将解析viewport属性，并根据viewport属性布局。 <br>false表示不支持meta标签的viewport属性，将不解析viewport属性，进行默认布局。 <br>传入null或undefined时为true。 |

## minFontSize

```TypeScript
minFontSize(size: number)
```

设置网页字体大小最小值。对于html前端元素，若元素字体大小低于该接口设置值，将采用接口设置值渲染字体大小。 当属性没有显式调用时，默认网页字体大小最小值为8。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-minFontSize(size: number): WebAttribute--><!--Device-WebAttribute-minFontSize(size: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置网页字体大小最小值，单位px。 <br>输入值的范围为[-2^31, 2^31-1]，实际渲染时超过72px的值按照72px进行渲染，低于1px的值按照1px进行渲染。 <br>传入null或undefined时为8。 |

## minLogicalFontSize

```TypeScript
minLogicalFontSize(size: number)
```

设置网页逻辑字体大小最小值。 对于html前端未指定font-size样式的元素： 1. 若元素字体大小低于该接口设置值，将采用接口设置值渲染字体大小。 2. 若minLogicalFontSize和minFontSize同时设置时，对于未指定font-size样式元素，将采用两者中的较大值。 当属性没有显式调用时，默认网页逻辑字体大小最小值为8。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-minLogicalFontSize(size: number): WebAttribute--><!--Device-WebAttribute-minLogicalFontSize(size: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 设置网页逻辑字体大小最小值，单位px。 <br>输入值的范围为[-2^31, 2^31-1]，实际渲染时超过72px的值按照72px进行渲染，低于1px的值按照1px进行渲染。 <br>传入null或undefined时为8。 |

## mixedMode

```TypeScript
mixedMode(mixedMode: MixedMode)
```

设定当安全源尝试从非安全源加载资源时的行为。当属性没有显式调用时，默认值为MixedMode.None，即禁止安全源从非安全源加载内容。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-mixedMode(mixedMode: MixedMode): WebAttribute--><!--Device-WebAttribute-mixedMode(mixedMode: MixedMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mixedMode | [MixedMode](arkts-arkweb-mixedmode-e.md) | 是 | 要设置的混合内容模式。 <br>传入undefined或null时为MixedMode.All。 |

## multiWindowAccess

```TypeScript
multiWindowAccess(multiWindow: boolean)
```

设置是否开启多窗口权限。当属性没有显式调用时，默认不开启。 使能多窗口权限时，需要实现onWindowNew事件，示例代码参考[onWindowNew](#onwindownew)。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-multiWindowAccess(multiWindow: boolean): WebAttribute--><!--Device-WebAttribute-multiWindowAccess(multiWindow: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| multiWindow | boolean | 是 | 设置是否开启多窗口权限。 <br>true表示开启，false表示不开启。 |

## nativeEmbedOptions

```TypeScript
nativeEmbedOptions(options?: EmbedOptions)
```

设置同层渲染相关配置，该属性仅在[enableNativeEmbedMode](#enablenativeembedmode)开启时生效，不支持动态修改。当属性没有显式调用时，默认为 `{supportDefaultIntrinsicSize: false}`。

**起始版本：** 16

**ArkTS模式：** 起始版本为16。

**废弃版本：** -1

<!--Device-WebAttribute-nativeEmbedOptions(options?: EmbedOptions): WebAttribute--><!--Device-WebAttribute-nativeEmbedOptions(options?: EmbedOptions): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EmbedOptions](arkts-arkweb-embedoptions-i.md) | 否 | 同层渲染相关配置。 <br>传入undefined或null时为`{supportDefaultIntrinsicSize: false}`。 |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions | NestedScrollOptionsExt)
```

调用以设置嵌套滚动选项。 > **说明：** > > - 可以设置上下左右四个方向，或者设置向前、向后两个方向的嵌套滚动模式，实现与父组件的滚动联动。 > > - 支持嵌套滚动的容器：Grid、List、Scroll、Swiper、 > Tabs、WaterFlow、Refresh、 > bindSheet。 > > - 支持嵌套滚动的输入事件：使用手势、鼠标、触控板。 > > - 嵌套滚动场景下，由于Web滚动到边缘时会优先触发过滚动的过界回弹效果，建议设置[overScrollMode](#overscrollmode)为 > `OverScrollMode.NEVER`，避免影响此场景的用户体验。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-nestedScroll(value: NestedScrollOptions | NestedScrollOptionsExt): WebAttribute--><!--Device-WebAttribute-nestedScroll(value: NestedScrollOptions | NestedScrollOptionsExt): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | NestedScrollOptions \| [NestedScrollOptionsExt](arkts-arkweb-nestedscrolloptionsext-i.md) | 是 | 可滚动组件滚动时的嵌套滚动选项。 <br> value为NestedScrollOptions（向前、向后两个方向）类型时，scrollForward、scrollBackward默认滚动选项为 NestedScrollMode.SELF_FIRST。 <br> value为NestedScrollOptionsExt（上下左右四个方向）类型时，scrollUp、scrollDown、scrollLeft、scrollRight默认滚动选项为 NestedScrollMode.SELF_FIRST。<br>**起始版本：** 14 |

## onActivateContent

```TypeScript
onActivateContent(callback: Callback<void>)
```

Web页面触发window.open(url, name)时，会根据name查找是否存在已绑定的Web实例。若存在，该实例将收到此回调以通知应用需将其展示至前端；若不存在，则通过 [onWindowNew](#onwindownew)通知应用创建新Web实例。 > **说明：** > > - 通过name绑定Web实例‌：需在[onWindowNew](#onwindownew)回调中调用event.handler.setWebController方法，并传入新Web实例的 > controller，以完成绑定。 > > - name‌命名需符合正则表达式[a-zA-Z0-9_]+。当该name被用作\&lt;a&gt;或\&lt;form&gt;标签的target属性值时，已绑定的Web实例同样会触发此回调。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-onActivateContent(callback: Callback<void>): WebAttribute--><!--Device-WebAttribute-onActivateContent(callback: Callback<void>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | 再次在原页面触发window.open后，在已打开的新页面触发该回调。 |

## onAdsBlocked

```TypeScript
onAdsBlocked(callback: OnAdsBlockedCallback)
```

一个页面发生广告过滤后，通过此回调接口通知过滤的详细信息。由于页面可能随时发生变化并不断产生网络请求，为了减少通知频次、降低对页面加载过程的影响，仅在页面加载完成时进行首次通知，此后发生的过滤将间隔1秒钟上报，无广告过滤则无通知。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onAdsBlocked(callback: OnAdsBlockedCallback): WebAttribute--><!--Device-WebAttribute-onAdsBlocked(callback: OnAdsBlockedCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAdsBlockedCallback](arkts-arkweb-onadsblockedcallback-t.md) | 是 | 广告过滤的回调。 |

## onAlert

```TypeScript
onAlert(callback: Callback<OnAlertEvent, boolean>)
```

网页触发alert()告警弹窗时触发回调。若不调用[handleCancel](arkts-arkweb-jsresult-c.md#handlecancel)或[handleConfirm](arkts-arkweb-jsresult-c.md#handleconfirm)接 口，会造成渲染进程阻塞。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onAlert(callback: Callback<OnAlertEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onAlert(callback: Callback<OnAlertEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnAlertEvent](arkts-arkweb-onalertevent-i.md), boolean&gt; | 是 | 网页触发alert()告警弹窗时触发。 <br>返回值boolean。当回调返回true时，应用可调用自定义弹窗能力（包括确认和取消），并根据用户的确认或取消操作调用JsResult通知Web组件最终确认结果。当回调返回false时，弹窗的处理结果会被视为取 消。<br>**起始版本：** 12 |

## onAudioStateChanged

```TypeScript
onAudioStateChanged(callback: Callback<OnAudioStateChangedEvent>)
```

设置网页上的音频播放状态发生改变时的回调函数。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onAudioStateChanged(callback: Callback<OnAudioStateChangedEvent>): WebAttribute--><!--Device-WebAttribute-onAudioStateChanged(callback: Callback<OnAudioStateChangedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnAudioStateChangedEvent](arkts-arkweb-onaudiostatechangedevent-i.md)&gt; | 是 | 网页上的音频播放状态发生改变时触发。 |

## onBeforeUnload

```TypeScript
onBeforeUnload(callback: Callback<OnBeforeUnloadEvent, boolean>)
```

即将完成页面刷新或关闭当前页面时触发此回调。 > **说明：** > > - 如果当前Web组件没有得到焦点，刷新或关闭当前页面时onBeforeUnload不会触发。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onBeforeUnload(callback: Callback<OnBeforeUnloadEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onBeforeUnload(callback: Callback<OnBeforeUnloadEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnBeforeUnloadEvent](arkts-arkweb-onbeforeunloadevent-i.md), boolean&gt; | 是 | 即将完成页面刷新或关闭当前页面时触发。 <br>返回值boolean。当回调返回true时，应用可以调用自定义弹窗能力（包括确认和取消），并且需要根据用户的确认或取消操作调用JsResult通知Web组件最终是否离开当前页面。当回调返回false时，函数中绘制的 自定义弹窗无效。<br>**起始版本：** 12 |

## onCameraCaptureStateChange

```TypeScript
onCameraCaptureStateChange(callback: OnCameraCaptureStateChangeCallback)
```

通知应用当前网页的摄像头状态，摄像头有三个状态：无状态、捕获中、暂停中。使用callback异步回调。 可以通过startCamera，stopCamera，closeCamera这三个接口来切换摄像头的状态。这三个接口分别对应开启，暂停，停止摄像头功能。示例使用场景详见 [startCamera](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#startcamera)。 > **说明：** > > 当前网页正在使用摄像头时，返回在捕获中状态。 > > 当前网页暂停使用摄像头时，返回暂停中状态。 > > 当前网页完全没有使用摄像头时，返回无状态。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

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

通知用户收到SSL客户端证书请求事件。 > **说明：** > > - Web组件有三种响应方式：[ClientAuthenticationHandler.confirm](arkts-arkweb-clientauthenticationhandler-c.md#confirm)（ > 继续）、[ClientAuthenticationHandler.cancel](arkts-arkweb-clientauthenticationhandler-c.md#cancel)（取消）或 > [ClientAuthenticationHandler.ignore](arkts-arkweb-clientauthenticationhandler-c.md#ignore)（忽略）。 > > - 如果调用ClientAuthenticationHandler.confirm或ClientAuthenticationHandler.cancel，ArkWeb会将认证结果存储在内存中（在应用程序的生命周期内），并且不会 > 对相同的主机和端口再次调用onClientAuthenticationRequest()。如果调用onClientAuthenticationRequest.ignore，ArkWeb则不会存储该认证结果。 > > - 需配置"ohos.permission.ACCESS_CERT_MANAGER"权限。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onClientAuthenticationRequest(callback: Callback<OnClientAuthenticationEvent>): WebAttribute--><!--Device-WebAttribute-onClientAuthenticationRequest(callback: Callback<OnClientAuthenticationEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnClientAuthenticationEvent](arkts-arkweb-onclientauthenticationevent-i.md)&gt; | 是 | 当需要用户提供的SSL客户端证书时触发的回调。<br>**起始版本：** 12 |

## onConfirm

```TypeScript
onConfirm(callback: Callback<OnConfirmEvent, boolean>)
```

网页调用confirm()告警时触发此回调。若不调用[handleCancel](arkts-arkweb-jsresult-c.md#handlecancel)或[handleConfirm](arkts-arkweb-jsresult-c.md#handleconfirm) 接口，会造成渲染进程阻塞。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onConfirm(callback: Callback<OnConfirmEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onConfirm(callback: Callback<OnConfirmEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnConfirmEvent](arkts-arkweb-onconfirmevent-i.md), boolean&gt; | 是 | 网页调用confirm()告警时触发。 <br>返回值boolean。当回调返回true时，应用可以调用自定义弹窗能力（包括确认和取消），并且需要根据用户的确认或取消操作调用JsResult通知Web组件最终确认结果。当回调返回false时，弹窗的处理结果会被视 为取消。<br>**起始版本：** 12 |

## onConsole

```TypeScript
onConsole(callback: Callback<OnConsoleEvent, boolean>)
```

通知宿主应用JavaScript console消息。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onConsole(callback: Callback<OnConsoleEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onConsole(callback: Callback<OnConsoleEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnConsoleEvent](arkts-arkweb-onconsoleevent-i.md), boolean&gt; | 是 | 网页收到JavaScript控制台消息时触发。 <br>返回值boolean。当返回true时，该条消息将不会再打印至hilog日志，返回false时仍会打印至hilog日志。<br>**起始版本：** 12 |

## onContextMenuHide

```TypeScript
onContextMenuHide(callback: OnContextMenuHideCallback)
```

长按特定元素（例如图片，链接）或鼠标右键，隐藏菜单。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onContextMenuHide(callback: OnContextMenuHideCallback): WebAttribute--><!--Device-WebAttribute-onContextMenuHide(callback: OnContextMenuHideCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnContextMenuHideCallback](arkts-arkweb-oncontextmenuhidecallback-t.md) | 是 | 上下文菜单隐藏时触发。 |

## onContextMenuShow

```TypeScript
onContextMenuShow(callback: Callback<OnContextMenuShowEvent, boolean>)
```

长按特定元素（例如图片，链接）或鼠标右键，弹出菜单。用于自定义右键菜单项、实现复制、保存、分享等功能、隐藏默认菜单项，提供更好的上下文交互体验。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onContextMenuShow(callback: Callback<OnContextMenuShowEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onContextMenuShow(callback: Callback<OnContextMenuShowEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnContextMenuShowEvent](arkts-arkweb-oncontextmenushowevent-i.md), boolean&gt; | 是 | 调用时触发的回调，以允许自定义显示上下文菜单。 <br>返回值boolean。返回true表示触发自定义菜单，返回false表示触发的自定义菜单无效，将使用系统默认菜单。<br>**起始版本：** 12 |

## onControllerAttached

```TypeScript
onControllerAttached(callback: () => void)
```

当Controller成功绑定到Web组件时触发该回调，并且该Controller必须为WebviewController，且禁止在该事件回调前调用Web组件相关的接口，否则会抛出js-error异常。 因该回调调用时网页还未加载，无法在回调中使用有关操作网页的接口，例如[zoomIn](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#zoomin)、 [zoomOut](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#zoomout)等，可以使用 [loadUrl](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#loadurl)、 [getWebId](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#getwebid)等操作网页不相关的接口。 组件生命周期详情可参考[Web组件的生命周期](../../../web/web-event-sequence.md)。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onControllerAttached(callback: () => void): WebAttribute--><!--Device-WebAttribute-onControllerAttached(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 当ArkWeb控制器初始化成功时触发的回调。 |

## onDataResubmitted

```TypeScript
onDataResubmitted(callback: Callback<OnDataResubmittedEvent>)
```

当网页表单可以重新提交时触发的回调函数。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onDataResubmitted(callback: Callback<OnDataResubmittedEvent>): WebAttribute--><!--Device-WebAttribute-onDataResubmitted(callback: Callback<OnDataResubmittedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnDataResubmittedEvent](arkts-arkweb-ondataresubmittedevent-i.md)&gt; | 是 | 网页表单可以重新提交时触发。<br>**起始版本：** 12 |

## onDetectedBlankScreen

```TypeScript
onDetectedBlankScreen(callback: OnDetectBlankScreenCallback)
```

Web组件检测到白屏时触发此回调。 > **说明：** > > - 需配合[blankScreenDetectionConfig](#blankscreendetectionconfig)使用。否则，默认关闭白屏检测功能，不会返回检测到白屏时的回调函数。

**起始版本：** 22

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-WebAttribute-onDetectedBlankScreen(callback: OnDetectBlankScreenCallback): WebAttribute--><!--Device-WebAttribute-onDetectedBlankScreen(callback: OnDetectBlankScreenCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnDetectBlankScreenCallback](arkts-arkweb-ondetectblankscreencallback-t.md) | 是 | 检测到白屏时触发。事件对象包含页面URL、白屏原因、检测到的内容节点数等诊断信息。 |

## onDownloadStart

```TypeScript
onDownloadStart(callback: Callback<OnDownloadStartEvent>)
```

通知主应用开始下载文件。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onDownloadStart(callback: Callback<OnDownloadStartEvent>): WebAttribute--><!--Device-WebAttribute-onDownloadStart(callback: Callback<OnDownloadStartEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnDownloadStartEvent](arkts-arkweb-ondownloadstartevent-i.md)&gt; | 是 | 开始下载时触发此回调。<br>**起始版本：** 12 |

## onErrorReceive

```TypeScript
onErrorReceive(callback: Callback<OnErrorReceiveEvent>)
```

网页加载遇到错误时触发该回调。主资源与子资源出错都会回调该接口，可以通过[isMainFrame](arkts-arkweb-webresourcerequest-c.md#ismainframe)来判断是否是主资源报错。出于性能考虑，建议此回调中尽量执 行简单逻辑。在无网络的情况下，触发此回调。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onErrorReceive(callback: Callback<OnErrorReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onErrorReceive(callback: Callback<OnErrorReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnErrorReceiveEvent](arkts-arkweb-onerrorreceiveevent-i.md)&gt; | 是 | 网页收到 Web 资源加载错误时触发。<br>**起始版本：** 12 |

## onFaviconReceived

```TypeScript
onFaviconReceived(callback: Callback<OnFaviconReceivedEvent>)
```

设置应用为当前页面接收到新的favicon时的回调函数。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFaviconReceived(callback: Callback<OnFaviconReceivedEvent>): WebAttribute--><!--Device-WebAttribute-onFaviconReceived(callback: Callback<OnFaviconReceivedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnFaviconReceivedEvent](arkts-arkweb-onfaviconreceivedevent-i.md)&gt; | 是 | 当前页面接收到新的favicon时触发。<br>**起始版本：** 12 |

## onFileSelectorShow

```TypeScript
onFileSelectorShow(callback: (event?: { callback: Function, fileSelector: object }) => void)
```

调用此函数以处理具有“文件”输入类型的HTML表单，以响应用户按下的“选择文件”按钮。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 9

**替代接口：** onShowFileSelector

<!--Device-WebAttribute-onFileSelectorShow(callback: (event?: { callback: Function, fileSelector: object }) => void): WebAttribute--><!--Device-WebAttribute-onFileSelectorShow(callback: (event?: { callback: Function, fileSelector: object }) => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: { callback: Function, fileSelector: object }) =&gt; void | 是 | 当触发文件选择器时需要执行的回调。 |

## onFirstContentfulPaint

```TypeScript
onFirstContentfulPaint(callback: Callback<OnFirstContentfulPaintEvent>)
```

设置网页首次内容绘制时触发的回调函数。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFirstContentfulPaint(callback: Callback<OnFirstContentfulPaintEvent>): WebAttribute--><!--Device-WebAttribute-onFirstContentfulPaint(callback: Callback<OnFirstContentfulPaintEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnFirstContentfulPaintEvent](arkts-arkweb-onfirstcontentfulpaintevent-i.md)&gt; | 是 | 回调函数，返回导航开始时间戳、首次内容绘制耗时等性能指标。<br>**起始版本：** 12 |

## onFirstMeaningfulPaint

```TypeScript
onFirstMeaningfulPaint(callback: OnFirstMeaningfulPaintCallback)
```

设置网页绘制页面主要内容回调函数。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

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

网页首屏渲染结束时触发此回调，使用callback异步回调。 > **说明：** > > - 首屏渲染（First Screen Paint，FSP），记录了视口内图片、文本或视频元素完成渲染所需的时间，是衡量页面首次加载到渲染完成的核心性能指标。当一定时间内视口内没有可见元素超出历史绘制区域时，将视口内元素绘制的 > 历史最大的时刻视为首屏渲染完成时刻。 > > - 接口在首屏绘制完成后，需要等待一定时间没有新的渲染信息需要处理后，才会上报回调。接口回调时刻和首屏渲染完成时刻不同。 > > - 渲染未完成时，若用户输入或滚动页面，将会立即上报回调函数。 > > - 该接口适用于在即时加载场景下获取首屏渲染时间，在预加载或预渲染场景下使用无法达到预期。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-WebAttribute-onFirstScreenPaint(callback: OnFirstScreenPaintCallback): WebAttribute--><!--Device-WebAttribute-onFirstScreenPaint(callback: OnFirstScreenPaintCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnFirstScreenPaintCallback](arkts-arkweb-onfirstscreenpaintcallback-t.md) | 是 | 首屏渲染完成时触发。事件对象包含页面URL、导航开始时间、首屏渲染时间等性能指标。 |

## onFullScreenEnter

```TypeScript
onFullScreenEnter(callback: OnFullScreenEnterCallback)
```

通知开发者Web组件进入全屏模式。用于隐藏状态栏和导航栏、调整页面布局以适应全屏、实现沉浸式视频播放等全屏体验。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFullScreenEnter(callback: OnFullScreenEnterCallback): WebAttribute--><!--Device-WebAttribute-onFullScreenEnter(callback: OnFullScreenEnterCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnFullScreenEnterCallback](arkts-arkweb-onfullscreenentercallback-t.md) | 是 | Web组件进入全屏时的回调信息，包含videoWidth、videoHeight和handler字段。 |

## onFullScreenExit

```TypeScript
onFullScreenExit(callback: () => void)
```

通知开发者Web组件退出全屏模式。用于恢复状态栏和导航栏、调整页面布局恢复正常显示、实现全屏与正常显示的平滑切换，提供更好的全屏交互体验。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onFullScreenExit(callback: () => void): WebAttribute--><!--Device-WebAttribute-onFullScreenExit(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 退出全屏模式时的回调函数，无参数。 |

## onGeolocationHide

```TypeScript
onGeolocationHide(callback: () => void)
```

通知用户先前被调用[onGeolocationShow](#ongeolocationshow)时收到地理位置信息获取请求已被取消。用于清理定位相关资源，优化资源使用。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onGeolocationHide(callback: () => void): WebAttribute--><!--Device-WebAttribute-onGeolocationHide(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 地理位置信息获取请求已被取消的回调函数。 |

## onGeolocationShow

```TypeScript
onGeolocationShow(callback: Callback<OnGeolocationShowEvent>)
```

通知用户收到地理位置信息获取请求，需配置"ohos.permission.LOCATION"、"ohos.permission.APPROXIMATELY_LOCATION"权限。使用callback异步回调。用于显示自定义的位置 权限申请弹窗、实现位置服务说明、根据应用需求选择是否授权，提供更好的位置权限管理体验。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onGeolocationShow(callback: Callback<OnGeolocationShowEvent>): WebAttribute--><!--Device-WebAttribute-onGeolocationShow(callback: Callback<OnGeolocationShowEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnGeolocationShowEvent](arkts-arkweb-ongeolocationshowevent-i.md)&gt; | 是 | 回调函数，请求显示地理位置权限时触发，返回地理位置信息请求对象。<br>**起始版本：** 12 |

## onHttpAuthRequest

```TypeScript
onHttpAuthRequest(callback: Callback<OnHttpAuthRequestEvent, boolean>)
```

通知收到HTTP认证请求。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onHttpAuthRequest(callback: Callback<OnHttpAuthRequestEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onHttpAuthRequest(callback: Callback<OnHttpAuthRequestEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnHttpAuthRequestEvent](arkts-arkweb-onhttpauthrequestevent-i.md), boolean&gt; | 是 | 当浏览器需要用户的凭据时触发。 <br>返回值boolean。返回true表示HTTP认证成功，返回false表示HTTP认证失败。<br>**起始版本：** 12 |

## onHttpErrorReceive

```TypeScript
onHttpErrorReceive(callback: Callback<OnHttpErrorReceiveEvent>)
```

网页加载资源遇到的HTTP错误（响应码>=400）时触发该回调。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onHttpErrorReceive(callback: Callback<OnHttpErrorReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onHttpErrorReceive(callback: Callback<OnHttpErrorReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnHttpErrorReceiveEvent](arkts-arkweb-onhttperrorreceiveevent-i.md)&gt; | 是 | 网页收到加载资源返回HTTP错误码时触发。<br>**起始版本：** 12 |

## onInputmethodAttached

```TypeScript
onInputmethodAttached(callback: OnInputmethodAttachedCallback)
```

网页绑定输入法成功时触发此回调，使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-onInputmethodAttached(callback: OnInputmethodAttachedCallback): WebAttribute--><!--Device-WebAttribute-onInputmethodAttached(callback: OnInputmethodAttachedCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnInputmethodAttachedCallback](arkts-arkweb-oninputmethodattachedcallback-t.md) | 是 | 设置Web组件检测到输入法绑定成功时的回调函数。 |

## onIntelligentTrackingPreventionResult

```TypeScript
onIntelligentTrackingPreventionResult(callback: OnIntelligentTrackingPreventionCallback)
```

智能防跟踪功能使能时，当追踪者cookie被拦截时触发该回调。 > **说明：** > > - 需要使用release包，debug包不生效。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onIntelligentTrackingPreventionResult(callback: OnIntelligentTrackingPreventionCallback): WebAttribute--><!--Device-WebAttribute-onIntelligentTrackingPreventionResult(callback: OnIntelligentTrackingPreventionCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnIntelligentTrackingPreventionCallback](arkts-arkweb-onintelligenttrackingpreventioncallback-t.md) | 是 | 智能防跟踪功能使能时，当追踪者cookie被拦截时触发的回调。 |

## onInterceptKeyEvent

```TypeScript
onInterceptKeyEvent(callback: (event: KeyEvent) => boolean)
```

设置键盘事件的回调函数，该回调在被Webview使用前触发。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onInterceptKeyEvent(callback: (event: KeyEvent) => boolean): WebAttribute--><!--Device-WebAttribute-onInterceptKeyEvent(callback: (event: KeyEvent) => boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event: KeyEvent) =&gt; boolean | 是 | 触发的KeyEvent事件。 <br>返回值为boolean类型，true表示将该KeyEvent传入Webview内核，false表示不将该KeyEvent传入Webview内核。 |

## onInterceptKeyboardAttach

```TypeScript
onInterceptKeyboardAttach(callback: WebKeyboardCallback)
```

当网页中的可编辑元素（如input标签）需要弹出软键盘时触发此回调。应用可以在回调中拦截系统软键盘的弹出，配置应用定制的软键盘（应用根据该接口可以决定使用系统默认软键盘/定制enter键的系统软键盘/全部由应用自定义的软键盘）。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onInterceptKeyboardAttach(callback: WebKeyboardCallback): WebAttribute--><!--Device-WebAttribute-onInterceptKeyboardAttach(callback: WebKeyboardCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [WebKeyboardCallback](arkts-arkweb-webkeyboardcallback-t.md) | 是 | 拦截网页拉起软键盘回调。 |

## onInterceptRequest

```TypeScript
onInterceptRequest(callback: Callback<OnInterceptRequestEvent, WebResourceResponse>)
```

当Web组件加载URL之前触发该回调，用于拦截URL并返回响应数据。`onInterceptRequest`可拦截所有跳转请求并返回响应数据，但无法访问POST请求体（Body）内容，且不支持分片缓冲（buffer）类型数据获取。 此类场景需改用[WebSchemeHandler](../arkts-apis/arkts-arkweb-webview-webschemehandler-c.md#webschemehandler)实现，依据具体业务需求进行判断。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onInterceptRequest(callback: Callback<OnInterceptRequestEvent, WebResourceResponse>): WebAttribute--><!--Device-WebAttribute-onInterceptRequest(callback: Callback<OnInterceptRequestEvent, WebResourceResponse>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnInterceptRequestEvent](arkts-arkweb-oninterceptrequestevent-i.md), [WebResourceResponse](arkts-arkweb-webresourceresponse-c.md)&gt; | 是 | 当Web组件加载url之前触发此回调。 <br>返回值WebResourceResponse。返回响应数据则按照响应数据加载，无响应数据则返回null表示按照原来的方式加载。<br>**起始版本：** 12 |

## onLargestContentfulPaint

```TypeScript
onLargestContentfulPaint(callback: OnLargestContentfulPaintCallback)
```

设置网页绘制页面最大内容回调函数。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

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

通知宿主应用页面已加载完成。此方法仅在主frame加载完成时被调用。对于片段跳转（即导航至#fragment_id），onLoadFinished同样会被触发。 > **说明：** > > - 片段导航也会触发onLoadFinished，但onPageEnd不会被触发。 > > - 如果主框架在页面完全加载之前被自动重定向，onLoadFinished只会触发一次。onPageEnd会在每次主框架导航时触发。 > > - 当弹出窗口的文档在加载之前被JavaScript修改时，它将模拟触发onLoadStarted，并将URL设置为空，因为显示当前正在加载的URL可能不安全。onPageBegin将不会被模拟。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-onLoadFinished(callback: Callback<OnLoadFinishedEvent>): WebAttribute--><!--Device-WebAttribute-onLoadFinished(callback: Callback<OnLoadFinishedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnLoadFinishedEvent](arkts-arkweb-onloadfinishedevent-i.md)&gt; | 是 | 网页加载结束时触发。 |

## onLoadIntercept

```TypeScript
onLoadIntercept(callback: Callback<OnLoadInterceptEvent, boolean>)
```

当Web组件加载url之前触发该回调，用于判断是否阻止此次访问。 > **说明：** > > - onLoadIntercept无法获取到完整的headers，如需获取完整headers建议在[onInterceptRequest](#oninterceptrequest)或者通过 > WebSchemeHandler的 > onRequestStart > 中获取。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onLoadIntercept(callback: Callback<OnLoadInterceptEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onLoadIntercept(callback: Callback<OnLoadInterceptEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnLoadInterceptEvent](arkts-arkweb-onloadinterceptevent-i.md), boolean&gt; | 是 | 导航触发时的回调包括iframe导航，在回调中可以选择允许或者取消此次导航。 <br>返回值为boolean类型。返回true表示取消此次导航，false表示允许此次导航。 <br>返回undefined或null时为false。<br>**起始版本：** 12 |

## onLoadStarted

```TypeScript
onLoadStarted(callback: Callback<OnLoadStartedEvent>)
```

通知宿主应用页面开始加载。此方法在每次主frame加载时调用一次，因此对于包含iframes或frameset的页面，onLoadStarted仅针对主frame调用一次。这意味着当嵌入式frame的内容发生变化时，如点击 iframe中的链接或Fragment跳转（即跳转到#fragment_id的导航）等，不会调用onLoadStarted。 > **说明：** > > - 当弹出窗口的文档在加载之前被JavaScript修改时，它将模拟触发onLoadStarted，并将URL设置为空，因为显示当前正在加载的URL可能不安全。onPageBegin将不会被模拟。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-onLoadStarted(callback: Callback<OnLoadStartedEvent>): WebAttribute--><!--Device-WebAttribute-onLoadStarted(callback: Callback<OnLoadStartedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnLoadStartedEvent](arkts-arkweb-onloadstartedevent-i.md)&gt; | 是 | 网页加载开始时触发。 |

## onMicrophoneCaptureStateChange

```TypeScript
onMicrophoneCaptureStateChange(callback: OnMicrophoneCaptureStateChangeCallback)
```

通知应用当前网页中麦克风状态，麦克风有三个状态：未工作、捕获中、暂停中。使用callback异步回调。 可以通过resumeMicrophone，pauseMicrophone，stopMicrophone这三个接口来切换麦克风的状态。这三个接口功能分别对应解除暂停，暂停，停止麦克风。示例使用场景详见 [resumeMicrophone&lt;sup&gt;23+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#resumemicrophone)。 > **说明：** > > 当前网页正在使用麦克风时，返回捕获中状态；当前网页暂停使用麦克风时，返回暂停中状态；当前网页完全没有使用麦克风时，返回未工作状态。 > > 当前麦克风处于捕获中状态时，设置暂停使用，当前麦克风变为暂停中状态。可通过ArkWeb设置麦克风开始使用状态进行恢复捕捉。 > > 当前麦克风处于捕获中状态时，设置停止使用，当前麦克风停止捕捉，麦克风变为未工作状态。除非重新前端开始捕捉，否则无法恢复。 > > 当前麦克风处于暂停中状态时，设置开始使用，当前麦克风继续捕捉，变为捕获中状态。 > > 当前麦克风处于暂停中状态时，设置停止使用，当前麦克风停止捕捉，变为未工作状态。除非重新前端开始捕捉，否则无法恢复。 > > 当前麦克风处于未工作状态时，设置开始使用以及暂停使用，麦克风状态均不发生变化。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-WebAttribute-onMicrophoneCaptureStateChange(callback: OnMicrophoneCaptureStateChangeCallback): WebAttribute--><!--Device-WebAttribute-onMicrophoneCaptureStateChange(callback: OnMicrophoneCaptureStateChangeCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnMicrophoneCaptureStateChangeCallback](arkts-arkweb-onmicrophonecapturestatechangecallback-t.md) | 是 | 回调函数。当麦克风捕获状态改变时触发，返回原来的状态和改变后的状态。 |

## onNativeEmbedGestureEvent

```TypeScript
onNativeEmbedGestureEvent(callback: (event: NativeEmbedTouchInfo) => void)
```

当手指触摸到同层标签时触发该回调。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onNativeEmbedGestureEvent(callback: (event: NativeEmbedTouchInfo) => void): WebAttribute--><!--Device-WebAttribute-onNativeEmbedGestureEvent(callback: (event: NativeEmbedTouchInfo) => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event: NativeEmbedTouchInfo) =&gt; void | 是 | 手指触摸到同层标签时触发该回调。 |

## onNativeEmbedLifecycleChange

```TypeScript
onNativeEmbedLifecycleChange(callback: (event: NativeEmbedDataInfo) => void)
```

当同层标签生命周期变化时触发该回调。 > **说明：** > > - 本接口与onNativeEmbedVisibilityChange都监控同层标签状态，但监控维度不同。 onNativeEmbedLifecycleChange监控生命周期状态（如CREATE/UPDATE/DESTROY/ENTER_BFCACHE/LEAVE_BFCACHE），适用于处理标签的创建、销毁、缓存等生命周期事件。 onNativeEmbedVisibilityChange监控视口内的可见性变化（Visible/Hidden），适用于处理标签滚动进出视口的场景。两者可根据实际需求配合使用或单独使用。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onNativeEmbedLifecycleChange(callback: (event: NativeEmbedDataInfo) => void): WebAttribute--><!--Device-WebAttribute-onNativeEmbedLifecycleChange(callback: (event: NativeEmbedDataInfo) => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event: NativeEmbedDataInfo) =&gt; void | 是 | 同层标签生命周期变化时触发该回调。 |

## onNativeEmbedMouseEvent

```TypeScript
onNativeEmbedMouseEvent(callback: MouseInfoCallback)
```

在同层标签上执行以下行为时触发该回调： - 使用鼠标左键、中键、右键进行点击或长按。 - 使用触摸板进行对应鼠标左键、中键、右键点击长按的操作。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

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

**ArkTS模式：** 起始版本为21。

**废弃版本：** -1

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

当网页中同层标签（例如&lt;embed\&gt;标签或&lt;object\&gt;标签）在视口内的可见性发生变化时，将触发该回调。同层标签默认不可见，若在页面首次加载时已可见，则会上报；若不可见，则不会上报。同层标签全部不可见才视为不可见，部分可见或 全部可见则视为可见。获取因同层标签CSS属性（包括visibility、display以及尺寸变化）导致的可见状态变化，需配置 [nativeEmbedOptions](#nativeembedoptions)，并将[EmbedOptions](arkts-arkweb-embedoptions-i.md#embedoptions)中的 supportCssDisplayChange参数设为true。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

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

当网页跳转提交时触发该回调。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onNavigationEntryCommitted(callback: OnNavigationEntryCommittedCallback): WebAttribute--><!--Device-WebAttribute-onNavigationEntryCommitted(callback: OnNavigationEntryCommittedCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnNavigationEntryCommittedCallback](arkts-arkweb-onnavigationentrycommittedcallback-t.md) | 是 | 网页跳转提交时触发的回调。 |

## onOverScroll

```TypeScript
onOverScroll(callback: Callback<OnOverScrollEvent>)
```

该接口在网页过度滚动时触发，用于通知网页过度滚动的偏移量。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onOverScroll(callback: Callback<OnOverScrollEvent>): WebAttribute--><!--Device-WebAttribute-onOverScroll(callback: Callback<OnOverScrollEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnOverScrollEvent](arkts-arkweb-onoverscrollevent-i.md)&gt; | 是 | 网页过度滚动时触发。<br>**起始版本：** 12 |

## onOverrideErrorPage

```TypeScript
onOverrideErrorPage(callback: OnOverrideErrorPageCallback)
```

网页加载遇到错误时触发该回调，可用于设置自定义错误页替换ArkWeb提供的默认错误页。默认仅mainframe加载出错时触发；启用subframe错误页功能后，subframe加载出错时也会触发。 > **说明：** > > - 该功能需通过调用 > [setErrorPageEnabled](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#seterrorpageenabled)&lt;sup &gt; >20+&lt;/sup&gt;启用mainframe错误页功能后才会生效。如需同时启用subframe错误页功能，请调用 > [setErrorPageEnabled](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#seterrorpageenabled) > 接口并将includeSubframe设置为true。 > > - 通过[errorPageEvent.request.isMainFrame()](arkts-arkweb-webresourcerequest-c.md#ismainframe)判断请求来源是mainframe还是subframe，以便在回调中 > 分别设置对应的自定义错误页。 > > - 通过[errorPageEvent.error.getErrorCode()](arkts-arkweb-webresourceerror-c.md#geterrorcode)获取的错误码大于0代表http协议错误，小于0代表网络错误。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-onOverrideErrorPage(callback: OnOverrideErrorPageCallback): WebAttribute--><!--Device-WebAttribute-onOverrideErrorPage(callback: OnOverrideErrorPageCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnOverrideErrorPageCallback](arkts-arkweb-onoverrideerrorpagecallback-t.md) | 是 | 网页加载遇到错误时触发。 |

## onOverrideUrlLoading

```TypeScript
onOverrideUrlLoading(callback: OnOverrideUrlLoadingCallback)
```

当URL将要加载到当前Web中时触发该回调，让宿主应用程序有机会获得控制权，判断是否阻止Web加载URL。 > **说明：** > > - POST请求不会触发该回调。 > > - iframe加载HTTP(s)协议或about:blank时不会触发该回调，而加载非HTTP(s)协议的跳转会触发；调用loadUrl(url: string)主动触发的跳转不会触发该回调。 > > - 不要在回调中使用相同的URL调用loadUrl(url: string)方法，然后返回true。 这样会不必要地中止当前加载，并用相同的URL发起一次新的加载。 要继续加载当前请求URL的正确做法是直接返回false，而不 > 是调用loadUrl(url: string)。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onOverrideUrlLoading(callback: OnOverrideUrlLoadingCallback): WebAttribute--><!--Device-WebAttribute-onOverrideUrlLoading(callback: OnOverrideUrlLoadingCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnOverrideUrlLoadingCallback](arkts-arkweb-onoverrideurlloadingcallback-t.md) | 是 | onOverrideUrlLoading的回调。 <br>返回值boolean。返回true表示中止加载URL，返回false表示继续在Web中加载URL。 |

## onPageBegin

```TypeScript
onPageBegin(callback: Callback<OnPageBeginEvent>)
```

网页开始加载时触发该回调，且只在主frame触发，iframe或者frameset的内容加载时不会触发此回调。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPageBegin(callback: Callback<OnPageBeginEvent>): WebAttribute--><!--Device-WebAttribute-onPageBegin(callback: Callback<OnPageBeginEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnPageBeginEvent](arkts-arkweb-onpagebeginevent-i.md)&gt; | 是 | 网页加载开始时触发。<br>**起始版本：** 12 |

## onPageEnd

```TypeScript
onPageEnd(callback: Callback<OnPageEndEvent>)
```

网页加载完成时触发该回调，且只在主frame触发，iframe或者frameset的内容加载时不会触发此回调。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPageEnd(callback: Callback<OnPageEndEvent>): WebAttribute--><!--Device-WebAttribute-onPageEnd(callback: Callback<OnPageEndEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnPageEndEvent](arkts-arkweb-onpageendevent-i.md)&gt; | 是 | 网页加载结束时触发。<br>**起始版本：** 12 |

## onPageVisible

```TypeScript
onPageVisible(callback: Callback<OnPageVisibleEvent>)
```

设置旧页面不再呈现，新页面即将可见时触发的回调函数。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPageVisible(callback: Callback<OnPageVisibleEvent>): WebAttribute--><!--Device-WebAttribute-onPageVisible(callback: Callback<OnPageVisibleEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnPageVisibleEvent](arkts-arkweb-onpagevisibleevent-i.md)&gt; | 是 | 旧页面不再呈现，新页面即将可见时触发的回调函数。<br>**起始版本：** 12 |

## onPdfLoadEvent

```TypeScript
onPdfLoadEvent(callback: Callback<OnPdfLoadEvent>)
```

通知用户PDF页面加载状态，包括成功或失败。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-onPdfLoadEvent(callback: Callback<OnPdfLoadEvent>): WebAttribute--><!--Device-WebAttribute-onPdfLoadEvent(callback: Callback<OnPdfLoadEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnPdfLoadEvent](arkts-arkweb-onpdfloadevent-i.md)&gt; | 是 | 当PDF加载成功或失败时，会触发回调，通知用户PDF页面加载状态。 |

## onPdfScrollAtBottom

```TypeScript
onPdfScrollAtBottom(callback: Callback<OnPdfScrollEvent>)
```

通知用户PDF页面已滚动到底。

**起始版本：** 20

**ArkTS模式：** 起始版本为20。

**废弃版本：** -1

<!--Device-WebAttribute-onPdfScrollAtBottom(callback: Callback<OnPdfScrollEvent>): WebAttribute--><!--Device-WebAttribute-onPdfScrollAtBottom(callback: Callback<OnPdfScrollEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnPdfScrollEvent](arkts-arkweb-onpdfscrollevent-i.md)&gt; | 是 | 当PDF滚动到垂直方向底部时，会触发回调，通知用户PDF页面已滚动到底。 |

## onPermissionRequest

```TypeScript
onPermissionRequest(callback: Callback<OnPermissionRequestEvent>)
```

通知收到获取权限请求，需配置"ohos.permission.CAMERA"、"ohos.permission.MICROPHONE"权限。用于自定义权限申请弹窗样式、实现细粒度的权限控制、在特定条件下拒绝或授予权限请求，提供更好 的权限管理体验。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPermissionRequest(callback: Callback<OnPermissionRequestEvent>): WebAttribute--><!--Device-WebAttribute-onPermissionRequest(callback: Callback<OnPermissionRequestEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnPermissionRequestEvent](arkts-arkweb-onpermissionrequestevent-i.md)&gt; | 是 | 收到权限请求时触发。事件对象包含请求的权限类型（如摄像头、麦克风）、请求来源等信息。 |

## onProgressChange

```TypeScript
onProgressChange(callback: Callback<OnProgressChangeEvent>)
```

网页加载进度变化时触发该回调。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onProgressChange(callback: Callback<OnProgressChangeEvent>): WebAttribute--><!--Device-WebAttribute-onProgressChange(callback: Callback<OnProgressChangeEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnProgressChangeEvent](arkts-arkweb-onprogresschangeevent-i.md)&gt; | 是 | 页面加载进度变化时触发的回调。<br>**起始版本：** 12 |

## onPrompt

```TypeScript
onPrompt(callback: Callback<OnPromptEvent, boolean>)
```

网页调用prompt()告警时触发此回调。若不调用[handleCancel](arkts-arkweb-jsresult-c.md#handlecancel)或 [handlePromptConfirm](arkts-arkweb-jsresult-c.md#handlepromptconfirm)接口，会造成渲染进程阻塞。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onPrompt(callback: Callback<OnPromptEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onPrompt(callback: Callback<OnPromptEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnPromptEvent](arkts-arkweb-onpromptevent-i.md), boolean&gt; | 是 | 网页调用prompt()告警时触发。 <br>返回值boolean。当回调返回true时，应用可以调用自定义弹窗能力（包括确认、取消和输入），并且需要根据用户的确认或取消操作调用JsResult通知Web组件最终处理结果。当回调返回false时，弹窗的处理结果 会被视为取消。<br>**起始版本：** 12 |

## onRefreshAccessedHistory

```TypeScript
onRefreshAccessedHistory(callback: Callback<OnRefreshAccessedHistoryEvent>)
```

导航完成时触发该回调，用于应用更新其访问的历史链接。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onRefreshAccessedHistory(callback: Callback<OnRefreshAccessedHistoryEvent>): WebAttribute--><!--Device-WebAttribute-onRefreshAccessedHistory(callback: Callback<OnRefreshAccessedHistoryEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnRefreshAccessedHistoryEvent](arkts-arkweb-onrefreshaccessedhistoryevent-i.md)&gt; | 是 | 在导航完成时触发。<br>**起始版本：** 12 |

## onRenderExited

```TypeScript
onRenderExited(callback: Callback<OnRenderExitedEvent>)
```

应用渲染进程异常退出时触发该回调。 多个Web组件可能共享单个渲染进程，每个受影响的Web组件都会触发该回调。 应用处理该回调时，可以调用绑定的webviewController相关接口来恢复页面。例如[refresh](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#refresh) 、[loadUrl](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#loadurl)等。 组件生命周期回调详情可参考[Web组件的生命周期](../../../web/web-event-sequence.md)。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onRenderExited(callback: Callback<OnRenderExitedEvent>): WebAttribute--><!--Device-WebAttribute-onRenderExited(callback: Callback<OnRenderExitedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnRenderExitedEvent](arkts-arkweb-onrenderexitedevent-i.md)&gt; | 是 | 渲染过程退出时触发。<br>**起始版本：** 12 |

## onRenderExited

```TypeScript
onRenderExited(callback: (event?: { detail: object }) => boolean)
```

应用渲染进程因错误或崩溃退出时触发回调。 多个Web组件可能共享单个渲染进程，每个受影响的Web组件都会触发该回调。 应用处理该回调时，可以调用绑定的WebViewController接口来恢复页面。例如[refresh](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#refresh)、 [loadUrl](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#loadurl)等。 详情可参考[Web组件的生命周期](../../../web/web-event-sequence.md)。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 9

**替代接口：** onRenderExited

<!--Device-WebAttribute-onRenderExited(callback: (event?: { detail: object }) => boolean): WebAttribute--><!--Device-WebAttribute-onRenderExited(callback: (event?: { detail: object }) => boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: { detail: object }) =&gt; boolean | 是 | 渲染过程退出时触发。 |

## onRenderProcessNotResponding

```TypeScript
onRenderProcessNotResponding(callback: OnRenderProcessNotRespondingCallback)
```

渲染进程无响应时触发该回调函数。如果Web组件无法处理输入事件，或者无法在合理的时间范围内导航到新的URL，则认为网页进程无响应，并将触发该回调。 只要网页进程一直无响应，此回调仍可能会持续触发，直到网页进程再次响应，此时[onRenderProcessResponding](#onrenderprocessresponding)将会触发。 应用可以通过WebviewController接口 [terminateRenderProcess](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#terminaterenderprocess)来终止关联的渲染进程，这可能会影响 同一渲染进程的其他Web组件。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

<!--Device-WebAttribute-onRenderProcessNotResponding(callback: OnRenderProcessNotRespondingCallback): WebAttribute--><!--Device-WebAttribute-onRenderProcessNotResponding(callback: OnRenderProcessNotRespondingCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnRenderProcessNotRespondingCallback](arkts-arkweb-onrenderprocessnotrespondingcallback-t.md) | 是 | 渲染进程无响应时触发的回调。 |

## onRenderProcessResponding

```TypeScript
onRenderProcessResponding(callback: OnRenderProcessRespondingCallback)
```

渲染进程由无响应状态变回正常运行状态时触发该回调函数，该回调表明该网页并非真正卡死。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

<!--Device-WebAttribute-onRenderProcessResponding(callback: OnRenderProcessRespondingCallback): WebAttribute--><!--Device-WebAttribute-onRenderProcessResponding(callback: OnRenderProcessRespondingCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnRenderProcessRespondingCallback](arkts-arkweb-onrenderprocessrespondingcallback-t.md) | 是 | 渲染进程由无响应状态变回正常运行状态时触发的回调。 |

## onRequestSelected

```TypeScript
onRequestSelected(callback: () => void)
```

当Web组件获取焦点时触发回调。如果组件在未获焦状态下加载网页并成功获取焦点，将触发两次回调。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onRequestSelected(callback: () => void): WebAttribute--><!--Device-WebAttribute-onRequestSelected(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 当网页获取焦点时触发的回调。 |

## onResourceLoad

```TypeScript
onResourceLoad(callback: Callback<OnResourceLoadEvent>)
```

通知Web组件所加载的资源文件url信息。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onResourceLoad(callback: Callback<OnResourceLoadEvent>): WebAttribute--><!--Device-WebAttribute-onResourceLoad(callback: Callback<OnResourceLoadEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnResourceLoadEvent](arkts-arkweb-onresourceloadevent-i.md)&gt; | 是 | 加载url时触发。<br>**起始版本：** 12 |

## onSafeBrowsingCheckFinish

```TypeScript
onSafeBrowsingCheckFinish(callback: OnSafeBrowsingCheckResultCallback)
```

网站安全风险检查结束时触发的回调。 > **说明：** > > - 需要使用release包，debug包不生效。 > > - 开启未成年模式，设置网页内容拦截，触发回调。

**起始版本：** 21

**ArkTS模式：** 起始版本为21。

**废弃版本：** -1

<!--Device-WebAttribute-onSafeBrowsingCheckFinish(callback: OnSafeBrowsingCheckResultCallback): WebAttribute--><!--Device-WebAttribute-onSafeBrowsingCheckFinish(callback: OnSafeBrowsingCheckResultCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnSafeBrowsingCheckResultCallback](arkts-arkweb-onsafebrowsingcheckresultcallback-t.md) | 是 | 收到网站安全风险检查结果时触发的回调。 |

## onSafeBrowsingCheckResult

```TypeScript
onSafeBrowsingCheckResult(callback: OnSafeBrowsingCheckResultCallback)
```

收到网站安全风险检查结果时触发的回调。 > **说明：** > > - 需要使用release包，debug包不生效。 > > - 开启未成年模式，设置网页内容拦截，触发回调。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onSafeBrowsingCheckResult(callback: OnSafeBrowsingCheckResultCallback): WebAttribute--><!--Device-WebAttribute-onSafeBrowsingCheckResult(callback: OnSafeBrowsingCheckResultCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnSafeBrowsingCheckResultCallback](arkts-arkweb-onsafebrowsingcheckresultcallback-t.md) | 是 | 收到网站安全风险检查结果时触发的回调。 |

## onScaleChange

```TypeScript
onScaleChange(callback: Callback<OnScaleChangeEvent>)
```

当页面显示比例发生变化时，触发该回调。用于监听用户缩放行为，提供更好的页面缩放体验。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onScaleChange(callback: Callback<OnScaleChangeEvent>): WebAttribute--><!--Device-WebAttribute-onScaleChange(callback: Callback<OnScaleChangeEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnScaleChangeEvent](arkts-arkweb-onscalechangeevent-i.md)&gt; | 是 | 当页面显示比例发生变化时，触发该回调。<br>**起始版本：** 12 |

## onScreenCaptureRequest

```TypeScript
onScreenCaptureRequest(callback: Callback<OnScreenCaptureRequestEvent>)
```

通知收到屏幕捕获请求。用于控制页面截图权限、实现隐私保护、防止敏感信息泄露，保护用户隐私和数据安全。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onScreenCaptureRequest(callback: Callback<OnScreenCaptureRequestEvent>): WebAttribute--><!--Device-WebAttribute-onScreenCaptureRequest(callback: Callback<OnScreenCaptureRequestEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnScreenCaptureRequestEvent](arkts-arkweb-onscreencapturerequestevent-i.md)&gt; | 是 | 收到屏幕捕获请求时触发。事件对象包含请求来源URL、请求的捕获模式等信息。 |

## onScroll

```TypeScript
onScroll(callback: Callback<OnScrollEvent>)
```

通知网页全局滚动位置。 > **说明：** > > 通知的是页面全局滚动位置，局部滚动位置的变化是无法触发此回调。 > > 判断页面是否是全局滚动，在滚动前后打印window.pageYOffset或者window.pageXOffset。 > > 如果是全局滚动，window.pageYOffset或者window.pageXOffset的值在滚动前后会有变化，反之没有变化。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onScroll(callback: Callback<OnScrollEvent>): WebAttribute--><!--Device-WebAttribute-onScroll(callback: Callback<OnScrollEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnScrollEvent](arkts-arkweb-onscrollevent-i.md)&gt; | 是 | 当页面滚动到指定位置时触发。<br>**起始版本：** 12 |

## onSearchResultReceive

```TypeScript
onSearchResultReceive(callback: Callback<OnSearchResultReceiveEvent>)
```

回调通知调用方网页页内查找的结果。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onSearchResultReceive(callback: Callback<OnSearchResultReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onSearchResultReceive(callback: Callback<OnSearchResultReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnSearchResultReceiveEvent](arkts-arkweb-onsearchresultreceiveevent-i.md)&gt; | 是 | 通知调用方网页页内查找的结果。<br>**起始版本：** 12 |

## onShowFileSelector

```TypeScript
onShowFileSelector(callback: Callback<OnShowFileSelectorEvent, boolean>)
```

用于处理具有“文件”输入类型的HTML表单。若不调用此函数或返回false，Web组件会提供默认的“选择文件”处理界面。若返回true，应用可以自定义“选择文件”的响应行为。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onShowFileSelector(callback: Callback<OnShowFileSelectorEvent, boolean>): WebAttribute--><!--Device-WebAttribute-onShowFileSelector(callback: Callback<OnShowFileSelectorEvent, boolean>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnShowFileSelectorEvent](arkts-arkweb-onshowfileselectorevent-i.md), boolean&gt; | 是 | 通知Web组件文件选择的结果。 <br>返回值boolean。当返回值为true时，应用可以自定义“选择文件”的响应行为。当返回值为false时，函数中绘制的自定义弹窗无效，Web组件将使用系统默认的“选择文件”处理界面。<br>**起始版本：** 12 |

## onSslErrorEvent

```TypeScript
onSslErrorEvent(callback: OnSslErrorEventCallback)
```

通知用户加载资源（主资源+子资源）时发生SSL错误，如果只想处理主资源的SSL错误，请用[isMainFrame](arkts-arkweb-webresourcerequest-c.md#ismainframe)字段进行区分。 > **说明：** > > - 主资源：浏览器加载网页的入口文件，通常是HTML文档。 > > - 子资源：主资源中引用的依赖文件，由主资源解析过程中遇到特定标签时触发加载。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onSslErrorEvent(callback: OnSslErrorEventCallback): WebAttribute--><!--Device-WebAttribute-onSslErrorEvent(callback: OnSslErrorEventCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnSslErrorEventCallback](arkts-arkweb-onsslerroreventcallback-t.md) | 是 | 通知用户加载资源时发生SSL错误。 |

## onSslErrorEventReceive

```TypeScript
onSslErrorEventReceive(callback: Callback<OnSslErrorEventReceiveEvent>)
```

通知用户加载资源时发生SSL错误，只支持主资源。 如果需要支持子资源，请使用[OnSslErrorEvent](#onsslerrorevent)接口。 > **说明：** > > - 主资源：浏览器加载网页的入口文件，通常是HTML文档。 > > - 子资源：主资源中引用的依赖文件，由主资源解析过程中遇到特定标签时触发加载。 > > - 应用程序需要调用[handler.handleCancel()](arkts-arkweb-sslerrorhandler-c.md#handlecancel)或 > [handler.handleConfirm()](arkts-arkweb-sslerrorhandler-c.md#handleconfirm)处理该回调，如果没有处理该回调则默认取消资源加载。handleConfirm()或者 > handleCancel()的行为可能会被记录下来，以便为将来的SSL错误做出响应。 > > - 应用程序可以用于显示自定义错误页面或静默记录问题。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onSslErrorEventReceive(callback: Callback<OnSslErrorEventReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onSslErrorEventReceive(callback: Callback<OnSslErrorEventReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnSslErrorEventReceiveEvent](arkts-arkweb-onsslerroreventreceiveevent-i.md)&gt; | 是 | 当网页收到SSL错误时触发。<br>**起始版本：** 12 |

## onSslErrorReceive

```TypeScript
onSslErrorReceive(callback: (event?: { handler: Function, error: object }) => void)
```

通知用户加载资源时发生SSL错误。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 9

**替代接口：** onSslErrorEventReceive

<!--Device-WebAttribute-onSslErrorReceive(callback: (event?: { handler: Function, error: object }) => void): WebAttribute--><!--Device-WebAttribute-onSslErrorReceive(callback: (event?: { handler: Function, error: object }) => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: { handler: Function, error: object }) =&gt; void | 是 | 当网页检测到SSL错误时触发的回调。 |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: TextSelectionChangeCallback)
```

设置Web组件选区文本改变时的回调函数。 > **说明：** > > - 支持手势选中、鼠标选中以及JS选中选区。 > > - 使用上述方式选中内容结束后触发回调。 > > - 使用同样方式选中和上一次相同内容时，不触发回调；使用不同方式选中和上一次相同内容时，依然触发。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-WebAttribute-onTextSelectionChange(callback: TextSelectionChangeCallback): WebAttribute--><!--Device-WebAttribute-onTextSelectionChange(callback: TextSelectionChangeCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TextSelectionChangeCallback](arkts-arkweb-textselectionchangecallback-t.md) | 是 | 文本选区变化时触发。回调参数包含当前选中的文本内容。 |

## onTitleReceive

```TypeScript
onTitleReceive(callback: Callback<OnTitleReceiveEvent>)
```

当页面文档标题`&lt;title&gt;`元素发生变更时，触发回调。若当前页面未显示设置标题，ArkWeb将在加载完成前基于页面的URL生成标题并返回给应用。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onTitleReceive(callback: Callback<OnTitleReceiveEvent>): WebAttribute--><!--Device-WebAttribute-onTitleReceive(callback: Callback<OnTitleReceiveEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnTitleReceiveEvent](arkts-arkweb-ontitlereceiveevent-i.md)&gt; | 是 | 页面文档标题发生变更时触发。<br>**起始版本：** 12 |

## onTouchIconUrlReceived

```TypeScript
onTouchIconUrlReceived(callback: Callback<OnTouchIconUrlReceivedEvent>)
```

接收到apple-touch-icon URL地址时触发的回调函数。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onTouchIconUrlReceived(callback: Callback<OnTouchIconUrlReceivedEvent>): WebAttribute--><!--Device-WebAttribute-onTouchIconUrlReceived(callback: Callback<OnTouchIconUrlReceivedEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnTouchIconUrlReceivedEvent](arkts-arkweb-ontouchiconurlreceivedevent-i.md)&gt; | 是 | 接收到的apple-touch-icon URL地址时触发。<br>**起始版本：** 12 |

## onUrlLoadIntercept

```TypeScript
onUrlLoadIntercept(callback: (event?: { data: string | WebResourceRequest }) => boolean)
```

当Web组件加载url之前触发该回调，用于判断是否阻止此次访问。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 10

**替代接口：** onLoadIntercept

<!--Device-WebAttribute-onUrlLoadIntercept(callback: (event?: { data: string | WebResourceRequest }) => boolean): WebAttribute--><!--Device-WebAttribute-onUrlLoadIntercept(callback: (event?: { data: string | WebResourceRequest }) => boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event?: { data: string \| WebResourceRequest }) =&gt; boolean | 是 | url的相关信息。 <br>返回值：boolean，true表示阻止此次加载，false表示允许此次加载。 |

## onVerifyPin

```TypeScript
onVerifyPin(callback: OnVerifyPinCallback)
```

通知用户进行PIN码认证。使用callback异步回调。

**起始版本：** 22

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-WebAttribute-onVerifyPin(callback: OnVerifyPinCallback): WebAttribute--><!--Device-WebAttribute-onVerifyPin(callback: OnVerifyPinCallback): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnVerifyPinCallback](arkts-arkweb-onverifypincallback-t.md) | 是 | 当需要用户进行PIN码认证时触发的回调。 |

## onViewportFitChanged

```TypeScript
onViewportFitChanged(callback: OnViewportFitChangedCallback)
```

网页meta中viewport-fit配置项更改时触发该回调，应用可在此回调中自适应布局视口。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

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

通知应用有窗口关闭请求。和[onWindowNew](#onwindownew)一样，从安全角度考虑，应用应确保用户可以知道他们交互的页面已关闭。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onWindowExit(callback: () => void): WebAttribute--><!--Device-WebAttribute-onWindowExit(callback: () => void): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 窗口请求关闭的回调函数。 |

## onWindowNew

```TypeScript
onWindowNew(callback: Callback<OnWindowNewEvent>)
```

在开启multiWindowAccess（多窗口访问）属性的情况下，通知应用有新建窗口请求。如需获取更丰富的窗口信息建议使用onWindowNewExt。 若不调用[setWebController](arkts-arkweb-controllerhandler-c.md#setwebcontroller)接口，会造成渲染进程阻塞。 如果没有创建新窗口，调用[setWebController](arkts-arkweb-controllerhandler-c.md#setwebcontroller)接口时设置成null，通知Web没有创建新窗口。 新窗口需避免直接覆盖在原Web组件上，且应与主页面以相同形式明确显示其URL（如地址栏）以防止用户混淆。若无法实现可信的URL可视化管理，则需考虑禁止创建新窗口。 需注意：新窗口请求来源无法可靠追溯，可能由第三方iframe发起，应用需默认采取沙箱隔离、限制权限等防御性措施以确保安全。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onWindowNew(callback: Callback<OnWindowNewEvent>): WebAttribute--><!--Device-WebAttribute-onWindowNew(callback: Callback<OnWindowNewEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnWindowNewEvent](arkts-arkweb-onwindownewevent-i.md)&gt; | 是 | 网页要求用户创建窗口时触发的回调。<br>**起始版本：** 12 |

## onWindowNewExt

```TypeScript
onWindowNewExt(callback: Callback<OnWindowNewExtEvent>)
```

在启用[multiWindowAccess](#multiwindowaccess)的情况下，通知应用有新建窗口请求。 > **说明：** > > - 若不调用[setWebController](arkts-arkweb-controllerhandler-c.md#setwebcontroller)接口，会造成渲染进程阻塞。 > > - 若未创建新窗口，调用[setWebController](arkts-arkweb-controllerhandler-c.md#setwebcontroller)接口并设置成null，通知Web未创建新窗口。 > > - 新窗口需避免直接覆盖在原Web组件上，且应与主页面以相同形式明确显示其URL（如地址栏）以防止用户混淆。若无法确保URL的显示和验证机制可靠，则需考虑禁止创建新窗口。 > > - 新窗口请求来源无法可靠追溯，可能由第三方iframe发起，应用需默认采取沙箱隔离、限制权限等防御性措施以确保安全。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onWindowNewExt(callback: Callback<OnWindowNewExtEvent>): WebAttribute--><!--Device-WebAttribute-onWindowNewExt(callback: Callback<OnWindowNewExtEvent>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[OnWindowNewExtEvent](arkts-arkweb-onwindownewextevent-i.md)&gt; | 是 | 网页要求用户创建窗口时触发的回调。 |

## onlineImageAccess

```TypeScript
onlineImageAccess(onlineImageAccess: boolean)
```

设置是否允许从网络加载图片资源（通过 HTTP 和 HTTPS 访问的资源）。当属性没有显式调用时，默认允许。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-onlineImageAccess(onlineImageAccess: boolean): WebAttribute--><!--Device-WebAttribute-onlineImageAccess(onlineImageAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onlineImageAccess | boolean | 是 | 设置是否允许从网络加载图片资源。 <br>true 表示允许，false 表示不允许。 <br>传入 undefined 或 null 时为 false。 |

## optimizeParserBudget

```TypeScript
optimizeParserBudget(optimizeParserBudget: boolean)
```

设置是否开启分段解析HTML优化。当属性没有显式调用时，默认使用解析时间作为HTML分段解析的分段点。 ArkWeb内核在解析HTML文档结构时采取分段解析策略，旨在避免过多占用主线程资源，并使网页具有渐进式加载能力。ArkWeb内核默认使用解析时间作为分段点，当单次解析时间超过阈值时，会中断解析，随后进行布局和渲染操作。 开启优化后，ArkWeb内核将不仅检查解析时间是否超出限制，还会额外判断解析的Token（HTML文档的最小解析单位，例如`&lt;div&gt;`、`attr="xxx"`等）数量是否超过内核规定的阈值，并下调此阈值。当页面的FCP（ First Contentful Paint 首次内容绘制）触发时会恢复成默认的中断判断逻辑。这将使得网页在FCP到来之前的解析操作更频繁，从而提高首帧内容被提前解析完成并进入渲染阶段的可能性，同时有效缩减首帧渲染的工作量，最终实 现FCP时间提前。 由于页面的FCP触发时会恢复成默认分段解析逻辑，因此分段解析HTML优化仅对每个Web组件加载的首个页面生效。

**起始版本：** 15

**ArkTS模式：** 起始版本为15。

**废弃版本：** -1

<!--Device-WebAttribute-optimizeParserBudget(optimizeParserBudget: boolean): WebAttribute--><!--Device-WebAttribute-optimizeParserBudget(optimizeParserBudget: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| optimizeParserBudget | boolean | 是 | 设置开启分段解析HTML优化。 <br>true表示使用解析个数代替解析时间作为HTML分段解析的分段点，并减少每段解析的个数上限。false表示使用解析时间作为HTML分段解析的分段点。 <br>传入undefined或null时为false。 |

## overScrollMode

```TypeScript
overScrollMode(mode: OverScrollMode)
```

设置Web过滚动模式。开启时，用户在Web根页面滑动到边缘时，Web会通过弹性动画弹回界面，根页面上的内部页面不会触发回弹。该属性没有显式调用时，默认关闭。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-overScrollMode(mode: OverScrollMode): WebAttribute--><!--Device-WebAttribute-overScrollMode(mode: OverScrollMode): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [OverScrollMode](arkts-arkweb-overscrollmode-e.md) | 是 | 设置Web的过滚动模式为关闭或开启。 <br>传入undefined或null时为OverScrollMode.NEVER。 |

## overviewModeAccess

```TypeScript
overviewModeAccess(overviewModeAccess: boolean)
```

设置是否使用概览模式加载网页，即缩小内容以适应屏幕宽度。当属性没有显式调用时，默认允许使用概览模式加载网页。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-overviewModeAccess(overviewModeAccess: boolean): WebAttribute--><!--Device-WebAttribute-overviewModeAccess(overviewModeAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| overviewModeAccess | boolean | 是 | 设置是否使用概览模式加载网页。 <br>true表示使用，false表示不使用。 <br>传入undefined或null时为false。 |

## password

```TypeScript
password(password: boolean)
```

设置是否应保存密码。该接口为空接口。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 10

**替代接口：** enableAutofill

<!--Device-WebAttribute-password(password: boolean): WebAttribute--><!--Device-WebAttribute-password(password: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| password | boolean | 是 | 设置为true时，表示允许Web保存密码。 <br>设置为false时，表示不允许Web保存密码。 <br>传入undefined或null时为false。 |

## pinchSmooth

```TypeScript
pinchSmooth(isEnabled: boolean)
```

设置网页是否开启捏合流畅模式。该属性没有显式调用时，默认不开启捏合流畅模式。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-pinchSmooth(isEnabled: boolean): WebAttribute--><!--Device-WebAttribute-pinchSmooth(isEnabled: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean | 是 | 网页是否开启捏合流畅模式。 <br>true表示设置网页开启捏合流畅模式，false表示设置网页不开启捏合流畅模式。 <br>传入undefined或null时为false。 |

## registerNativeEmbedRule

```TypeScript
registerNativeEmbedRule(tag: string, type:string)
```

注册使用同层渲染的HTML标签名和类型。标签名仅支持使用&lt;object\&gt;和&lt;embed\&gt;。标签类型只能使用ASCII可显示字符。 若指定类型与W3C定义的&lt;object\&gt;或&lt;embed\&gt;标准类型重合，ArkWeb内核将其识别为非同层标签。 本接口同样受enableNativeEmbedMode接口控制，在未使能同层渲染时本接口无效。在不使用本接口的情况下，ArkWeb内核默认将"native/"前缀类型的&lt;embed\&gt;标签识别为同层标签。 具体使用详情请参考[同层渲染](../../../web/web-same-layer.md#web页面中同层渲染输入框)指南。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

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

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-WebAttribute-rotateRenderEffect(effect: WebRotateEffect): WebAttribute--><!--Device-WebAttribute-rotateRenderEffect(effect: WebRotateEffect): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [WebRotateEffect](arkts-arkweb-webrotateeffect-e.md) | 是 | 设置Web组件旋转时，宽高动画过程中组件内容的填充方式。 |

## runJavaScriptOnDocumentEnd

```TypeScript
runJavaScriptOnDocumentEnd(scripts: Array<ScriptItem>)
```

将JavaScript脚本注入到Web组件中，当指定页面或者文档加载完成时，该脚本将在其来源与scriptRules匹配的任何页面中执行。当属性没有显式调用时，默认不将JavaScript脚本注入到Web组件中。 > **说明：** > > - 该脚本将在页面的任何JavaScript代码之后运行，并且DOM树此时已经加载、渲染完毕。 > > - 该脚本按照数组本身顺序执行。 > > - 内容相同的脚本多次注入时将被静默去重，不展示，不提醒，使用首次注入时的scriptRules。

**起始版本：** 15

**ArkTS模式：** 起始版本为15。

**废弃版本：** -1

<!--Device-WebAttribute-runJavaScriptOnDocumentEnd(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-runJavaScriptOnDocumentEnd(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | Array&lt;[ScriptItem](arkts-arkweb-scriptitem-i.md)&gt; | 是 | 需要注入的ScriptItem数组。 <br>传入undefined或null时不将JavaScript脚本注入到Web组件中。 |

## runJavaScriptOnDocumentStart

```TypeScript
runJavaScriptOnDocumentStart(scripts: Array<ScriptItem>)
```

将JavaScript脚本注入到Web组件中，当指定页面或者文档开始加载时，该脚本将在其来源与scriptRules匹配的任何页面中执行。当属性没有显式调用时，默认不将JavaScript脚本注入到Web组件中。 > **说明：** > > - 网页文档根元素（HTML Element）创建后、但尚未加载任何其他内容之前注入脚本。 > > - 该脚本按照数组本身顺序执行。 > > - 内容相同的脚本多次注入时将被静默去重，不展示，不提醒，使用首次注入时的scriptRules。

**起始版本：** 15

**ArkTS模式：** 起始版本为15。

**废弃版本：** -1

<!--Device-WebAttribute-runJavaScriptOnDocumentStart(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-runJavaScriptOnDocumentStart(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | Array&lt;[ScriptItem](arkts-arkweb-scriptitem-i.md)&gt; | 是 | 需要注入的ScriptItem数组。 <br>传入undefined或null时不将JavaScript脚本注入到Web组件中。 |

## runJavaScriptOnHeadEnd

```TypeScript
runJavaScriptOnHeadEnd(scripts: Array<ScriptItem>)
```

将JavaScript脚本注入到Web组件中，当页面DOM树head标签解析完成时，该脚本将在其来源与scriptRules匹配的任何页面中执行。当属性没有显式调用时，默认不将JavaScript脚本注入到Web组件中。 > **说明：** > > - 该脚本按照数组本身顺序执行。 > > - 内容相同的脚本多次注入时将被静默去重，不展示，不提醒，使用首次注入时的scriptRules。

**起始版本：** 15

**ArkTS模式：** 起始版本为15。

**废弃版本：** -1

<!--Device-WebAttribute-runJavaScriptOnHeadEnd(scripts: Array<ScriptItem>): WebAttribute--><!--Device-WebAttribute-runJavaScriptOnHeadEnd(scripts: Array<ScriptItem>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scripts | Array&lt;[ScriptItem](arkts-arkweb-scriptitem-i.md)&gt; | 是 | 需要注入的ScriptItem数组。 <br>传入undefined或null时不将JavaScript脚本注入到Web组件中。 |

## scrollbarLayoutPolicy

```TypeScript
scrollbarLayoutPolicy(policy: ScrollbarLayoutPolicy)
```

选择Web组件内垂直滚动条的布局方式，用于适配不同语言的书写方向。CONTENT模式适用于需要跟随网页CSS direction属性的场景，SYSTEM模式适用于多语言应用中需要跟随系统语言方向设置的场景，如阿拉伯语、希伯来语等从 右到左书写的语言。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebAttribute-scrollbarLayoutPolicy(policy: ScrollbarLayoutPolicy): WebAttribute--><!--Device-WebAttribute-scrollbarLayoutPolicy(policy: ScrollbarLayoutPolicy): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [ScrollbarLayoutPolicy](arkts-arkweb-scrollbarlayoutpolicy-e.md) | 是 | 设置Web组件内垂直滚动条布局模式。可选值：CONTENT（跟随网页css的direction属性设置），SYSTEM（根据系统语种的左右书写方向 进行布局，对于从右向左书写的语言，滚动条将布局在左侧。对于网页内嵌套的多层滚动条均适用）。 |

## selectionMenuOptions

```TypeScript
selectionMenuOptions(expandedMenuOptions: Array<ExpandedMenuItemOptions>)
```

Web组件自定义菜单扩展项接口，允许用户设置扩展项的文本内容、图标、回调方法。 该接口只支持选中纯文本，当选中内容包含图片及其他非文本内容时，action信息中会显示乱码。 > **说明：** > > 本接口在与[editMenuOptions](#editmenuoptions)同时使用时，本接口不生效。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** 20

**替代接口：** editMenuOptions

<!--Device-WebAttribute-selectionMenuOptions(expandedMenuOptions: Array<ExpandedMenuItemOptions>): WebAttribute--><!--Device-WebAttribute-selectionMenuOptions(expandedMenuOptions: Array<ExpandedMenuItemOptions>): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| expandedMenuOptions | Array&lt;[ExpandedMenuItemOptions](arkts-arkweb-expandedmenuitemoptions-i.md)&gt; | 是 | 扩展菜单选项。<br/>菜单项数量，及菜单的content大小、startIcon图标尺寸，与 ArkUI Menu组件保持一致。 |

## tableData

```TypeScript
tableData(tableData: boolean)
```

设置是否应保存表单数据。当属性没有显式调用时，默认允许Web保存表单数据。该接口为空接口。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 10

**替代接口：** enableAutofill

<!--Device-WebAttribute-tableData(tableData: boolean): WebAttribute--><!--Device-WebAttribute-tableData(tableData: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tableData | boolean | 是 | 设置为true时，表示允许Web保存表单数据。 <br>设置为false时，表示不允许Web保存表单数据。 <br>传入undefined或null时为true。 |

## textAutosizing

```TypeScript
textAutosizing(textAutosizing: boolean)
```

设置Web组件是否开启文本字体大小自动调整。当属性没有显式调用时，Web组件默认开启文本字体大小自动调整。 文本字体大小自动调整生效后，对于字号过小的文本将自动加大字号至16px~32px，避免屏幕较小（默认视口宽度 &lt; 980px）的设备因为缺少移动端适配出现字体过小的可读性问题。 &gt; **说明：** > > - 文本字体大小自动调整生效需要满足的前置条件： > > - 设备形态为：Phone、Tablet、Wearable、TV。 > > - Web组件视口宽度 &lt; 980px。 &gt; > - 页面文本量大，页面文本的字号*字符数 ≥ 3920。 > > - 前端无metaViewport设置，或metaViewport设置中无"width"和"initial-scale"属性。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-textAutosizing(textAutosizing: boolean): WebAttribute--><!--Device-WebAttribute-textAutosizing(textAutosizing: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textAutosizing | boolean | 是 | 文本自动调整大小。 <br>true表示文本自动调整大小，false表示文本不自动调整大小。 <br>传入undefined或null时为true。 |

## textZoomAtio

```TypeScript
textZoomAtio(textZoomAtio: number)
```

设置页面的文本缩放百分比。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 9

**替代接口：** [textZoomRatio](#textzoomratio)

<!--Device-WebAttribute-textZoomAtio(textZoomAtio: number): WebAttribute--><!--Device-WebAttribute-textZoomAtio(textZoomAtio: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textZoomAtio | number | 是 | 要设置的页面的文本缩放百分比。100表示原始大小，大于100表示放大，小于100表示缩小。 <br>取值范围为(0, 2147483647]。 |

## textZoomRatio

```TypeScript
textZoomRatio(textZoomRatio: number)
```

设置页面的文本缩放百分比。当属性没有显式调用时，默认缩放百分比为100%。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-textZoomRatio(textZoomRatio: number): WebAttribute--><!--Device-WebAttribute-textZoomRatio(textZoomRatio: number): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textZoomRatio | number | 是 | 要设置的页面的文本缩放百分比，100表示原始大小，大于100表示放大，小于100表示缩小。 <br>取值为整数，范围为(0, 2147483647]。 |

## userAgent

```TypeScript
userAgent(userAgent: string)
```

设置用户代理。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 10

**替代接口：** setCustomUserAgent

<!--Device-WebAttribute-userAgent(userAgent: string): WebAttribute--><!--Device-WebAttribute-userAgent(userAgent: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userAgent | string | 是 | 要设置的用户代理。 |

## verticalScrollBarAccess

```TypeScript
verticalScrollBarAccess(verticalScrollBar: boolean)
```

设置是否显示纵向滚动条，包括系统默认滚动条和用户自定义滚动条。该属性没有显式调用时，默认显示。 > **说明：** > > - 通过@State变量控制纵向滚动条的隐藏/显示后，需要调用controller.refresh()生效。 > > - 通过@State变量频繁动态改变时，建议切换开关变量和Web组件一一对应。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-verticalScrollBarAccess(verticalScrollBar: boolean): WebAttribute--><!--Device-WebAttribute-verticalScrollBarAccess(verticalScrollBar: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| verticalScrollBar | boolean | 是 | 设置是否显示纵向滚动条。 <br>true表示显示，false表示不显示。 <br>传入undefined或null时为false。 |

## webCursiveFont

```TypeScript
webCursiveFont(family: string)
```

设置网页的cursive font字体库，用于渲染html前端使用cursive字体的元素。 当属性没有显式调用时，默认网页的cursive font字体库为cursive。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webCursiveFont(family: string): WebAttribute--><!--Device-WebAttribute-webCursiveFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的cursive font字体库。 <br>传入null或undefined时为cursive。 |

## webFantasyFont

```TypeScript
webFantasyFont(family: string)
```

设置网页的fantasy font字体库，用于渲染html前端使用fantasy字体的元素。 当属性没有显式调用时，默认网页的fantasy font字体库为fantasy。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webFantasyFont(family: string): WebAttribute--><!--Device-WebAttribute-webFantasyFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的fantasy font字体库。 <br>传入null或undefined时为fantasy。 |

## webFixedFont

```TypeScript
webFixedFont(family: string)
```

设置网页的fixed font字体库，用于渲染html前端使用monospace字体的元素。 当属性没有显式调用时，默认网页的fixed font字体库为monospace。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webFixedFont(family: string): WebAttribute--><!--Device-WebAttribute-webFixedFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的fixed font字体库，传入值为字体名称字符串，如"monospace"、"Arial"等。 <br>传入null或undefined时为monospace。 |

## webSansSerifFont

```TypeScript
webSansSerifFont(family: string)
```

设置网页的sans-serif font字体库，用于渲染html前端使用sans-serif字体的元素。 当属性没有显式调用时，默认网页的sans-serif font字体库为sans-serif。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webSansSerifFont(family: string): WebAttribute--><!--Device-WebAttribute-webSansSerifFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的sans-serif font字体库。 <br>传入null或undefined时为sans-serif。 |

## webSerifFont

```TypeScript
webSerifFont(family: string)
```

设置网页的serif font字体库，用于渲染html前端使用serif字体的元素。 当属性没有显式调用时，默认网页的serif font字体库为serif。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webSerifFont(family: string): WebAttribute--><!--Device-WebAttribute-webSerifFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的serif font字体库。 <br>传入null或undefined时为serif。 |

## webStandardFont

```TypeScript
webStandardFont(family: string)
```

设置网页的standard font字体库，用于渲染html前端未指定字体样式的元素。 当属性没有显式调用时，默认网页的standard font字体库为sans-serif。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-webStandardFont(family: string): WebAttribute--><!--Device-WebAttribute-webStandardFont(family: string): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| family | string | 是 | 设置网页的standard font字体库。 <br>传入null或undefined时为sans-serif。 |

## wideViewModeAccess

```TypeScript
wideViewModeAccess(wideViewModeAccess: boolean)
```

设置Web是否支持html中meta标签的viewport属性。该接口为空接口。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 10

**替代接口：** [metaViewport](#metaviewport)

<!--Device-WebAttribute-wideViewModeAccess(wideViewModeAccess: boolean): WebAttribute--><!--Device-WebAttribute-wideViewModeAccess(wideViewModeAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wideViewModeAccess | boolean | 是 | 设置Web是否支持html中meta标签的viewport属性。<br/>true表示支持html中meta标签的viewport属性，false表示 不支持html中meta标签的viewport属性。 |

## zoomAccess

```TypeScript
zoomAccess(zoomAccess: boolean)
```

设置是否支持手势进行缩放。该属性没有显式调用时，默认支持。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebAttribute-zoomAccess(zoomAccess: boolean): WebAttribute--><!--Device-WebAttribute-zoomAccess(zoomAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoomAccess | boolean | 是 | 设置是否支持手势进行缩放。 <br>true表示支持，false表示不支持。 <br>传入undefined或null时为false。 |

## zoomControlAccess

```TypeScript
zoomControlAccess(zoomControlAccess: boolean)
```

设置是否允许通过组合按键（Ctrl+'-/+'或Ctrl+鼠标滚轮/触摸板）进行缩放。 当属性没有显式调用时，默认允许通过组合按键进行缩放。

**起始版本：** 22

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-WebAttribute-zoomControlAccess(zoomControlAccess: boolean): WebAttribute--><!--Device-WebAttribute-zoomControlAccess(zoomControlAccess: boolean): WebAttribute-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoomControlAccess | boolean | 是 | 设置是否允许通过组合按键进行缩放。true表示支持，false表示不支持。传入null或undefined时为false。 |

