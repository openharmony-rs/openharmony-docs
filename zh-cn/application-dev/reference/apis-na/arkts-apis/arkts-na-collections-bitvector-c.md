# BitVector

按顺序排列的比特值集合，每个比特值只能是0或1。 如果多个线程同时访问BitVector实例， 并且至少有一个线程修改了数组结构， 则必须在外部进行同步。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-collections-class BitVector--><!--Device-collections-class BitVector-End-->

**系统能力：** SystemCapability.Utils.Lang

## $_iterator

```TypeScript
$_iterator(): IterableIterator<int>
```

返回一个迭代位向量的迭代器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-$_iterator(): IterableIterator<int>--><!--Device-BitVector-$_iterator(): IterableIterator<int>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;int&gt; | 一个新的可迭代迭代器对象。 |

## constructor

```TypeScript
constructor(length: int)
```

用于创建BitVector对象的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-constructor(length: int)--><!--Device-BitVector-constructor(length: int)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | int | 是 | BitVector对象的长度。 |

## flipBitByIndex

```TypeScript
flipBitByIndex(index: int): void
```

翻转位向量中指定索引处的比特值。（0翻转为1，1翻转为0）

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-flipBitByIndex(index: int): void--><!--Device-BitVector-flipBitByIndex(index: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 位向量中的索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | flipBitByIndex方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |
| [10200001](../../apis-arkts/errorcode-utils.md#10200001-参数范围越界错误) | index的值超出范围。 |

## flipBitsByRange

```TypeScript
flipBitsByRange(fromIndex: int, toIndex: int): void
```

翻转位向量中一定范围内的比特值。（0翻转为1，1翻转为0）

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-flipBitsByRange(fromIndex: int, toIndex: int): void--><!--Device-BitVector-flipBitsByRange(fromIndex: int, toIndex: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromIndex | int | 是 | 起始索引位置，包含该索引位置的值。 |
| toIndex | int | 是 | 结束索引，不包含该索引的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | flipBitsByRange方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |
| [10200001](../../apis-arkts/errorcode-utils.md#10200001-参数范围越界错误) | fromIndex或toIndex的值超出范围。 |

## getBitCountByRange

```TypeScript
getBitCountByRange(element: int, fromIndex: int, toIndex: int): int
```

统计位向量中一定范围内某个比特元素出现的次数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-getBitCountByRange(element: int, fromIndex: int, toIndex: int): int--><!--Device-BitVector-getBitCountByRange(element: int, fromIndex: int, toIndex: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | int | 是 | 要统计的元素（0表示0，否则表示1）。 |
| fromIndex | int | 是 | 起始索引位置，包含该索引位置的值。 |
| toIndex | int | 是 | 结束索引，不包含该索引的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | number类型，返回某个比特元素出现的次数 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | getBitCountByRange方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |
| [10200001](../../apis-arkts/errorcode-utils.md#10200001-参数范围越界错误) | fromIndex或toIndex的值超出范围。 |

## getBitsByRange

```TypeScript
getBitsByRange(fromIndex: int, toIndex: int): BitVector
```

返回位向量中一定索引范围内的比特值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-getBitsByRange(fromIndex: int, toIndex: int): BitVector--><!--Device-BitVector-getBitsByRange(fromIndex: int, toIndex: int): BitVector-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromIndex | int | 是 | 起始索引位置，包含该索引位置的值。 |
| toIndex | int | 是 | 结束索引，不包含该索引的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BitVector](arkts-na-collections-bitvector-c.md) | BitVector类型，返回位向量中一定索引范围内的比特值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | getBitsByRange方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |
| [10200001](../../apis-arkts/errorcode-utils.md#10200001-参数范围越界错误) | fromIndex或toIndex的值超出范围。 |

## getIndexOf

```TypeScript
getIndexOf(element: int, fromIndex: int, toIndex: int): int
```

在位向量中查找某个比特值在指定范围内第一次出现的位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-getIndexOf(element: int, fromIndex: int, toIndex: int): int--><!--Device-BitVector-getIndexOf(element: int, fromIndex: int, toIndex: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | int | 是 | 要查找的元素（0表示0，否则表示1）。 |
| fromIndex | int | 是 | 起始索引位置，包含该索引位置的值。 |
| toIndex | int | 是 | 结束索引，不包含该索引的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | number类型，返回指定比特在范围内第一次出现的索引， 如果此范围内不包含该元素则返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | getIndexOf方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |
| [10200001](../../apis-arkts/errorcode-utils.md#10200001-参数范围越界错误) | fromIndex或toIndex的值超出范围。 |

## getLastIndexOf

```TypeScript
getLastIndexOf(element: int, fromIndex: int, toIndex: int): int
```

在位向量中查找某个比特值在指定范围内最后一次出现的位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-getLastIndexOf(element: int, fromIndex: int, toIndex: int): int--><!--Device-BitVector-getLastIndexOf(element: int, fromIndex: int, toIndex: int): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | int | 是 | 要查找的元素（0表示0，否则表示1）。 |
| fromIndex | int | 是 | 起始索引位置，包含该索引位置的值。 |
| toIndex | int | 是 | 结束索引，不包含该索引的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | number类型，返回指定比特在范围内最后一次出现的索引， 如果此范围内不包含该元素则返回-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | getLastIndexOf方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |
| [10200001](../../apis-arkts/errorcode-utils.md#10200001-参数范围越界错误) | fromIndex或toIndex的值超出范围。 |

## has

```TypeScript
has(element: int, fromIndex: int, toIndex: int): boolean
```

检查位向量是否包含特定的比特元素。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-has(element: int, fromIndex: int, toIndex: int): boolean--><!--Device-BitVector-has(element: int, fromIndex: int, toIndex: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | int | 是 | 要检查的元素（0表示0，否则表示1）。 |
| fromIndex | int | 是 | 起始索引位置，包含该索引位置的值。 |
| toIndex | int | 是 | 结束索引，包含该索引的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型，如果位向量包含指定元素则返回true， 否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | has方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |
| [10200001](../../apis-arkts/errorcode-utils.md#10200001-参数范围越界错误) | fromIndex或toIndex的值超出范围。 |

## pop

```TypeScript
pop(): int | undefined
```

取出并移除位向量末尾的比特元素。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-pop(): int | undefined--><!--Device-BitVector-pop(): int | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | int类型，如果位弹出成功则返回对应的int值，否则返回undefined。 |

## push

```TypeScript
push(element: int): boolean
```

将比特元素追加到位向量的末尾。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-push(element: int): boolean--><!--Device-BitVector-push(element: int): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | int | 是 | 要追加到此位向量的元素（0表示0，否则表示1）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean类型，如果添加成功返回true，失败返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | push方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |

## resize

```TypeScript
resize(size: int): void
```

调整位向量的长度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-resize(size: int): void--><!--Device-BitVector-resize(size: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | int | 是 | bitVector的新大小。如果count大于bitVector当前大小， 则额外的比特元素将设置为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | resize方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |

## setAllBits

```TypeScript
setAllBits(element: int): void
```

将位向量中的所有比特设置为特定的元素。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-setAllBits(element: int): void--><!--Device-BitVector-setAllBits(element: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | int | 是 | 要设置的元素（0表示0，否则表示1）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | setAllBits方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |

## setBitsByRange

```TypeScript
setBitsByRange(element: int, fromIndex: int, toIndex: int): void
```

将位向量中一定范围内的比特设置为特定的元素。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-setBitsByRange(element: int, fromIndex: int, toIndex: int): void--><!--Device-BitVector-setBitsByRange(element: int, fromIndex: int, toIndex: int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| element | int | 是 | 要设置的元素（0表示0，否则表示1）。 |
| fromIndex | int | 是 | 起始索引位置，包含该索引位置的值。 |
| toIndex | int | 是 | 结束索引，不包含该索引的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | setBitsByRange方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |
| [10200001](../../apis-arkts/errorcode-utils.md#10200001-参数范围越界错误) | fromIndex或toIndex的值超出范围。 |

## values

```TypeScript
values(): IterableIterator<int>
```

返回位向量中值的可迭代对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BitVector-values(): IterableIterator<int>--><!--Device-BitVector-values(): IterableIterator<int>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;int&gt; | 一个新的可迭代迭代器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../apis-arkts/errorcode-utils.md#10200011-传入的thisobject不是容器类的实例) | values方法无法被绑定。 |
| [10200201](../../apis-arkts/errorcode-utils.md#10200201-concurrent修改错误) | 并发修改错误。 |

