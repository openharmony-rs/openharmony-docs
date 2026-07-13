# getSystemFontList

## getSystemFontList

```TypeScript
function getSystemFontList(): Array<string>
```

获取系统字体列表。

该接口仅在PC/2in1设备上生效，在其他设备上返回空数组。

推荐使用[getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-getsystemfontfullnamesbytype-f.md#getsystemfontfullnamesbytype-1)接口获取系统最新支持的字体列表数据。

> **说明：**
>
> -getSystemFontList需要先通过[UIContext](arkts-arkui-uicontext.md)中的
> [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取
> [Font](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用getSystemFontList可能导致
> [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
>
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的
> [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的
> [Font](arkts-arkui-uicontext.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** getSystemFontList

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 系统的字体名列表。 |

**示例：**

```TypeScript
// xxx.ets
import { font } from '@kit.ArkUI';

@Entry
@Component
struct FontExample {
  fontList: Array<string> = new Array<string>();

  build() {
    Column() {
      Button("getSystemFontList")
        .width('60%')
        .height('6%')
        .onClick(() => {
          this.fontList = font.getSystemFontList(); // 建议使用 this.getUIContext().getFont().getSystemFontList()接口
        })
    }.width('100%')
  }
}

```

