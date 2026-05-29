# AutoFillRequest

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->

当AutoFillExtensionAbility触发回调函数时，会提供给开发者页面数据。

## 导入模块

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## FillRequest

自动填充请求信息。

**起始版本：** 26.0.0

**原子化服务API**：从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

| 名称        | 类型                                                                    | 只读 | 可选 | 说明           |
| ----------- | ----------------------------------------------------------------------- | ---- | ---- | ------------- |
| type        | [AutoFillType](js-apis-inner-application-autoFillType.md)               | 否   | 否   | 自动填充类型。 |
| viewData    | [ViewData](js-apis-inner-application-viewData.md)                       | 否   | 否   | 页面数据。 |
| triggerType | [AutoFillTriggerType](js-apis-inner-application-autoFillTriggerType.md) | 否   | 是   | 自动填充服务的拉起类型。 |

## SaveRequest

自动保存请求信息。

**起始版本：** 26.0.0

**原子化服务API**：从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

| 名称     | 类型                                              | 只读 | 可选 | 说明       |
| -------- | ------------------------------------------------- | ---- | ---- | ---------- |
| viewData | [ViewData](js-apis-inner-application-viewData.md) | 否   | 否   | 页面数据。 |

## FillFailureResult

自动填充失败结果。

**起始版本：** 26.0.0

**原子化服务API**：从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

| 名称    | 类型   | 只读 | 可选 | 说明      |
| ------- | ------ | ---- | ---- | -------- |
| errCode | number | 否   | 否   | 错误码。 |
