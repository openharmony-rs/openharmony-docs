# Job(定义ArkTS的任务执行结果)

表示任务结果的句柄，用于等待任务完成并获取返回值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class Job--><!--Device-unnamed-export class Job-End-->

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

<!--Device-Job-Await(): T--><!--Device-Job-Await(): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 任务的返回值，类型与创建任务时指定的泛型类型一致。 |

