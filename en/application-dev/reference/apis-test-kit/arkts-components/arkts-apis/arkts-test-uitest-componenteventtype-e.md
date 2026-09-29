# ComponentEventType

```TypeScript
declare enum ComponentEventType
```

Enumerates the component operation event types that can be listened for.

**Since:** 22

<!--Device-unnamed-declare enum ComponentEventType--><!--Device-unnamed-declare enum ComponentEventType-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## COMPONENT_UNDEFINED

```TypeScript
COMPONENT_UNDEFINED = 0
```

Non-component operation event.

Note: This value can only be used as a return value. If it is passed in an API, an exception will be thrown.

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ComponentEventType-COMPONENT_UNDEFINED = 0--><!--Device-ComponentEventType-COMPONENT_UNDEFINED = 0-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## COMPONENT_CLICKED

```TypeScript
COMPONENT_CLICKED = 1
```

Component clicked event.

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ComponentEventType-COMPONENT_CLICKED = 1--><!--Device-ComponentEventType-COMPONENT_CLICKED = 1-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## COMPONENT_LONG_CLICKED

```TypeScript
COMPONENT_LONG_CLICKED = 2
```

Component long-clicked event.

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ComponentEventType-COMPONENT_LONG_CLICKED = 2--><!--Device-ComponentEventType-COMPONENT_LONG_CLICKED = 2-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## COMPONENT_SCROLL_START

```TypeScript
COMPONENT_SCROLL_START = 3
```

Component scroll start event.

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ComponentEventType-COMPONENT_SCROLL_START = 3--><!--Device-ComponentEventType-COMPONENT_SCROLL_START = 3-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## COMPONENT_SCROLL_END

```TypeScript
COMPONENT_SCROLL_END = 4
```

Component scroll end event.

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ComponentEventType-COMPONENT_SCROLL_END = 4--><!--Device-ComponentEventType-COMPONENT_SCROLL_END = 4-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.

## COMPONENT_TEXT_CHANGED

```TypeScript
COMPONENT_TEXT_CHANGED = 5
```

Text change event of the [text input component](../../../ui/arkts-common-components-text-input.md).

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-ComponentEventType-COMPONENT_TEXT_CHANGED = 5--><!--Device-ComponentEventType-COMPONENT_TEXT_CHANGED = 5-End-->

**System capability:** SystemCapability.Test.UiTest

**Test API:** This API is used only in automated test scripts.
