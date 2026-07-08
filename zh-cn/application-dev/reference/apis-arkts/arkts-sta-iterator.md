# Iterator
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供ArkTS-Sta迭代协议相关接口。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## IteratorResult

export class IteratorResult\<out T>

迭代器单次迭代结果。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| done | boolean | 否 | 否 | 是否已完成迭代。`true`表示迭代已结束，此时`value`为`undefined`；`false`表示迭代未结束，`value`为当前迭代值。 |
| value | T \| undefined | 是 | 否 | 当前迭代值。 |

### constructor

constructor()

创建完成状态的迭代结果。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
const result = new IteratorResult<int>();
console.info(result.done); // true
console.info(result.value); // undefined
```

### constructor

constructor(done: boolean, value: T | undefined)

按完成状态和值创建迭代结果。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| done | boolean | 是 | 是否已完成迭代。 |
| value | T \| undefined | 是 | 当前迭代值。 |

**示例：**

```ts
const result = new IteratorResult<int>(false, 1);
console.info(result.done); // false
console.info(result.value); // 1
```

### constructor

constructor(value: T)

创建未完成且包含当前值的迭代结果。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| value | T | 是 | 当前迭代值。 |

**示例：**

```ts
const result = new IteratorResult<int>(1);
console.info(result.done); // false
console.info(result.value); // 1
```

## Iterator

export interface Iterator\<out T>

迭代器接口，提供获取下一次迭代结果的能力。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### next

next(): IteratorResult\<T>

返回下一次迭代结果。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| IteratorResult\<T> | 下一次迭代结果。 |

**示例：**

```ts
class MyIterator implements Iterator<int> {
    private used: boolean = false;
    private index: int = 0;
    private cache: Array<int>;
    constructor(arr: Array<int>) {
        this.cache = arr;
        this.used = arr.length == 0;
    }
    next(): IteratorResult<int> {
        if (this.used) {
            return new IteratorResult<int>();
        }
        const res = new IteratorResult<int>(this.cache[this.index]);
        this.index++;
        this.used = this.index == this.cache.length;
        return res;
    }
}

const it: Iterator<int> = new MyIterator([1, 2, 3]);
console.info(it.next().value); // 1
console.info(it.next().value); // 2
console.info(it.next().value); // 3
console.info(it.next().value); // undefined
```

## Iterable

export interface Iterable\<out T>

可迭代接口，提供获取迭代器的能力。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### $_iterator

$_iterator(): Iterator\<T>

返回可迭代迭代器。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| Iterator\<T> | 可迭代迭代器。 |

**示例：**

```ts
class IntRange implements Iterable<int> {
    private start: int;
    private end: int;

    constructor(start: int, end: int) {
        this.start = start;
        this.end = end;
    }

    $_iterator(): Iterator<int> {
        return new IntRangeIterator(this.start, this.end);
    }
}

class IntRangeIterator implements Iterator<int> {
    private current: int;
    private end: int;

    constructor(start: int, end: int) {
        this.current = start;
        this.end = end;
    }

    next(): IteratorResult<int> {
        if (this.current >= this.end) {
            return new IteratorResult<int>();
        }
        return new IteratorResult<int>(this.current++);
    }

    $_iterator(): Iterator<int> {
        return this;
    }
}

const range = new IntRange(1, 4);
const iterator = range.$_iterator();
console.info(iterator.next().value); // 1
console.info(iterator.next().value); // 2
console.info(iterator.next().value); // 3
console.info(iterator.next().done);  // true
```

## IterableIterator

export interface IterableIterator\<out T> extends Iterator\<T>, Iterable\<T>

同时满足`Iterator`和`Iterable`协议的迭代器。继承自[Iterator](#iterator-1)和[Iterable](#iterable)。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### $_iterator

$_iterator(): IterableIterator\<T>

返回可迭代迭代器。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| :--- | :--- |
| IterableIterator\<T> | 可迭代迭代器。 |

**示例：**

```ts
class StepIterator implements IterableIterator<int> {
    private current: int;
    private step: int;
    private max: int;

    constructor(start: int, step: int, max: int) {
        this.current = start;
        this.step = step;
        this.max = max;
    }

    next(): IteratorResult<int> {
        if (this.current > this.max) {
            return new IteratorResult<int>();
        }
        const value = this.current;
        this.current += this.step;
        return new IteratorResult<int>(value);
    }

    $_iterator(): IterableIterator<int> {
        return this;
    }
}

const iter: IterableIterator<int> = new StepIterator(0, 5, 15);
const it1 = iter.$_iterator();
console.info(it1.next().value); // 0
console.info(it1.next().value); // 5
console.info(it1.next().value); // 10
console.info(it1.next().value); // 15
console.info(it1.next().done);  // true
```

## iteratorForEach

export function iteratorForEach\<V>(x: Iterator\<V>, fn: (x: V) => void): void

依次读取迭代器中的值并调用`fn`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| x | Iterator\<V> | 是 | 要遍历的迭代器。 |
| fn | (x: V) => void | 是 | 对每个值执行的回调。 |

**示例：**

```ts
class OneIterator implements Iterator<int> {
    private used: boolean = false;
    next(): IteratorResult<int> {
        if (this.used) {
            return new IteratorResult<int>();
        }
        this.used = true;
        return new IteratorResult<int>(1);
    }
}

iteratorForEach<int>(new OneIterator(), (value: int): void => {
    console.info(value); // 1
});
```
