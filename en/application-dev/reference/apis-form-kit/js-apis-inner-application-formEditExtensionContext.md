# FormEditExtensionContext
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

**FormEditExtensionContext**, inherited from [UIExtensionContext](../apis-ability-kit/js-apis-inner-application-uiExtensionContext.md), is the context of [FormEditExtensionAbility](./js-apis-app-form-formEditExtensionAbility.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import
```ts
import { FormEditExtensionAbility } from '@kit.FormKit';
```
## FormEditExtensionContext
You can use **FormEditExtensionContext** to access specific **FormEditExtensionAbility** resources.

### startSecondPage

startSecondPage(want: Want): Promise<[AbilityResult](../apis-ability-kit/js-apis-inner-ability-abilityResult.md)>

Starts the widget provider page to be edited. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.Form

**Parameters**

  | Name| Type   | Mandatory| Description                                  |
  | ------ | ------ | ---- | ------------------------------------- |
  | want  |  [Want](../apis-ability-kit/js-apis-app-ability-want.md)  | Yes  | Information about the editing page that needs to be started by the home screen of a third-party application.|

**Return value**

  | Type| Description   |
  | ------ | ------ |
  | Promise<[AbilityResult](../apis-ability-kit/js-apis-inner-ability-abilityResult.md)>  |  Promise used to return the ability result. |

**Error codes**

For details about the error codes, see [Form Error Codes](errorcode-form.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                 |
| 16500050 | An IPC connection error happened.                            |
| 16501000 | An internal functional error occurred.                       |
| 16500100 | Failed to obtain the configuration information.                        |

**Example**

```ts
import { FormEditExtensionAbility } from '@kit.FormKit'
import { Want, UIExtensionContentSession } from '@kit.AbilityKit';

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
        console.info(TAG, `startSecondPage result want: ${JSON.stringify(data)}`)
      });
    } catch (e) {
      console.error(TAG, `startSecondPage failed:${e}`)
      return
    }
  }
}

```

### startUIAbility<sup>23+<sup>

startUIAbility(want: Want): Promise&lt;void&gt;

Starts UIAbility of the application to which a widget belongs. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.Form

**Parameters**

  | Name| Type   | Mandatory| Description                                  |
  | ------ | ------ | ---- | ------------------------------------- |
  | want  |  [Want](../apis-ability-kit/js-apis-app-ability-want.md#want)  | Yes  | Want information of the UIAbility of the application.|

**Return value**

  | Type| Description   |
  | ------ | ------ |
  | Promise&lt;void&gt;   |  Promise that returns no value. |

**Error codes**

For details about the error codes, see [Form Error Codes](errorcode-form.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 16500050 | An IPC connection error happened.                            |
| 16500100 | Failed to obtain the configuration information.                        |
| 16000130 | The target UIAbility does not belong to the caller.                       |
| 16501014 | The form edit page is not in the foreground. The current operation is not supported. |
| 16000121 | The target component type is not a UIAbility.                       |

**Example**

```ts
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
      console.error(TAG, `startUIAbility failed:${e}`);
      return
    }
  }
}
```
