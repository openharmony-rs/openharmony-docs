# Atomics (实例化原子类型接口)

ArkTS-Sta提供了一组实例化的原子类型，用于直接对单个共享值或对象引用执行原子操作。

> **说明：**
>
> - 本文档仅适用于ArkTS-Sta。
>
> - 本文档中的实例化原子类型接口是当前推荐用法，更符合ArkTS-Sta的设计规范。
>
> - 基于typedArray的静态Atomics接口主要为兼容保留，不再作为推荐用法，相关内容请参见[基于typedArray的静态Atomics接口](arkts-sta-legacyatomics.md)。

当前支持的实例化原子类型包括：AtomicReference\<T>、AtomicInt、AtomicLong、AtomicShort、AtomicByte、AtomicFloat、AtomicDouble、AtomicChar和AtomicBoolean。

实例化原子类型的各个方法不是每种原子类都支持，各方法支持类型见下表：

**类型支持表：**
| function |AtomicReference\<T>|AtomicInt|AtomicLong|AtomicShort|AtomicByte|AtomicFloat|AtomicDouble|AtomicChar|AtomicBoolean|
|--|--|--|--|--|--|--|--|--|--|
|constructor|支持|支持|支持|支持|支持|支持|支持|支持|支持|
|load|支持|支持|支持|支持|支持|支持|支持|支持|支持|
|store|支持|支持|支持|支持|支持|支持|支持|支持|支持|
|exchange|支持|支持|支持|支持|支持|支持|支持|支持|支持|
|compareAndSwap|支持|支持|支持|支持|支持|支持|支持|支持|支持|
|fetchAdd|不支持|支持|支持|支持|支持|支持|支持|不支持|不支持|
|fetchSub|不支持|支持|支持|支持|支持|支持|支持|不支持|不支持|
|fetchAnd|不支持|支持|支持|支持|支持|不支持|不支持|不支持|不支持|
|fetchOr|不支持|支持|支持|支持|支持|不支持|不支持|不支持|不支持|
|fetchXor|不支持|支持|支持|支持|支持|不支持|不支持|不支持|不支持|
|isLockFree|支持|支持|支持|支持|支持|支持|支持|支持|支持|

## AtomicReference\<T>

AtomicReference\<T>用于对对象引用执行原子读写、交换和比较交换操作。

> **说明：**
>
> AtomicReference\<T>在compareAndSwap操作中按引用比较expected与当前值是否相等，在exchange、store和load操作中读写的也是引用值本身。当T为数值类型时，相关操作处理的仍是引用而不是数值内容，因此不适合用于数值类型的原子操作；如需对数值执行原子操作，请使用对应的[AtomicInt](#atomicint)、[AtomicLong](#atomiclong)、[AtomicShort](#atomicshort)、[AtomicByte](#atomicbyte)、[AtomicFloat](#atomicfloat)或[AtomicDouble](#atomicdouble)。

### constructor

constructor(ref: T)

构造AtomicReference\<T>实例，并使用ref作为初始引用值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| ref | T | 是 | AtomicReference\<T>的初始引用值。当泛型T包含null时，也可以传入null。不建议泛型T设置为数值类型使用，如需进行数值原子操作，请直接使用对应的数值原子类。|

**示例：**
```ts
class Container {
    value: int = 1;
}

let atomicRef = new AtomicReference<Container>(new Container());
```

### load

load(): T

原子读取当前引用值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前保存的引用值。 |

**示例：**
```ts
let atomicRef = new AtomicReference<string>("hello");
console.info(atomicRef.load()); // hello
```

### store

store(ref: T): void

原子写入新的引用值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| ref | T | 是 | 要写入的新引用值。 |

**示例：**
```ts
let atomicRef = new AtomicReference<string>("hello");
atomicRef.store("world");
console.info(atomicRef.load()); // world
```

### exchange

exchange(ref: T): T

原子写入新的引用值，并返回更新前的旧引用值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| ref | T | 是 | 要写入的新引用值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| T | 返回更新前的旧引用值。 |

**示例：**
```ts
let atomicRef = new AtomicReference<string>("a");
let oldValue = atomicRef.exchange("b");
console.info(oldValue); // a
console.info(atomicRef.load()); // b
```

### compareAndSwap

compareAndSwap(expected: T, ref: T): T

如果当前引用值等于expected，则将其替换为ref；如果不相等，则不做修改。此方法返回修改前的旧引用值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | T | 是 | 预期的当前引用值。 |
| ref | T | 是 | 匹配成功时要写入的新引用值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| T | 成功时返回expected，失败时返回实际的旧引用值。 |

**示例：**
```ts
let atomicRef = new AtomicReference<string>("a");
let oldValue = atomicRef.compareAndSwap("a", "b");
console.info(oldValue); // a
console.info(atomicRef.load()); // b
```

### isLockFree

static isLockFree(): boolean

判断AtomicReference\<T>的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicReference.isLockFree().toString());
```

## AtomicInt

AtomicInt用于对int类型值执行原子读写、交换、比较交换、加减和按位运算。

### constructor

constructor(val: int)

构造AtomicInt实例，并使用val作为初始值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | int | 是 | AtomicInt的初始值。取值范围为[-2147483648, 2147483647]。 |

**示例：**
```ts
let atomicInt = new AtomicInt(1);
```

### load

load(): int

原子读取当前值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| int | 返回当前保存的值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(5);
console.info(atomicInt.load().toString()); // 5
```

### store

store(val: int): void

原子写入新值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | int | 是 | 要写入的新值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(1);
atomicInt.store(2);
console.info(atomicInt.load().toString()); // 2
```

### exchange

exchange(val: int): int

原子写入新值，并返回更新前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | int | 是 | 要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| int | 返回更新前的旧值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(1);
let oldValue = atomicInt.exchange(2);
console.info(oldValue.toString()); // 1
console.info(atomicInt.load().toString()); // 2
```

### compareAndSwap

compareAndSwap(expected: int, val: int): int

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。此方法返回修改前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | int | 是 | 预期的当前值。 |
| val | int | 是 | 匹配成功时要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| int | 成功时返回expected，失败时返回实际的旧值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(1);
let oldValue = atomicInt.compareAndSwap(1, 2);
console.info(oldValue.toString()); // 1
console.info(atomicInt.load().toString()); // 2
```

### fetchAdd

fetchAdd(val: int): int

原子将当前值加上val，并返回加法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | int | 是 | 执行加法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| int | 返回加法执行前的旧值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(1);
let oldValue = atomicInt.fetchAdd(4);
console.info(oldValue.toString()); // 1
console.info(atomicInt.load().toString()); // 5
```

### fetchSub

fetchSub(val: int): int

原子将当前值减去val，并返回减法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | int | 是 | 执行减法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| int | 返回减法执行前的旧值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(10);
let oldValue = atomicInt.fetchSub(3);
console.info(oldValue.toString()); // 10
console.info(atomicInt.load().toString()); // 7
```

### fetchAnd

fetchAnd(val: int): int

原子将当前值与val执行按位与运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | int | 是 | 执行按位与运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| int | 返回按位与运算前的旧值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(15);
let oldValue = atomicInt.fetchAnd(6);
console.info(oldValue.toString()); // 15
console.info(atomicInt.load().toString()); // 6
```

### fetchOr

fetchOr(val: int): int

原子将当前值与val执行按位或运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | int | 是 | 执行按位或运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| int | 返回按位或运算前的旧值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(3);
let oldValue = atomicInt.fetchOr(4);
console.info(oldValue.toString()); // 3
console.info(atomicInt.load().toString()); // 7
```

### fetchXor

fetchXor(val: int): int

原子将当前值与val执行按位异或运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | int | 是 | 执行按位异或运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| int | 返回按位异或运算前的旧值。 |

**示例：**
```ts
let atomicInt = new AtomicInt(5);
let oldValue = atomicInt.fetchXor(3);
console.info(oldValue.toString()); // 5
console.info(atomicInt.load().toString()); // 6
```

### isLockFree

static isLockFree(): boolean

判断AtomicInt的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicInt.isLockFree().toString());
```

## AtomicLong

AtomicLong用于对long类型值执行原子读写、交换、比较交换、加减和按位运算。

### constructor

constructor(val: long)

构造AtomicLong实例，并使用val作为初始值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | long | 是 | AtomicLong的初始值。取值范围为[-9223372036854775808, 9223372036854775807]。 |

**示例：**
```ts
let atomicLong = new AtomicLong(16);
```

### load

load(): long

原子读取当前值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| long | 返回当前保存的值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(16);
console.info(atomicLong.load().toString()); // 16
```

### store

store(val: long): void

原子写入新值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | long | 是 | 要写入的新值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(16);
atomicLong.store(20);
console.info(atomicLong.load().toString()); // 20
```

### exchange

exchange(val: long): long

原子写入新值，并返回更新前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | long | 是 | 要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| long | 返回更新前的旧值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(16);
let oldValue = atomicLong.exchange(18);
console.info(oldValue.toString()); // 16
console.info(atomicLong.load().toString()); // 18
```

### compareAndSwap

compareAndSwap(expected: long, val: long): long

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。此方法返回修改前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | long | 是 | 预期的当前值。 |
| val | long | 是 | 匹配成功时要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| long | 成功时返回expected，失败时返回实际的旧值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(16);
let oldValue = atomicLong.compareAndSwap(16, 20);
console.info(oldValue.toString()); // 16
console.info(atomicLong.load().toString()); // 20
```

### fetchAdd

fetchAdd(val: long): long

原子将当前值加上val，并返回加法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | long | 是 | 执行加法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| long | 返回加法执行前的旧值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(16);
let oldValue = atomicLong.fetchAdd(4);
console.info(oldValue.toString()); // 16
console.info(atomicLong.load().toString()); // 20
```

### fetchSub

fetchSub(val: long): long

原子将当前值减去val，并返回减法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | long | 是 | 执行减法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| long | 返回减法执行前的旧值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(16);
let oldValue = atomicLong.fetchSub(6);
console.info(oldValue.toString()); // 16
console.info(atomicLong.load().toString()); // 10
```

### fetchAnd

fetchAnd(val: long): long

原子将当前值与val执行按位与运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | long | 是 | 执行按位与运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| long | 返回按位与运算前的旧值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(10);
let oldValue = atomicLong.fetchAnd(7);
console.info(oldValue.toString()); // 10
console.info(atomicLong.load().toString()); // 2
```

### fetchOr

fetchOr(val: long): long

原子将当前值与val执行按位或运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | long | 是 | 执行按位或运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| long | 返回按位或运算前的旧值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(2);
let oldValue = atomicLong.fetchOr(4);
console.info(oldValue.toString()); // 2
console.info(atomicLong.load().toString()); // 6
```

### fetchXor

fetchXor(val: long): long

原子将当前值与val执行按位异或运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | long | 是 | 执行按位异或运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| long | 返回按位异或运算前的旧值。 |

**示例：**
```ts
let atomicLong = new AtomicLong(5);
let oldValue = atomicLong.fetchXor(3);
console.info(oldValue.toString()); // 5
console.info(atomicLong.load().toString()); // 6
```

### isLockFree

static isLockFree(): boolean

判断AtomicLong的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicLong.isLockFree().toString());
```

## AtomicShort

AtomicShort用于对short类型值执行原子读写、交换、比较交换、加减和按位运算。

### constructor

constructor(val: short)

构造AtomicShort实例，并使用val作为初始值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | short | 是 | AtomicShort的初始值。取值范围为[-32768, 32767]。 |

**示例：**
```ts
let atomicShort = new AtomicShort(3);
```

### load

load(): short

原子读取当前值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| short | 返回当前保存的值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(3);
console.info(atomicShort.load().toString()); // 3
```

### store

store(val: short): void

原子写入新值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | short | 是 | 要写入的新值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(3);
atomicShort.store(4);
console.info(atomicShort.load().toString()); // 4
```

### exchange

exchange(val: short): short

原子写入新值，并返回更新前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | short | 是 | 要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| short | 返回更新前的旧值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(3);
let oldValue = atomicShort.exchange(5);
console.info(oldValue.toString()); // 3
console.info(atomicShort.load().toString()); // 5
```

### compareAndSwap

compareAndSwap(expected: short, val: short): short

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。此方法返回修改前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | short | 是 | 预期的当前值。 |
| val | short | 是 | 匹配成功时要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| short | 成功时返回expected，失败时返回实际的旧值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(7);
let oldValue = atomicShort.compareAndSwap(7, 2);
console.info(oldValue.toString()); // 7
console.info(atomicShort.load().toString()); // 2
```

### fetchAdd

fetchAdd(val: short): short

原子将当前值加上val，并返回加法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | short | 是 | 执行加法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| short | 返回加法执行前的旧值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(2);
let oldValue = atomicShort.fetchAdd(3);
console.info(oldValue.toString()); // 2
console.info(atomicShort.load().toString()); // 5
```

### fetchSub

fetchSub(val: short): short

原子将当前值减去val，并返回减法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | short | 是 | 执行减法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| short | 返回减法执行前的旧值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(8);
let oldValue = atomicShort.fetchSub(3);
console.info(oldValue.toString()); // 8
console.info(atomicShort.load().toString()); // 5
```

### fetchAnd

fetchAnd(val: short): short

原子将当前值与val执行按位与运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | short | 是 | 执行按位与运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| short | 返回按位与运算前的旧值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(7);
let oldValue = atomicShort.fetchAnd(6);
console.info(oldValue.toString()); // 7
console.info(atomicShort.load().toString()); // 6
```

### fetchOr

fetchOr(val: short): short

原子将当前值与val执行按位或运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | short | 是 | 执行按位或运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| short | 返回按位或运算前的旧值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(3);
let oldValue = atomicShort.fetchOr(4);
console.info(oldValue.toString()); // 3
console.info(atomicShort.load().toString()); // 7
```

### fetchXor

fetchXor(val: short): short

原子将当前值与val执行按位异或运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | short | 是 | 执行按位异或运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| short | 返回按位异或运算前的旧值。 |

**示例：**
```ts
let atomicShort = new AtomicShort(5);
let oldValue = atomicShort.fetchXor(3);
console.info(oldValue.toString()); // 5
console.info(atomicShort.load().toString()); // 6
```

### isLockFree

static isLockFree(): boolean

判断AtomicShort的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicShort.isLockFree().toString());
```

## AtomicByte

AtomicByte用于对byte类型值执行原子读写、交换、比较交换、加减和按位运算。

### constructor

constructor(val: byte)

构造AtomicByte实例，并使用val作为初始值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | byte | 是 | AtomicByte的初始值。取值范围为[-128, 127]。 |

**示例：**
```ts
let atomicByte = new AtomicByte(5);
```

### load

load(): byte

原子读取当前值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| byte | 返回当前保存的值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(5);
console.info(atomicByte.load().toString()); // 5
```

### store

store(val: byte): void

原子写入新值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | byte | 是 | 要写入的新值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(5);
atomicByte.store(6);
console.info(atomicByte.load().toString()); // 6
```

### exchange

exchange(val: byte): byte

原子写入新值，并返回更新前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | byte | 是 | 要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| byte | 返回更新前的旧值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(5);
let oldValue = atomicByte.exchange(1);
console.info(oldValue.toString()); // 5
console.info(atomicByte.load().toString()); // 1
```

### compareAndSwap

compareAndSwap(expected: byte, val: byte): byte

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。此方法返回修改前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | byte | 是 | 预期的当前值。 |
| val | byte | 是 | 匹配成功时要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| byte | 成功时返回expected，失败时返回实际的旧值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(5);
let oldValue = atomicByte.compareAndSwap(5, 2);
console.info(oldValue.toString()); // 5
console.info(atomicByte.load().toString()); // 2
```

### fetchAdd

fetchAdd(val: byte): byte

原子将当前值加上val，并返回加法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | byte | 是 | 执行加法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| byte | 返回加法执行前的旧值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(1);
let oldValue = atomicByte.fetchAdd(4);
console.info(oldValue.toString()); // 1
console.info(atomicByte.load().toString()); // 5
```

### fetchSub

fetchSub(val: byte): byte

原子将当前值减去val，并返回减法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | byte | 是 | 执行减法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| byte | 返回减法执行前的旧值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(8);
let oldValue = atomicByte.fetchSub(3);
console.info(oldValue.toString()); // 8
console.info(atomicByte.load().toString()); // 5
```

### fetchAnd

fetchAnd(val: byte): byte

原子将当前值与val执行按位与运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | byte | 是 | 执行按位与运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| byte | 返回按位与运算前的旧值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(7);
let oldValue = atomicByte.fetchAnd(6);
console.info(oldValue.toString()); // 7
console.info(atomicByte.load().toString()); // 6
```

### fetchOr

fetchOr(val: byte): byte

原子将当前值与val执行按位或运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | byte | 是 | 执行按位或运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| byte | 返回按位或运算前的旧值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(3);
let oldValue = atomicByte.fetchOr(4);
console.info(oldValue.toString()); // 3
console.info(atomicByte.load().toString()); // 7
```

### fetchXor

fetchXor(val: byte): byte

原子将当前值与val执行按位异或运算，并返回运算前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | byte | 是 | 执行按位异或运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| byte | 返回按位异或运算前的旧值。 |

**示例：**
```ts
let atomicByte = new AtomicByte(5);
let oldValue = atomicByte.fetchXor(3);
console.info(oldValue.toString()); // 5
console.info(atomicByte.load().toString()); // 6
```

### isLockFree

static isLockFree(): boolean

判断AtomicByte的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicByte.isLockFree().toString());
```

## AtomicFloat

AtomicFloat用于对float类型值执行原子读写、交换、比较交换、加减运算。

### constructor

constructor(val: float)

构造AtomicFloat实例，并使用val作为初始值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | float | 是 | AtomicFloat的初始值。有限值范围为[-3.40282346638528860e+38, 3.40282346638528860e+38]，最小正非零值为1.4e-45，并支持NaN、Float.POSITIVE_INFINITY和Float.NEGATIVE_INFINITY。 |

**示例：**
```ts
let atomicFloat = new AtomicFloat(1.5);
```

### load

load(): float

原子读取当前值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| float | 返回当前保存的值。 |

**示例：**
```ts
let atomicFloat = new AtomicFloat(1.5);
console.info(atomicFloat.load().toString()); // 1.5
```

### store

store(val: float): void

原子写入新值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | float | 是 | 要写入的新值。 |

**示例：**
```ts
let atomicFloat = new AtomicFloat(1.5);
atomicFloat.store(2.5);
console.info(atomicFloat.load().toString()); // 2.5
```

### exchange

exchange(val: float): float

原子写入新值，并返回更新前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | float | 是 | 要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| float | 返回更新前的旧值。 |

**示例：**
```ts
let atomicFloat = new AtomicFloat(1.5);
let oldValue = atomicFloat.exchange(2.5);
console.info(oldValue.toString()); // 1.5
console.info(atomicFloat.load().toString()); // 2.5
```

### compareAndSwap

compareAndSwap(expected: float, val: float): float

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。此方法返回修改前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | float | 是 | 预期的当前值。 |
| val | float | 是 | 匹配成功时要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| float | 成功时返回expected，失败时返回实际的旧值。 |

**示例：**
```ts
let atomicFloat = new AtomicFloat(1.5);
let oldValue = atomicFloat.compareAndSwap(1.5, 3.0);
console.info(oldValue.toString()); // 1.5
console.info(atomicFloat.load().toString()); // 3
```

### fetchAdd

fetchAdd(val: float): float

原子将当前值加上val，并返回加法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | float | 是 | 执行加法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| float | 返回加法执行前的旧值。 |

**示例：**
```ts
let atomicFloat = new AtomicFloat(1.5);
let oldValue = atomicFloat.fetchAdd(0.5);
console.info(oldValue.toString()); // 1.5
console.info(atomicFloat.load().toString()); // 2
```

### fetchSub

fetchSub(val: float): float

原子将当前值减去val，并返回减法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | float | 是 | 执行减法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| float | 返回减法执行前的旧值。 |

**示例：**
```ts
let atomicFloat = new AtomicFloat(3.5);
let oldValue = atomicFloat.fetchSub(1.0);
console.info(oldValue.toString()); // 3.5
console.info(atomicFloat.load().toString()); // 2.5
```

### isLockFree

static isLockFree(): boolean

判断AtomicFloat的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicFloat.isLockFree().toString());
```

## AtomicDouble

AtomicDouble用于对double类型值执行原子读写、交换、比较交换、加减运算。

### constructor

constructor(val: double)

构造AtomicDouble实例，并使用val作为初始值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | double | 是 | AtomicDouble的初始值。有限值范围为[-1.7976931348623157e+308, 1.7976931348623157e+308]，最小正非零值为4.9e-324，并支持NaN、Double.POSITIVE_INFINITY和Double.NEGATIVE_INFINITY。 |

**示例：**
```ts
let atomicDouble = new AtomicDouble(10.0);
```

### load

load(): double

原子读取当前值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| double | 返回当前保存的值。 |

**示例：**
```ts
let atomicDouble = new AtomicDouble(10.0);
console.info(atomicDouble.load().toString()); // 10
```

### store

store(val: double): void

原子写入新值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | double | 是 | 要写入的新值。 |

**示例：**
```ts
let atomicDouble = new AtomicDouble(10.0);
atomicDouble.store(11.5);
console.info(atomicDouble.load().toString()); // 11.5
```

### exchange

exchange(val: double): double

原子写入新值，并返回更新前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | double | 是 | 要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| double | 返回更新前的旧值。 |

**示例：**
```ts
let atomicDouble = new AtomicDouble(10.0);
let oldValue = atomicDouble.exchange(12.0);
console.info(oldValue.toString()); // 10
console.info(atomicDouble.load().toString()); // 12
```

### compareAndSwap

compareAndSwap(expected: double, val: double): double

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。此方法返回修改前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | double | 是 | 预期的当前值。 |
| val | double | 是 | 匹配成功时要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| double | 成功时返回expected，失败时返回实际的旧值。 |

**示例：**
```ts
let atomicDouble = new AtomicDouble(7.5);
let oldValue = atomicDouble.compareAndSwap(7.5, 12.0);
console.info(oldValue.toString()); // 7.5
console.info(atomicDouble.load().toString()); // 12
```

### fetchAdd

fetchAdd(val: double): double

原子将当前值加上val，并返回加法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | double | 是 | 执行加法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| double | 返回加法执行前的旧值。 |

**示例：**
```ts
let atomicDouble = new AtomicDouble(1.5);
let oldValue = atomicDouble.fetchAdd(0.5);
console.info(oldValue.toString()); // 1.5
console.info(atomicDouble.load().toString()); // 2
```

### fetchSub

fetchSub(val: double): double

原子将当前值减去val，并返回减法执行前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | double | 是 | 执行减法运算的操作数。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| double | 返回减法执行前的旧值。 |

**示例：**
```ts
let atomicDouble = new AtomicDouble(10.0);
let oldValue = atomicDouble.fetchSub(2.5);
console.info(oldValue.toString()); // 10
console.info(atomicDouble.load().toString()); // 7.5
```

### isLockFree

static isLockFree(): boolean

判断AtomicDouble的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicDouble.isLockFree().toString());
```

## AtomicChar

AtomicChar用于对char类型值执行原子读写、交换和比较交换操作。

### constructor

constructor(val: char)

构造AtomicChar实例，并使用val作为初始值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | char | 是 | AtomicChar的初始值。取值范围为[c'\u0000', c'\uFFFF']，表示一个UTF-16码元。 |

**示例：**
```ts
let atomicChar = new AtomicChar(c'a');
```

### load

load(): char

原子读取当前值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| char | 返回当前保存的值。 |

**示例：**
```ts
let atomicChar = new AtomicChar(c'a');
console.info(atomicChar.load()); // a
```

### store

store(val: char): void

原子写入新值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | char | 是 | 要写入的新值。 |

**示例：**
```ts
let atomicChar = new AtomicChar(c'a');
atomicChar.store(c'b');
console.info(atomicChar.load()); // b
```

### exchange

exchange(val: char): char

原子写入新值，并返回更新前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | char | 是 | 要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| char | 返回更新前的旧值。 |

**示例：**
```ts
let atomicChar = new AtomicChar(c'a');
let oldValue = atomicChar.exchange(c'b');
console.info(oldValue); // a
console.info(atomicChar.load()); // b
```

### compareAndSwap

compareAndSwap(expected: char, val: char): char

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。此方法返回修改前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | char | 是 | 预期的当前值。 |
| val | char | 是 | 匹配成功时要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| char | 成功时返回expected，失败时返回实际的旧值。 |

**示例：**
```ts
let atomicChar = new AtomicChar(c'a');
let oldValue = atomicChar.compareAndSwap(c'a', c'b');
console.info(oldValue); // a
console.info(atomicChar.load()); // b
```

### isLockFree

static isLockFree(): boolean

判断AtomicChar的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicChar.isLockFree().toString());
```

## AtomicBoolean

AtomicBoolean用于对boolean类型值执行原子读写、交换和比较交换操作。

### constructor

constructor(val: boolean)

构造AtomicBoolean实例，并使用val作为初始值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | boolean | 是 | AtomicBoolean的初始值。取值为true时表示初始值为真，取值为false时表示初始值为假。 |

**示例：**
```ts
let atomicBoolean = new AtomicBoolean(false);
```

### load

load(): boolean

原子读取当前值。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | 返回当前保存的值。 |

**示例：**
```ts
let atomicBoolean = new AtomicBoolean(false);
console.info(atomicBoolean.load().toString()); // false
```

### store

store(val: boolean): void

原子写入新值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | boolean | 是 | 要写入的新值。 |

**示例：**
```ts
let atomicBoolean = new AtomicBoolean(false);
atomicBoolean.store(true);
console.info(atomicBoolean.load().toString()); // true
```

### exchange

exchange(val: boolean): boolean

原子写入新值，并返回更新前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| val | boolean | 是 | 要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | 返回更新前的旧值。 |

**示例：**
```ts
let atomicBoolean = new AtomicBoolean(false);
let oldValue = atomicBoolean.exchange(true);
console.info(oldValue.toString()); // false
console.info(atomicBoolean.load().toString()); // true
```

### compareAndSwap

compareAndSwap(expected: boolean, val: boolean): boolean

如果当前值等于expected，则将其替换为val；如果不相等，则不做修改。此方法返回修改前的旧值。

**参数：**
| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| expected | boolean | 是 | 预期的当前值。 |
| val | boolean | 是 | 匹配成功时要写入的新值。 |

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功时返回expected，失败时返回实际的旧值。 |

**示例：**
```ts
let atomicBoolean = new AtomicBoolean(false);
let oldValue = atomicBoolean.compareAndSwap(false, true);
console.info(oldValue.toString()); // false
console.info(atomicBoolean.load().toString()); // true
```

### isLockFree

static isLockFree(): boolean

判断AtomicBoolean的实现是否为无锁实现。

**返回值：**
| 类型 | 说明 |
| -------- | -------- |
| boolean | true表示无锁实现，false表示内部可能使用阻塞式同步机制。 |

**示例：**
```ts
console.info(AtomicBoolean.isLockFree().toString());
```
