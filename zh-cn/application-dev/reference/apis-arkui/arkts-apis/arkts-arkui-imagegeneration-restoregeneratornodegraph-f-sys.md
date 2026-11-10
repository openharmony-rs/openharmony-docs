# restoreGeneratorNodeGraph（系统接口）

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## restoreGeneratorNodeGraph

```TypeScript
function restoreGeneratorNodeGraph(uiContext: UIContext): Promise<void>
```

恢复AI节点图Sheet页。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-imageGeneration-function restoreGeneratorNodeGraph(uiContext: UIContext): Promise<void>--><!--Device-imageGeneration-function restoreGeneratorNodeGraph(uiContext: UIContext): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | ui显示对话框的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回恢复操作的结果。 |
