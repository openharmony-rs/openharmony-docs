# PromiseFulfilledResult(定义ArkTS的异步操作)

表示已解析Promise的结果。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class PromiseFulfilledResult--><!--Device-unnamed-export class PromiseFulfilledResult-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

构造一个空的PromiseFulfilledResult。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseFulfilledResult-constructor()--><!--Device-PromiseFulfilledResult-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(value: T)
```

使用指定值构造PromiseFulfilledResult。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseFulfilledResult-constructor(value: T)--><!--Device-PromiseFulfilledResult-constructor(value: T)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 已解析的值。 |

## status

```TypeScript
status: string
```

Promise的状态。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseFulfilledResult-status: string--><!--Device-PromiseFulfilledResult-status: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## value

```TypeScript
value: T
```

已解析Promise的值。

**类型：** T

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromiseFulfilledResult-value: T--><!--Device-PromiseFulfilledResult-value: T-End-->

**系统能力：** SystemCapability.Utils.Lang

