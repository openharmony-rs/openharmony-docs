# TextArea

多行文本输入框组件，当输入的文本内容超过组件宽度时会自动换行显示，适用于评论输入、反馈表单、内容编辑等需要多行文本输入的场景。

高度未设置时，组件无默认高度，自适应内容高度。宽度未设置时，默认撑满最大宽度。

## 子组件

无

## TextArea

```TypeScript
TextArea(value?: TextAreaOptions)
```

定义TextArea组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextAreaOptions](arkts-arkui-textareaoptions-i.md) | 否 | TextArea组件参数。默认值：详见TextAreaOptions。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextAreaOptions](arkts-arkui-textareaoptions-i.md) | TextArea初始化参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [TextAreaSubmitCallback](arkts-arkui-textareasubmitcallback-t.md) | 软键盘按下回车键时的回调事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TextAreaType](arkts-arkui-textareatype-e.md) | 多行文本输入框类型。 |

## 示例

```TypeScript
### 示例1（设置与获取光标位置）

从API version 8开始，该示例通过[controller](arkts-arkui-textareacontroller-c.md)实现了光标位置的设置与获取。


```

```TypeScript
### 示例2（设置计数器）

从API version 10开始，该示例通过[maxLength](#maxlength10)、[showCounter](#showcounter10)属性实现了计数器的功能。


```

```TypeScript
### 示例3（设置自定义键盘）

该示例通过[customKeyboard](#customkeyboard10)（从API version 10开始）属性分别将value中的入参类型设置为[CustomBuilder](ts-types.md#custombuilder8)和ComponentContent，实现了自定义键盘的功能。

从API version 22开始[customKeyboard](#customkeyboard10)属性新增了入参类型ComponentContent。


```

```TypeScript
### 示例4（设置输入法回车键类型）

从API version 11开始，该示例通过[enterKeyType](#enterkeytype11)属性实现了动态切换输入法回车键的效果。


```

```TypeScript
### 示例5（设置文本断行规则）

从API version 12开始，该示例通过[wordBreak](#wordbreak12)属性实现了TextArea不同断行规则下的效果。


```

```TypeScript
### 示例6（设置文本样式）

从API version 12开始，该示例通过[lineHeight](#lineheight12)、[letterSpacing](#letterspacing12)、[decoration](#decoration12)属性展示了不同样式的文本效果。


```

```TypeScript
### 示例7（设置文字特性效果）

从API version 12开始，该示例通过[fontFeature](#fontfeature12)属性实现了文本在不同文字特性下的展示效果。


```

```TypeScript
### 示例8（自定义键盘避让）

该示例通过[customKeyboard](#customkeyboard10)（从API version 10开始）属性配置[KeyboardOptions](ts-basic-components-richeditor.md#keyboardoptions12)（从API version 12开始）接口实现了自定义键盘避让的效果。


```

```TypeScript
### 示例9（设置文本自适应）

从API version 12开始，该示例通过[minFontSize](#minfontsize12)、[maxFontSize](#maxfontsize12)、[heightAdaptivePolicy](#heightadaptivepolicy12)属性展示了文本自适应字号的效果。


```

```TypeScript
### 示例10（设置文本行间距）

从API version 12开始，该示例通过[lineSpacing](#linespacing12)属性展示了文本在不同行间距下的展示效果，同时，配置[LineSpacingOptions](ts-text-common.md#linespacingoptions20对象说明)中的onlyBetweenLines（从API version 20开始）属性，可以设置文本的行间距是否仅在行与行之间生效。


```

```TypeScript
### 示例11（设置自动填充）

从API version 12开始，该示例通过[contentType](#contenttype12)、[enableAutoFill](#enableautofill12)属性实现了文本自动填充的功能。
```

```TypeScript
### 示例12（设置折行规则）

从API version 12开始，该示例通过[lineBreakStrategy](#linebreakstrategy12)属性实现了TextArea不同折行规则下的效果。


```

```TypeScript
### 示例13（支持插入和删除回调）

从API version 12开始，该示例通过[onWillInsert](#onwillinsert12)、[onDidInsert](#ondidinsert12)、[onWillDelete](#onwilldelete12)、[onDidDelete](#ondiddelete12)接口实现了插入和删除的功能。


```

```TypeScript
### 示例14（文本扩展自定义菜单）

从API version 12开始，该示例通过[editMenuOptions](#editmenuoptions12)接口实现了文本设置自定义菜单扩展项的文本内容、图标以及回调的功能，同时，可以在[onPrepareMenu](ts-text-common.md#属性-1)（从API version 20开始）回调中，进行菜单数据的设置。


```

```TypeScript
### 示例15（文本设置省略模式）

该示例通过[textOverflow](#textoverflow12)、[ellipsisMode](#ellipsismode18)、[maxLines](#maxlines10)属性展示了文本超长省略以及调整省略位置的效果，通过MULTILINE_START和MULTILINE_CENTER两种类型实现了单行文本和多行文本场景下的省略号在行首和行中的效果。

从API version 10开始，通过[maxLines](#maxlines10)属性设置文本显示的最大行数。

从API version 12开始，通过[textOverflow](#textoverflow12)属性设置文本超长时的显示方式。

从API version 18开始，通过[ellipsisMode](#ellipsismode18)属性设置省略号位置。

从API version 24开始，[EllipsisMode](ts-appendix-enums.md#ellipsismode11)新增了MULTILINE_START和MULTILINE_CENTER枚举。


```

```TypeScript
### 示例16（自定义复制、剪切、粘贴）

该示例通过[onCopy](#oncopy8)、[onCut](#oncut8)、[onPaste](#onpaste)、[onWillCopy](#onwillcopy)、[onWillCut](#onwillcut)展示如何监听文本选择菜单的复制、剪切、粘贴按钮、如何屏蔽系统粘贴功能并实现自定义的粘贴能力、如何屏蔽系统复制功能，以及如何屏蔽系统剪切功能，同时，可以通过[maxFontScale](#maxfontscale18)、[minFontScale](#minfontscale18)属性设置文本最大和最小的字体缩放倍数。

从API版本26.0.0开始，新增[onWillCopy](#onwillcopy)、[onWillCut](#onwillcut)接口。


```

```TypeScript
### 示例17（设置最小字体范围与最大字体范围）

从API version 18开始，该示例通过[minFontScale](#minfontscale18)、[maxFontScale](#maxfontscale18)设置字体显示最小与最大范围（该示例使用系统接口，应用类型需调整为系统应用，可参考HarmonyAppProvision的[系统接口说明](../../../reference/development-intro-api.md#系统接口说明)）。
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
// xxx.ets
import { abilityManager, Configuration } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct TextAreaExample {
  @State currentFontSizeScale: number = 1;
  @State minFontScale: number = 0.85;
  @State maxFontScale: number = 2;

  // 设置字体大小
  async setFontScale(scale: number): Promise<void> {
    let configInit: Configuration = {
      fontSizeScale: scale
    };
    // 更新配置-字体大小，调用系统接口更新字体配置
    // 需在工程的module.json5文件的requestPermissions字段配置权限：ohos.permission.UPDATE_CONFIGURATION
    abilityManager.updateConfiguration(configInit, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to updateConfiguration. Code: ${err.code}, message: ${err.message}`);
      } else {
        this.currentFontSizeScale = scale;
        console.info('updateConfiguration success.');
      }
    });
  }

  build() {
    Column() {
      Column({ space: 30 }) {
        Text('通过minFontScale、maxFontScale调整文本显示的最大和最小字体缩放倍数。')
        TextArea({
          placeholder: 'The text area can hold an unlimited amount of text. input your word...',
          text: '通过minFontScale、maxFontScale调整文本显示的最大和最小字体缩放倍数。'
        })
          .minFontScale(this.minFontScale) // 设置最小字体缩放倍数，参数为undefined则跟随系统默认倍数缩放
          .maxFontScale(this.maxFontScale) // 设置最大字体缩放倍数，参数为undefined则跟随系统默认倍数缩放
      }.width('100%')
      // 以下按钮只用做字体大小倍数调整，不在示例图中呈现
      Column() {
        Row() {
          Button('1倍').onClick(() => {
            this.setFontScale(1)
          }).margin(10)
          Button('1.75倍').onClick(() => {
            this.setFontScale(1.75)
          }).margin(10)
        }

        Row() {
          Button('2倍').onClick(() => {
            this.setFontScale(2)
          }).margin(10)
          Button('3.2倍').onClick(() => {
            this.setFontScale(3.2)
          }).margin(10)
        }
      }.margin({ top: 50 })
    }
  }
}
```

```TypeScript
### 示例18（设置选中指定区域的文本内容）

从API version 10开始，该示例通过[setTextSelection](#settextselection10)方法展示如何设置选中指定区域的文本内容以及菜单的显隐策略。


```

```TypeScript
### 示例19（设置文本描边）

从API version 20开始，该示例通过[strokeWidth](#strokewidth20)和[strokeColor](#strokecolor20)属性设置文本的描边宽度及颜色。

从API版本26.0.0开始，新增[strokeJoinStyle](#strokejoinstyle)接口，支持设置文本描边拐角样式。


```

```TypeScript
### 示例20（设置中西文自动间距）

从API version 20开始，该示例通过[enableAutoSpacing](#enableautospacing20)属性设置中西文自动间距。


```

```TypeScript
### 示例21（设置最大行数）

从API version 20开始，该示例通过[maxLines](#maxlines20)属性设置显示最大行数，超出最大行数后可滚动。


```

```TypeScript
### 示例22（设置最小行数）

从API version 20开始，该示例通过[minLines](#minlines20)属性设置显示的最小行数。


```

```TypeScript
### 示例23（设置字符计数颜色以及超出字符颜色）

从API version 22开始，该示例通过[showCounter](#showcounter10)属性的counterTextColor和counterTextOverflowColor设置字符计数颜色以及超出字符颜色。


```

```TypeScript
### 示例24（设置滚动条颜色）

从API version 22开始，该示例通过[scrollBarColor](#scrollbarcolor22)属性设置滚动条颜色。


```

```TypeScript
### 示例25（设置placeholder富文本样式）

从API version 22开始，该示例通过[setStyledPlaceholder](ts-universal-attributes-text-style.md#setstyledplaceholder22)接口设置placeholder富文本样式。

原始文本支持多种语言，不同语言内容时样式起始索引下标start和length会有差异，以下仅以中文设置富文本样式为例。


```

```TypeScript
### 示例26（设置输入法扩展信息）

从API version 22开始，该示例通过[IMEClient](ts-text-common.md#imeclient20对象说明)的setExtraConfig设置输入法扩展信息。
```

```TypeScript
### 示例27（设置行首标点符号压缩和行尾标点符号悬挂）

本示例通过[compressLeadingPunctuation](#compressleadingpunctuation23)接口设置行首标点符号压缩，通过[punctuationOverflow](#punctuationoverflow)设置行尾标点符号悬挂。

左侧有间距的标点符号位于行首时，标点会直接压缩间距至左侧边界。

当文本自动换行后，如果剩余内容（含标点符号）能够放入上一行，则标点符号悬挂生效。

从API版本23开始，新增compressLeadingPunctuation接口。

从API版本26.0.0开始，新增punctuationOverflow接口。


```

```TypeScript
### 示例28（设置自适应间距）

该示例通过[includeFontPadding](#includefontpadding23)接口增加首行尾行间距和[fallbackLineSpacing](#fallbacklinespacing23)接口设置自适应行间距。

从API version 23开始，新增[includeFontPadding](#includefontpadding23)和[fallbackLineSpacing](#fallbacklinespacing23)接口。


```

```TypeScript
### 示例29（设置文本拖拽时的背板样式）

该示例通过[selectedDragPreviewStyle](#selecteddragpreviewstyle23)接口设置文本拖拽时的背板样式。

从API version 23开始，新增selectedDragPreviewStyle接口。


```

```TypeScript
### 示例30（删除文本框内的最后一个字符）

该示例通过调用[deleteBackward](ts-universal-attributes-text-style.md#deletebackward23)接口删除文本框内最后一个字符。

从API version 23开始，新增[deleteBackward](ts-universal-attributes-text-style.md#deletebackward23)接口。


```

```TypeScript
### 示例31（设置文本排版方向）

该示例通过[textDirection](#textdirection23)接口设置文本排版方向。

从API version 23开始，新增textDirection接口。


```

```TypeScript
### 示例32（将指定范围的文字滚动到可视区内）

本示例通过[scrollToVisible](./ts-universal-attributes-text-style.md#scrolltovisible23)将可视区外的文本滚动到可视区内。

从API version 23开始，新增scrollToVisible接口。


```

```TypeScript
### 示例33（设置水平滚动）

本示例通过[horizontalScrolling](#horizontalscrolling24)设置水平滚动。

从API version 24开始，新增horizontalScrolling接口。


```

```TypeScript
### 示例34（设置文本排版时是否使能孤字优化）

该示例通过[orphanCharOptimization](#orphancharoptimization)接口设置使能孤字优化，确保段落最后一行不出现孤字。

从API版本26.0.0开始，新增orphanCharOptimization接口。

该效果图会因设备尺寸差异有显示区别，仅供参考。


```

```TypeScript
### 示例35（设置文本着色器效果）

该示例通过[shaderStyle](#shaderstyle)接口实现对TextArea组件内文本着色效果。

从API版本26.0.0开始，新增shaderStyle接口。


```

```TypeScript
### 示例36（设置文本选择的AI菜单）

该示例通过[enableSelectedDataDetector](#enableselecteddatadetector22)，配置文本选择AI菜单功能。

从API version 22开始，新增enableSelectedDataDetector。
```
