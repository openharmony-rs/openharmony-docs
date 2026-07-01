# @ohos.util.PlainArray (非线性容器PlainArray)  
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

PlainArray可用于存储具有关联关系的key-value键值对集合，其中key值唯一且类型为number，每个key对应一个value。

PlainArray依据泛型定义，采用轻量级结构，通过二分查找算法在集合中查找 key 值，并映射到其他数组中的value值。

PlainArray和[LightWeightMap](js-apis-lightweightmap.md)都是用来存储键值对，且均采用轻量级结构，但PlainArray的key值类型仅限于number。

**推荐使用场景：** 当需要存储key值为number类型的键值对时，可以使用PlainArray。

文档中使用了泛型，涉及以下泛型类型参数：
- T：Type，泛型类型参数，可以是任意类型

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 容器类使用静态语言实现，限制了存储位置和属性，不支持自定义属性和方法。

## 导入模块

```ts
import { PlainArray } from '@kit.ArkTS';  
```


## PlainArray

### 属性

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 否 | PlainArray的元素个数。 |


### constructor

constructor()

PlainArray的构造函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200012 | The PlainArray's constructor cannot be directly invoked. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
```


### isEmpty

isEmpty(): boolean

判断容器是否为空。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 为空返回true，不为空返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The isEmpty method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
let result = plainArray.isEmpty();
console.info("result:", result); // result: true
```


### has

ArkTS-Dyn: has(key: number): boolean

ArkTS-Sta: has(key: int): boolean

判断容器中是否包含指定key。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 指定key。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含指定key返回true，否则返回false。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The has method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
let result = plainArray.has(1);
console.info("result:", result); // result: true
```

### get

get(key: number): T

获取指定key所对应的value。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | number | 是 | 查找的指定key。取值范围为[-2147483648, 2147483647]，即int32范围。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回key映射的value值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The get method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.get(1);
console.info("result:", result);  // result: squirrel
```

### get<sup>23+</sup>

get(key: int): T \| undefined

获取指定key所对应的value值。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | int | 是 | 查找的指定key。需要小于等于int32_max（即2147483647）。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T \| undefined | 返回key映射的value值，key不存在返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.get(1);
```

### getIndexOfKey

ArkTS-Dyn: getIndexOfKey(key: number): number

ArkTS-Sta: getIndexOfKey(key: int): int

查找指定key对应的下标值，如果未找到则返回-1。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 指定key。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: number <br> ArkTS-Sta: int | 返回指定key对应的下标值，查找失败返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getIndexOfKey method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getIndexOfKey(2);
console.info("result:", result); // result: 1
```

### getIndexOfValue

ArkTS-Dyn: getIndexOfValue(value: T): number

ArkTS-Sta: getIndexOfValue(value: T): int

查找指定value元素第一次出现的下标值，如果未找到则返回-1。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 指定value元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: number <br> ArkTS-Sta: int | 返回指定value元素第一次出现时的下标值，查找失败返回-1。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getIndexOfValue method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getIndexOfValue("squirrel");
console.info("result:", result);  // result: 0
```


### getKeyAt

ArkTS-Dyn: getKeyAt(index: number): number

ArkTS-Sta: getKeyAt(index: int): int

查找指定下标元素键值对中的key值。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: number <br> ArkTS-Sta: int | 返回该下标元素键值对中的key值，失败返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The getKeyAt method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getKeyAt(1);
console.info("result:", result); // result: 2
```

### getValueAt

ArkTS-Dyn: getValueAt(index: number): T

ArkTS-Sta: getValueAt(index: int): T

查找指定下标元素键值对中的value值，失败则返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 指定下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回该下标元素键值对中的value值，失败返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The getValueAt method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.getValueAt(1);
console.info("result:", result);  // result: sparrow
```

### clone

clone(): PlainArray&lt;T&gt;

克隆一个实例，并返回克隆后的实例。修改克隆后的实例并不会影响原实例。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| PlainArray&lt;T&gt; | 返回新的对象的克隆实例。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The clone method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let newPlainArray = plainArray.clone();
console.info("result:", newPlainArray.get(1));  // result: squirrel
```

### add

ArkTS-Dyn: add(key: number, value: T): void

ArkTS-Sta: add(key: int, value: T): void

向容器中添加一组数据。若指定的key不存在，则新增键值对，且length增加；若指定的key存在，则替换该key对应的value值。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 添加成员数据的键名。需要小于等于int32_max即2147483647。 |
| value | T | 是 | 添加成员数据的值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The add method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
console.info("result:", plainArray.get(1));  // result: squirrel
```

### remove

remove(key: number): T

删除指定key对应的键值对。指定key不存在时，返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | number | 是 | 指定key。取值范围为[-2147483648, 2147483647]，即int32范围。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回所删除的键值对中的value值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The remove method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.remove(2);
console.info("result:", result);  // result: sparrow
```

### removeAt

removeAt(index: number): T

删除指定下标对应的元素。指定[0, PlainArray.length-1]以外的值时会返回undefined。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | number | 是 | 指定元素下标。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回删除的元素。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The removeAt method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.removeAt(1);
console.info("result:", result);  // result: sparrow
```

### remove<sup>23+</sup>

remove(key: int): T \| undefined

删除指定key所对应的键值对。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | int | 是 | 指定key。需要小于等于int32_max（即2147483647）。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T \| undefined | 返回所删除的键值对中的value值，key不存在则返回undefined。 |

  **错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.remove(2);
```

### removeAt<sup>23+</sup>

removeAt(index: int): T \| undefined

删除指定下标所对应的元素。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | int | 是 | 指定元素下标。需要小于等于int32_max（即2147483647）。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T \| undefined | 返回删除的元素，删除失败则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |

**示例：**

```ts
let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.removeAt(1);
```

### removeRangeFrom

ArkTS-Dyn: removeRangeFrom(index: number, size: number): number

ArkTS-Sta: removeRangeFrom(index: int, size: int): int

删除指定范围内的元素。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 删除元素的起始下标。需要小于等于int32_max即2147483647。 |
| size | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 期望删除元素个数。需要小于等于int32_max即2147483647。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: number <br> ArkTS-Sta: int | 实际删除元素个数。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The removeRangeFrom method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
// 从下标1开始删除元素
let result = plainArray.removeRangeFrom(1, 3);
console.info("result:", result);  // result: 1
```

### setValueAt

ArkTS-Dyn: setValueAt(index: number, value: T): void

ArkTS-Sta: setValueAt(index: int, value: T): void

替换容器中指定下标对应键值对中的value值。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | ArkTS-Dyn: number <br> ArkTS-Sta: int | 是 | 指定替换数据下标。取值范围为[0, PlainArray.length-1]，且需要小于等于int32_max即2147483647。 |
| value | T | 是 | 替换键值对中的值。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200001 | The value of index is out of range. |
| 10200011 | The setValueAt method cannot be bound. |

**示例：**

ArkTS-Dyn示例：

```ts
let plainArray = new PlainArray<string | number>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
// 替换plainArray中下标为1的键值对中的value值为3546
plainArray.setValueAt(1, 3546);
// 获取并打印plainArray中下标为1的键值对中的value值
let result = plainArray.getValueAt(1);
console.info("result:", result);  // result: 3546
```

ArkTS-Sta示例：

```ts
let plainArray: PlainArray<string | int> = new PlainArray<string | int>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
plainArray.setValueAt(1, 3546);
let result = plainArray.getValueAt(1); 
console.info("result:", result);  // result: 3546
```


### toString

toString(): String

获取包含容器中所有键和值的字符串。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| String | 返回对应字符串。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The toString method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let result = plainArray.toString();
console.info("result:", result);  // result: 1:squirrel,2:sparrow
```

### clear

clear(): void

清除容器中的所有元素，并将length置为0。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The clear method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
plainArray.clear();
let result = plainArray.isEmpty();
console.info("result:", result);  // result: true
```

### forEach

forEach(callbackFn: (value: T, index?: number, PlainArray?: PlainArray&lt;T&gt;) => void, thisArg?: Object): void

在遍历PlainArray实例对象中每一个元素的过程中，对每个元素执行回调函数。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | function | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值为当前实例对象。 |

callbackFn的参数说明：
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前遍历到的元素。 |
| index | number | 否 | 当前遍历到的下标值。 |
| PlainArray | PlainArray&lt;T&gt;| 否 | 当前调用forEach方法的实例对象，默认值为当前实例对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The forEach method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
plainArray.forEach((value: string, index: number) => {
  console.info("value:" + value, "index:" + index);
});
// value:squirrel index:1
// value:sparrow index:2
```

```ts
// 不建议在forEach中使用add、remove、removeAt方法，因其可能导致迭代过程中的状态异常，建议使用for循环来进行安全的插入与删除操作。
let plainArray = new PlainArray<string>();
for (let i = 0; i < 10; i++) {
  plainArray.add(i, "123");
}

for (let i = 0; i < 10; i++) {
  plainArray.remove(i);
}
```

### forEach<sup>23+</sup>

forEach(callbackFn: PlainArrayForEachCb\<T\>): void

通过回调函数遍历实例对象上的元素以及元素对应的下标值。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackFn | [PlainArrayForEachCb\<T\>](#plainarrayforeachcbt23) | 是 | 回调函数。 |

**示例：**

```ts
import { PlainArrayForEachCb } from '@kit.ArkTS';

let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");
let plainArrayCb: PlainArrayForEachCb<string> = (value: string, key: int, PlainArray: PlainArray<string>) => {
  console.info("value: " + value, " key: " + key);
}
plainArray.forEach(plainArrayCb);
```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;[number, T]&gt;

返回一个包含key-value键值对的迭代器对象，其中key是number类型。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;[number, T]&gt; | 返回一个迭代器。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 10200011 | The Symbol.iterator method cannot be bound. |

**示例：**

```ts
let plainArray = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");

for (let item of plainArray) {
  console.info("value:" + item[1], "index:" + item[0]);
}
// value:squirrel index:1
// value:sparrow index:2
```
```ts
// 不建议在Symbol.iterator中使用add、remove、removeAt方法，会导致死循环等不可预知的风险，可使用for循环来进行插入和删除。
let plainArray = new PlainArray<string>();
for(let i = 0; i < 10; i++) {
  plainArray.add(i,"123");
}

for(let i = 0; i < 10; i++) {
  plainArray.remove(i);
}
```

### \$_iterator<sup>23+</sup>

\$_iterator\(): IterableIterator&lt;[int, T]&gt;

返回一个包含key-value键值对的迭代器对象，其中key是int类型。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;[int, T]&gt; | 返回一个迭代器。 |

**示例：**

```ts
let plainArray: PlainArray<string> = new PlainArray<string>();
plainArray.add(1, "squirrel");
plainArray.add(2, "sparrow");

let iter = plainArray.$_iterator();
let temp: IteratorResult<[int, string]> = iter.next();
while(!temp.done) {
  console.info("key:" + temp.value![0]);
  console.info("value:" + temp.value![1]);
  temp = iter.next();
}
```

### PlainArrayForEachCb\<T\><sup>23+</sup>

type PlainArrayForEachCb\<T\> = (value: T, key: int, PlainArray: PlainArray\<T\>) => void

PlainArray中forEach方法的回调函数。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | T | 是 | 当前遍历到元素的值。 |
| key | int | 是 | 当前遍历到元素的键。 |
| PlainArray | [PlainArray&lt;T&gt;](#plainarray)| 是 | 当前调用[forEach](#foreach23)方法的实例对象。 |