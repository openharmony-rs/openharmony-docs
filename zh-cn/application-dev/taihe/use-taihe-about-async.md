# 使用 Taihe 进行异步相关开发

## 简介

在Taihe中使用注解`@async`将声明的函数或方法转换为Async版，使用注解`@promise`将声明的函数或方法转换为Promise版。

## 基本概念

理解以下示例需要对[@rename](./use-taihe-about-overload.md)有基础的了解。

**Taihe声明代码**

```rust
@rename("add")
@async function addAsync(a: i32, b: i32): i32;

@rename("add")
@promise function addPromise(a: i32, b: i32): i32;

function addSync(a: i32, b: i32): i32;
```

使用 `@async` 和 `@promise` 注解后，会在生成的 ets 代码中增加函数的异步版本。注解可应用于全局函数和对象成员方法。

注：`@rename` 注解可参考[文档](./use-taihe-about-overload.md)

**生成ets代码**
```typescript
import {BusinessError as _taihe_BusinessError} from "@ohos.base";
native function _taihe_addAsync_native(a: int, b: int): int;
native function _taihe_addPromise_native(a: int, b: int): int;
native function _taihe_addSync_native(a: int, b: int): int;
export function add(a: int, b: int, callback: _taihe_AsyncCallback<int>): void {
    taskpool.execute((): int => {
        return _taihe_addAsync_native(a, b);
    })
    .then((ret: Any): void => {
        callback(null, ret as int);
    })
    .catch((ret: Any): void => {
        callback(ret as _taihe_BusinessError, undefined);
    });
}
export function add(a: int, b: int): Promise<int> {
    return new Promise<int>((resolve, reject): void => {
        taskpool.execute((): int => {
            return _taihe_addPromise_native(a, b);
        })
        .then((ret: Any): void => {
            resolve(ret as int);
        })
        .catch((ret: Any): void => {
            reject(ret as Error);
        });
    });
}
export function addSync(a: int, b: int): int {
    return _taihe_addSync_native(a, b);
}
type _taihe_AsyncCallback<T, E = void> =
    (error: _taihe_BusinessError<E>|null, data: T|undefined) => void;
```

## 使用示例

### Taihe 声明

```rust
@rename("add")
@async function addAsync(a: i32, b: i32): i32;

@rename("add")
@promise function addPromise(a: i32, b: i32): i32;

function addSync(a: i32, b: i32): i32;
```

### C++ 实现

```cpp
int32_t addSync(int32_t a, int32_t b) {
    return a + b;
}

TH_EXPORT_CPP_API_addAsync(addSync);
TH_EXPORT_CPP_API_addPromise(addSync);
TH_EXPORT_CPP_API_addSync(addSync);
```

### ets 使用
```typescript
// 使用同步版本的函数
console.log("addSync: ", async_test.addSync(1, 2))

// 使用 async 版本
async_test.add(10, 20, (error: BusinessError|null, data?: int) => {
    if (error !== null && error.code !== 0) {
        console.log("async ERROR ", error);
    } else {
        console.log("async success ", data);
    }
})

// 使用 promise 版本
try {
    let retPromise = await async_test.add(0, 2);
    console.log("async promise success ")
} catch (error) {
    console.error("async promise ERROR ", error)
}
```

输出结果如下：
```sh
addSync:  3
async success  30
async promise success
MyStr
```
