# FormEditExtensionContext

FormEditExtensionContext是 [FormEditExtensionAbility](arkts-form-app-form-formeditextensionability-formeditextensionability-c.md)的上下文，继承自 [UIExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensioncontext-c.md)。用于管理卡片编辑场景的上下文环境，支持拉起卡片提供方页面和所属应用UIAbility，适用于卡片编 辑流程中需要与卡片提供方交互的场景。

**继承/实现关系：** FormEditExtensionContext extends UIExtensionContext

**起始版本：** 23

<!--Device-unnamed-declare class FormEditExtensionContext--><!--Device-unnamed-declare class FormEditExtensionContext-End-->

**系统能力：** SystemCapability.Ability.Form

## startSecondPage

```TypeScript
startSecondPage(want: Want): Promise<AbilityResult>
```

拉起需要被编辑的卡片提供方页面。使用Promise异步回调。 - 用户在卡片编辑界面点击编辑按钮，需要打开卡片提供方的编辑页面。 - 用户需要修改卡片配置或内容时，拉起卡片提供方应用进行编辑。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormEditExtensionContext-startSecondPage(want: Want): Promise<AbilityResult>--><!--Device-FormEditExtensionContext-startSecondPage(want: Want): Promise<AbilityResult>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 需要拉起的编辑页面信息。必须包含bundleName字段，且parameters中需包含secPageAbilityName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AbilityResult](../../apis-ability-kit/arkts-apis/arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise对象，返回被启动方退出时的结果码和数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | An IPC connection error happened. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormEditExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession, Want } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExampleFormEditExtensionAbility'

export default class ExampleFormEditAbility extends FormEditExtensionAbility {
  abilityName: string = 'FormEditSecPageAbility'

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    try {
      this.context.startSecondPage({
        bundleName: 'com.example.formEditDemo',
        parameters: {
          "secPageAbilityName": this.abilityName
        }

      }).then(data => {
        console.info(TAG, `startSecondPage result want: ${data.resultCode}`)
      });
    } catch (e) {
      console.error(TAG, `startSecondPage failed, code: ${e.code}, message: ${e.message}`)
      return
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormEditExtensionAbility } from '@kit.FormKit';
import { Want, UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

const TAG: string = '[testTag] ExampleFormEditExtensionAbility'

export default class ExampleFormEditAbility extends FormEditExtensionAbility {
  abilityName: string = 'FormEditSecPageAbility'

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    try {
      this.context.startSecondPage({
        bundleName: 'com.example.formEditDemo',
        parameters: {
          "secPageAbilityName": this.abilityName
        } as Record<string, RecordData>

      }).then(data => {
        console.info(TAG, `startSecondPage result resultCode: ${data.resultCode}`)
      });
    } catch (error) {
      console.error(TAG, `startSecondPage failed: code: ${error.code} message: ${error.message}`)
      return
    }
  }
}
```

## startUIAbility

```TypeScript
startUIAbility(want: Want): Promise<void>
```

拉起卡片所属应用的UIAbility。使用Promise异步回调。说明：需在卡片编辑页面处于前台时调用，页面不在前台时调用将返回错误码16501014。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormEditExtensionContext-startUIAbility(want: Want): Promise<void>--><!--Device-FormEditExtensionContext-startUIAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 用于指定要拉起的UIAbility的Want信息。必须包含abilityName字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000130](../../apis-ability-kit/errorcode-ability.md#16000130-uiability不属于调用方) | The target UIAbility does not belong to the caller. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | An IPC connection error happened. |
| [16501014](../errorcode-form.md#16501014-半模态卡片编辑页不在前台) | The form edit page is not in the foreground. The current operation is not supported. |
| [16000121](../../apis-ability-kit/errorcode-ability.md#16000121-待启动的目标组件类型不是uiability) | The target component type is not a UIAbility. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormEditExtensionAbility } from '@kit.FormKit'
import { Want, UIExtensionContentSession } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExampleFormEditExtensionAbility'

export default class ExampleFormEditAbility extends FormEditExtensionAbility {
  abilityName: string = 'FormEditSecPageAbility'

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    try {
      this.context.startUIAbility({
        abilityName: 'EntryAbility1',
      }).then(() => {
        console.info(TAG, `startUIAbility success`);
      });
    } catch (e) {
      console.error(TAG, `startUIAbility failed, code: ${e.code}, message: ${e.message}`);
      return
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormEditExtensionAbility } from '@kit.FormKit';
import { Want, UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

const TAG: string = '[testTag] ExampleFormEditExtensionAbility'

export default class ExampleFormEditAbility extends FormEditExtensionAbility {
  abilityName: string = 'FormEditSecPageAbility'

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    try {
      this.context.startSecondPage({
        bundleName: 'com.example.formEditDemo',
        parameters: {
          "secPageAbilityName": this.abilityName
        } as Record<string, RecordData>

      }).then(data => {
        console.info(TAG, `startSecondPage result resultCode: ${data.resultCode}`)
      });
    } catch (error) {
      console.error(TAG, `startSecondPage failed: code: ${error.code} message: ${error.message}`)
      return
    }
  }
}
```

