# RouterPageState

Enumerates the states of a page during routing. **RouterPageState** is used in [RouterPageInfo](arkts-arkui-uiobserver-routerpageinfo-c.md) as the callback parameter for passive observation via [routerPageUpdate](arkts-arkui-uiobserver-on-f.md#onrouterpageupdate).

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_APPEAR

```TypeScript
ABOUT_TO_APPEAR = 0
```

The page is about to be displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ABOUT_TO_DISAPPEAR

```TypeScript
ABOUT_TO_DISAPPEAR = 1
```

The page is about to be destroyed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ON_PAGE_SHOW

```TypeScript
ON_PAGE_SHOW = 2
```

The page is displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ON_PAGE_HIDE

```TypeScript
ON_PAGE_HIDE = 3
```

The page is hidden.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ON_BACK_PRESS

```TypeScript
ON_BACK_PRESS = 4
```

The page is returned.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
