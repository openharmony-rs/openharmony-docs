# @ohos.measure(Text Measurement)

The **measure** module provides APIs for measuring text metrics, such as text height and width.
 > **NOTE**
 >
 > - This module cannot be used in the file declaration of the [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md). In
 > other words, the APIs of this module can be used only after a component instance is created; they cannot be called
 > in the lifecycle of the UIAbility.
 >
 > - To perform more complex text measurements, you are advised to call the corresponding graphics measurement API,
 > specifically [Paragraph](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraphstyle-i.md).
 >
 > - Avoid using [ApplicationContext.setFontSizeScale](../../apis-ability-kit/arkts-apis/arkts-ability-applicationcontext-c.md#setfontsizescale)
 > during text measurement API calls. To ensure timing consistency and the accuracy of measurement results, manually
 > listen for font scale changes.
 >
 > - For measuring text after truncation, direct use of the string length for truncation may lead to inaccuracies.
 > This is because certain Unicode characters (for example, emojis) have code points with a length greater than 1, and
 > truncating by string length can split these multi-code-point characters, resulting in incorrect text display or
 > measurement errors. As such, you are advised to perform iterative processing based on Unicode code points during
 > truncation.


## 导入模块

```TypeScript
import { MeasureText, MeasureOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [MeasureText(Text Measurement)](arkts-arkui-measure-measuretext-c.md) | 定义测算文本相关接口。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [MeasureOptions(Text Measurement)](arkts-arkui-measure-measureoptions-i.md) | 被计算文本属性。 |

