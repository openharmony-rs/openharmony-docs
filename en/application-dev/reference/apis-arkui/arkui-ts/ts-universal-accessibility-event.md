# Accessibility Control Actions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-09-01T12:00:26.963Z -->

After accessibility mode is enabled, this module provides the capabilities of intercepting accessibility control operations and listening for the focus acquisition and blur states of accessibility nodes. You can use onAccessibilityFocus to listen for focus acquisition and blur state changes of a component, and use onAccessibilityActionIntercept to intercept and determine accessibility control operations before they are triggered. This is suitable for scenarios where the component interaction logic needs to be customized in accessibility mode.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - Currently, the APIs can be triggered only by enabling accessibility mode.

## onAccessibilityFocus

onAccessibilityFocus(callback: AccessibilityFocusCallback): T

In accessibility mode, this API sets the callback for the focus acquisition and blur states of an accessibility node. When the accessibility focus moves into or out of the current component, causing the focus acquisition or blur state to change, the callback is triggered.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory| Description                                                        |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| callback | [AccessibilityFocusCallback](#accessibilityfocuscallback) | Yes | Callback invoked when the focus acquisition or blurred state of the current component changes in accessibility mode, to notify the registrant of the current state. Setting the input parameter to undefined cancels the callback registration. |

**Return value**

| Type   | Description             |
| ------ | ---------------- |
| T | Current component.|

## AccessibilityFocusCallback

type AccessibilityFocusCallback = (isFocus: boolean) => void

Defines the callback type used in **onAccessibilityFocus**.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory| Description             |
| ------ | ------ | ---- | ---------------- |
| isFocus | boolean | Yes | Whether the component has focus.<br>true: the current component has focus.<br>false: the current component is blurred. |

## onAccessibilityActionIntercept<sup>20+</sup>

onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback): T

In accessibility mode, this API notifies the registered callback before an accessibility control operation is triggered, and the registrant decides whether to intercept the accessibility control operation. For components that do not support click operations, the callback is not triggered even if it is registered.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory| Description                                                        |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| callback | [AccessibilityActionInterceptCallback](#accessibilityactioninterceptcallback20) | Yes | Callback invoked when accessibility mode is enabled and the component supports clicking, to notify the registrant of the accessibility control operation before it is triggered, so that the registrant decides whether to intercept the operation. The callback is not triggered when accessibility mode is disabled or the component does not support clicking.<br> When the input parameter is set to undefined, the callback registration is canceled. |

**Return value**

| Type   | Description             |
| ------ | ---------------- |
| T | Current component.|

## AccessibilityActionInterceptCallback<sup>20+</sup>

type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult

Defines the callback type used in onAccessibilityActionIntercept.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory| Description             |
| ------ | ------ | ---- | ---------------- |
| action | [AccessibilityAction](#accessibilityaction20) | Yes | Type of the accessibility control operation currently triggered. |

**Return value**

| Type   | Description             |
| ------ | ---------------- |
| [AccessibilityActionInterceptResult](#accessibilityactioninterceptresult20) | Result of intercepting an accessibility control operation, used to determine whether to intercept the accessibility control operation of the current component and the subsequent processing method. |

## AccessibilityAction<sup>20+</sup>

Enumerates types of accessibility control operations triggered by components.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value | Description            |
| ---- | ---- | ------------------ |
| UNDEFINED_ACTION | 0 | Undefined accessibility control operation. |
| ACCESSIBILITY_CLICK | 1 | Accessibility click action.|

## AccessibilityActionInterceptResult<sup>20+</sup>

Enumerates possible results for accessibility action interception.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value | Description            |
| ---- | ---- | ------------------ |
| ACTION_INTERCEPT | 0 | Intercepts the accessibility control action received by the current component. After the callback processing is complete, the component won't respond.|
| ACTION_CONTINUE | 1 | Does not intercept the accessibility control operation received by the current component. After the callback handling is complete, the current component is allowed to respond to the accessibility control operation and execute its processing logic. |
| ACTION_RISE | 2 | Does not intercept the accessibility control operation received by the current component. After the callback handling is complete, the component still needs to respond and execute its processing logic, and the accessibility control operation information is passed to the parent component. When the information is passed to the next component that uses onAccessibilityActionIntercept, the callback registered in that component is triggered, but the processing logic of that component is not triggered. After the processing is complete, ACTION_RISE can continue to be used to pass the accessibility control operation information to the parent component. |

## Example

### Example 1: Setting onAccessibilityActionIntercept to Intercept Click Events

This example demonstrates how to use the onAccessibilityActionIntercept event to intercept the click event of a Toggle component before it is triggered in accessibility mode, and the developer decides whether to allow the click event.

```ts
// xxx.ets
@Entry
@Component
struct OnAccessibilityActionInterceptExample {
  @State private isOn: boolean = false;

  build() {
    NavDestination() {
      Column() {
        Text('onAccessibilityActionIntercept')
        Row() {
          Text('Label message')
          Blank()
          Toggle({ type: ToggleType.Switch, isOn: $$this.isOn })
            .onAccessibilityActionIntercept((action: AccessibilityAction) => {
              // When an accessibility click operation is triggered, display a confirmation dialog box for the user to decide whether to allow it.
              if (action === AccessibilityAction.ACCESSIBILITY_CLICK) {
                this.getUIContext().showAlertDialog({
                  title: 'Title',
                  message: 'Message content',
                  primaryButton: {
                    value: 'OK',
                    action: () => {
                      this.isOn = !this.isOn;
                    }
                  },
                  secondaryButton: {
                    value: 'Cancel',
                    action: () => {
                    }
                  }
                });
                // Intercept this click and prevent the default click behavior of the component.
                return AccessibilityActionInterceptResult.ACTION_INTERCEPT;
              } else {
                // Do not intercept other accessibility operations; allow them directly.
                return AccessibilityActionInterceptResult.ACTION_CONTINUE;
              }
            })
        }.width('100%')
      }
      .padding(24)
      .width('100%')
    }
  }
}
```

### Example 2: Setting the onAccessibilityFocus Callback

Since API version 18, the callback is triggered when the focus acquisition or blur state changes. This example demonstrates the basic usage of [onAccessibilityFocus](#onaccessibilityfocus). When the focus moves to "onAccessibilityFocus takes effect", "[testingTag] isFocus current is true" is printed. When the focus moves to a position other than "onAccessibilityFocus takes effect", "[testingTag] isFocus current is false" is printed.

```ts
// xxx.ets
@Entry
@Component
struct OnAccessibilityFocusExample {

  build() {
    NavDestination() {
      Column() {
        Text("onAccessibilityFocus doesn't take effect")
        Text('onAccessibilityFocus takes effect')
        .onAccessibilityFocus((isFocus: boolean) => {
          console.info(`[testingTag] isFocus current is ${isFocus}`);
        })
      }
      .padding(24)
      .width('100%')
    }
  }
}
```