# InvokeMode（系统接口）

```TypeScript
export enum InvokeMode
```

枚举函数调用方式。表示API调用是如何执行的，以及它的结果是如何交付的。

**起始版本：** 26.1.0

<!--Device-power-export enum InvokeMode--><!--Device-power-export enum InvokeMode-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

## ASYNC

```TypeScript
ASYNC = 1
```

异步调用。调用者立即返回，结果通过Promise传递。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeMode-ASYNC = 1--><!--Device-InvokeMode-ASYNC = 1-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

## SYNC

```TypeScript
SYNC = 0
```

同步调用。调用方阻塞，直到API返回结果。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InvokeMode-SYNC = 0--><!--Device-InvokeMode-SYNC = 0-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。
