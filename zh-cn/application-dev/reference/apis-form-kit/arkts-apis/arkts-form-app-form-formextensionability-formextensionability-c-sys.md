# FormExtensionAbility（系统接口）

```TypeScript
declare class FormExtensionAbility
```

卡片扩展类。包含卡片提供方接收创建卡片、修改可见性等的通知接口。

**起始版本：** 9

<!--Device-unnamed-declare class FormExtensionAbility--><!--Device-unnamed-declare class FormExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.Form

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止FormExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

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

<!--Device-FormExtensionAbility-onAcquireFormData?(formId: string): Record<string, Object>--><!--Device-FormExtensionAbility-onAcquireFormData?(formId: string): Record<string, Object>-End-->

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

<!--Del-->
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

<!--DelEnd-->

## onShareForm

```TypeScript
onShareForm?(formId: string): Record<string, Object>
```

卡片提供方接收卡片分享的通知接口。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormExtensionAbility-onShareForm?(formId: string): Record<string, Object>--><!--Device-FormExtensionAbility-onShareForm?(formId: string): Record<string, Object>-End-->

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

<!--Del-->
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

<!--DelEnd-->

## 附录

FormExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Ability Kit | [@ohos.ability.particleAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-particleability.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
