# UI组件适配（文本）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## onEditChanged

ArkTS-Dyn接口声明：[onEditChanged(callback: (isEditing:boolean) => void)](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#oneditchangeddeprecated)

替代的ArkTS-Sta接口声明：[onEditChange(callback: Callback<boolean>)](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#oneditchange8)



ArkTS-Dyn示例：

```
TextInput({ text: "TextInput支持输入状态变化时回调" })
  .onEditChanged((status: boolean) => {
    this.editStatus = status;
  })
```

ArkTS-Sta示例：

```
TextInput({ text: "TextInput支持输入状态变化时回调" })
  .onEditChange((status: boolean) => {
    this.editStatus = status;
  })
```

## measureTextSize

ArkTS-Dyn接口声明：[measureTextSize(options: MeasureOptions): SizeOptions](../reference/apis-arkui/js-apis-measure.md#measuretextmeasuretextsizedeprecated)

替代的ArkTS-Sta接口声明：[measureTextSize(options: MeasureOptions): SizeOptions](../reference/apis-arkui/js-apis-arkui-UIContext.md#measuretextsize12)



ArkTS-Dyn示例：

```
textSize: SizeOptions = MeasureText.measureTextSize({
  textContent: "Hello World",
  fontSize: '50px'
})
```

ArkTS-Sta示例：

```
@State uiContext: UIContext = this.getUIContext();

@State uiContextMeasure: MeasureUtils = this.uiContext.getMeasureUtils();

textSize : SizeOptions = this.uiContextMeasure.measureTextSize({
  textContent: "Hello World",
  fontSize: '50px'
})
```

## measureText

ArkTS-Dyn接口声明：[measureText(options: MeasureOptions): number](../reference/apis-arkui/js-apis-measure.md#measuretextmeasuretextdeprecated)

替代的ArkTS-Sta接口声明：[measureText(options: MeasureOptions): number](../reference/apis-arkui/js-apis-arkui-UIContext.md#measuretext12)



ArkTS-Dyn示例：

```
@State textWidth: number = MeasureText.measureText({
  textContent: "Hello World",
  fontSize: '50px'
})
```

ArkTS-Sta示例：

```
@State uiContext: UIContext = this.getUIContext();

@State uiContextMeasure: MeasureUtils = this.uiContext.getMeasureUtils();

@State textWidth: number = this.uiContextMeasure.measureText({
  textContent: "Hello World",
  fontSize: '50px'
})
```

## getFontByName

ArkTS-Dyn接口声明：[getFontByName(fontName: string): FontInfo](../reference/apis-arkui/js-apis-font.md#fontgetfontbynamedeprecated)

替代的ArkTS-Sta接口声明：[getFontByName(fontName: string): font.FontInfo](../reference/apis-arkui/js-apis-arkui-UIContext.md#getfontbyname)



ArkTS-Dyn示例：

```
import { font } from '@kit.ArkUI';
font.getFontByName('HarmonyOS Sans Italic')
```

ArkTS-Sta示例：

```
import { UIContext, Font } from '@ohos.arkui.UIContext';

let uiContext:UIContext = this.getUIContext();
let font: Font | undefined = uiContext.getFont();
if (font) {
  font.getFontByName('Sans Italic');
}
```

## getSystemFontList

ArkTS-Dyn接口声明：[getSystemFontList(): Array<string>](../reference/apis-arkui/js-apis-font.md#fontgetsystemfontlistdeprecated)

替代的ArkTS-Sta接口声明：[getSystemFontList(): Array<string>](../reference/apis-arkui/js-apis-arkui-UIContext.md#getsystemfontlist)



ArkTS-Dyn示例：

```
font.getSystemFontList()
```

ArkTS-Sta示例：

```
import { UIContext, Font } from '@ohos.arkui.UIContext';

let uiContext:UIContext = this.getUIContext();
let font: Font | undefined = uiContext.getFont();
if (font) {
  font.getSystemFontList();
}
```

## registerFont

ArkTS-Dyn接口声明：[registerFont(options: FontOptions): void](../reference/apis-arkui/js-apis-font.md#fontregisterfontdeprecated)

替代的ArkTS-Sta接口声明：[registerFont(options: font.FontOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#registerfont)



ArkTS-Dyn示例：

```
font.registerFont({familyName: 'mediumRawFile', familySrc: $rawfile('font/medium.ttf')})
```

ArkTS-Sta示例：

```
let uiContext:UIContext = this.getUIContext();
let font:Font = uiContext.getFont();

font.registerFont({familyName: 'medium', familySrc: '/font/medium.ttf'});
```

## CROSS_DEVICE

ArkTS-Dyn接口声明：[CopyOptions.CROSS_DEVICE](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#copyoptions9)

替代的ArkTS-Sta接口声明：ArkTS-Sta暂无替代接口。