# 使用Taihe进行高层异步相关开发
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @Jemtaly; @tongdiaoZS; @m0_52007851; @zhangrunze13-->
<!--Tester: @m30041553-->
<!--Adviser: @fang-jinxu-->

## 简介

> 注意：本文档介绍的是使用`@async`和`@promise`注解来将C++侧的同步函数自动转换为ArkTS侧的异步函数的方式。对于需要在C++侧实现真正的异步逻辑（如跨线程、异步I/O等）的场景，请参考[使用Taihe进行底层异步相关开发](use-taihe-about-async-types.md)。

在Taihe中使用注解`@async`将声明的函数或方法转换为接收`AsyncCallback`的异步版本，使用注解`@promise`将声明的函数或方法转换为返回`Promise`的异步版本。

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

使用`@async`和`@promise`注解后，会在生成的ets代码中增加函数的异步版本。注解可应用于全局函数和对象成员方法。

注：`@rename`注解可参考[文档](./use-taihe-about-overload.md)

**生成ets代码**
```typescript
import {BusinessError as _taihe_BusinessError} from "@ohos.base";
native function _taihe_addAsync_native(a: int, b: int): int;
native function _taihe_addPromise_native(a: int, b: int): int;
native function _taihe_addSync_native(a: int, b: int): int;
export function add(a: int, b: int, callback: _taihe_AsyncCallback<int>): void {
    launch() {
        try {
            let res = _taihe_addAsync_native(a, b);
            callback(null, res);
        } catch (err) {
            callback(err as _taihe_BusinessError, undefined);
        }
    }
}
export function add(a: int, b: int): Promise<int> {
    return new Promise<int>((resolve, reject): void => {
        launch() {
            try {
                let res = _taihe_addPromise_native(a, b);
                resolve(res);
            } catch (err) {
                reject(err as Error);
            }
        }
    });
}
export function addSync(a: int, b: int): int {
    return _taihe_addSync_native(a, b);
}
type _taihe_AsyncCallback<T, E = void> =
    (error: _taihe_BusinessError<E>|null, data: T|undefined) => void;
```

## 使用示例

### Taihe声明

```rust
@rename("add")
@async function addAsync(a: i32, b: i32): i32;

@rename("add")
@promise function addPromise(a: i32, b: i32): i32;

function addSync(a: i32, b: i32): i32;
```

### C++实现

```cpp
int32_t addSync(int32_t a, int32_t b) {
    return a + b;
}

TH_EXPORT_CPP_API_addAsync(addSync);
TH_EXPORT_CPP_API_addPromise(addSync);
TH_EXPORT_CPP_API_addSync(addSync);
```

### ets使用
```typescript
// 使用同步版本的函数
console.info("addSync: ", async_test.addSync(1, 2))

// 使用async版本
async_test.add(10, 20, (error: BusinessError|null, data?: int) => {
    if (error !== null && error.code !== 0) {
        console.info("async ERROR ", error);
    } else {
        console.info("async success ", data);
    }
})

// 使用promise版本
try {
    let retPromise = await async_test.add(0, 2);
    console.info("async promise success ")
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
