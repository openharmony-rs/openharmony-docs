# 属性字符串（StyledString/MutableStyledString）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @HelloCrease-->

属性字符串StyledString/MutableStyledString（其中MutableStyledString继承自StyledString，下文统称为StyledString），可用于在字符或段落级别上设置文本样式。将StyledString应用到文本组件上，可以采用多种方式修改文本，包括调整字号、添加字体颜色、使文本具备可点击性，以及通过自定义方式绘制文本等。具体使用方法请参考[属性字符串](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md)的文档。

属性字符串提供多种类型样式对象，涵盖各种常见的文本样式格式，例如文本装饰线样式、文本行高样式、文本阴影样式等。也可以自行创建CustomSpan，以应用自定义样式。 

## 创建并应用StyledString和MutableStyledString

  可以通过TextController提供的[setStyledString](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#setstyledstring12)方法，将属性字符串附加到文本组件，并推荐在[onPageShow](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#onpageshow)或者文本组件的[onAppear](../reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#onappear)回调中触发绑定。
  > **说明：**
  >
  > 在aboutToAppear中调用setStyledString方法时，由于该方法运行阶段组件尚未完成创建并成功挂载节点树，因此无法在页面初始化时显示属性字符串。
  >
  > 从API version 15开始，在aboutToAppear中调用setStyledString方法，页面初始化时可以显示属性字符串。

  <!-- @[createStyledString_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/CreateApply.ets) -->

  ![StyledString_Init](figures/span_string_init.png)

## 设置文本样式

属性字符串目前提供了多种Style对象，包括[TextStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#textstyle)、[TextShadowStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#textshadowstyle)、[DecorationStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#decorationstyle)、[BaselineOffsetStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#baselineoffsetstyle)、[LineHeightStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#lineheightstyle)、[LetterSpacingStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#letterspacingstyle)，用于设置文本的各类样式。

- 创建及应用文本字体样式对象（TextStyle）

  <!-- @[styledStringTextStyle_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringTextStyle.ets) -->

  ![StyledString_TextStyle](figures/StyledString_TextStyle.png)

- 创建及应用文本阴影对象（TextShadowStyle）

  <!-- @[styledStringTextShadowStyle_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringTextShadowStyle.ets) -->

  ![StyledString_TextShadow](figures/styled_string_text_shadow.png)

- 创建及应用文本装饰线对象（DecorationStyle）

  <!-- @[styledStringDecorationStyle_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringDecorationStyle.ets) -->

  ![StyledString_Decoration](figures/styled_string_decoration.jpg)

- 创建及应用文本基线偏移量对象（BaselineOffsetStyle）

  <!-- @[styledStringBaselineOffsetStyle_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringBaselineOffsetStyle.ets) -->

  ![StyledString_Baseline](figures/styled_string_baselineoffset.png)

- 创建及应用文本行高对象（LineHeightStyle）

  <!-- @[styledStringLineHeightStyle_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringLineHeightStyle.ets) -->

  ![StyledString_lineHeight](figures/styled_string_lineHeight.png)

- 创建及应用文本字符间距对象（LetterSpacingStyle）

  <!-- @[styledStringLetterSpacingStyle_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringLetterSpacingStyle.ets) -->

  ![StyledString_letterSpacing](figures/styled_string_letterspacing.png)

## 设置段落样式

可通过[ParagraphStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#paragraphstyle)设置段落样式布局。下图显示了如何分割文本中的段落，段落以换行符 \n 结尾。

![paragraphs](figures/styledstringParagraphs.png)

以下代码示例展示了如何创建ParagraphStyle并应用。如果将ParagraphStyle附加到段落开头、末尾或之间的任何位置，均会应用样式，非段落区间内则不会应用样式。

  <!-- @[styledStringParagraphStyleOne_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringParagraphStyleOne.ets) -->

  ![styled_string_paragraph1](figures/styled_string_paragraph1.png)
  
  除了可以在创建属性字符串时就预设样式，也可以后续通过[replaceStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#replacestyle)清空原样式替换新样式，同时需要在附加的文本组件controller上主动触发更新绑定的属性字符串。

  <!-- @[styledStringReplaceParagraphStyle_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringReplaceParagraphStyle.ets) -->

  ![styled_string_paragraph2](figures/styled_string_paragraph2.gif)

## 支持将属性字符串转换成Paragraph

可通过[getParagraphs](../reference/apis-arkui/arkts-apis-uicontext-measureutils.md#getparagraphs20)将属性字符串根据文本布局选项转换成对应的[Paragraph](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#paragraph)数组。

- 以下示例展示了通过MeasureUtils的getParagraphs方法测算文本，当内容超出最大显示行数的时候，截断文本显示并展示“...全文”的效果。

  <!-- @[styledStringConvertedToParagraph_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringConvertedToParagraph.ets) -->

  ![StyledString_GetParagraphs](figures/StyledString_GetParagraphs.png)


## 使用图片

可通过[ImageAttachment](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#imageattachment)来添加图片。

以下示例展示了如何将图片和文本附加到同一个MutableStyledString对象上，并实现图文混排。

> **说明：**
>
> 属性字符串的构造函数[constructor](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#constructor)中，当入参value的类型为ImageAttachment或CustomSpan时，styles参数不生效。需要设置styles时，通过[setStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#setstyle)、[insertStyledString](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#insertstyledstring)等方法实现。

  <!-- @[styledStringImageAttachment_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringImageAttachment.ets) -->

  ![StyledString_ImageAttachment](figures/StyledStringImageAttachment.png)

## 设置事件

可通过[GestureStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#gesturestyle)设置onClick、onLongPress事件来使文本响应点击长按事件。

除了初始化属性字符串对象即初始样式对象，亦可通过[setStyle](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#setstyle)接口再叠加新样式或更新已有样式，同时需要在附加的文本组件controller上主动触发更新绑定的属性字符串。

  <!-- @[styledStringGestureStyle_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringGestureStyle.ets) -->

  ![styled_string_event](figures/styled_string_event.gif)

## 格式转换

可以通过[toHtml](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#tohtml14)、[fromHtml](../reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#fromhtml)接口实现属性字符串与HTML格式字符串的相关转换，当前支持转换的HTML标签范围：\<p>、\<span>、\<img>、\<br>、\<strong>、\<b>、\<a>、\<i>、\<em>、\<s>、\<u>、\<del>、\<sup>、\<sub>。

- 以下示例展示了如何将属性字符串转换成HTML格式，并展示了如何从HTML格式转换回属性字符串。

<!-- @[styledStringHtml_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringHtml.ets) -->

![](figures/styled_string_html.gif)

- 将HTML中\<strong>、\<b>、\<a>、\<i>、\<em>、\<s>、\<u>、\<del>、\<sup>、\<sub>标签及其style属性中的background-color转换为属性字符串并转回HTML。
 
  <!-- @[styledStringHtmlOne_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringHtmlOne.ets) -->

  ![styled_string_html_2](figures/styled_string_html_2.gif)

## 场景示例

该示例通过ParagraphStyle、LineHeightStyle、TextStyle对象展示了会员过期提示的效果。

<!-- @[styledStringSceneExample_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/TextComponent/entry/src/main/ets/pages/propertyString/StyledStringSceneExample.ets) -->

``` TypeScript
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
export struct StyledStringSceneExample {
  alignCenterParagraphStyleAttr: ParagraphStyle = new ParagraphStyle({ textAlign: TextAlign.Center });
  //行高样式对象
  lineHeightStyle1: LineHeightStyle = new LineHeightStyle(LengthMetrics.vp(24));
  //Bold样式
  boldTextStyle: TextStyle = new TextStyle({ fontWeight: FontWeight.Bold });
  //创建含段落样式的对象paragraphStyledString1
  //'app.string.StyledStringSceneExample_Text_1'资源文件中的value值为"您的豪华钻石已过期1天\n续费可继续享受会员专属权益"
  paragraphStyledString1: MutableStyledString =
    new MutableStyledString(resource.resourceToString($r('app.string.StyledStringSceneExample_Text_1')), [
      {
        start: 0,
        length: 4,
        styledKey: StyledStringKey.PARAGRAPH_STYLE,
        styledValue: this.alignCenterParagraphStyleAttr
      },
      {
        start: 0,
        length: 4,
        styledKey: StyledStringKey.LINE_HEIGHT,
        styledValue: new LineHeightStyle(LengthMetrics.vp(40))
      },
      {
        start: 11,
        length: 14,
        styledKey: StyledStringKey.FONT,
        styledValue: new TextStyle({ fontSize: LengthMetrics.vp(14), fontColor: Color.Grey })
      },
      {
        start: 11,
        length: 4,
        styledKey: StyledStringKey.PARAGRAPH_STYLE,
        styledValue: this.alignCenterParagraphStyleAttr
      },
      {
        start: 11,
        length: 4,
        styledKey: StyledStringKey.LINE_HEIGHT,
        styledValue: this.lineHeightStyle1
      }
    ]);
  //'app.string.StyledStringSceneExample_Text_2'资源文件中的value值为"\n￥4.88￥15"
  paragraphStyledString2: MutableStyledString =
    new MutableStyledString(resource.resourceToString($r('app.string.StyledStringSceneExample_Text_2')), [
    {
      start: 0,
      length: 4,
      styledKey: StyledStringKey.PARAGRAPH_STYLE,
      styledValue: this.alignCenterParagraphStyleAttr
    },
    {
      start: 0,
      length: 4,
      styledKey: StyledStringKey.LINE_HEIGHT,
      styledValue: new LineHeightStyle(LengthMetrics.vp(60))
    },
    {
      start: 0,
      length: 6,
      styledKey: StyledStringKey.FONT,
      styledValue: this.boldTextStyle
    },
    {
      start: 1,
      length: 1,
      styledKey: StyledStringKey.FONT,
      styledValue: new TextStyle({ fontSize: LengthMetrics.vp(18) })
    },
    {
      start: 2,
      length: 4,
      styledKey: StyledStringKey.FONT,
      styledValue: new TextStyle({ fontSize: LengthMetrics.vp(40) })
    },
    {
      start: 6,
      length: 3,
      styledKey: StyledStringKey.FONT,
      styledValue: new TextStyle({ fontColor: Color.Grey, fontSize: LengthMetrics.vp(14) })
    },
    {
      start: 6,
      length: 3,
      styledKey: StyledStringKey.DECORATION,
      styledValue: new DecorationStyle({ type: TextDecorationType.LineThrough, color: Color.Grey })
    }
  ]);
  //'app.string.StyledStringSceneExample_Text_3'资源文件中的value值为"\n02时06分后将失去该优惠"
  paragraphStyledString3: MutableStyledString =
    new MutableStyledString(resource.resourceToString($r('app.string.StyledStringSceneExample_Text_3')), [
    {
      start: 0,
      length: 4,
      styledKey: StyledStringKey.PARAGRAPH_STYLE,
      styledValue: this.alignCenterParagraphStyleAttr
    },
    {
      start: 0,
      length: 4,
      styledKey: StyledStringKey.LINE_HEIGHT,
      styledValue: new LineHeightStyle(LengthMetrics.vp(30))
    },
    {
      start: 1,
      length: 2,
      styledKey: StyledStringKey.FONT,
      styledValue: new TextStyle({ fontColor: '#FFD700', fontWeight: FontWeight.Bold })
    },
    {
      start: 4,
      length: 2,
      styledKey: StyledStringKey.FONT,
      styledValue: new TextStyle({ fontColor: '#FFD700', fontWeight: FontWeight.Bold })
    }
  ]);
  controller: TextController = new TextController();

  build() {
    NavDestination() {
      Column({ space: 12 }) {
        //'app.string.StyledStringSceneExample_title'资源文件中的value值为"场景示例"
        ComponentCard({ title: $r('app.string.StyledStringSceneExample_title') }) {
          Row() {
            Column({ space: 5 }) {
              Text(undefined, { controller: this.controller })
                .id('text1')
                .width(240)
                .copyOption(CopyOptions.InApp)
                .draggable(true)
                .onAppear(() => {
                  this.paragraphStyledString2.appendStyledString(this.paragraphStyledString3);
                  this.paragraphStyledString1.appendStyledString(this.paragraphStyledString2);
                  this.controller.setStyledString(this.paragraphStyledString1);
                })
              //'app.string.StyledStringSceneExample_Button_1'资源文件中的value值为"限时4.88元 立即续费"
              Button($r('app.string.StyledStringSceneExample_Button_1'))
                .width(200)
                .fontColor(Color.White)
                .fontSize(18)
                .backgroundColor('#3CB371')
                .margin({ bottom: 10 })
            }
            .borderWidth(1).borderColor('#FFDEAD')
            .margin({ left: 10 })
          }
          .height('60%')
        }
      }
      .width('100%')
      .height('100%')
      .padding({ left: 12, right: 12 })
    }
    .backgroundColor('#f1f2f3')
    //'app.string.StyledStringSceneExample_title'资源文件中的value值为"场景示例"
    .title($r('app.string.StyledStringSceneExample_title'))
  }
}
```

![StyledString_SceneDemo](figures/styledString_sceneDemo.png)
