# reloadForms

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## reloadForms

```TypeScript
function reloadForms(context: UIAbilityContext, moduleName: string, abilityName: string, formName: string): Promise<int>
```

对于当前应用中moduleName、abilityName、formName相同的卡片，每次加桌会分配不同的卡片ID。卡片提供方可通过本接口批量更新这些卡片。与reloadAllForms相比，本接口可精确指定更新特定配置的卡片， 适用于仅需更新特定卡片场景；reloadAllForms更新当前应用所有已加桌卡片，适用于全局刷新场景。本接口在应用主进程中调用，通知FormExtension进程进行批量更新，仅支持在 [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)中使用，使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function reloadForms(context: UIAbilityContext, moduleName: string, abilityName: string, formName: string): Promise<int>--><!--Device-formProvider-function reloadForms(context: UIAbilityContext, moduleName: string, abilityName: string, formName: string): Promise<int>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | 是 | [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)的上下文，用于校验应用身份。 |
| moduleName | string | 是 | 指定卡片的moduleName，需与 [form_config.json](../../../form/arkts-ui-widget-configuration.md#配置文件字段说明)中配置的module名称一致。需与abilityName、 formName配合使用，三者必须同时匹配才能定位到对应卡片。 |
| abilityName | string | 是 | 指定卡片的abilityName，需与 [form_config.json](../../../form/arkts-ui-widget-configuration.md#配置文件字段说明)中配置的ability名称一致。 |
| formName | string | 是 | 指定卡片在[form_config.json](../../../form/arkts-ui-widget-configuration.md#配置文件字段说明)中配置的卡 片名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象。返回请求更新卡片的数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { formProvider } from '@kit.FormKit';

try {
  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
  let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  // 请开发者替换为实际请求更新的卡片信息
  let moduleName: string = 'entry';
  let abilityName: string = 'EntryFormAbility';
  let formName: string = 'formName';
  formProvider.reloadForms(context, moduleName, abilityName, formName).then((reloadNum: number) => {
    console.info(`reloadForms success, reload number: ${reloadNum}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { formProvider } from '@kit.FormKit';

try {
  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
  let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  // 请开发者替换为实际请求更新的卡片信息
  let moduleName: string = 'entry';
  let abilityName: string = 'EntryFormAbility';
  let formName: string = 'formName';
  formProvider.reloadForms(context, moduleName, abilityName, formName).then((reloadNum: int) => {
    console.info(`reloadForms success, reload number: ${reloadNum}`);
  }).catch((error) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

