# AutoSaveCallback

当保存请求完成时所触发的回调接口。

**起始版本：** 23

<!--Device-autoFillManager-export interface AutoSaveCallback--><!--Device-autoFillManager-export interface AutoSaveCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

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

**示例**

参见autoFillManager.requestAutoSave。

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

**示例**

参见autoFillManager.requestAutoSave。

## onFailure

```TypeScript
onFailure: OnFailureFn
```

当保存请求失败时，该回调被调用。

**类型：** [OnFailureFn](arkts-ability-autofillmanager-onfailurefn-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AutoSaveCallback-onFailure: OnFailureFn--><!--Device-AutoSaveCallback-onFailure: OnFailureFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onSuccess

```TypeScript
onSuccess: OnSuccessFn
```

当保存请求成功时，该回调被调用。

**类型：** [OnSuccessFn](arkts-ability-autofillmanager-onsuccessfn-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AutoSaveCallback-onSuccess: OnSuccessFn--><!--Device-AutoSaveCallback-onSuccess: OnSuccessFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

