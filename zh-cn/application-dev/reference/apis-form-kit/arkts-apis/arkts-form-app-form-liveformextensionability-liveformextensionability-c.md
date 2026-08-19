# LiveFormExtensionAbility

Interactive widget extension class. It provides APIs for the widget provider to receive notifications about widget creation and destruction.

**继承/实现关系：** LiveFormExtensionAbility extends ExtensionAbility

**起始版本：** 23

<!--Device-unnamed-declare class LiveFormExtensionAbility--><!--Device-unnamed-declare class LiveFormExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';
```

## onLiveFormCreate

```TypeScript
onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void
```

Called after the UI content of **LiveFormExtensionAbility** is created.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LiveFormExtensionAbility-onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void--><!--Device-LiveFormExtensionAbility-onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| liveFormInfo | [LiveFormInfo](arkts-form-app-form-liveformextensionability-liveforminfo-i.md) | 是 | Interactive widget information, including the widget ID. |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | 是 | UI information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';

const TAG: string = '[testTag] LiveFormExtAbility';

export default class LiveFormExtAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    console.info(TAG, `onLiveFormCreate, formId: ${liveFormInfo.formId}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { UIExtensionContentSession } from '@kit.AbilityKit';
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';

const TAG: string = '[testTag] LiveFormExtAbility';

export default class LiveFormExtAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    console.info(TAG, `onLiveFormCreate, formId: ${liveFormInfo.formId}`);
  }
}
```

## onLiveFormDestroy

```TypeScript
onLiveFormDestroy(liveFormInfo: LiveFormInfo): void
```

Called to clear resources when this **LiveFormExtensionAbility** is destroyed.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-LiveFormExtensionAbility-onLiveFormDestroy(liveFormInfo: LiveFormInfo): void--><!--Device-LiveFormExtensionAbility-onLiveFormDestroy(liveFormInfo: LiveFormInfo): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| liveFormInfo | [LiveFormInfo](arkts-form-app-form-liveformextensionability-liveforminfo-i.md) | 是 | Interactive widget information, including the widget ID. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';

const TAG: string = '[testTag] LiveFormExtAbility';

export default class LiveFormExtAbility extends LiveFormExtensionAbility {
  onLiveFormDestroy(liveFormInfo: LiveFormInfo) {
    console.info(TAG, `onLiveFormDestroy, liveFormInfo: ${liveFormInfo.formId}`);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';

const TAG: string = '[testTag] LiveFormExtAbility';

export default class LiveFormExtAbility extends LiveFormExtensionAbility {
  onLiveFormDestroy(liveFormInfo: LiveFormInfo) {
    console.info(TAG, `onLiveFormDestroy, formId: ${liveFormInfo.formId}`);
  }
}
```

## context

```TypeScript
context: LiveFormExtensionContext
```

Context of the **LiveFormExtensionAbility**. This context is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

**类型：** [LiveFormExtensionContext](arkts-form-liveformextensioncontext-c.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LiveFormExtensionAbility-context: LiveFormExtensionContext--><!--Device-LiveFormExtensionAbility-context: LiveFormExtensionContext-End-->

**系统能力：** SystemCapability.Ability.Form

## liveFormContext

```TypeScript
liveFormContext: LiveFormExtensionContext
```

Context of the **LiveFormExtensionAbility**. This context is inherited from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

**类型：** [LiveFormExtensionContext](arkts-form-liveformextensioncontext-c.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiveFormExtensionAbility-liveFormContext: LiveFormExtensionContext--><!--Device-LiveFormExtensionAbility-liveFormContext: LiveFormExtensionContext-End-->

**系统能力：** SystemCapability.Ability.Form

