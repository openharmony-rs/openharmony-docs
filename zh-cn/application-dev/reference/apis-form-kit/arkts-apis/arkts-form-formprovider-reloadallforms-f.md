# reloadAllForms

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## reloadAllForms

```TypeScript
function reloadAllForms(context: UIAbilityContext): Promise<int>
```

在应用主进程通过本接口可以通知FormExtension进程批量更新当前应用下已经加桌的所有卡片，仅支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)中调用，使用Promise异步回 调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function reloadAllForms(context: UIAbilityContext): Promise<int>--><!--Device-formProvider-function reloadAllForms(context: UIAbilityContext): Promise<int>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | 是 | [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)的上下文，用于校验应用身份。 |

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
  formProvider.reloadAllForms(context).then((reloadNum: number) => {
    console.info(`reloadAllForms success, reload number: ${reloadNum}`);
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
  formProvider.reloadAllForms(context).then((reloadNum: int) => {
    console.info(`reloadAllForms success, reload number: ${reloadNum}`);
  }).catch((error) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

