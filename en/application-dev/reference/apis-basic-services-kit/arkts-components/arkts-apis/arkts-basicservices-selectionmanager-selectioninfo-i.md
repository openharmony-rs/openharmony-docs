# SelectionInfo

```TypeScript
interface SelectionInfo
```

Defines the information of a word selection event.

**Since:** 24

<!--Device-selectionManager-interface SelectionInfo--><!--Device-selectionManager-interface SelectionInfo-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## Modules to Import

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application where words are selected.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-bundleName: string--><!--Device-SelectionInfo-bundleName: string-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## displayID

```TypeScript
displayID: number
```

ID of the screen where the window with selected words is located.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-displayID: int--><!--Device-SelectionInfo-displayID: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## endDisplayX

```TypeScript
endDisplayX: number
```

X-coordinate of the screen where the word selection ends, in px.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-endDisplayX: int--><!--Device-SelectionInfo-endDisplayX: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## endDisplayY

```TypeScript
endDisplayY: number
```

Y-coordinate of the screen where the word selection ends, in px.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-endDisplayY: int--><!--Device-SelectionInfo-endDisplayY: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## endWindowX

```TypeScript
endWindowX: number
```

X-coordinate of the window where the word selection ends, in px.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-endWindowX: int--><!--Device-SelectionInfo-endWindowX: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## endWindowY

```TypeScript
endWindowY: number
```

Y-coordinate of the window where the word selection ends, in px.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-endWindowY: int--><!--Device-SelectionInfo-endWindowY: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## selectionType

```TypeScript
selectionType: SelectionType
```

Word selection types.

**Type:** [SelectionType](arkts-basicservices-selectionmanager-selectiontype-e.md)

**Default:** MOUSE_MOVE

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-selectionType: SelectionType--><!--Device-SelectionInfo-selectionType: SelectionType-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## startDisplayX

```TypeScript
startDisplayX: number
```

X-coordinate of the screen where the word selection starts, in px.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-startDisplayX: int--><!--Device-SelectionInfo-startDisplayX: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## startDisplayY

```TypeScript
startDisplayY: number
```

Y-coordinate of the screen where the word selection starts, in px.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-startDisplayY: int--><!--Device-SelectionInfo-startDisplayY: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## startWindowX

```TypeScript
startWindowX: number
```

X-coordinate of the window where the word selection starts, in px.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-startWindowX: int--><!--Device-SelectionInfo-startWindowX: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## startWindowY

```TypeScript
startWindowY: number
```

Y-coordinate of the window where the word selection starts, in px.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-startWindowY: int--><!--Device-SelectionInfo-startWindowY: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection

## windowID

```TypeScript
windowID: number
```

ID of the window where words are selected.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SelectionInfo-windowID: int--><!--Device-SelectionInfo-windowID: int-End-->

**System capability:** SystemCapability.SelectionInput.Selection
