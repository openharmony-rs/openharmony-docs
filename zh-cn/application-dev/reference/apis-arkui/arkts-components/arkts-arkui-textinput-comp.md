# TextInput

单行文本输入框组件，用于接收用户的单行文本输入。支持多种输入类型（如文本、密码、邮箱、数字等）、自定义样式（字体、颜色、下划线、装饰线等）、输入过滤、密码输入模式、自动填充等功能，适用于登录注册、搜索、表单填写等多种场景。能够解决文本输入验证、格式化、安全输入等常见需求，简化开发流程、提升用户体验并增强数据安全性。

> **说明：** > > 该组件仅支持单文本样式，若需实现富文本样式，建议使用RichEditor组件。

## 子组件

无

## TextInput

```TypeScript
TextInput(value?: TextInputOptions)
```

定义单行文本输入组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextInputOptions](arkts-arkui-textinputoptions-i.md) | 否 | TextInput组件参数。默认值undefined。不设置该参数时，输入框初始化为空。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PasswordIcon](arkts-arkui-passwordicon-i.md) | PasswordIcon对象。 |
| [SubmitEvent](arkts-arkui-submitevent-i.md) | 定义用户提交事件。 |
| [TextInputOptions](arkts-arkui-textinputoptions-i.md) | TextInput初始化参数。 |
| [UnderlineColor](arkts-arkui-underlinecolor-i.md) | 定义下划线颜色宽度属性。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnContentScrollCallback](arkts-arkui-oncontentscrollcallback-t.md) | 文本内容滚动回调。 |
| [OnPasteCallback](arkts-arkui-onpastecallback-t.md) | 粘贴回调。 |
| [OnSubmitCallback](arkts-arkui-onsubmitcallback-t.md) | 提交回调。 |
| [OnTextSelectionChangeCallback](arkts-arkui-ontextselectionchangecallback-t.md) | 文本选择变化回调或光标位置变化回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContentType](arkts-arkui-contenttype-e.md) | 自动填充类型。 |
| [EnterKeyType](arkts-arkui-enterkeytype-e.md) | 输入法回车键类型。 |
| [InputType](arkts-arkui-inputtype-e.md) | 单行文本输入框类型。 |
| [TextInputStyle](arkts-arkui-textinputstyle-e.md) | 文本输入样式。 |

## 示例

```TypeScript
### 示例1（设置与获取光标位置）

从API version 8开始，该示例通过[controller](arkts-arkui-textinputcontroller-c.md)实现了光标位置的设置与获取的功能，同时，可以使用!!实现text参数的双向数据绑定（从API version 18开始）。


```

```TypeScript
### 示例2（设置下划线）

从API version 10开始支持，该示例通过[showUnderline](arkts-arkui-textinput-comp-attribute.md#showunderline)、[showError](arkts-arkui-textinput-comp-attribute.md#showerror)、[showUnit](arkts-arkui-textinput-comp-attribute.md#showunit)、[passwordIcon](#passwordicon10)属性展示了下划线在不同场景的效果，同时，可以通过[underlineColor](#underlinecolor12)（从API version 12开始）支持配置下划线颜色。


```

```TypeScript
### 示例3（设置自定义键盘）

该示例通过[customKeyboard](#customkeyboard10)（从API version 10开始）属性分别将value中的入参类型设置为[CustomBuilder](ts-types.md#custombuilder8)和ComponentContent，实现了自定义键盘的功能。

从API version 22开始[customKeyboard](#customkeyboard10)属性新增了入参类型ComponentContent。


```

```TypeScript
### 示例4（设置右侧清除按钮样式）

该示例通过[cancelButton](#cancelbutton11)属性展示了自定义右侧清除按钮样式的效果。


```

```TypeScript
### 示例5（设置计数器）

该示例通过[maxLength](#maxlength)、[showCounter](#showcounter11)（从API version 11开始）、[showUnderline](arkts-arkui-textinput-comp-attribute.md#showunderline)（从API version 10开始）属性实现了计数器的功能。


```

```TypeScript
### 示例6（电话号码格式化）

该示例通过[onChange](#onchange)回调实现了电话号码格式化为XXX XXXX XXXX的功能。


```

```TypeScript
### 示例7（设置文本断行规则）

从API version 12开始，该示例通过[wordBreak](#wordbreak12)属性实现了TextInput不同断行规则下的效果。


```

```TypeScript
### 示例8（设置文本样式）

从API version 12开始，该示例通过[lineHeight](#lineheight12)、[letterSpacing](#letterspacing12)、[decoration](#decoration12)属性展示了不同样式的文本效果。


```

```TypeScript
### 示例9（设置文字特性效果）

从API version 12开始，该示例通过[fontFeature](#fontfeature12)属性实现了文本在不同文字特性下的展示效果。


```

```TypeScript
### 示例10（自定义键盘避让）

该示例通过[customKeyboard](#customkeyboard10)（从API version 10开始）属性配置[KeyboardOptions](ts-basic-components-richeditor.md#keyboardoptions12)（从API version 12开始）接口实现了自定义键盘避让的效果。


```

```TypeScript
### 示例11（设置文本自适应）

从API version 12开始，该示例通过[minFontSize](#minfontsize12)、[maxFontSize](#maxfontsize12)、[heightAdaptivePolicy](#heightadaptivepolicy12)属性实现了文本自适应字号的功能。


```

```TypeScript
### 示例12（设置折行规则）

从API version 12开始，该示例通过[lineBreakStrategy](#linebreakstrategy12)属性实现了TextInput不同折行规则下的效果。


```

```TypeScript
### 示例13（支持插入和删除回调）

从API version 12开始，该示例通过[onWillInsert](#onwillinsert12)、[onDidInsert](#ondidinsert12)、[onWillDelete](#onwilldelete12)、[onDidDelete](#ondiddelete12)接口实现了插入和删除的效果。


```

```TypeScript
### 示例14（文本扩展自定义菜单）

从API version 12开始，该示例通过[editMenuOptions](#editmenuoptions12)接口实现了文本设置自定义菜单扩展项的文本内容、图标以及回调的功能，同时，可以在[onPrepareMenu](ts-text-common.md#属性-1)（从API version 20开始）回调中，进行菜单数据的设置。


```

```TypeScript
### 示例15（设置symbol类型清除按钮）

从API version 18开始，该示例通过[cancelButton](#cancelbutton18)属性展示了自定义右侧symbol类型清除按钮样式的效果。


```

```TypeScript
### 示例16（文本设置省略模式）

该示例通过[textOverflow](#textoverflow12)、[ellipsisMode](#ellipsismode18)、[style](#style9)属性展示了文本超长省略以及调整省略位置的效果，通过MULTILINE_START和MULTILINE_CENTER两种类型实现了单行文本和多行文本场景下的省略号在行首和行中的效果。

从API version 9开始，通过[style](#style9)设置输入框的风格。

从API version 12开始，通过[textOverflow](#textoverflow12)设置文本超长时的显示方式。

从API version 18开始，通过[ellipsisMode](#ellipsismode18)设置省略号位置。

从API version 24开始，[EllipsisMode](ts-appendix-enums.md#ellipsismode11)新增了MULTILINE_START和MULTILINE_CENTER枚举。


```

```TypeScript
### 示例17（输入框支持输入状态变化等回调）

从API version 8开始，该示例通过[onEditChange](#oneditchange8)、[onCopy](#oncopy8)、[onCut](#oncut8)、[onPaste](#onpaste8)、[onContentScroll](#oncontentscroll10)（从API version 10开始）、[onWillCopy](#onwillcopy)、[onWillCut](#onwillcut)接口实现了输入框监测输入状态变化、复制、剪切、粘贴、文本内容滚动回调的效果、如何屏蔽系统复制功能，以及如何屏蔽系统剪切功能，同时，可以通过设置[selectAll](#selectall11)（从API version 11开始）属性，输入框初始状态下是否全选文本。

从API版本26.0.0开始，新增[onWillCopy](#onwillcopy)、[onWillCut](#onwillcut)接口。


```

```TypeScript
### 示例18（设置最小字体范围与最大字体范围）

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
struct TextInputExample {
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
        console.error(`Failed to update configuration. Code: ${err.code}, message: ${err.message}`);
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
        TextInput({
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
            this.setFontScale(1);
          }).margin(10)
          Button('1.75倍').onClick(() => {
            this.setFontScale(1.75);
          }).margin(10)
        }

        Row() {
          Button('2倍').onClick(() => {
            this.setFontScale(2);
          }).margin(10)
          Button('3.2倍').onClick(() => {
            this.setFontScale(3.2);
          }).margin(10)
        }
      }.margin({ top: 50 })
    }
  }
}
```

```TypeScript
### 示例19（设置选中指定区域的文本内容）

从API version 10开始，该示例通过[setTextSelection](#settextselection10)方法展示如何设置选中指定区域的文本内容以及菜单的显隐策略。


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
### 示例22（设置字符计数颜色以及超出字符颜色）

从API version 22开始，该示例通过[showCounter](#showcounter11)属性的counterTextColor和counterTextOverflowColor设置字符计数颜色以及超出字符颜色。


```

```TypeScript
### 示例23（设置placeholder富文本样式）

从API version 22开始，该示例通过[setStyledPlaceholder](ts-universal-attributes-text-style.md#setstyledplaceholder22)接口设置placeholder富文本样式。


```

```TypeScript
### 示例24（设置输入法扩展信息）

从API version 22开始，该示例通过[IMEClient](ts-text-common.md#imeclient20对象说明)的setExtraConfig设置输入法扩展信息。
```

```TypeScript
### 示例25（设置内联输入风格编辑态时滚动条的显示模式）

从API version 10开始，该示例通过[barState](#barstate10)接口设置内联输入风格编辑态时滚动条的显示或隐藏状态。


```

```TypeScript
### 示例26（设置行首标点符号压缩和行尾标点符号悬挂）

本示例通过[compressLeadingPunctuation](#compressleadingpunctuation23)接口设置行首标点符号压缩，通过[punctuationOverflow](#punctuationoverflow)设置行尾标点符号悬挂。

左侧有间距的标点符号位于行首时，标点会直接压缩间距至左侧边界。

文本自动换行后，剩余内容（含标点符号）需要能够放入上一行，标点符号悬挂才生效。

从API版本23开始，新增compressLeadingPunctuation接口。

从API版本26.0.0开始，新增punctuationOverflow接口。


```

```TypeScript
### 示例27（设置自适应间距）

该示例通过[includeFontPadding](#includefontpadding23)接口增加首行尾行间距和[fallbackLineSpacing](#fallbacklinespacing23)接口设置自适应行间距。

从API version 23开始，新增[includeFontPadding](#includefontpadding23)和[fallbackLineSpacing](#fallbacklinespacing23)接口。


```

```TypeScript
### 示例28（设置文本拖拽时的背板样式）

该示例通过[selectedDragPreviewStyle](#selecteddragpreviewstyle23)接口设置文本拖拽时的背板样式。

从API version 23开始，新增selectedDragPreviewStyle接口。


```

```TypeScript
### 示例29（删除文本框内的最后一个字符）

该示例通过调用[deleteBackward](ts-universal-attributes-text-style.md#deletebackward23)接口删除文本框内最后一个字符。

从API version 23开始，新增[deleteBackward](ts-universal-attributes-text-style.md#deletebackward23)接口。


```

```TypeScript
### 示例30（设置文本排版方向）

该示例通过[textDirection](#textdirection23)接口设置文本排版方向。

从API version 23开始，新增textDirection接口。


```

```TypeScript
### 示例31（将指定范围的文字滚动到可视区内）

本示例通过[scrollToVisible](./ts-universal-attributes-text-style.md#scrolltovisible23)将可视区外的文本滚动到可视区内。

从API version 23开始，新增scrollToVisible接口。


```

```TypeScript
### 示例32（设置文本排版时是否使能孤字优化）

该示例通过[orphanCharOptimization](#orphancharoptimization)接口设置使能孤字优化，确保段落最后一行不出现孤字。

从API版本26.0.0开始，新增orphanCharOptimization接口。

该效果图会因设备尺寸差异有显示区别，仅供参考。

不开启孤字优化：



开启孤字优化：


```

```TypeScript
### 示例33（设置文本着色器效果）

该示例通过[shaderStyle](#shaderstyle)接口实现对TextInput组件内文本着色效果。

从API版本26.0.0开始，新增shaderStyle接口。


```

```TypeScript
### 示例34（设置文本选择的AI菜单）

该示例通过[enableSelectedDataDetector](#enableselecteddatadetector22)，配置文本选择AI菜单功能。

从API version 22开始，新增enableSelectedDataDetector。
```
