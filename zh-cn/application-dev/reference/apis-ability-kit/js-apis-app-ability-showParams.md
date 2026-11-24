# @ohos.app.ability.ShowParams (ShowParams)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @dsz2025; @yangxuguang-huawei; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

ShowParams作为显示UIAbility的API（例如[showAbility()](js-apis-inner-application-uiAbilityContext.md#showability)）的入参，用于指定当前UIAbility的显示参数，包括但不限于窗口是否获得焦点。

**起始版本：** 26.1.0

## 导入模块

```ts
import { ShowParams } from '@kit.AbilityKit';
```

## ShowParams

ShowParams用于指定当前UIAbility显示时的参数。

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| windowShowParams | [window.WindowShowParams](../apis-arkui/arkts-apis-window-i.md#windowshowparams) | 否 | 否 | 显示UIAbility时的窗口参数，包括窗口是否自动获取焦点、是否自动抬升至顶层。<br>**原子化服务API**：从API版本26.1.0开始，该接口支持在原子化服务中使用。<br>**起始版本：** 26.1.0 |

**示例：**

```ts
// Index.ets
import { common, ShowParams } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State showAbility: string = 'showAbility'

  build() {
    Row() {
      Column() {
        Text(this.showAbility)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let params: ShowParams = {
              windowShowParams: {
                windowFocused: false,
                raiseTop: true
              }
            };

            // 显示当前UIAbility
            context.showAbility(params).then(() => {
              console.info(`showAbility success`);
            }).catch((err: BusinessError) => {
              console.error(`showAbility fail, err: ${JSON.stringify(err)}`);
            });
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
