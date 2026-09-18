# SheetKeyboardAvoidMode

Define the mode of sheet how to avoid keyboard.

@enum { number }

**Since:** 13

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

Sheet will not aovid keyboard.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE_AND_RESIZE

```TypeScript
TRANSLATE_AND_RESIZE = 1
```

Firstly sheet will avoid keyboard by changing its height. And then sheet will avoid by resizing after reaching its maximum height.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_ONLY

```TypeScript
RESIZE_ONLY = 2
```

Sheet will only avoid keyboard by resizing the content.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE_AND_SCROLL

```TypeScript
TRANSLATE_AND_SCROLL = 3
```

Firstly sheet will avoid keyboard by changing its height. And then sheet will avoid keyboard by scrolling after reaching its maximum height.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## POPUP_SHEET

```TypeScript
POPUP_SHEET = 4
```

Popup sheet will avoid keyboard by default.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
