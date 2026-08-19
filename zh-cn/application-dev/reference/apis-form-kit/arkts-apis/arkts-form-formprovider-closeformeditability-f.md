# closeFormEditAbility

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## closeFormEditAbility

```TypeScript
function closeFormEditAbility(isMainPage?: boolean): void
```

关闭卡片编辑页。适用于卡片编辑完成或取消编辑的场景，例如用户完成参数配置后关闭编辑页、取消编辑操作等。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formProvider-function closeFormEditAbility(isMainPage?: boolean): void--><!--Device-formProvider-function closeFormEditAbility(isMainPage?: boolean): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMainPage | boolean | 否 | 是否关闭主编辑页。 <br>- true：关闭主编辑页，适合在主编辑页完成配置后关闭的场景。 <br>- false：关闭非主编辑页，适合在多级编辑页场景下关闭当前非主编辑页的场景。 <br>默认值：true（通常关闭当前编辑页时使用默认值即可）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported due to limited device capabilities. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16501015](../errorcode-form.md#16501015-不能关闭其他应用的半模态卡片编辑页) | Cannot close the widget editing page opened by other apps. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formProvider } from '@kit.FormKit';

const TAG: string = 'FormEditDemo-Page] -->';

@Entry
@Component
struct Page {
  @State message: string = 'Hello World';

  aboutToAppear(): void {
    console.info(`${TAG} aboutToAppear.....`);
  }

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('PageHelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Top },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          console.info(`${TAG} onClick.....`);
          try {
            formProvider.closeFormEditAbility();
            console.info(`${TAG} close FormEditAbility success.`);
          } catch (error) {
            console.error(`${TAG} close FormEditAbility failed, code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { formProvider } from '@kit.FormKit';
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'

@Entry
@Component
struct Index {
  @State stateVar: string = 'state var';
  message: string = 'var';

  build() {
    Column(undefined) {
      Text('Hello World').fontSize(20)
      Button(this.message).backgroundColor('#FFFF00FF')
        .onClick((e: ClickEvent) => {
          try {
            formProvider.closeFormEditAbility();
            console.info('close FormEditAbility success.');
          } catch (error) {
            console.error(`close FormEditAbility failed, code: ${error.code}, message: ${error.message}`);
          }
        })
      Text(this.stateVar).fontSize(20)
      Child({ stateVar: this.stateVar })
    }
  }
}

@Component
struct Child {
  @State stateVar: string = 'Child';

  build() {
    Text(this.stateVar).fontSize(50)
  }
}
```

