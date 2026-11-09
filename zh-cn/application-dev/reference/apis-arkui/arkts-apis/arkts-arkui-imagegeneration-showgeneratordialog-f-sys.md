# showGeneratorDialog（系统接口）

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## showGeneratorDialog

```TypeScript
function showGeneratorDialog(uiContext: UIContext, options?: GeneratorDialogOptions): Promise<Array<GeneratorResult>>
```

打开AI图像生成任务弹窗并执行AI图像生成操作。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-imageGeneration-function showGeneratorDialog(uiContext: UIContext, options?: GeneratorDialogOptions): Promise<Array<GeneratorResult>>--><!--Device-imageGeneration-function showGeneratorDialog(uiContext: UIContext, options?: GeneratorDialogOptions): Promise<Array<GeneratorResult>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | UI显示的上下文。 |
| options | [GeneratorDialogOptions](arkts-arkui-imagegeneration-generatordialogoptions-i-sys.md) | 否 | 生成图像任务参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[GeneratorResult](arkts-arkui-imagegeneration-generatorresult-i-sys.md)&gt;&gt; | 返回生成图像的结果。 |
