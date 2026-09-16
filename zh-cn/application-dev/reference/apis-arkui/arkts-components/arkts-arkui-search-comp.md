# Search

搜索框组件，支持搜索图标、清除按钮、搜索按钮、placeholder提示文本、自定义键盘等功能配置，适用于浏览器的搜索内容输入框、应用内搜索等场景。

> **说明：** > > 该组件仅支持单文本样式，若需实现富文本样式，建议使用RichEditor组件。

## 子组件

无

## Search

```TypeScript
Search(options?: SearchOptions)
```

定义搜索组件构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SearchOptions](arkts-arkui-searchoptions-i.md) | 否 | 搜索框组件初始化选项。当需要设置搜索框的初始值、提示文本、图标或控制器时传入此参数，不传入时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CancelButtonOptions](arkts-arkui-cancelbuttonoptions-i.md) | 定义清除按钮选项。 |
| [CancelButtonSymbolOptions](arkts-arkui-cancelbuttonsymboloptions-i.md) | 定义清除按钮Symbol图标选项。 |
| [IconOptions](arkts-arkui-iconoptions-i.md) | 定义图标选项。 |
| [SearchButtonOptions](arkts-arkui-searchbuttonoptions-i.md) | 定义搜索按钮选项。 |
| [SearchOptions](arkts-arkui-searchoptions-i.md) | Search初始化参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SearchSubmitCallback](arkts-arkui-searchsubmitcallback-t.md) | 点击搜索图标、搜索按钮或者按下软键盘搜索按钮时的回调事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CancelButtonStyle](arkts-arkui-cancelbuttonstyle-e.md) | 清除按钮样式枚举。 |
| [SearchType](arkts-arkui-searchtype-e.md) | 搜索输入框类型。 |

## 示例

```TypeScript
### 示例1（设置与获取光标位置）

从API version 8开始，该示例通过[controller](arkts-arkui-searchcontroller-c.md)实现了光标位置的设置与获取的功能。


```

```TypeScript
### 示例2（设置搜索和删除图标）

该示例通过[searchButton](#searchbutton)（从API version 8开始）、[searchIcon](#searchicon10)（从API version 10开始）、[cancelButton](#cancelbutton10)（从API version 10开始）属性展示了设置搜索和删除图标的效果。


```

```TypeScript
### 示例3（设置自定义键盘）

该示例通过[customKeyboard](#customkeyboard10)（从API version 10开始）属性分别将value中的入参类型设置为[CustomBuilder](ts-types.md#custombuilder8)和ComponentContent，实现了自定义键盘的功能。

从API version 22开始[customKeyboard](#customkeyboard10)属性新增了入参类型ComponentContent。


```

```TypeScript
### 示例4（设置输入法回车键类型）

该示例通过[enterKeyType](#enterkeytype12)（从API version 12开始）属性实现了动态切换输入法回车键的效果。


```

```TypeScript
### 示例5（设置文本样式）

从API version 12开始，该示例通过[lineHeight](#lineheight12)、[letterSpacing](#letterspacing12)、[decoration](#decoration12)属性展示了不同样式的文本效果。


```

```TypeScript
### 示例6（设置文字特性效果）

该示例通过[fontFeature](#fontfeature12)（从API version 12开始）属性实现了文本在不同文字特性下的展示效果。


```

```TypeScript
### 示例7（自定义键盘避让）

该示例通过[customKeyboard](#customkeyboard10)（从API version 10开始）属性配置[KeyboardOptions](ts-basic-components-richeditor.md#keyboardoptions12)（从API version 12开始）接口实现了自定义键盘避让的效果。


```

```TypeScript
### 示例8（设置文本自适应）

从API version 12开始，该示例通过[minFontSize](#minfontsize12)、[maxFontSize](#maxfontsize12)属性展示了文本自适应字号的效果。


```

```TypeScript
### 示例9（支持插入和删除回调）

从API version 12开始，该示例通过[onWillInsert](#onwillinsert12)、[onDidInsert](#ondidinsert12)、[onWillDelete](#onwilldelete12)、[onDidDelete](#ondiddelete12)接口实现了插入和删除的效果。从API version 15开始，通过[onWillChange](#onwillchange15)接口展示了文本内容将要发生变化时的具体信息。


```

```TypeScript
### 示例10（文本扩展自定义菜单）

从API version 12开始，该示例通过[editMenuOptions](#editmenuoptions12)接口实现了文本设置自定义菜单扩展项的文本内容、图标以及回调的功能，同时，可以在[onPrepareMenu](ts-text-common.md#属性-1)（从API version 20开始）回调中，进行菜单数据的设置。


```

```TypeScript
### 示例11（设置symbol类型清除按钮）

从API version 10开始，该示例通过[searchIcon](#searchicon10)、[cancelButton](#cancelbutton10)属性展示了自定义右侧symbol类型清除按钮样式的效果。


```

```TypeScript
### 示例12（设置文本是否可复制）

该示例通过[copyOption](#copyoption9)、[onWillCopy](#onwillcopy)、[onWillCut](#onwillcut)接口展示如何设置文本复制、如何拦截系统复制、如何拦截系统剪切。

从API版本26.0.0开始，新增[onWillCopy](#onwillcopy)、[onWillCut](#onwillcut)接口。


```

```TypeScript
### 示例13（设置文本水平对齐/光标样式/选中背景色）

该示例通过[textAlign](#textalign9)（从API version 9开始）、[caretStyle](#caretstyle10)（从API version 10开始）、[selectedBackgroundColor](#selectedbackgroundcolor12)（从API version 12开始）属性展示如何设置文本的水平对齐、光标样式和选中背景色。


```

```TypeScript
### 示例14（设置默认获焦并拉起软键盘）

该示例通过[defaultFocus](ts-universal-attributes-focus.md#defaultfocus9)（从API version 9开始）、[enableKeyboardOnFocus](#enablekeyboardonfocus10)（从API version 10开始）属性展示如何设置默认获焦并拉起软键盘。


```

```TypeScript
### 示例15（关闭系统文本选择菜单）

该示例通过[selectionMenuHidden](#selectionmenuhidden10)（从API version 10开始）属性展示如何关闭系统文本选择菜单。


```

```TypeScript
### 示例16（对输入的文本进行过滤）

从API version 12开始，该示例通过[inputFilter](#inputfilter12)属性展示如何对输入的文本进行内容的过滤，以限制输入内容。


```

```TypeScript
### 示例17（设置选中指定区域的文本内容）

该示例通过[setTextSelection](#settextselection12)（从API version 12开始）方法展示如何设置选中指定区域的文本内容以及菜单的显隐策略。


```

```TypeScript
### 示例18（设置文本滚动事件）

从API version 10开始，该示例通过[onContentScroll](#oncontentscroll10)事件展示如何设置文本滚动事件的回调。


```

```TypeScript
### 示例19（设置最小字体范围与最大字体范围）

从API version 18开始，该示例通过[minFontScale](#minfontscale18)、[maxFontScale](#maxfontscale18)设置字体显示最小与最大范围。调整系统字体大小后，文本字体大小不会超过[minFontScale](#minfontscale18)、[maxFontScale](#maxfontscale18)设置的范围。如下示例展示了Search组件在不同的字体大小限制条件下，调整系统字体后的放大缩小效果。
```

```TypeScript
// AppScope/app.json5，修改如下代码。
{
  "app": {
    "bundleName": "com.example.myapplication",
    "vendor": "example",
    "versionCode": 1000000,
    "versionName": "1.0.0",
    "icon": "$media:app_icon",
    "label": "$string:app_name",
    "configuration": "$profile:configuration"
  }
}
```

```TypeScript
 
```

```TypeScript
### 示例20（设置文本描边）

从API version 20开始，该示例通过[strokeWidth](#strokewidth20)和[strokeColor](#strokecolor20)属性设置文本的描边宽度及颜色。

从API版本26.0.0开始，新增[strokeJoinStyle](#strokejoinstyle)接口，支持设置文本描边拐角样式。


```

```TypeScript
### 示例21（设置中西文自动间距）

从API version 20开始，该示例通过[enableAutoSpacing](#enableautospacing20)属性设置中西文自动间距。


```

```TypeScript
### 示例22（设置placeholder富文本样式）

从API version 22开始，该示例通过[setStyledPlaceholder](ts-universal-attributes-text-style.md#setstyledplaceholder22)接口设置placeholder富文本样式。


```

```TypeScript
### 示例23（设置输入法扩展信息）

从API version 22开始，该示例通过[IMEClient](ts-text-common.md#imeclient20对象说明)的setExtraConfig设置输入法扩展信息。
```

```TypeScript
### 示例24（设置输入框分割线颜色）

从API version 23开始，该示例通过[dividerColor](#dividercolor23)接口设置输入框分割线颜色。


```

```TypeScript
### 示例25（设置行首标点压缩）

该示例通过[compressLeadingPunctuation](#compressleadingpunctuation23)接口设置行首标点压缩，左侧有间距的标点符号位于行首时，标点会直接压缩间距至左侧边界。

从API version 23开始，支持compressLeadingPunctuation接口。


```

```TypeScript
### 示例26（设置自适应间距）

该示例通过[includeFontPadding](#includefontpadding23)接口增加首行尾行间距和[fallbackLineSpacing](#fallbacklinespacing23)接口设置自适应行间距。

从API version 23开始，新增[includeFontPadding](#includefontpadding23)和[fallbackLineSpacing](#fallbacklinespacing23)接口。


```

```TypeScript
### 示例27（设置文本拖拽时的背板样式）

该示例通过[selectedDragPreviewStyle](#selecteddragpreviewstyle23)接口设置文本拖拽时的背板样式。

从API version 23开始，新增selectedDragPreviewStyle接口。


```

```TypeScript
### 示例28（删除文本框内的最后一个字符）

该示例通过调用[deleteBackward](ts-universal-attributes-text-style.md#deletebackward23)接口删除文本框内最后一个字符。

从API version 23开始，新增[deleteBackward](ts-universal-attributes-text-style.md#deletebackward23)接口。


```

```TypeScript
### 示例29（设置文本排版方向）

该示例通过[textDirection](#textdirection23)接口设置文本排版方向。

从API version 23开始，新增textDirection接口。


```

```TypeScript
### 示例30（将指定范围的文字滚动到可视区内）

本示例通过[scrollToVisible](./ts-universal-attributes-text-style.md#scrolltovisible23)将可视区外的文本滚动到可视区内。

从API version 23开始，新增scrollToVisible接口。


```

```TypeScript
### 示例31（设置文本着色器效果）

该示例通过[shaderStyle](#shaderstyle)接口实现对Search组件内文本着色效果。

从API版本26.0.0开始，新增shaderStyle接口。


```

```TypeScript
### 示例32（设置文本选择的AI菜单）

该示例通过[enableSelectedDataDetector](#enableselecteddatadetector22)，配置文本选择AI菜单功能。

从API version 22开始，新增enableSelectedDataDetector。
```
