# openFormEditAbility

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## openFormEditAbility

```TypeScript
function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void
```

打开卡片编辑页。适用于需要用户配置卡片参数的场景，例如设置卡片显示内容、选择数据源、配置更新频率等。

**起始版本：** 23

<!--Device-formProvider-function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void--><!--Device-formProvider-function openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityName | string | 是 | 编辑页的ability名称。 |
| formId | string | 是 | 卡片标识。 |
| isMainPage | boolean | 否 | 是否为主编辑页。 <br>- true：表示是主编辑页，适合首次配置卡片基本信息的场景。 <br>- false：表示不是主编辑页，适合进行卡片细节调整或高级配置的场景。 <br>默认值：true（通常首次编辑卡片时使用默认值即可）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function openFormEditAbility cannot work correctly due to limited device capabilities. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501007](../errorcode-form.md#16501007-卡片不可信) | Form is not trust. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

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
          formProvider.openFormEditAbility('ability://EntryFormEditAbility', '1386529921');
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

import { State } from '@ohos.arkui.stateManagement'
import { formProvider } from '@kit.FormKit';

const TAG: string = 'FormEditDemo-Page] -->';

@Component
struct Page {
  @State message: string = 'Hello World';

  aboutToAppear(): void {
    console.info(`${TAG} aboutToAppear.....`);
  }

  build() {
    Column() {
      Text(this.message)
        .id('PageHelloWorld')
        .fontSize(50)
        .onClick(() => {
          console.info(`${TAG} onClick.....`);
          formProvider.openFormEditAbility('ability://EntryFormEditAbility', '1386529921');
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

