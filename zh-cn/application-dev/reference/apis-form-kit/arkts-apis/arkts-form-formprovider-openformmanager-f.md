# openFormManager

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## openFormManager

```TypeScript
function openFormManager(want: Want): void
```

打开当前应用的卡片管理页面。适用于卡片管理场景，例如预览当前应用所有可以加桌的卡片、添加卡片到负一屏或桌面等。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function openFormManager(want: Want): void--><!--Device-formProvider-function openFormManager(want: Want): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 打开卡片管理页面的请求中的want参数，需包含以下字段。 <br>bundleName: 卡片所属应用的包名。 <br>abilityName: 卡片所属的ability名称。 <br>parameters: <br>- ohos.extra.param.key.form_dimension: [卡片尺寸](arkts-form-forminfo-formdimension-e.md)。 <br>- ohos.extra.param.key.form_name: 卡片名称。 <br>- ohos.extra.param.key.module_name: 卡片所属的模块名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

const want: Want = {
  bundleName: 'com.example.formbutton',
  abilityName: 'EntryFormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  },
};
try {
  formProvider.openFormManager(want);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { formProvider } from '@kit.FormKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

const want: Want = {
  bundleName: 'com.example.formbutton',
  abilityName: 'EntryFormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  } as Record<string,RecordData>
};
try {
  formProvider.openFormManager(want);
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

