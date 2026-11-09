# startSmartCanvasService（系统接口）

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## startSmartCanvasService

```TypeScript
function startSmartCanvasService(
    context: common.ServiceExtensionContext | common.UIAbilityContext | common.UIExtensionContext): Promise<void>
```

启动智能画布服务。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-imageGeneration-function startSmartCanvasService(    context: common.ServiceExtensionContext | common.UIAbilityContext | common.UIExtensionContext): Promise<void>--><!--Device-imageGeneration-function startSmartCanvasService(    context: common.ServiceExtensionContext | common.UIAbilityContext | common.UIExtensionContext): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [common.ServiceExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-serviceextensioncontext-t-sys.md) &#124; [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) &#124; [common.UIExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiextensioncontext-t.md) | 是 | different ability context. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |
