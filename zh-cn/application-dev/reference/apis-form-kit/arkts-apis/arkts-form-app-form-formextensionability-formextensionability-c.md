# FormExtensionAbility

Widget extension class. It provides APIs to notify the widget provider that a widget is being created or the widget visibility status is being changed.

**起始版本：** 23

<!--Device-unnamed-declare class FormExtensionAbility--><!--Device-unnamed-declare class FormExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
```

## onAcquireFormState

```TypeScript
onAcquireFormState?(want: Want): formInfo.FormState
```

Called to notify the widget provider that the widget host is requesting the widget state. By default, the initial widget state is returned. (You can override this API as required.)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onAcquireFormState?(want: Want): formInfo.FormState--><!--Device-FormExtensionAbility-onAcquireFormState?(want: Want): formInfo.FormState-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Description of the widget state, including the bundle name, ability name, module name, and widget name. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| formInfo.FormState | Enumerated values of the current widget status. |

**示例**

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

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onAddForm(want: Want): formBindingData.FormBindingData--><!--Device-FormExtensionAbility-onAddForm(want: Want): formBindingData.FormBindingData-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want information of the widget. You can set the **parameters** field to one or more values enumerated in [widget parameters](arkts-form-forminfo-formparam-e.md), such as widget ID, widget name, and widget style. The information must be managed as persistent data to facilitate subsequent widget update and deletion. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| formBindingData.FormBindingData | A **formBindingData.FormBindingData** object containing the data to be displayed on the widget. |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
'use static'

import { formBindingData, FormExtensionAbility } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onAddForm(want: Want) : formBindingData.FormBindingData {
    console.info('testTag', 'onAddForm testing');
    // 返回一个FormBindingData对象。
    const formData = '';
    return formBindingData.createFormBindingData(formData);
  }
}
```

## onCastToNormalForm

```TypeScript
onCastToNormalForm(formId: string): void
```

Called to notify the widget provider that a temporary widget has been converted to a normal one. Temporary widgets and normal widgets are concepts of the widget host. Temporary widgets have a brief existence, appearing following particular events or user interactions and vanishing automatically upon task completion. Normal widgets maintain a lasting presence, continuing to exist unless explicitly removed or altered by the user. Function widgets developed in normal cases are normal widgets. Currently, the widget host does not use temporary widgets.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onCastToNormalForm(formId: string): void--><!--Device-FormExtensionAbility-onCastToNormalForm(formId: string): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | ID of the widget that requests to be converted to a normal one. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onCastToNormalForm(formId: string) {
    // 卡片提供方收到卡片使用方将临时卡片转常态卡片的通知时触发，开发者需根据实际需求做相应的处理
    console.info(`FormExtensionAbility onCastToNormalForm, formId: ${formId}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onCastToNormalForm(formId: string) {
    // 卡片提供方收到卡片使用方将临时卡片转常态卡片的通知时触发，开发者需根据实际需求做相应的处理
    console.info(`FormExtensionAbility onCastToNormalForm, formId: ${formId}`);
  }
}
```

## onChangeFormVisibility

```TypeScript
onChangeFormVisibility(newStatus: Record<string, int>): void
```

Called to notify the widget provider that the widget visibility status is being changed. This API is valid only for system applications when **formVisibleNotify** is set to **true**.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormExtensionAbility-onChangeFormVisibility(newStatus: Record<string, int>): void--><!--Device-FormExtensionAbility-onChangeFormVisibility(newStatus: Record<string, int>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newStatus | Record&lt;string, int&gt; | 是 | ID and visibility status of the widget to be changed.<br>**起始版本：** 11 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formBindingData, FormExtensionAbility, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

// ArkTS规范中ets文件无法使用Object.keys和for..in...获取Object的key值，请使用自定义函数getObjKeys代替。
// 使用时请将此函数单独抽离至一个ts文件中并导出，在需要用到的ets文件中导入此函数后使用。
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

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onChangeFormVisibility(newStatus: Record<string, int>) {
    console.info('testTag', 'onChangeFormVisibility testing');
  }
}
```

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

Called when system configuration items change. The **onConfigurationUpdate** callback is triggered only when the FormExtensionAbility is alive. <!--Del-->Since API version 20, for system applications, the **onConfigurationUpdate** callback within the FormExtensionAbility will be triggered when the system language changes.<!--DelEnd-->

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onConfigurationUpdate(newConfig: Configuration): void--><!--Device-FormExtensionAbility-onConfigurationUpdate(newConfig: Configuration): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newConfig | [Configuration](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md) | 是 | New configuration. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
import { Configuration } from '@kit.AbilityKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onConfigurationUpdate(newConfig: Configuration) {
    // 仅当前formExtensionAbility存活时更新配置才会触发此生命周期。
    // 需要注意：formExtensionAbility创建后10秒内无操作将会被清理。
    console.info(`onConfigurationUpdate, config: ${newConfig?.language}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { FormExtensionAbility } from '@kit.FormKit';
import { Configuration } from '@kit.AbilityKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onConfigurationUpdate(newConfig: Configuration) {
    // 仅当前formExtensionAbility存活时更新配置才会触发此生命周期。
    // 需要注意：formExtensionAbility创建后10秒内无操作将会被清理。
    console.info(`onConfigurationUpdate, config language: ${newConfig.language}`);
  }
}
```

## onFormEvent

```TypeScript
onFormEvent(formId: string, message: string): void
```

Called to instruct the widget provider to process the widget event.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onFormEvent(formId: string, message: string): void--><!--Device-FormExtensionAbility-onFormEvent(formId: string, message: string): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | ID of the widget that requests the event. |
| message | string | 是 | Event message. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    console.info(`FormExtensionAbility onFormEvent, formId: ${formId}, message: ${message}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

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

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void--><!--Device-FormExtensionAbility-onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | Widget ID. |
| newFormLocation | formInfo.FormLocation | 是 | Enumerated value of the latest widget location. |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
'use static'

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

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onRemoveForm(formId: string): void--><!--Device-FormExtensionAbility-onRemoveForm(formId: string): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | ID of the widget to be destroyed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onRemoveForm(formId: string) {
    console.info(`FormExtensionAbility onRemoveForm, formId: ${formId}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

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

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void--><!--Device-FormExtensionAbility-onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | Widget ID. |
| newDimension | formInfo.FormDimension | 是 | Widget dimension. For example, **Dimension_1_2** indicates a 1 x 2 widget. |
| newRect | formInfo.Rect | 是 | Widget position information, including the X and Y coordinates of the widget's top- left corner, as well as its width and height. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { FormExtensionAbility, formInfo } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onSizeChanged(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect) {
    console.info(`FormExtensionAbility onSizeChanged, formId: ${formId}, newDimension: ${newDimension}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

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

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onStop?(): void--><!--Device-FormExtensionAbility-onStop?(): void-End-->

**系统能力：** SystemCapability.Ability.Form

**示例**

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

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onUpdateForm(formId: string, wantParams?: Record<string, Object>): void--><!--Device-FormExtensionAbility-onUpdateForm(formId: string, wantParams?: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | ID of the widget that requests to be updated. |
| wantParams | Record&lt;string, Object&gt; | 否 | Parameters used for the update. |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
'use static'

import { formBindingData, FormExtensionAbility, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onUpdateForm(formId: string, wantParams?: Record<string, Object>) {
    console.info('testTag', 'onUpdateForm testing');
    let param: Record<string, string> = {
      'temperature': '22c',
      'time': '22:00'
    }
    let obj2: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
    formProvider.updateForm(formId, obj2).then(() => {
      console.info(`FormExtensionAbility context updateForm`);
    }).catch((e) => {
      console.error(`FormExtensionAbility context updateForm failed, code: ${e.code} message: ${e.message}`);
    });
  }
}
```

## context

```TypeScript
context: FormExtensionContext
```

Context of the FormExtensionAbility. This context is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md). This API can be used in atomic services since API version 11.

**类型：** [FormExtensionContext](arkts-form-formextensioncontext-c-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-context: FormExtensionContext--><!--Device-FormExtensionAbility-context: FormExtensionContext-End-->

**系统能力：** SystemCapability.Ability.Form

## onAcquireFormState

```TypeScript
onAcquireFormState?: OnAcquireFormStateFn
```

Called to return a FormState object. &lt;p&gt;You must override this callback if you want this ability to return the actual form state. Otherwise, this method returns DEFAULT by default.&lt;/p&gt;

**类型：** [OnAcquireFormStateFn](arkts-form-onacquireformstatefn-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onAcquireFormState?: OnAcquireFormStateFn--><!--Device-FormExtensionAbility-onAcquireFormState?: OnAcquireFormStateFn-End-->

**系统能力：** SystemCapability.Ability.Form

## onStop

```TypeScript
onStop?: OnStopFn
```

Called when this ability breaks the last link, notifying the provider that the provider process is about to stop.

**类型：** [OnStopFn](arkts-form-onstopfn-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormExtensionAbility-onStop?: OnStopFn--><!--Device-FormExtensionAbility-onStop?: OnStopFn-End-->

**系统能力：** SystemCapability.Ability.Form

