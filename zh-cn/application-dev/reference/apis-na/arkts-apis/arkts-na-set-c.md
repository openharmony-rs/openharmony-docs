# Set

Set的实现。

**继承/实现关系：** Set implements ReadonlySet<K>

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export class Set--><!--Device-unnamed-export class Set-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## $_iterator

```TypeScript
$_iterator(): IterableIterator<K>
```

返回该Set的默认迭代器，即values()迭代器。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-$_iterator(): IterableIterator<K>--><!--Device-Set-$_iterator(): IterableIterator<K>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;K&gt; | 该Set的默认迭代器。 |

## add

```TypeScript
add(val: K): this
```

向该Set中放入一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-add(val: K): this--><!--Device-Set-add(val: K): this-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | K | 是 | 待放入该Set的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 添加该值后的Set。 |

## clear

```TypeScript
clear(): void
```

删除该Set中的所有元素。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-clear(): void--><!--Device-Set-clear(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(bucketsCount: int)
```

创建一个具有指定桶数量的Set实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-constructor(bucketsCount: int)--><!--Device-Set-constructor(bucketsCount: int)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bucketsCount | int | 是 | 内部map的桶数量。 <br>取值约束：应为整数。 |

## constructor

```TypeScript
constructor(set: Set<K>)
```

根据另一个Set创建一个新的Set实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-constructor(set: Set<K>)--><!--Device-Set-constructor(set: Set<K>)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| set | Set&lt;K&gt; | 是 | 用于初始化的另一个Set实例。 |

## constructor

```TypeScript
constructor(values: K[])
```

根据数组创建一个新的Set实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-constructor(values: K[])--><!--Device-Set-constructor(values: K[])-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | K[] | 是 | 用于初始化的数组。 |

## constructor

```TypeScript
constructor(elements?: Iterable<K> | FixedArray<K> | null)
```

根据可迭代对象或FixedArray创建一个新的Set实例。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-constructor(elements?: Iterable<K> | FixedArray<K> | null)--><!--Device-Set-constructor(elements?: Iterable<K> | FixedArray<K> | null)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elements | Iterable&lt;K&gt; \| FixedArray&lt;K&gt; \| null | 否 | 用于初始化的可迭代对象、FixedArray 或null。 |

## delete

```TypeScript
delete(val: K): boolean
```

从该Set中移除一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-delete(val: K): boolean--><!--Device-Set-delete(val: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | K | 是 | 待移除的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果该值已被移除则返回true。 |

## entries

```TypeScript
entries(): IterableIterator<[K, K]>
```

返回该Set中每个值对应的[v, v]键值对的可迭代对象。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-entries(): IterableIterator<[K, K]>--><!--Device-Set-entries(): IterableIterator<[K, K]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[K, K]&gt; | [v, v]键值对的可迭代对象。 |

## forEach

```TypeScript
forEach(callbackfn: (k: K, v: K, set: Set<K>) => void): void
```

按插入顺序，对Set对象中的每个值调用一次给定的函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-forEach(callbackfn: (k: K, v: K, set: Set<K>) => void): void--><!--Device-Set-forEach(callbackfn: (k: K, v: K, set: Set<K>) => void): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackfn | (k: K, v: K, set: Set&lt;K&gt;) =&gt; void | 是 | 要应用的函数。 |

## has

```TypeScript
has(val: K): boolean
```

检查某个值是否在该Set中。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-has(val: K): boolean--><!--Device-Set-has(val: K): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| val | K | 是 | 待在该Set中查找的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果该值在Set中则返回true。 |

## keys

```TypeScript
keys(): IterableIterator<K>
```

尽管名称如此，该方法返回Set中的元素。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-keys(): IterableIterator<K>--><!--Device-Set-keys(): IterableIterator<K>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;K&gt; | 该Set中值的可迭代对象。 |

## toString

```TypeScript
toString(): string
```

将该Set转换为字符串。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-toString(): string--><!--Device-Set-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示该Set的字符串。 |

## values

```TypeScript
values(): IterableIterator<K>
```

返回Set中的元素。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Set-values(): IterableIterator<K>--><!--Device-Set-values(): IterableIterator<K>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;K&gt; | 该Set中值的可迭代对象。 |

