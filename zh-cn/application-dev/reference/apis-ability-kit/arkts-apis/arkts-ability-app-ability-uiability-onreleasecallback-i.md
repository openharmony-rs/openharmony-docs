# OnReleaseCallback

注册通用组件服务端Stub（桩）断开监听通知的回调函数类型。

**起始版本：** 9

<!--Device-unnamed-export interface OnReleaseCallback--><!--Device-unnamed-export interface OnReleaseCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
import { Callee, Caller, OnReleaseCallback, OnRemoteStateChangeCallback, CalleeCallback } from '@kit.AbilityKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
(msg: string): void
```

定义OnRelease的回调函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnReleaseCallback-(msg: string): void--><!--Device-OnReleaseCallback-(msg: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msg | string | 是 | 用于传递释放消息。 |

