# FloatViewConfiguration

```TypeScript
interface FloatViewConfiguration
```

Provides parameter configuration required for creating a float view controller.

**Since:** 26.0.0

<!--Device-floatView-interface FloatViewConfiguration--><!--Device-floatView-interface FloatViewConfiguration-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## context

```TypeScript
context: BaseContext
```

Context environment.

**Type:** [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FloatViewConfiguration-context: BaseContext--><!--Device-FloatViewConfiguration-context: BaseContext-End-->

**System capability:** SystemCapability.Window.SessionManager

## isConfirmOnClose

```TypeScript
isConfirmOnClose?: boolean
```

This field controls whether user confirmation is required when the close button is clicked. **true** if clicking the close button requires user confirmation, otherwise no confirmation is needed. Default value: default value is false.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FloatViewConfiguration-isConfirmOnClose?: boolean--><!--Device-FloatViewConfiguration-isConfirmOnClose?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## templateType

```TypeScript
templateType: FloatViewTemplateType
```

Template type of the float view.

**Type:** [FloatViewTemplateType](arkts-arkui-floatview-floatviewtemplatetype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FloatViewConfiguration-templateType: FloatViewTemplateType--><!--Device-FloatViewConfiguration-templateType: FloatViewTemplateType-End-->

**System capability:** SystemCapability.Window.SessionManager
