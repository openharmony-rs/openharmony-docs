# TemplateProperty

```TypeScript
interface TemplateProperty
```

Provides parameter configuration required for switching the float view template and modifying the size of the window.

**Since:** 26.0.0

<!--Device-floatView-interface TemplateProperty--><!--Device-floatView-interface TemplateProperty-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## size

```TypeScript
size: window.Size
```

Window size required for updating the template type.

**Type:** [window.Size](arkts-arkui-window-size-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TemplateProperty-size: window.Size--><!--Device-TemplateProperty-size: window.Size-End-->

**System capability:** SystemCapability.Window.SessionManager

## templateType

```TypeScript
templateType: FloatViewTemplateType
```

Template type of the float view.

**Type:** [FloatViewTemplateType](arkts-arkui-floatview-floatviewtemplatetype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TemplateProperty-templateType: FloatViewTemplateType--><!--Device-TemplateProperty-templateType: FloatViewTemplateType-End-->

**System capability:** SystemCapability.Window.SessionManager
