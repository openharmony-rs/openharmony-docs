# PatternLock

The **PatternLock** component allows users to use a pattern password for authentication. It enters the input state once a finger is pressed against it, and exits the input state and completes the input once the finger leaves the screen.

> **NOTE** > > - If you require additional features, use > [custom components](../../../ui/state-management/arkts-create-custom-components.md). For example, the custom > component<!--RP1--> > [CustomPatternLock](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/UI/CustomPatternLock) > <!--RP1End--> implements the pattern lock function using the [Canvas](arkts-arkui-canvas-comp.md#canvas) component. You can extend its > functionality as required.

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
| controller | [PatternLockController](arkts-arkui-patternlock-comp-patternlockcontroller-c.md) | No | Controller of a component to reset the component status. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CircleStyleOptions](arkts-arkui-patternlock-comp-circlestyleoptions-i.md) | Describes the parameters of the ring style. |

### Enums

| Name | Description |
| --- | --- |
| [PatternLockChallengeResult](arkts-arkui-patternlock-comp-patternlockchallengeresult-e.md) | Authentication challenge result of the pattern password. |

## Examples

### Example 1: Creating a Pattern Lock

This example shows the basic usage of the PatternLock component.



```TypeScript
// xxx.ets
@Entry
@Component
struct PatternLockExample {
  @State passwords: number[] = [];
  @State message: string = 'please input password!';
  private patternLockController: PatternLockController = new PatternLockController();

  build() {
    Column() {
      Text(this.message).textAlign(TextAlign.Center).margin(20).fontSize(20)
      PatternLock(this.patternLockController)
        .sideLength(200)
        .circleRadius(9)
        .pathStrokeWidth(5)
        .activeColor('#707070')
        .selectedColor('#707070')
        .pathColor('#707070')
        .backgroundColor('#F5F5F5')
        .regularColor(Color.Black)
        .autoReset(true)
        .onDotConnect((index: number) => {
          console.info('onDotConnect index: ' + index);
        })
    }.width('100%').height('100%')
  }
}
```

### Example 2: Verifying the Password

This example shows how to use the [sideLength](arkts-arkui-patternlock-comp-attribute.md#sidelength) attribute to set the size of the nine-grid, the [circleRadius](arkts-arkui-patternlock-comp-attribute.md#circleradius) attribute to set the radius of the dots in the grid, and the [onPatternComplete](arkts-arkui-patternlock-comp-attribute.md#onpatterncomplete) attribute to set the callback invoked when password input is complete.

When the user completes the password input, different responses are given based on the input:- If the password length is less than 5, a message is displayed to prompt the user to re-enter the password.- After the first input, a message is displayed to prompt the user to enter the password again.- After the second input, the system checks whether the two inputs match. If they match, a message is displayed to indicate that the password setup is successful; otherwise, the user is prompted to re-enter the password.

The user can click Reset PatternLock to reset the password lock.

```TypeScript
// xxx.ets
import { LengthUnit } from '@kit.ArkUI';

@Entry
@Component
struct PatternLockExample {
  @State passwords: number[] = [];
  @State message: string = 'Please input password';
  private patternLockController: PatternLockController = new PatternLockController();

  build() {
    Column() {
      Text(this.message).textAlign(TextAlign.Center).margin(20).fontSize(20)
      PatternLock(this.patternLockController)
        .sideLength(200)
        .circleRadius(9)
        .pathStrokeWidth(5)
        .activeColor('#707070')
        .selectedColor('#707070')
        .pathColor('#707070')
        .backgroundColor('#F5F5F5')
        .autoReset(true)
        .activateCircleStyle({
          color: '#707070',
          radius: { value: 16, unit: LengthUnit.VP },
          enableWaveEffect: true
        })
        .onDotConnect((index: number) => {
          console.info('onDotConnect index: ' + index);
        })
        .onPatternComplete((input: Array<number>) => {
          // If the length of the entered password is less than 5, the system prompts the user to enter the password again.
          if (input.length < 5) {
            this.message = 'The password length needs to be at least 5, please enter again.';
            return;
          }
          // Check whether the password length is greater than 0.
          if (this.passwords.length > 0) {
            // Check whether the two passwords are the same. If yes, the system displays a message indicating that the password is set successfully. If no, the system prompts the user to enter the password again.
            if (this.passwords.toString() === input.toString()) {
              this.passwords = input;
              this.message = 'Set password successfully: ' + this.passwords.toString();
              this.patternLockController.setChallengeResult(PatternLockChallengeResult.CORRECT);
            } else {
              this.message = 'Inconsistent passwords, please enter again.';
              this.patternLockController.setChallengeResult(PatternLockChallengeResult.WRONG);
            }
          } else {
            // The system prompts the user to enter the password again.
            this.passwords = input;
            this.message = 'Please enter again.';
          }
        })
      Button('Reset PatternLock').margin(30).onClick(() => {
        // Reset the pattern lock.
        this.patternLockController.reset();
        this.passwords = [];
        this.message = 'Please input password';
      })
    }.width('100%').height('100%')
  }
}
```
