# @ohos.app.form.FormExtensionAbility (FormExtensionAbility)(系统接口)

FormExtensionAbility为卡片扩展模块，提供卡片创建、销毁、刷新等生命周期回调。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口仅可在Stage模型下使用。
> - 当前页面仅包含本模块的系统接口，其他公共接口参见[@ohos.app.form.FormExtensionAbility (FormExtensionAbility)](./js-apis-app-form-formExtensionAbility.md)。

## 导入模块

```ts
import { FormExtensionAbility } from '@kit.FormKit';
```

## 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 名称    | 类型                                                         | 只读 | 可选 | 说明                                                         |
| ------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| onShareForm      | [onShareFormFn](#onshareformfn23)          | 否   | 是  | 卡片提供方接收卡片分享的通知接口。 |
| onAcquireFormData | [onAcquireFormDataFn](#onacquireformdatafn23) | 否   | 是   | 卡片提供方接收卡片请求自定义数据的通知接口。 |

## onShareForm

onShareForm?(formId: string): Record\<string, Object>

卡片提供方接收卡片分享的通知接口。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型                   | 说明                                         |
| ---------------------- | -------------------------------------------- |
| Record\<string, Object> | 卡片要分享的数据，由开发者自行决定传入的键值对。 |

**示例：**

```ts
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
};
```

## onAcquireFormData<sup>10+</sup>

onAcquireFormData?(formId: string): Record\<string, Object>

卡片提供方接收卡片请求自定义数据的通知接口。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型                   | 说明                                         |
| ---------------------- | -------------------------------------------- |
| Record\<string, Object> | 卡片的自定义数据，由开发者自行决定传入的键值对。 |

**示例：**

```ts
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
};
```
## OnShareFormFn<sup>23+</sup>

type OnShareFormFn = (formId: string) => Record\<string, Object>

卡片提供方接收卡片分享的通知接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| formId | string | 是   | 卡片标识。 |

**返回值：**

| 类型                    | 说明                                             |
| ----------------------- | ------------------------------------------------ |
| Record\<string, Object> | 卡片要分享的数据，由开发者自行决定传入的键值对。 |

**示例：**

```ts
'use static'

import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onShareFormFn(formId: string) {
    console.info(`FormExtensionAbility onShareForm, formId: ${formId}`);
    let wantParams: Record<string, Object> = {
      'temperature': '20',
      'time': '2022-8-8 09:59',
    };
    return wantParams;
  }
}
```

## OnAcquireFormDataFn<sup>23+</sup>

type OnAcquireFormDataFn = (formId: string) => Record\<string, Object>

卡片提供方接收卡片请求自定义数据的通知接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| formId | string | 是   | 卡片标识。 |

**返回值：**

| 类型                    | 说明                                             |
| ----------------------- | ------------------------------------------------ |
| Record\<string, Object> | 卡片的自定义数据，由开发者自行决定传入的键值对。 |

**示例：**

```ts
'use static'

import { FormExtensionAbility } from '@kit.FormKit';

export default class MyFormExtensionAbility extends FormExtensionAbility {
  onAcquireFormDataFn(formId: string) {
    console.info(`FormExtensionAbility onAcquireFormData, formId: ${formId}`);
    let wantParams: Record<string, Object> = {
      'temperature': '20',
      'time': '2022-8-8 09:59',
    };
    return wantParams;
  }
}
```
