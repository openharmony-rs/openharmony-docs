# CompletableJob(定义ArkTS的任务执行结果)

继承自Job的可完成任务，允许手动设置任务的完成或失败状态。

**继承/实现关系：** CompletableJob extends Job<T>

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class CompletableJob--><!--Device-unnamed-export class CompletableJob-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## Await

```TypeScript
Await(): T
```

等待任务完成并返回结果。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletableJob-Await(): T--><!--Device-CompletableJob-Await(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 任务的返回值，类型与创建任务时指定的泛型类型一致。 |

## constructor

```TypeScript
constructor()
```

构造一个CompletableJob实例，开发者可通过finish和fail方法设置任务结果。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletableJob-constructor()--><!--Device-CompletableJob-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## fail

```TypeScript
fail(): void
```

将任务状态置为失败，并设置一个空的Error。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletableJob-fail(): void--><!--Device-CompletableJob-fail(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## fail

```TypeScript
fail(error: Error): void
```

将任务状态置为失败，并将失败原因设置为指定的Error。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletableJob-fail(error: Error): void--><!--Device-CompletableJob-fail(error: Error): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | Error | 是 | 任务失败时设置的Error。 |

## finish

```TypeScript
finish(): void
```

将任务状态置为完成态，并将值设置为undefined。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletableJob-finish(): void--><!--Device-CompletableJob-finish(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## finish

```TypeScript
finish<T>(value: T): void
```

将任务状态置为完成态，并将值设置为指定值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CompletableJob-finish<T>(value: T): void--><!--Device-CompletableJob-finish<T>(value: T): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 任务完成时设置的值。 |

