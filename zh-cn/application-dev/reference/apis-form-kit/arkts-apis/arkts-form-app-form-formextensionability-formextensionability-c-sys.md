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

## onAcquireFormData

```TypeScript
onAcquireFormData?(formId: string): Record<string, Object>
```

卡片提供方接收卡片请求自定义数据的通知接口。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| object | 卡片的自定义数据，由开发者自行决定传入的键值对。<br>**适用版本：** 10 |
| Record&lt;string, Object&gt; | 卡片的自定义数据，由开发者自行决定传入的键值对。<br>**适用版本：** 11 |

**示例**

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onAcquireFormData(formId: string) {
    console.info(`FormExtensionAbility onAcquireFormData, formId: ${formId}`);
    let wantParams: Record<string, Object> = {
      'temperature': '20',
      'time': '2022-8-8 09:59',
    };
    return wantParams;
  }
}
```

## onShareForm

```TypeScript
onShareForm?(formId: string): Record<string, Object>
```

卡片提供方接收卡片分享的通知接口。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| object | 卡片要分享的数据，由开发者自行决定传入的键值对。<br>**适用版本：** 9 - 10 |
| Record&lt;string, Object&gt; | 卡片要分享的数据，由开发者自行决定传入的键值对。<br>**适用版本：** 11 |

**示例**

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onShareForm(formId: string) {
    console.info(`FormExtensionAbility onShareForm, formId: ${formId}`);
    let wantParams: Record<string, Object> = {
      'temperature': '20',
      'time': '2022-8-8 09:59',
    };
    return wantParams;
  }
}
```
