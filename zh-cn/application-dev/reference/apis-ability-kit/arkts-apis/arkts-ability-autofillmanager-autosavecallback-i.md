# AutoSaveCallback

当保存请求完成时所触发的回调接口。

**起始版本：** 11

<!--Device-autoFillManager-export interface AutoSaveCallback--><!--Device-autoFillManager-export interface AutoSaveCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

<a id="onfailure"></a>
## onFailure

```TypeScript
onFailure(): void
```

当保存请求失败时，该回调被调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AutoSaveCallback-onFailure(): void--><!--Device-AutoSaveCallback-onFailure(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

参见[autoFillManager.requestAutoSave](#autofillmanagerrequestautosave)。

<a id="onsuccess"></a>
## onSuccess

```TypeScript
onSuccess(): void
```

当保存请求成功时，该回调被调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AutoSaveCallback-onSuccess(): void--><!--Device-AutoSaveCallback-onSuccess(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例：**

参见[autoFillManager.requestAutoSave](#autofillmanagerrequestautosave)。

