# openGeneratorNodeGraph（系统接口）

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## openGeneratorNodeGraph

```TypeScript
function openGeneratorNodeGraph(uiContext: UIContext, options?: GeneratorNodeGraphOptions): Promise<void>
```

打开AI节点图Sheet页。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-imageGeneration-function openGeneratorNodeGraph(uiContext: UIContext, options?: GeneratorNodeGraphOptions): Promise<void>--><!--Device-imageGeneration-function openGeneratorNodeGraph(uiContext: UIContext, options?: GeneratorNodeGraphOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 用于ui显示的对话框的上下文。 |
| options | [GeneratorNodeGraphOptions](arkts-arkui-imagegeneration-generatornodegraphoptions-i-sys.md) | 否 | 节点图任务参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回结果 |
