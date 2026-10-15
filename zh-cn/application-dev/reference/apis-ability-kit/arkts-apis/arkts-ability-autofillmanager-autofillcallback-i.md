# AutoFillCallback

```TypeScript
export interface AutoFillCallback
```

自动填充回调。

**起始版本：** 26.0.0

<!--Device-autoFillManager-export interface AutoFillCallback--><!--Device-autoFillManager-export interface AutoFillCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## onFailure

```TypeScript
onFailure: OnFillFailureFn
```

当自动填充请求失败时，该回调被调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-AutoFillCallback-onFailure: OnFillFailureFn--><!--Device-AutoFillCallback-onFailure: OnFillFailureFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例**

参见autoFillManager.requestAutoFill。

## onSuccess

```TypeScript
onSuccess: OnFillSuccessFn
```

当自动填充请求成功时，该回调被调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-AutoFillCallback-onSuccess: OnFillSuccessFn--><!--Device-AutoFillCallback-onSuccess: OnFillSuccessFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**示例**

参见autoFillManager.requestAutoFill。
