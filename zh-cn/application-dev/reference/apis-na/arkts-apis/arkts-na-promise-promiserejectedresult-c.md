# PromiseRejectedResult(定义ArkTS的异步操作)

表示已拒绝Promise的结果。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class PromiseRejectedResult--><!--Device-unnamed-export class PromiseRejectedResult-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

使用默认Error构造PromiseRejectedResult。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseRejectedResult-constructor()--><!--Device-PromiseRejectedResult-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(reason: Error)
```

使用指定原因构造PromiseRejectedResult。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseRejectedResult-constructor(reason: Error)--><!--Device-PromiseRejectedResult-constructor(reason: Error)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | Error | 是 | 拒绝原因。 |

## reason

```TypeScript
reason: Error
```

Promise被拒绝的原因。

**类型：** Error

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseRejectedResult-reason: Error--><!--Device-PromiseRejectedResult-reason: Error-End-->

**系统能力：** SystemCapability.Utils.Lang

## status

```TypeScript
status: string
```

Promise的状态。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseRejectedResult-status: string--><!--Device-PromiseRejectedResult-status: string-End-->

**系统能力：** SystemCapability.Utils.Lang

