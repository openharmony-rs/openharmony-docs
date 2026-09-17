# Range

Describes the range of the selected text.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## end

```TypeScript
end: number
```

Index of the last selected character in the text box. The value is an integer greater than or equal to 0, and cannot exceed the actual text length. The **end** value must be greater than the **start** value.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## start

```TypeScript
start: number
```

Index of the first selected character in the text box. The value is an integer greater than or equal to 0, and cannot exceed the actual text length.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework
