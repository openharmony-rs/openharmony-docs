# FormEditExtensionContext

<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=2a2c17aef02dee6707c724274ac2637725c68be6 translatedAt=2026-09-15T01:57:07.715Z pushedAt=2026-09-15T07:29:51.690Z -->

FormEditExtensionContext is the context of [FormEditExtensionAbility](./js-apis-app-form-formEditExtensionAbility.md), and inherits from [UIExtensionContext](../apis-ability-kit/js-apis-inner-application-uiExtensionContext.md). It is used to manage the context environment in widget editing scenarios, supporting the launch of widget provider pages and the owning app's UIAbility. It is applicable to scenarios where interaction with the widget provider is required during the widget editing process.

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

Provides access to resources specific to FormEditExtensionAbility.

### startSecondPage

startSecondPage(want: Want): Promise&lt;AbilityResult&gt;

Starts the widget provider page to be edited. This API uses a promise to return the result.

**Use cases**

- When a user taps the edit button on the widget editing page, the widget provider's editing page needs to be opened.

- When a user needs to modify widget configuration or content, the widget provider app needs to be launched for editing.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description                                  |
| ------ | ------ | ---- | ------------------------------------- |
| want  |  [Want](../apis-ability-kit/js-apis-app-ability-want.md)  | Yes   | Information about the editing page to start. The bundleName field is mandatory, and parameters must contain secPageAbilityName.|

 **Return value**

| Type| Description   |
| ------ | ------ |
| Promise&lt;[AbilityResult](../apis-ability-kit/js-apis-inner-ability-abilityResult.md)&gt;  |  Promise used to return the result code and data when the started party exits.  |

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                 |
| 16500050 | An IPC connection error happened.                            |
| 16501000 | An internal functional error occurred.                       |
| 16500100 | Failed to obtain the configuration information.                        |

**Example**

```ts
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

### startUIAbility<sup>23+<sup>

startUIAbility(want: Want): Promise&lt;void&gt;

Launches the UIAbility of the application to which the widget belongs. This API uses a promise to return the result. Note: This API must be called when the widget editing page is in the foreground. Otherwise, error code 16501014 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description                                  |
| ------ | ------ | ---- | ------------------------------------- |
| want  |  [Want](../apis-ability-kit/js-apis-app-ability-want.md#want)  | Yes   | Want information used to specify the UIAbility to start. The abilityName field must be included.|

**Return value**

| Type| Description   |
| ------ | ------ |
| Promise&lt;void&gt;   |  Promise that returns no value.  |

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

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
      console.error(TAG, `startUIAbility failed, code: ${e.code}, message: ${e.message}`);
      return
    }
  }
}
```