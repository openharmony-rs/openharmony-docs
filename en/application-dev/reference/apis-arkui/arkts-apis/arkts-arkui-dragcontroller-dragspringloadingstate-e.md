# DragSpringLoadingState

Enumerates hover detection states during drag operations. Under default system configuration, if no CANCEL occurs, the state reporting is as follows: Hover still--&gt;500ms--&gt;BEGIN--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;END

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BEGIN

```TypeScript
BEGIN
```

Initial state when a dragged item enters the component boundary and remains stationary for the specified duration. This state enables preparation operations.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## UPDATE

```TypeScript
UPDATE
```

Periodic notification state during sustained hover detection. In this state, periodic updates refresh UI effects to highlight the hover state.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END
```

Final state indicating completion of the hover detection cycle, which is triggered when the dragged item remains stationary after the last update notification. Hover detection will only restart after the dragged item exits and re-enters the component boundary or enters a child component. In this state, the application can perform cleanup, navigation, or view switching operations.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CANCEL

```TypeScript
CANCEL
```

Interruption state of hover detection triggered by termination events, which include the following: finger or mouse release, window switching, screen off, exiting the component boundary, entering child components, or exceeding the movement threshold within the component. The application will restore the UI style and cancel pending navigation and view switching operations.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
