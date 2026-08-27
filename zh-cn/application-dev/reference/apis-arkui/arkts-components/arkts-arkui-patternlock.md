# PatternLock

图案密码锁组件，以九宫格图案的方式输入密码，用于密码验证场景。组件支持自定义九宫格尺寸、圆点及连线样式、选中/激活状态颜色等外观属性，支持密码输入过程中的实时反馈以及密码验证结果（正确/错误）的状态设置。手指在PatternLock组 件区域按下时开始进入输入状态，手指离开屏幕时结束输入状态完成密码输入。
> **说明：** > > - 如果开发者有其他功能需求，可以使用[自定义组件](../../../ui/state-management/arkts-create-custom-components.md)。例如自定义组件<!--RP1--> > [CustomPatternLock](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/UI/CustomPatternLock) > <!--RP1End-->，通过Canvas组件实现了图案密码锁功能，开发者可在此基础上自行进行功能扩展。

## 子组件

无

## PatternLock

```TypeScript
PatternLock(controller?: PatternLockController)
```

创建图案密码锁组件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [PatternLockController](arkts-arkui-patternlockcontroller-c.md) | 否 | 设置PatternLock组件控制器，用于重置组件状态和设置图案密码状态。当需要程序化控制组件状态（如重置密码锁、设置密码验证结果）时 传入此参数；不传入时无法通过控制器手动操作组件状态（即无法调用reset()、setChallengeResult()等方法）。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CircleStyleOptions](arkts-arkui-circlestyleoptions-i.md) | 圆环样式的参数说明。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PatternLockChallengeResult](arkts-arkui-patternlockchallengeresult-e.md) | 图案密码状态。 |

## 示例

该示例展示了PatternLock组件的基本使用方法。

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

通过'Reset PatternLock'按钮，用户可以重置密码锁。

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
          // 输入的密码长度小于5时，提示重新输入
          if (input.length < 5) {
            this.message = 'The password length needs to be at least 5, please enter again.';
            return;
          }
          // 判断密码长度是否大于0
          if (this.passwords.length > 0) {
            // 判断两次输入的密码是否相同，相同则提示密码设置成功，否则提示重新输入
            if (this.passwords.toString() === input.toString()) {
              this.passwords = input;
              this.message = 'Set password successfully: ' + this.passwords.toString();
              this.patternLockController.setChallengeResult(PatternLockChallengeResult.CORRECT);
            } else {
              this.message = 'Inconsistent passwords, please enter again.';
              this.patternLockController.setChallengeResult(PatternLockChallengeResult.WRONG);
            }
          } else {
            // 提示第二次输入密码
            this.passwords = input;
            this.message = 'Please enter again.';
          }
        })
      Button('Reset PatternLock').margin(30).onClick(() => {
        // 重置密码锁
        this.patternLockController.reset();
        this.passwords = [];
        this.message = 'Please input password';
      })
    }.width('100%').height('100%')
  }
}
```
