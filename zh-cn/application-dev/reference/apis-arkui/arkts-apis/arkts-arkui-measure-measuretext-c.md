# MeasureText

定义测算文本相关接口。

**起始版本：** 9

<!--Device-unnamed-export default class MeasureText--><!--Device-unnamed-export default class MeasureText-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { MeasureOptions } from '@kit.ArkUI';
```

## measureText

```TypeScript
static measureText(options: MeasureOptions): number
```

计算指定文本作为单行文本显示时的宽度。如果文本包含多行（由换行符`\n`分隔），则返回其中最长的行的宽度。

> **说明：**  
>  
> -measureText需要先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getMeasureUtils](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmeasureutils12)方法获取  
> [MeasureUtils](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用measureText可能导致  
> [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。  
>  
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getMeasureUtils](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmeasureutils12)方法获取当前UI上下文关  
> 联的[MeasureUtils](arkts-arkui-uicontext.md)对象。  
>  
> - measureText接口的计算结果始终是单行文本的宽度，入参options中配置的布局约束（如constraintWidth、maxLines）对measureText的结果没有影响。如果需要计算布局约束下的宽度，请使用  
> [measureTextSize](../../../../reference/apis-arkui/arkts-apis-uicontext-measureutils.md#measuretextsize12)方法。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** measureText

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureText-static measureText(options: MeasureOptions): number--><!--Device-MeasureText-static measureText(options: MeasureOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MeasureOptions](arkts-arkui-measure-measureoptions-i.md) | 是 | 被计算文本描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 文本宽度。<br/>单位：px |

**示例：**

```TypeScript
import { MeasureText } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State textWidth: number = MeasureText.measureText({
    // 建议使用 this.getUIContext().getMeasureUtils().measureText()接口
    textContent: "Hello World",
    fontSize: '50px'
  });

  build() {
    Row() {
      Column() {
        Text(`The width of 'Hello World': ${this.textWidth}`)
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

## measureTextSize

```TypeScript
static measureTextSize(options: MeasureOptions): SizeOptions
```

计算指定文本的宽度和高度。

> **说明：**  
>  
> -measureTextSize需要先通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getMeasureUtils](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmeasureutils12)方法获取  
> [MeasureUtils](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。且直接使用measureTextSize可能导致  
> [UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。  
>  
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getMeasureUtils](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmeasureutils12)方法获取当前UI上下文关  
> 联的[MeasureUtils](arkts-arkui-uicontext.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** measureTextSize

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureText-static measureTextSize(options: MeasureOptions): SizeOptions--><!--Device-MeasureText-static measureTextSize(options: MeasureOptions): SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MeasureOptions](arkts-arkui-measure-measureoptions-i.md) | 是 | 被计算文本描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeOptions](arkts-arkui-units-sizeoptions-i.md) | 返回文本所占布局宽度和高度。<br/>**说明:** <br/>文本宽度以及高度返回值单位均为px。 |

**示例：**

```TypeScript
import { MeasureText } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  textSize: SizeOptions = MeasureText.measureTextSize({
    // 建议使用 this.getUIContext().getMeasureUtils().measureTextSize()接口
    textContent: "Hello World",
    fontSize: '50px'
  });

  build() {
    Row() {
      Column() {
        Text(`The width of 'Hello World': ${this.textSize.width}`)
        Text(`The height of 'Hello World': ${this.textSize.height}`)
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

