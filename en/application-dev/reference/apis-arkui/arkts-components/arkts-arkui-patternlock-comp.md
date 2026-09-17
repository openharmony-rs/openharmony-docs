# PatternLock

The **PatternLock** component allows users to use a pattern password for authentication. It enters the input state once a finger is pressed against it, and exits the input state and completes the input once the finger leaves the screen.

> **NOTE** > > - If you require additional features, use > [custom components](../../../ui/state-management/arkts-create-custom-components.md). For example, the custom > component<!--RP1--> > [CustomPatternLock](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/UI/CustomPatternLock) > <!--RP1End--> implements the pattern lock function using the Canvas component. You can extend its > functionality as required.

## Child Components

Not supported

## PatternLock

```TypeScript
PatternLock(controller?: PatternLockController)
```

Creates a pattern lock component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [PatternLockController](arkts-arkui-patternlockcontroller-c.md) | No | Controller of a component to reset the component status. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CircleStyleOptions](arkts-arkui-circlestyleoptions-i.md) | Describes the parameters of the ring style. |

### Enums

| Name | Description |
| --- | --- |
| [PatternLockChallengeResult](arkts-arkui-patternlockchallengeresult-e.md) | Authentication challenge result of the pattern password. |

## Examples

```TypeScript
### Example 1: Creating a Pattern Lock

This example shows the basic usage of the PatternLock component.


```

```TypeScript
### Example 2: Verifying the Password

This example shows how to use the [sideLength](arkts-arkui-patternlock-comp-attribute.md#sidelength) attribute to set the size of the nine-grid, the [circleRadius](arkts-arkui-patternlock-comp-attribute.md#circleradius) attribute to set the radius of the dots in the grid, and the [onPatternComplete](arkts-arkui-patternlock-comp-attribute.md#onpatterncomplete) attribute to set the callback invoked when password input is complete.

When the user completes the password input, different responses are given based on the input:- If the password length is less than 5, a message is displayed to prompt the user to re-enter the password.- After the first input, a message is displayed to prompt the user to enter the password again.- After the second input, the system checks whether the two inputs match. If they match, a message is displayed to indicate that the password setup is successful; otherwise, the user is prompted to re-enter the password.

The user can click Reset PatternLock to reset the password lock.
```
