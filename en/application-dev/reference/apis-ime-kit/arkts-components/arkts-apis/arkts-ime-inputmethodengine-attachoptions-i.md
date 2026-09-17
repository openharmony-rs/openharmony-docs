# AttachOptions

Defines additional options for binding an input method.

**Since:** 19

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## isSimpleKeyboardEnabled

```TypeScript
isSimpleKeyboardEnabled?: boolean
```

Whether to enable the simple keyboard. This attribute is set by the edit box application. The value **true** means that the simple keyboard is enabled, and the value **false** means the opposite.

If this attribute is not set or is set to an invalid value, the simple keyboard is disabled by default.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## requestKeyboardReason

```TypeScript
requestKeyboardReason?: RequestKeyboardReason
```

Reason for requesting the keyboard. This attribute is set by the edit box application. If this attribute is not set or is set to an invalid value, the keyboard will not be triggered by default.

**Type:** [RequestKeyboardReason](arkts-ime-inputmethodengine-requestkeyboardreason-e.md)

**Since:** 19

**System capability:** SystemCapability.MiscServices.InputMethodFramework
