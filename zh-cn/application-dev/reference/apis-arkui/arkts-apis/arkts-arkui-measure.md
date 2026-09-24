# @ohos.measure(文本计算)

本模块提供文本宽度、高度等相关计算，支持多种文本属性配置（如字体大小、样式、粗细、行高等），适用于需要在组件构建前获知文本尺寸的场景，例如自适应布局、文本裁剪、动态调整UI尺寸等，帮助开发者实现更精准的布局计算和性能优化。

> **说明：**
 >
 > - 该模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在创建组件实例后使用。
 >
 > - 如需更多测算文本参数，建议使用图形对应[Paragraph](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraph-c.md)下的测算接口。
 >
 > - 调用文本计算接口时，不建议同时使用
 > [ApplicationContext.setFontSizeScale](../../apis-ability-kit/arkts-apis/arkts-ability-applicationcontext-c.md#setfontsizescale)设置
 > 应用字体大小缩放比例。为了确保时序的一致性，建议开发者自行监听字体缩放变化，以保证测算结果的准确性。
 >
 > - 在测算裁剪后的文本时，由于某些Unicode字符（如emoji）的码位长度大于1，直接按字符串长度裁剪会导致不准确的结果。建议基于Unicode码点进行迭代处理，避免错误截断字符，确保测算结果准确。



## 导入模块

```TypeScript
import { MeasureText, MeasureOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [MeasureText](arkts-arkui-measure-measuretext-c.md) | 定义测算文本相关接口。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [MeasureOptions](arkts-arkui-measure-measureoptions-i.md) | 被计算文本属性。 |
