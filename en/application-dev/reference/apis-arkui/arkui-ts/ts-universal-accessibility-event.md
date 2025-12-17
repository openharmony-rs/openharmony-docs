# Accessibility Control Actions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

When accessibility mode is enabled, you can choose whether to intercept accessibility control actions.

>**NOTE**
>
>  - The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - Currently, accessibility events can be triggered only when accessibility mode is enabled.

## onAccessibilityFocus

onAccessibilityFocus(callback: AccessibilityFocusCallback): T

Triggered when the accessibility component gains or loses focus. Callback triggered when the component gains or loses focus.

**Widget capability**: This API can be used in ArkTS widgets since API version 18.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory| Description                                                        |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| callback | [AccessibilityFocusCallback](ts-universal-accessibility-event.md#accessibilityfocuscallback) | Yes  | Callback that notifies the registered component of focus and blur events.|

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
| isFocus | boolean | Yes| Whether the component has gained or lost focus.<br>**true**: The component has gained focus.<br>**false**: The component has lost focus.|

## onAccessibilityActionIntercept<sup>20+</sup>

onAccessibilityActionIntercept(callback: AccessibilityActionInterceptCallback): T

Registers a callback to intercept accessibility control actions in accessibility mode. The callback is invoked before an accessibility action is triggered, allowing the component to determine whether to intercept the action. This callback is not supported by components that lack click capability.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory| Description                                                        |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| callback | [AccessibilityActionInterceptCallback](ts-universal-accessibility-event.md#accessibilityactioninterceptcallback20) | Yes  | Callback to be invoked before an accessibility action is triggered. The application that registers this callback can decide whether to intercept the action.<br> Set to **undefined** to unregister the callback.|

**Return value**

| Type   | Description             |
| ------ | ---------------- |
| T | Current component.|

## AccessibilityActionInterceptCallback<sup>20+</sup>

type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult

Defines the callback type used in **onAccessibilityActionIntercept** to handle accessibility event interception.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory| Description             |
| ------ | ------ | ---- | ---------------- |
| action | [AccessibilityAction](ts-universal-accessibility-event.md#accessibilityaction20) | Yes| Type of accessibility action being triggered.|

**Return value**

| Type   | Description             |
| ------ | ---------------- |
| [AccessibilityActionInterceptResult](ts-universal-accessibility-event.md#accessibilityactioninterceptresult20) | Decision on whether to intercept the accessibility action.|

## AccessibilityAction<sup>20+</sup>

Enumerates types of accessibility control operations triggered by components.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value | Description            |
| ---- | ---- | ------------------ |
| UNDEFINED_ACTION | 0 | Undefined accessibility action.|
| ACCESSIBILITY_CLICK | 1 | Accessibility click action.|

## AccessibilityActionInterceptResult<sup>20+</sup>

Enumerates possible results for accessibility action interception.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value | Description            |
| ---- | ---- | ------------------ |
| ACTION_INTERCEPT | 0 | Intercept the accessibility control action received by the current component. After the callback processing is complete, the component won't respond.|
| ACTION_CONTINUE | 1 | Allow the accessibility control action received by the current component. After the callback processing is complete, the component processes it normally.|
| ACTION_RISE | 2 | Intercept accessibility control action received by the current component. After the callback processing is complete, the component responds and executes its own processing logic. The action information is then passed to the parent component. This triggers the **onAccessibilityActionIntercept** callback of the parent (if registered) but not the parent's default processing logic. The parent can continue passing the action upward using **ACTION_RISE**.|

## Example

The example demonstrates how to use the **onAccessibilityActionIntercept** event to intercept a click event on a **Toggle** component in accessibility mode before the click event is processed.

```ts
// xxx.ets
@Entry
@Component
struct SwitchBootcamp {
  @State private isOn: boolean = false;

  build() {
    NavDestination() {
      Column() {
        Text('onTouchIntercept')
        Row() {
          Text('Label message')
          Blank()
          Toggle({ type: ToggleType.Switch, isOn: $$this.isOn })
            .onAccessibilityActionIntercept((action : AccessibilityAction) => {
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
                })
                return AccessibilityActionInterceptResult.ACTION_INTERCEPT;
              } else {
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
