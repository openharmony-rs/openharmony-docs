# @arkts.collections

本模块提供的ArkTS容器集，可以用于并发场景下的高性能数据传递。功能与JavaScript内建的对应容器类似，但ArkTS容器实例无法通过`"."`或者`"[]"`添加或更新属性。ArkTS容器在多个并发实例间传递时，其默认行为是引用传递，支持多个并发实例可以同时操作同一个容器实例。另外，也支持拷贝传递，即每个并发实例持有一个ArkTS容器实例。ArkTS容器并不是线程安全的，内部使用了fail-fast（快速失败）机制：当检测多个并发实例同时对容器进行结构性改变时，会触发异常。因此，在多线程读写容器时，容器使用方需要使用ArkTS提供的异步锁机制保证ArkTS容器的安全访问。当前ArkTS容器集主要包含以下几种容器：[Array](arkts-collections.md),[Map](arkts-collections.md), [Set](arkts-collections.md), TypedArray([Int8Array](arkts-collections.md),[Uint8Array](arkts-collections.md),[Int16Array](arkts-collections.md),[Uint16Array](arkts-collections.md),[Int32Array](arkts-collections.md),[Uint32Array](arkts-collections.md),[Uint8ClampedArray](arkts-collections.md) and [Float32Array](arkts-collections.md)),[ArrayBuffer](arkts-collections.md),[BitVector](arkts-collections.md), and [ConcatArray](arkts-collections.md).
> **说明**  
>  
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。

**起始版本：** 12

<!--Device-unnamed-declare namespace collections--><!--Device-unnamed-declare namespace collections-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { collections } from '@kit.ArkTS';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Array](arkts-arkts-collections-array-c.md) | 一种线性数据结构，底层基于数组实现，可以在ArkTS上并发实例间传递。推荐使用引用传递以提升传递性能。 > **说明**  >  > - 本模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > 本节使用以下标识来表示泛型的使用：  - T：Type，支持[Sendable支持的数据类型](../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。**装饰器**：\@Sendable |
| [ArrayBuffer](arkts-arkts-collections-arraybuffer-c.md) | ArkTS TypedArray（[Int8Array](arkts-collections.md)、[Uint8Array](arkts-collections.md)、[Int16Array](arkts-collections.md)、[Uint16Array](arkts-collections.md)、[Int32Array](arkts-collections.md)、[Uint32Array](arkts-collections.md)、[Uint8ClampedArray](arkts-collections.md)、[Float32Array](arkts-collections.md)）的底层数据结构。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > **装饰器类型**：\@Sendable |
| [BitVector](arkts-arkts-collections-bitvector-c.md) | 一种线性数据结构，底层基于数组实现。BitVector 中存储的元素为 bit 值，能够存储和处理 bit 级别的操作。 @Sendable |
| [Float32Array](arkts-arkts-collections-float32array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。 @Sendable |
| [Int16Array](arkts-arkts-collections-int16array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > **装饰器类型：** \@Sendable |
| [Int32Array](arkts-arkts-collections-int32array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > **装饰器**：\@Sendable |
| [Int8Array](arkts-arkts-collections-int8array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > **装饰器类型**：\@Sendable |
| [Map](arkts-arkts-collections-map-c.md) | 一种基于键值对存储的非线性数据结构。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > 本节使用以下标识符来表示泛型的使用：  - K：键。  - V：值。K和V类型都需为[Sendable支持的数据类型](../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。**装饰器类型**：\@Sendable |
| [Set](arkts-arkts-collections-set-c.md) | 一种非线性数据结构。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > 本节使用以下标识来表示泛型的使用：  - T：Type，支持[Sendable支持的数据类型](../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。**装饰器类型：** \@Sendable |
| [Uint16Array](arkts-arkts-collections-uint16array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > **装饰器类型**：\@Sendable |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > **装饰器**：\@Sendable |
| [Uint8Array](arkts-arkts-collections-uint8array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > **装饰器类型：** \@Sendable |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md)实现。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > **装饰器类型**：\@Sendable |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConcatArray](arkts-arkts-collections-concatarray-i.md) | 该接口定义了支持数组连接操作的对象，并继承了`ISendable`接口，使其兼具高效数组拼接和跨线程传递能力。 > **说明**  >  > - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  > 文档中存在泛型的使用，涉及以下泛型标记符：  - T：Type，支持[Sendable支持的数据类型](../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ArrayFromMapFn](arkts-arkts-collections-arrayfrommapfn-t.md) | ArkTS Array归约函数类型，被Array类的'from'接口使用。 |
| [ArrayPredicateFn](arkts-arkts-collections-arraypredicatefn-t.md) | ArkTS Array归约函数类型，被Array类的'some'和'every'接口使用，用来判断数组元素是否满足测试条件。 |
| [ArrayReduceCallback](arkts-arkts-collections-arrayreducecallback-t.md) | ArkTS Array归约函数类型，被Array类的'reduceRight'接口使用。 |
| [ISendable](arkts-arkts-collections-isendable-t.md) | ISendable是所有Sendable类型（除`null`和`undefined`）的父类型。自身没有任何必须的方法和属性。 |
| [TypedArrayCompareFn](arkts-arkts-collections-typedarraycomparefn-t.md) | ArkTS TypedArray排序函数类型。 |
| [TypedArrayForEachCallback](arkts-arkts-collections-typedarrayforeachcallback-t.md) | ArkTS TypedArray遍历函数类型。 |
| [TypedArrayFromMapFn](arkts-arkts-collections-typedarrayfrommapfn-t.md) | ArkTS TypedArray映射函数类型。 |
| [TypedArrayMapCallback](arkts-arkts-collections-typedarraymapcallback-t.md) | ArkTS TypedArray转换映射函数类型。 |
| [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md) | ArkTS TypedArray断言测试函数类型。 |
| [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md) | ArkTS TypedArray归约函数类型。 |

