# ArkWeb术语解释

## A

### accessStep

WebviewController接口，判断当前页面是否可前进或后退指定步数。

### Active Focus Traversal；主动走焦

开发者或用户主观行为导致的焦点移动，如requestFocus申请焦点、按键走焦、点击申请焦点等。

### Ad Blocking；广告拦截

拦截网页广告的功能。

### Alert Dialog；警告框

显示包含可选信息的对话框。

### AlertDialog

ArkUI提供的警告对话框组件，用于显示包含可选信息的对话框。

### ArkUI Gestures；ArkUI手势

Web组件作为通用组件接收的ArkUI手势，作用于Web组件本身而非网页。

### ArkWeb

ArkWeb（方舟Web）提供了Web组件，用于在应用中显示Web页面内容。

### ArkWeb Gestures；ArkWeb手势

ArkWeb组件接收触摸事件自动生成的手势，作用于网页上。

### ASDF Webview

元服务内嵌网页渲染使用的官方Webview组件之一。

### Async Clipboard API

W3C异步剪贴板接口，提供给网页开发者读写系统剪贴板的方法。

### AtomicServiceEnhancedWeb

元服务内嵌页面使用的增强型Web组件，提供更丰富的Web能力。

### Attribute Change；属性变更

组件属性变更导致焦点转移。

### autofocus

W3C标准属性，表示元素应在页面加载时或dialog显示时获焦。

## B

### backToTop

Web组件属性，开启后通过点击状态栏可将Web页面滚动到页面顶部。

### backward

WebviewController接口，返回上一个Web页面。

### bindContextMenu

ArkUI接口，将自定义菜单与Web组件绑定。

### bindSelectionMenu

Web组件接口，实现自定义菜单功能，支持长按图片、链接、文本触发菜单。

### bypassVsyncCondition

Web组件属性，用于加快Web组件首帧滚动绘制。

## C

### Chromium Version；Chromium版本

ArkWeb内核基于谷歌Chromium内核开发，不同系统版本对应不同Chromium版本。

### Click/Touch for focus；点击申请获焦

通过手势、鼠标或触摸板点击使组件获焦。

### Clipboard Event

W3C剪贴板事件接口，描述cut、copy和paste事件。

### ClipboardItem

W3C剪贴板对象，用于写入任意类型内容到系统剪贴板。

### Clipboard；剪贴板

用于存储复制或剪切数据的系统组件。

### Component Focus；组件焦点

当前应用界面上唯一的一个可交互组件。

### Component Removal；组件移除

焦点所在的组件被移除时触发焦点转移。

### ConfirmDialog

ArkUI提供的确认对话框组件，用于验证用户是否接受某个操作。

### Context Menu；上下文菜单

用户通过右键点击或长按触发的快捷菜单。

### copyImage

WebContextMenuResult接口，复制网页中的图片到剪贴板。

### copyOptions

Web组件属性，指定Web组件上剪贴板复制的范围。

### CopyOptions.InApp

剪贴板复制范围选项，支持应用内复制。

### CopyOptions.LocalDevice

剪贴板复制范围选项，支持设备内复制，默认值。

### CopyOptions.None

剪贴板复制范围选项，不支持复制。

### createImageAssetRequest

photoAccessHelper接口，创建图片资源请求。

### Custom Menu；自定义菜单

开发者自定义触发时机与视觉呈现的菜单。

### CustomContentDialog

ArkUI提供的自定义内容对话框组件，用于自定义弹框内容区。

## D

### Data Detector；智能分词

自动识别页面中的电话号码、网址等信息并提供交互操作。

### dataDetectorConfig

Web组件属性，配置智能分词识别类型和预览菜单功能。

### dataTransfer.setData

H5拖拽接口，设置拖拽数据。

### DatePicker

ArkUI日期选择器组件，与Web组件结合时会抢焦。

### DocumentSaveOptions

picker模块提供的文档保存选项对象。

### DocumentSelectOptions

picker模块提供的文档选择选项对象。

### DocumentViewPicker

picker模块提供的文档选择器。

### Drag and Drop；拖放

Drag and Drop，将元素从一个位置拖到另一个位置并放置的操作。

### dragging；拖滑

手指未离开屏幕时的滚动行为。

### Drag；拖拽功能

Drag功能，在网页中实现元素的拖放交互。

## E

### editMenuOptions

Web组件接口，对文本选中菜单进行自定义操作。

### EditMenuOptions

文本选中菜单自定义选项对象，包含onCreateMenu和onMenuItemClick方法。

### enableDataDetector

Web组件属性，设置是否启用智能分词功能。

### enablePreviewMenu

智能分词配置项，设置是否启用分词长按预览功能。

### enableScrollInteraction

List组件属性，设置是否允许滚动交互。

### enableSelectedDataDetector

Web组件属性，单独配置文本选择AI菜单的启用情况。

## F

### Files

H5拖拽数据格式，文件类型。

### FileSelectorResult

文件选择器结果对象，用于处理文件上传结果。

### FlingCancel

手势事件，取消抛滑时触发。

### FlingStart

手势事件，滚动过程中手指抬起且速度足够快时触发抛滑。

### Fling；抛滑

手指离开屏幕时带有速度，离手后页面继续滚动。

### Focus Chain；焦点链

焦点在应用内组件之间转移的路径。

### Focus Transition；走焦

焦点在组件或元素之间转移的行为。

### focusable

Web组件属性，控制组件是否能够获取焦点。

### Focus；焦点

当前应用界面上唯一的一个可交互元素。

### forceEnableZoom

Web组件属性，控制网页强制缩放功能。

## G

### Gesture Blocking；手势拦截

拦截Web组件的手势事件。

### Gesture Conflict Handling；手势冲突处理

处理ArkUI手势与ArkWeb手势的冲突。

### Gesture Recognition；手势识别

识别用户触摸屏交互产生的手势。

### GestureControl

手势控制模块，提供手势类型定义。

### GestureJudgeResult

手势判断结果，包含REJECT和CONTINUE两个值。

### GestureRecognizer

手势识别器，用于识别用户手势。

### GestureType.PAN_GESTURE

手势类型，滑动手势。

### Gesture；手势
用户通过触摸屏幕进行的交互动作，如点击、长按、滑动等。Web组件支持多种手势事件处理。

### getAcceptableFileTypes

文件选择器参数接口，获取可接受的文件类型。

### getAcceptType

文件选择器回调接口，返回accept属性值转换的文件扩展名数组。

### getDescriptions

文件选择器参数接口，获取文件类型描述。

### getLinkUrl

WebContextMenuParam接口，获取上下文菜单点击位置的链接URL。

### getMimeTypes

文件选择器回调接口，返回accept属性值拆分后的字符串数组。

### getPageOffset

WebviewController接口，获取Web组件的滚动偏移量。

### getPreviewHeight

WebContextMenuParam接口，获取预览窗口高度。

### getPreviewWidth

WebContextMenuParam接口，获取预览窗口宽度。

### getSourceUrl

WebContextMenuParam接口，获取图片源URL。

### getSuggestedName

文件选择器参数接口，获取建议的文件名。

## H

### handleCancel

JsResult接口，处理弹框取消操作。

### handleConfirm

JsResult接口，处理弹框确认操作。

### handleFileList

FileSelectorResult接口，将选择的文件路径提交给ArkWeb。

### handlePromptConfirm

JsResult接口，处理提示框确认并返回输入值。

### HAP

HarmonyOS Ability Package，鸿蒙应用包。包含应用代码、资源和配置文件的部署单元。

## I

### IMAGE

WebElementType枚举值，图片类型元素。

### IMAGE_VIDEO_TYPE

PhotoViewMIMETypes枚举值，图片和视频类型。

### Incognito Mode；无痕浏览模式

不保留浏览记录和数据的浏览模式。

### initialScale

Web组件属性，设置页面初始缩放比例。

### isAcceptAllOptionExcluded

文件选择器参数接口，判断是否排除全部接受选项。

## J

### JsResult

弹框结果对象，用于处理网页弹框的确认或取消操作。

## K

### Keyboard traversal；按键走焦

通过Tab键、Shift+Tab键在组件之间转移焦点。

### keyboard zoom；键盘缩放

通过Ctrl+'-'/'+'或Ctrl+鼠标滚轮进行页面缩放。

### KeyCode

按键码枚举，定义键盘按键对应的数值。

## L

### LONG_PRESS

WebResponseType枚举值，长按响应类型。

### LongPress

手势事件，按下且不移动经过延迟后触发。

## M

### maintainVisibleContentPosition

List组件属性，保持可见内容位置不变。

### max-fling-speed-x

viewport meta标签属性，限制横向抛滑速度。

### max-fling-speed-y

viewport meta标签属性，限制纵向抛滑速度。

### maximum-scale

viewport meta标签属性，设置页面最大缩放比例。

### maxSelectNumber

PhotoSelectOptions属性，设置最大选择数量。

### Media Playback Hosting；媒体播放托管

Web组件的媒体播放由应用侧托管。

### Menu

ArkUI菜单组件，以垂直列表形式显示菜单项。

### MenuBuilder

菜单构建器，用于创建上下文菜单的ArkUI组件。与Web组件绑定可实现自定义右键菜单功能。

### MenuItem

ArkUI菜单项组件，展示菜单中具体的菜单项。

### MenuType.PREVIEW_MENU

菜单类型，预览菜单。

### MenuType.SELECTION_MENU

菜单类型，选择菜单。

### minimum-scale

viewport meta标签属性，设置页面最小缩放比例。

### mouse wheel zoom；鼠标滚轮缩放

通过Ctrl+鼠标滚轮进行页面缩放。

## N

### navigator.clipboard.read

W3C剪贴板接口，从系统剪贴板读取任意类型内容。

### navigator.clipboard.readText

W3C剪贴板接口，从系统剪贴板读取文本。

### navigator.clipboard.write

W3C剪贴板接口，将任意类型内容写入系统剪贴板。

### navigator.clipboard.writeText

W3C剪贴板接口，将文本写入系统剪贴板。

### NdkGestureSetting

原生（NDK）手势设置接口，用于配置和管理设备手势识别功能。

### Nested Scrolling；嵌套滑动

Web组件与父容器之间协调滚动行为的机制，支持同步滚动和惯性处理。

### nestedScroll

Web组件属性，设置嵌套滚动的模式。

### NestedScrollMode

嵌套滚动模式枚举，包含PARENT_FIRST和SELF_FIRST等值。

### Network Hosting；网络托管

Web组件的网络请求由应用侧托管。

## O

### onAlert

Web组件事件，监听网页alert方法。

### onAppear

菜单显示回调，菜单弹出时触发。

### onBackPress

应用侧回调，用户按返回键时触发。

### onBlur

应用侧通用失焦回调接口，组件失焦时触发。

### onConfirm

Web组件事件，监听网页confirm方法。

### onContextMenuShow

Web组件事件，上下文菜单弹出时触发。

### onCreateMenu

文本选中菜单回调，自定义菜单项。

### onDisappear

菜单消失回调，菜单关闭时触发。

### onDragEnd

拖拽事件，由Web发起的拖拽元素结束拖拽时触发。

### onDragEnter

拖拽事件，拖拽元素进入Web区域时触发。

### onDragLeave

拖拽事件，拖拽元素离开Web区域时触发。

### onDragMove

拖拽事件，拖拽元素在Web区域移动时触发。

### onDragStart

拖拽事件，拖拽开始时触发。

### onDrop

拖拽事件，拖拽元素落入Web区域时触发。

### onFocus

应用侧通用获焦回调接口，组件获焦时触发。

### onGestureRecognizerJudgeBegin

手势识别器判断回调，识别器即将成功时触发。

### onKeyPreIme

Web组件事件，拦截键盘输入。

### onMenuItemClick

文本选中菜单回调，处理菜单项点击事件。

### onPrompt

Web组件事件，监听网页prompt方法。

### onScaleChange

Web组件事件，监听页面缩放比例变化。

### onScrollFrameBegin

Scroll组件事件，滚动帧开始时触发。

### onShowFileSelector

Web组件事件，处理前端页面文件上传请求。

### overlay attribute；overlay属性类型组件

ArkUI组件类型，默认抢焦，如Menu、DatePicker、TimePicker、弹窗等。

## P

### pageDown

WebviewController接口，将Web组件内容向下滚动半个视口或到底部。

### pageUp

WebviewController接口，将Web组件内容向上滚动半个视口或到顶部。

### PARENT_FIRST

NestedScrollMode枚举值，父组件优先滚动。

### Passive Focus Traversal；被动走焦

焦点因系统或其他操作而转移，无需开发者直接干预。

### Password Safe；密码保险箱

ArkWeb提供的隐私保护功能，可安全存储和自动填充用户密码。

### PASTE

TextMenuItemId枚举值，粘贴菜单项。

### paste

WebContextMenuResult接口，从剪贴板粘贴内容到网页。

### pasteAndMatchStyle

WebContextMenuResult接口，粘贴并匹配样式。

### photoAccessHelper

媒体库模块，提供图片和视频访问接口。

### PhotoSelectOptions

photoAccessHelper提供的图片选择选项对象。

### PhotoViewMIMETypes

photoAccessHelper提供的图片视图MIME类型枚举。

### PhotoViewPicker

photoAccessHelper提供的图片选择器。

### PickerMediaType

cameraPicker提供的媒体类型枚举。

### PickerProfile

cameraPicker提供的选择器配置对象。

### PinchBegin

手势事件，捏合开始时触发。

### PinchEnd

手势事件，捏合结束时触发。

### PinchGesture

ArkUI捏合手势，双指或多指捏合触发。

### PinchUpdate

手势事件，捏合过程中触发。

### preventDefault

H5接口，阻止事件默认行为。

## Q

### QR Code；二维码

一种二维条形码，通过特定几何图形记录信息。Web菜单支持识别页面中的二维码图片。

## R

### read

W3C剪贴板接口，从系统剪贴板读取任意类型内容。

### READ_PASTEBOARD

应用访问剪贴板内容所需的权限。

### readText

W3C剪贴板接口，从系统剪贴板读取文本。

### RenderMode.SYNC_RENDER

渲染模式，同步渲染。

### requestFocus

WebviewController接口，组件主动申请获焦。

### runJavaScriptExt

WebviewController接口，执行JavaScript脚本并支持ArrayBuffer参数。

## S

### SaveButton

ArkUI安全组件，用于保存文件。

### SaveButtonOnClickResult

保存按钮点击结果，包含SUCCESS等值。

### SaveButtonOptions

保存按钮配置选项对象。

### SaveDescription

保存按钮描述枚举，如SAVE_IMAGE。

### SaveIconStyle

保存按钮图标样式枚举。

### scale

Web组件方法，调整Web组件的缩放比例。

### ScrollBegin

手势事件，滚动开始时触发。

### scrollBy

WebviewController接口，将页面滚动指定的偏移量。

### ScrollEnd

手势事件，滚动结束时触发。

### scrollTo

WebviewController接口，将页面滚动到指定的绝对位置。

### ScrollType.EVENT

滚动类型枚举值，事件滚动。

### ScrollUpdate

手势事件，滚动时触发，包括抛滑和拖滑。

### selectAll

WebContextMenuResult接口，选中全部内容。

### selection-api

W3C选区API，用于操作文本选区。

### selectionchange

H5事件，选区变更时触发。

### SelectionMenuOptionsExt

自定义菜单选项扩展对象，包含preview、menuType等配置。

### SELF_FIRST

NestedScrollMode枚举值，子组件优先滚动。

### setScrollable

WebviewController接口，设置Web是否禁用触摸滚动。

### Status Bar；状态栏

设备顶部显示系统状态的区域，点击可返回页面顶部。

### Subsystem

子系统，OpenHarmony架构中的功能模块划分单元。

## T

### tabindex

W3C标准属性，定义Web组件内元素的焦点顺序。

### Text Selection Menu；文本选中菜单

用户选中文本时动态显示的上下文交互组件。

### text/html

H5拖拽数据格式，HTML类型。

### text/plain

H5拖拽数据格式，文本类型。

### text/uri-list

H5拖拽数据格式，链接类型。

### TextDataDetectorConfig

智能分词配置对象，包含enablePreviewMenu和types等属性。

### TextDataDetectorType

智能分词识别类型枚举，包含电话、链接、邮箱、地址、时间等。

### TextMenuItem

文本菜单项对象，定义菜单项名称、图标、ID等内容。

### TextMenuItemId

文本菜单项ID枚举，包含CUT、COPY、PASTE等值。

### TextRange

文本范围对象，表示选中文本的范围。

### TimePicker

ArkUI时间选择器组件，与Web组件结合时会抢焦。

### Touch Events

W3C触摸事件标准，描述触摸屏交互事件。

### TouchCancel

触摸事件，取消触摸时发送给Web组件。

## U

### UI Events

W3C用户界面事件标准，描述键盘、鼠标等交互事件。

### User-Agent；用户代理

标识浏览器类型和版本的字符串信息。

### user-scalable

viewport meta标签属性，设置是否允许用户缩放。

### user-select

CSS样式属性，设置文本是否可选中。

## W

### Web Element Focus；网页元素焦点

当前网页界面上唯一的一个可交互元素。

### WebBypassVsyncCondition.SCROLLBY_FROM_ZERO_OFFSET

绕过Vsync条件，从零偏移开始scrollBy。

### WebContextMenuParam

上下文菜单参数对象，包含点击位置对应HTML元素信息和位置信息。

### WebContextMenuResult

上下文菜单结果对象，提供常见的菜单能力如复制、粘贴等。

### WebElementType

Web元素类型枚举，包含IMAGE、LINK、TEXT等值。

### WebLayoutMode.FIT_CONTENT

Web布局模式，全量展开模式。

### WebResponseType

Web响应类型枚举，包含LONG_PRESS等值。

### window.alert

JavaScript接口，显示警告框。

### window.confirm

JavaScript接口，显示确认框。

### window.getSelection

JavaScript接口，获取当前选区。

### window.innerHeight

JavaScript属性，获取窗口内部高度。

### window.prompt

JavaScript接口，显示提示框。

### write

W3C剪贴板接口，将任意类型内容写入系统剪贴板。

### writeText

W3C剪贴板接口，将文本写入系统剪贴板。

## X

### XMLHttpRequest

用于发送HTTP请求的JavaScript对象。

## Z

### zoomAccess

Web组件属性，控制是否可以缩放。

### zoomControlAccess

Web组件属性，设置是否允许通过组合按键进行缩放。
