# @arkts.collections

本模块提供的ArkTS容器集，可以用于并发场景下的高性能数据传递。功能与JavaScript内建的对应容器类似，但ArkTS容器实例无法通过`"."`或者`"[]"`添加或更新属性。
ArkTS容器在多个并发实例间传递时，其默认行为是引用传递，支持多个并发实例可以同时操作同一个容器实例。另外，也支持拷贝传递，即每个并发实例持有一个ArkTS容器实例。
ArkTS容器并不是线程安全的，内部使用了fail-fast（快速失败）机制：当检测多个并发实例同时对容器进行结构性改变时，会触发异常。因此，在多线程读写容器时，容器使用方需要使用ArkTS提供的异步锁机制保证ArkTS容器的安全访问。
当前ArkTS容器集主要包含以下几种容器：[Array](arkts-collections.md#collections),
[Map](arkts-collections.md#collections), [Set](arkts-collections.md#collections), TypedArray
([Int8Array](arkts-collections.md#collections),
[Uint8Array](arkts-collections.md#collections),
[Int16Array](arkts-collections.md#collections),
[Uint16Array](arkts-collections.md#collections),
[Int32Array](arkts-collections.md#collections),
[Uint32Array](arkts-collections.md#collections),
[Uint8ClampedArray](arkts-collections.md#collections) and
[Float32Array](arkts-collections.md#collections)),
[ArrayBuffer](arkts-collections.md#collections),
[BitVector](arkts-collections.md#collections), and
[ConcatArray](arkts-collections.md#collections).

> **说明**
>
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Array](arkts-arkts-collections-array-c.md) | 一种线性数据结构，底层基于数组实现，可以在ArkTS上并发实例间传递。<br/>推荐使用引用传递以提升传递性能。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 本模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; 本节使用以下标识来表示泛型的使用：<br/><br/>- T：Type，支持<br/>[Sendable支持的数据类型](../../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。<br/>**装饰器**：\@Sendable<br/> |
| [ArrayBuffer](arkts-arkts-collections-arraybuffer-c.md) | ArkTS TypedArray（[Int8Array](arkts-collections.md#collections)、<br/>[Uint8Array](arkts-collections.md#collections)、<br/>[Int16Array](arkts-collections.md#collections)、<br/>[Uint16Array](arkts-collections.md#collections)、<br/>[Int32Array](arkts-collections.md#collections)、<br/>[Uint32Array](arkts-collections.md#collections)、<br/>[Uint8ClampedArray](arkts-collections.md#collections)、<br/>[Float32Array](arkts-collections.md#collections)）的底层数据结构。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器类型**：\@Sendable<br/> |
| [BitVector](arkts-arkts-collections-bitvector-c.md) | 一种线性数据结构，底层基于数组实现。BitVector 中存储的元素为 bit 值，能够存储和处理 bit 级别的操作。<br/><br/>&gt; **NOTE**<br/>&gt;<br/>&gt; - 此模块仅支持在 ArkTS 文件（文件后缀为 .ets）中导入使用。<br/>&gt; **装饰器**：\@Sendable<br/> |
| [Float32Array](arkts-arkts-collections-float32array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md#collections)实现。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器类型：** \@Sendable<br/> |
| [Int16Array](arkts-arkts-collections-int16array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md#collections)实现。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器类型：** \@Sendable<br/> |
| [Int32Array](arkts-arkts-collections-int32array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md#collections)实现。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器**：\@Sendable<br/> |
| [Int8Array](arkts-arkts-collections-int8array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md#collections)实现。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器类型**：\@Sendable<br/> |
| [Map](arkts-arkts-collections-map-c.md) | 一种基于键值对存储的非线性数据结构。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; 本节使用以下标识符来表示泛型的使用：<br/><br/>- K：键。<br/>- V：值。<br/>K和V类型都需为<br/>[Sendable支持的数据类型](../../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。<br/>**装饰器类型**：\@Sendable<br/> |
| [Set](arkts-arkts-collections-set-c.md) | 一种非线性数据结构。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; 本节使用以下标识来表示泛型的使用：<br/><br/>- T：Type，支持[Sendable支持的数据类型](../../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。<br/>**装饰器类型：** \@Sendable<br/> |
| [Uint16Array](arkts-arkts-collections-uint16array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md#collections)实现。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器类型**：\@Sendable<br/> |
| [Uint32Array](arkts-arkts-collections-uint32array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md#collections)实现。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器**：\@Sendable<br/> |
| [Uint8Array](arkts-arkts-collections-uint8array-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md#collections)实现。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器类型：** \@Sendable<br/> |
| [Uint8ClampedArray](arkts-arkts-collections-uint8clampedarray-c.md) | 一种线性数据结构，底层基于[ArkTS ArrayBuffer](arkts-collections.md#collections)实现。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; **装饰器类型**：\@Sendable<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConcatArray](arkts-arkts-collections-concatarray-i.md) | 该接口定义了支持数组连接操作的对象，并继承了`ISendable`接口，使其兼具高效数组拼接和跨线程传递能力。<br/><br/>&gt; **说明**<br/>&gt;<br/>&gt; - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。<br/>&gt; 文档中存在泛型的使用，涉及以下泛型标记符：<br/><br/>- T：Type，支持[Sendable支持的数据类型](../../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ArrayFromMapFn](arkts-arkts-collections-arrayfrommapfn-t.md) | ArkTS Array归约函数类型，被Array类的'from'接口使用。<br/> |
| [ArrayPredicateFn](arkts-arkts-collections-arraypredicatefn-t.md) | ArkTS Array归约函数类型，被Array类的'some'和'every'接口使用，用来判断数组元素是否满足测试条件。<br/> |
| [ArrayReduceCallback](arkts-arkts-collections-arrayreducecallback-t.md) | ArkTS Array归约函数类型，被Array类的'reduceRight'接口使用。<br/> |
| [ISendable](arkts-arkts-collections-isendable-t.md) | ISendable是所有Sendable类型（除`null`和`undefined`）的父类型。自身没有任何必须的方法和属性。<br/> |
| [TypedArrayCompareFn](arkts-arkts-collections-typedarraycomparefn-t.md) | ArkTS TypedArray排序函数类型。<br/> |
| [TypedArrayForEachCallback](arkts-arkts-collections-typedarrayforeachcallback-t.md) | ArkTS TypedArray遍历函数类型。<br/> |
| [TypedArrayFromMapFn](arkts-arkts-collections-typedarrayfrommapfn-t.md) | ArkTS TypedArray映射函数类型。<br/> |
| [TypedArrayMapCallback](arkts-arkts-collections-typedarraymapcallback-t.md) | ArkTS TypedArray转换映射函数类型。<br/> |
| [TypedArrayPredicateFn](arkts-arkts-collections-typedarraypredicatefn-t.md) | ArkTS TypedArray断言测试函数类型。<br/> |
| [TypedArrayReduceCallback](arkts-arkts-collections-typedarrayreducecallback-t.md) | ArkTS TypedArray归约函数类型。<br/> |

