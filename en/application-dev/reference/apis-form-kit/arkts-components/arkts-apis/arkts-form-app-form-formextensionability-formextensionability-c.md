# FormExtensionAbility

Widget extension class. It provides APIs to notify the widget provider that a widget is being created or the widget visibility status is being changed.

**Since:** 9

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
```

## onAcquireFormState

```TypeScript
onAcquireFormState?(want: Want): formInfo.FormState
```

Called to notify the widget provider that the widget host is requesting the widget state. By default, the initial widget state is returned. (You can override this API as required.)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Description of the widget state, including the bundle name, ability name, module name, and widget name. |

**Return value:**

| Type | Description |
| --- | --- |
| [formInfo.FormState](arkts-form-forminfo-formstate-e.md) | Enumerated values of the current widget status. |

**Examples**

```TypeScript
import { FormExtensionAbility, formInfo } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onAcquireFormState(want: Want) {
    console.info(`FormExtensionAbility onAcquireFormState, want: ${want}`);
    return formInfo.FormState.UNKNOWN;
  }
}
```

## onAddForm

```TypeScript
onAddForm(want: Want): formBindingData.FormBindingData
```

Called to notify the widget provider that a widget is being created.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information of the widget. You can set the **parameters** field to one or more values enumerated in [widget parameters](arkts-form-forminfo-formparam-e.md), such as widget ID, widget name, and widget style. The information must be managed as persistent data to facilitate subsequent widget update and deletion. |

**Return value:**

| Type | Description |
| --- | --- |
| [formBindingData.FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | A **formBindingData.FormBindingData** object containing the data to be displayed on the widget. |

**Examples**

```TypeScript
import { formBindingData, FormExtensionAbility } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onAddForm(want: Want) {
    console.info(`FormExtensionAbility onAddForm, want: ${want.abilityName}`);
    let temperatureData: Record<string, string> = {
      'temperature': '11°C',
      'time': '11:00'
    };

    let formBindingDataObj: formBindingData.FormBindingData = formBindingData.createFormBindingData(temperatureData);
    return formBindingDataObj;
  }
}
```

## onCastToNormalForm

```TypeScript
onCastToNormalForm(formId: string): void
```

Called to notify the widget provider that a temporary widget has been converted to a normal one. Temporary widgets and normal widgets are concepts of the widget host. Temporary widgets have a brief existence, appearing following particular events or user interactions and vanishing automatically upon task completion. Normal widgets maintain a lasting presence, continuing to exist unless explicitly removed or altered by the user. Function widgets developed in normal cases are normal widgets. Currently, the widget host does not use temporary widgets.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | ID of the widget that requests to be converted to a normal one. |

**Examples**

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onCastToNormalForm(formId: string) {
    // Called to notify the widget provider that a temporary widget has been converted to a normal one. You need to perform operations as required.
    console.info(`FormExtensionAbility onCastToNormalForm, formId: ${formId}`);
  }
}
```

## onChangeFormVisibility

```TypeScript
onChangeFormVisibility(newStatus: Record<string, number>): void
```

Called to notify the widget provider that the widget visibility status is being changed. This API is valid only for system applications when **formVisibleNotify** is set to **true**.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newStatus | Record&lt;string, number&gt; | Yes | ID and visibility status of the widget to be changed.<br>**Since:** 11 |

**Examples**

```TypeScript
import { formBindingData, FormExtensionAbility, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

// According to the ArkTS specification, Object.keys and for..in... cannot be used in .ets files to obtain the key value of an object. Use the user-defined function getObjKeys instead.
// Extract this function to a .ts file and export it. Import this function to the required .ets file before using it.
function getObjKeys(obj: Object): string[] {
  let keys = Object.keys(obj);
  return keys;
}

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onChangeFormVisibility(newStatus: Record<string, number>) {
    console.info(`FormExtensionAbility onChangeFormVisibility, newStatus: ${newStatus}`);
    let param: Record<string, string> = {
      'temperature': '22°C',
      'time': '22:00'
    }
    let formBindingDataObj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);

    let keys: string[] = getObjKeys(newStatus);

    for (let i: number = 0; i < keys.length; i++) {
      console.info(`FormExtensionAbility onChangeFormVisibility, key: ${keys[i]}, value= ${newStatus[keys[i]]}`);
      formProvider.updateForm(keys[i], formBindingDataObj).then(() => {
        console.info('FormExtensionAbility context updateForm');
      }).catch ((error: BusinessError) => {
        console.error(`Operation updateForm failed, code: ${error.code}, message: ${error.message}`);
      });
    }
  }
}
```

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

Called when system configuration items change. The **onConfigurationUpdate** callback is triggered only when the FormExtensionAbility is alive. <!--Del-->Since API version 20, for system applications, the **onConfigurationUpdate** callback within the FormExtensionAbility will be triggered when the system language changes.<!--DelEnd-->

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newConfig | [Configuration](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md) | Yes | New configuration. |

**Examples**

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
import { Configuration } from '@kit.AbilityKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onConfigurationUpdate(newConfig: Configuration) {
    // This lifecycle callback is triggered only when the configuration is updated while the FormExtensionAbility is alive.
    // If no operation is performed within 10 seconds after a FormExtensionAbility instance is created, the instance will be deleted.
    console.info(`onConfigurationUpdate, config: ${newConfig?.language}`);
  }
}
```

## onFormEvent

```TypeScript
onFormEvent(formId: string, message: string): void
```

Called to instruct the widget provider to process the widget event.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | ID of the widget that requests the event. |
| message | string | Yes | Event message. |

**Examples**

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    console.info(`FormExtensionAbility onFormEvent, formId: ${formId}, message: ${message}`);
  }
}
```

## onFormLocationChanged

```TypeScript
onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void
```

Called when the widget location changes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Widget ID. |
| newFormLocation | [formInfo.FormLocation](arkts-form-forminfo-formlocation-e.md) | Yes | Enumerated value of the latest widget location. |

**Examples**

```TypeScript
import { formBindingData, FormExtensionAbility, formInfo } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';

export default class EntryFormAbility extends FormExtensionAbility {
  onAddForm(want: Want) {
    let formData: Record<string, string | Object> = {
      'data': 'addForm'
    };
    return formBindingData.createFormBindingData(formData);
  }
  onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation) {
    console.info('EntryFormAbility onFormLocationChanged current location: ' + newFormLocation);
  }
}
```

## onRemoveForm

```TypeScript
onRemoveForm(formId: string): void
```

Called to notify the widget provider that a widget is being destroyed.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | ID of the widget to be destroyed. |

**Examples**

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onRemoveForm(formId: string) {
    console.info(`FormExtensionAbility onRemoveForm, formId: ${formId}`);
  }
}
```

## onSizeChanged

```TypeScript
onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void
```

Called when the widget size changes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Widget ID. |
| newDimension | [formInfo.FormDimension](arkts-form-forminfo-formdimension-e.md) | Yes | Widget dimension. For example, **Dimension_1_2** indicates a 1 x 2 widget. |
| newRect | [formInfo.Rect](arkts-form-forminfo-rect-i.md) | Yes | Widget position information, including the X and Y coordinates of the widget's top- left corner, as well as its width and height. |

**Examples**

```TypeScript
import { FormExtensionAbility, formInfo } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect) {
    console.info(`FormExtensionAbility onSizeChanged, formId: ${formId}, newDimension: ${newDimension}`);
  }
}
```

## onStop

```TypeScript
onStop?(): void
```

Called when the widget process of the widget provider exits.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.Form

**Examples**

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onStop() {
    console.info(`FormExtensionAbility onStop`);
  }
}
```

## onUpdateForm

```TypeScript
onUpdateForm(formId: string, wantParams?: Record<string, Object>): void
```

Called to notify the widget provider that a widget is being updated, with update parameters carried. After obtaining the latest data, your application should call [updateForm](arkts-form-formprovider-updateform-f.md) of **formProvider** to update the widget data.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | ID of the widget that requests to be updated. |
| wantParams | Record&lt;string, Object&gt; | No | Parameters used for the update. |

**Examples**

```TypeScript
import { formBindingData, FormExtensionAbility, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onUpdateForm(formId: string, wantParams?: Record<string, Object>) {
    console.info(`FormExtensionAbility onUpdateForm, formId: ${formId},
        wantPara: ${wantParams?.['ohos.extra.param.key.host_bg_inverse_color']}`);
    let param: Record<string, string> = {
      'temperature': '22c',
      'time': '22:00'
    }
    let obj2: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
    formProvider.updateForm(formId, obj2).then(() => {
      console.info(`FormExtensionAbility context updateForm`);
    }).catch((error: BusinessError) => {
      console.error(`FormExtensionAbility context updateForm failed, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
    });
  }
}
```

## context

```TypeScript
context: FormExtensionContext
```

Context of the FormExtensionAbility. This context is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

This API can be used in atomic services since API version 11.

**Type:** [FormExtensionContext](arkts-form-formextensioncontext-c-sys.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form
