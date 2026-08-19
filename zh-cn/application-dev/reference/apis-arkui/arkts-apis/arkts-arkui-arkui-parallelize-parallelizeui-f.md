# ParallelizeUI

## 导入模块

```TypeScript
```

## ParallelizeUI

```TypeScript
@Builder
export declare function ParallelizeUI(
  options: ParallelOption | undefined,
  content_: CustomBuilder,
): void
```

声明式的并行化创建UI方法。options参数为undefined时，默认开启并行化创建。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ParallelizeUI(  options: ParallelOption | undefined,  content_: CustomBuilder,): void--><!--Device-unnamed-@Builderexport declare function ParallelizeUI(  options: ParallelOption | undefined,  content_: CustomBuilder,): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ParallelOption](arkts-arkui-arkui-parallelize-paralleloption-i.md) \| undefined | 是 | 使用ParallelizeUI方法创建组件时选择是否开启并行化的参数，当options参数为undefined时，默认开启并行化创建。 |
| content_ | CustomBuilder | 是 | 定义要创建的UI内容，通过尾随闭包"{...}"的形式传入。 |


## ParallelizeUI

```TypeScript
@Builder
export declare function ParallelizeUI<T>(
  options: ParallelOption | undefined,
  param: () => T,
  content_: CustomBuilderT<T>,
): void
```

声明式UI并行化创建接口。该方法支持在并行化环境中安全地使用外部定义的状态变量。options参数为undefined时，默认开启并行化创建。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ParallelizeUI<T>(  options: ParallelOption | undefined,  param: () => T,  content_: CustomBuilderT<T>,): void--><!--Device-unnamed-@Builderexport declare function ParallelizeUI<T>(  options: ParallelOption | undefined,  param: () => T,  content_: CustomBuilderT<T>,): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ParallelOption](arkts-arkui-arkui-parallelize-paralleloption-i.md) \| undefined | 是 | 使用ParallelizeUI方法创建组件时选择是否开启并行化的参数，当options参数为undefined时，默认开启并行化创建。 |
| param | () =&gt; T | 是 | 参数生成函数，用于生成content_调用时的参数。该函数会在UI线程调用，开发者可将并行创建需要用到的数据在此处进行拷贝。避免数据多线程读写引发的安全性问题。 |
| content_ | CustomBuilderT&lt;T&gt; | 是 | 定义要创建的UI内容。 |


## ParallelizeUI

```TypeScript
@Builder
export declare function ParallelizeUI<V, T>(
  options: ParallelOption | undefined,
  arr: Array<V>,
  param: (item: V, index: int) => T,
  content_: CustomBuilderT<T>
): void
```

声明式UI并行化循环创建接口。在非List和Grid中使用时，并行创建数组中定义的所有UI节点。在List或Grid容器中使用时，仅按需并行创建当前可见的节点。options参数为undefined时，默认开启并行化创建。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ParallelizeUI<V, T>(  options: ParallelOption | undefined,  arr: Array<V>,  param: (item: V, index: int) => T,  content_: CustomBuilderT<T>): void--><!--Device-unnamed-@Builderexport declare function ParallelizeUI<V, T>(  options: ParallelOption | undefined,  arr: Array<V>,  param: (item: V, index: int) => T,  content_: CustomBuilderT<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ParallelOption](arkts-arkui-arkui-parallelize-paralleloption-i.md) \| undefined | 是 | 使用ParallelizeUI方法创建组件时选择是否开启并行化的参数，当options参数为undefined时，默认开启并行化创建。 |
| arr | Array&lt;V&gt; | 是 | 数据源，为Array类型的数组。 |
| param | (item: V, index: int) =&gt; T | 是 | 参数生成函数，用于生成content_调用时的参数。该函数会在UI线程调用，开发者可将并行创建需要用到的数据在此处进行拷贝。避免数据多线程读写 引发的安全性问题。<br/>说明：<br/>- item是当前数据项，index是数据项索引值。 |
| content_ | CustomBuilderT&lt;T&gt; | 是 | 定义要创建的UI内容。param参数为param函数调用后返回的对象。 |

