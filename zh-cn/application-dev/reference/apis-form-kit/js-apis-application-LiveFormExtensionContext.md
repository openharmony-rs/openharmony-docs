# LiveFormExtensionContext

LiveFormExtensionContext是[LiveFormExtensionAbility](./js-apis-app-form-LiveFormExtensionAbility.md)的上下文，继承自[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口仅可在Stage模型下使用。

## 导入模块
```ts
import { LiveFormExtensionAbility } from '@kit.FormKit';
```

## LiveFormExtensionContext

LiveFormExtensionContext提供允许访问特定于LiveFormExtensionAbility资源的能力，继承自[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

## LiveFormExtensionContext.startAbilityByLiveForm

 startAbilityByLiveForm(want: Want): Promise\<void>

拉起一个应用的Ability。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                    | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 包含bundleName，abilityName以及用户自定参数用于拉起Ability。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported due to limited device capabilities. |
| 16500050 | IPC connection error.                                        |
| 16500100 | Failed to obtain the configuration information.              |
| 16501000 | An internal functional error occurred.                       |
| 16501011 | The form can not support this operation.                     |

**示例：**

ArkTS-Dyn示例：

```ts
import { LiveFormExtensionAbility } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyFormExtensionAbility extends LiveFormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 当触发卡片message事件时，执行startAbility
    console.info(`FormExtensionAbility onFormEvent, formId:${formId}, message:${message}`);
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.formstartability',
      abilityName: 'EntryAbility',
      parameters: {
        'message': message
      }
    };
    this.context.startAbilityByLiveForm(want).then(() => {
      console.info('StartAbility Success');
    }).catch((error: BusinessError) => {
      console.error(`StartAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
};
```

ArkTS-Sta示例：

```ts
'use static'

import { LiveFormExtensionAbility } from '@kit.FormKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class MyFormExtensionAbility extends LiveFormExtensionAbility {
  onFormEvent(formId: string, message: string) {
    // 当触发卡片message事件时，执行startAbility
    console.info(`FormExtensionAbility onFormEvent, formId:${formId}, message:${message}`);
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.formstartability',
      abilityName: 'EntryAbility',
      parameters: {
        'message': message
      } as Record<string,RecordData>
    };
    this.context.startAbilityByLiveForm(want).then(() => {
      console.info('StartAbility Success');
    }).catch((err) => {
      let error=err as BusinessError;
      console.error(`StartAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

