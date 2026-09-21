# FormExtensionAbility

```TypeScript
declare class FormExtensionAbility
```

卡片扩展类。包含卡片提供方接收创建卡片、修改可见性等的通知接口。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
```

## onAcquireFormState

```TypeScript
onAcquireFormState?(want: Want): formInfo.FormState
```

卡片提供方接收查询卡片状态通知接口。当卡片使用方（如桌面）需要获取卡片当前状态（如卡片是否可用、是否需要更新等）时，会调用此方法，该方法可重写。默认返回卡片初始状态（该方法可以选择性重写）。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | want表示获取卡片状态的描述。描述包括Bundle名称、能力名称、模块名称、卡片名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [formInfo.FormState](arkts-form-forminfo-formstate-e.md) | [formInfo.FormState枚举，表示卡片当前的状态。](../../apis-form-kit/arkts-apis/arkts-form-app-form-forminfo.md) |

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

卡片提供方接收创建卡片的通知接口。需要注意：FormExtensionAbility创建后10秒内无操作将会被清理，请避免在回调中执行耗时操作。

- 必须调用[formBindingData.createFormBindingData()](arkts-form-formbindingdata-createformbindingdata-f.md)创建卡片数据对象。  
- 调用顺序：先创建数据对象（如dataObj1），再调用formBindingData.createFormBindingData(dataObj1)创建FormBindingData对象。  
- 返回要求：必须返回FormBindingData对象，卡片要显示的数据通过参数传入。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 当前卡片相关的Want类型信息，其中Want中的parameters为自定义取值，取值可以包含[卡片参数枚举](arkts-form-forminfo-formparam-e.md)中的一个或多个，如卡片ID、卡片名称、卡片样式等。这些卡片信息必须作为持久数据进行管理，以便后续更新和删除卡片。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [formBindingData.FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | formBindingData.FormBindingData对象，卡片要显示的数据。可通过[formBindingData.createFormBindingData()](arkts-form-formbindingdata-createformbindingdata-f.md)创建。 |

**示例**

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

卡片提供方收到卡片使用方将临时卡片转常态卡片的通知接口。临时卡片、常态卡片是卡片使用方的概念，其中：临时卡片是短期存在的，在特定事件或用户行为后显示，完成后自动消失。常态卡片具有持久性，在用户主动清除或更改前将一直保留；日常开发的功能卡片均归属此类。在当前版本，卡片使用方不使用临时卡片。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 请求转换为常态的卡片标识。 |

**示例**

```TypeScript
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
onChangeFormVisibility(newStatus: Record<string, number>): void
```

卡片提供方接收修改可见性的通知接口。当卡片在桌面上的可见性发生变化（如卡片被遮挡、移出屏幕等）时，会触发此回调。开发者可以在此优化卡片的资源占用或暂停不必要的更新操作，并通过formProvider.updateForm()更新卡片数据。仅当FormExtensionAbility存活时才会触发此回调。该接口仅对系统应用生效，且需要将formVisibleNotify配置为true。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newStatus | Record&lt;string, number&gt; | 是 | 请求修改的卡片标识和可见状态。<br>**说明：** number参数是取值范围[0, 2]的整数，0是未知类型，1是可见状态，2是不可见状态。超出范围的值无效，不产生任何效果。该接口仅对系统应用生效，且需要将formVisibleNotify配置为true。<br>详细参考 [formInfo.VisibilityType](arkts-form-forminfo-visibilitytype-e.md)<br>**适用版本：** 11 |

**示例**

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

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

当系统配置项变更时调用，仅当FormExtensionAbility存活时才会触发onConfigurationUpdate回调。<!--Del-->此外，从API version 20开始，对于系统应用，当系统语言发生变更时会拉起FormExtensionAbility再触发onConfigurationUpdate回调。<!--DelEnd-->

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newConfig | [Configuration](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md) | 是 | 表示需要更新的配置信息。 |

**示例**

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

## onFormEvent

```TypeScript
onFormEvent(formId: string, message: string): void
```

卡片提供方接收处理卡片事件的通知接口，例如卡片使用方触发的自定义事件。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 请求触发事件的卡片标识。 |
| message | string | 是 | 事件消息，用于传递卡片事件的具体信息。消息内容由开发者自定义，通常为JSON格式字符串或特定标识符，用于标识事件类型或传递事件数据。 |

**示例**

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

当卡片位置发生变化时，触发该回调。开发者可以根据新的位置信息调整卡片的展示或预加载相关内容。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 发生位置变化的卡片标识。 |
| newFormLocation | [formInfo.FormLocation](arkts-form-forminfo-formlocation-e.md) | 是 | 卡片最新位置的枚举值，表示卡片当前所在的位置（如桌面、卡片中心等）。 |

**示例**

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

卡片提供方接收销毁卡片的通知接口。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 请求销毁的卡片标识。 |

**示例**

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

当卡片大小发生变化时（如用户调整卡片尺寸），触发该回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 发生大小变化的卡片标识。 |
| newDimension | [formInfo.FormDimension](arkts-form-forminfo-formdimension-e.md) | 是 | 卡片尺寸，例如 Dimension_1_2，表示 1 x 2 卡片。 |
| newRect | [formInfo.Rect](arkts-form-forminfo-rect-i.md) | 是 | 卡片位置信息，包括卡片左上角顶点的xy坐标和卡片的宽高。 |

**示例**

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

当卡片提供方的卡片进程退出时，触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

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

卡片提供方接收携带参数的更新卡片的通知接口。获取最新数据后调用formProvider的[updateForm](arkts-form-formprovider-updateform-f.md)接口刷新卡片数据。需要传入formId和FormBindingData对象，可通过formBindingData.createFormBindingData()创建数据对象。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 请求更新的卡片标识。 |
| wantParams | Record&lt;string, Object&gt; | 否 | 更新参数，用于携带卡片更新的额外信息。当需要传递自定义参数更新卡片时传入，不传入时为undefined。支持的参数包括：ohos.extra.param.key.host_bg_inverse_color（是否启用宿主背景反色）等。 |

**示例**

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

FormExtensionAbility的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

**类型：** [FormExtensionContext](arkts-form-formextensioncontext-c-sys.md)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form
