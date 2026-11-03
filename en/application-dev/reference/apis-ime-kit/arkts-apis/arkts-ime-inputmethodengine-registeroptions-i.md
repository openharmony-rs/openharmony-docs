# RegisterOptions

```TypeScript
interface RegisterOptions
```

Defines the options for registering a proxy input method.

**Since:** 26.1.0

<!--Device-inputMethodEngine-interface RegisterOptions--><!--Device-inputMethodEngine-interface RegisterOptions-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## inputPatternTypes

```TypeScript
inputPatternTypes?: Array<number>
```

Range of edit box patterns to proxy. Each element **must be** one of the PATTERN_* constants, such as [PATTERN_TEXT](arkts-ime-inputmethodengine-con.md#pattern_text) or [PATTERN_NUMBER](arkts-ime-inputmethodengine-con.md#pattern_number). If this parameter is not specified, all edit box patterns are proxied. This parameter cannot be an empty array.

**Type:** Array&lt;number&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RegisterOptions-inputPatternTypes?: Array<int>--><!--Device-RegisterOptions-inputPatternTypes?: Array<int>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
