# ArkUI子系统Changelog

## cl.arkui.1 属性字符串段落首个占位为CustomSpan或ImageAttachment时，支持设置段落样式

**访问级别**

公共能力

**变更原因**

历史版本中，[CustomSpan](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#customspan)或[ImageAttachment](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#imageattachment)在创建时未拷贝段落样式。因此，当属性字符串段落的首个占位为[CustomSpan](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#customspan)或[ImageAttachment](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#imageattachment)时，段落样式不生效。

**变更影响**

此变更涉及应用适配。

变更前：如果属性字符串段落内首个占位为[CustomSpan](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#customspan)或[ImageAttachment](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#imageattachment)，设置在该段落上的段落样式不生效。

变更后：如果属性字符串段落内首个占位为[CustomSpan](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#customspan)或[ImageAttachment](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#imageattachment)，设置在该段落上的段落样式生效。

**起始 API Level**

12

**变更发生版本**

从OpenHarmony SDK 7.0.0.21开始。

**变更的接口/组件**

[ParagraphStyle](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#paragraphstyle)

**适配指导**

接口默认效果变更，开发者需审视此变更是否对自身相关业务展示效果产生影响，若有影响需根据自身业务代码进行对应适配。

以下示例代码将属性字符串段落中类型为[ImageAttachment](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#imageattachment)的首个占位，设置段落样式为[TextAlign](../../../../zh-cn/application-dev/reference/apis-arkui/arkui-ts/ts-appendix-enums.md#textalign).End。

```ts
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct styled_string_paraStyle_demo {
  mutableStr: MutableStyledString = new MutableStyledString('TextAlign:End', [{
    start: 0,
    length: 5,
    styledKey: StyledStringKey.PARAGRAPH_STYLE,
    styledValue: new ParagraphStyle({
      textAlign: TextAlign.End
    })
  }]);
  mutableStr2: MutableStyledString = new MutableStyledString('TextAlign:End');
  controller: TextController = new TextController();
  controller2: TextController = new TextController();

  build() {
    Row() {
      Column({ space: 5 }) {
        Text(undefined, { controller: this.controller })
          .copyOption(CopyOptions.InApp)
          .draggable(true)
          .fontSize(30)
          .borderWidth(1)
          .width(300)
          .onAppear(() => {
            this.controller.setStyledString(this.mutableStr);
          })
        Text(undefined, { controller: this.controller2 })
          .copyOption(CopyOptions.InApp)
          .draggable(true)
          .fontSize(30)
          .borderWidth(1)
          .width(300)
          .onAppear(() => {
            this.mutableStr2.insertStyledString(0, new MutableStyledString(new ImageAttachment({
              resourceValue: $r('app.media.startIcon'),
              size: { width: 50, height: 50 },
              layoutStyle: { borderRadius: LengthMetrics.vp(10) },
              verticalAlign: ImageSpanAlignment.BASELINE,
              objectFit: ImageFit.Contain,
              syncLoad: true
            })))
            this.mutableStr2.setStyle({
              start: 0,
              length: 5,
              styledKey: StyledStringKey.PARAGRAPH_STYLE,
              styledValue: new ParagraphStyle({
                textAlign: TextAlign.End
              })
            }) // API版本26.0.0前，设置的TextAlign.End不会生效
            this.controller2.setStyledString(this.mutableStr2);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
