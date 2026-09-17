# RouterState

Describes the page routing state.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## index

```TypeScript
index: number
```

Index of the current page in the stack. The index starts from 1 from the bottom to the top of the stack.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Name of the current page, that is, the file name.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## params

```TypeScript
params: Object
```

Parameters carried on the current page.

**Type:** Object

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

Path of the current page.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
