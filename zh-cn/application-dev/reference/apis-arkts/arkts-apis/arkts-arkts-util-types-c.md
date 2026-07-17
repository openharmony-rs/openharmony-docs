# types

提供检查不同内置对象类型的 API，例如 ArrayBuffer、Map 和 Set，以避免类型错误导致的异常。

**起始版本：** 8

<!--Device-util-class types--><!--Device-util-class types-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

用于创建 **Types** 对象的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-constructor()--><!--Device-types-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let type = new util.types();

```

## isAnyArrayBuffer

```TypeScript
isAnyArrayBuffer(value: Object): boolean
```

判断入参是否为 ArrayBuffer 或 SharedArrayBuffer 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isAnyArrayBuffer(value: Object): boolean--><!--Device-types-isAnyArrayBuffer(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 ArrayBuffer 或 SharedArrayBuffer 类型，则返回 **true**；否则返回**false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isAnyArrayBuffer(new ArrayBuffer(0));
console.info("result = " + result);
// 输出结果：result = true

```

## isArgumentsObject

```TypeScript
isArgumentsObject(value: Object): boolean
```

判断入参是否为 **arguments** 对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isArgumentsObject(value: Object): boolean--><!--Device-types-isArgumentsObject(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 **arguments** 对象，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
function foo() {
    let result = type.isArgumentsObject(arguments);
    console.info("result = " + result);
}
let f = foo();
// 输出结果：result = true

```

## isArrayBuffer

```TypeScript
isArrayBuffer(value: Object): boolean
```

判断入参是否为 ArrayBuffer 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isArrayBuffer(value: Object): boolean--><!--Device-types-isArrayBuffer(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 ArrayBuffer 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isArrayBuffer(new ArrayBuffer(0));
console.info("result = " + result);
// 输出结果：result = true

```

## isArrayBufferView

```TypeScript
isArrayBufferView(value: Object): boolean
```

判断入参是否为 ArrayBufferView 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isArrayBufferView(value: Object): boolean--><!--Device-types-isArrayBufferView(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 ArrayBufferView 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isArrayBufferView(new Int8Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isAsyncFunction

```TypeScript
isAsyncFunction(value: Object): boolean
```

判断入参是否为异步函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isAsyncFunction(value: Object): boolean--><!--Device-types-isAsyncFunction(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为异步函数，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isAsyncFunction(async () => {});
console.info("result = " + result);
// 输出结果：result = true

```

该接口无法对Sendable class中的async成员函数进行有效判断，无替代方案。

```TypeScript
// /entry/src/main/ets/pages/test.ts
export async function* asyncGeneratorFunc() {}

```

```TypeScript
import { asyncGeneratorFunc } from './test'

@Sendable
class SendableClass {
  async asyncFunction() {}
}

let type = new util.types();
let result1 = type.isAsyncFunction(asyncGeneratorFunc);
console.info("result = " + result1);
// 输出结果：result = false

console.info("asyncGeneratorFunc.constructor.name === AsyncGeneratorFunction : " +
  (asyncGeneratorFunc.constructor.name === 'AsyncGeneratorFunction'));
// 输出结果：asyncGeneratorFunc.constructor.name === AsyncGeneratorFunction : true

const instance = new SendableClass();
let result2 = type.isAsyncFunction(instance.asyncFunction);
console.info("result = " + result2);
// 输出结果：result = false

```

## isBigInt64Array

```TypeScript
isBigInt64Array(value: Object): boolean
```

判断入参是否为 BigInt64Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isBigInt64Array(value: Object): boolean--><!--Device-types-isBigInt64Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 BigInt64Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isBigInt64Array(new BigInt64Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isBigUint64Array

```TypeScript
isBigUint64Array(value: Object): boolean
```

判断入参是否为 BigUint64Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isBigUint64Array(value: Object): boolean--><!--Device-types-isBigUint64Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 BigUint64Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isBigUint64Array(new BigUint64Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isBooleanObject

```TypeScript
isBooleanObject(value: Object): boolean
```

判断入参是否为 Boolean 类型。

> **NOTE**  
>  
> 本接口从 API version 8 起支持，从 API version 14 起废弃。无替代接口。

**起始版本：** 8

**废弃版本：** 14

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isBooleanObject(value: Object): boolean--><!--Device-types-isBooleanObject(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Boolean 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isBooleanObject(new Boolean(true));
console.info("result = " + result);
// 输出结果：result = true

```

## isBoxedPrimitive

```TypeScript
isBoxedPrimitive(value: Object): boolean
```

判断入参是否为 Boolean、Number、String 或 Symbol 类型。

> **NOTE**  
>  
> 本接口从 API version 8 起支持，从 API version 14 起废弃。无替代接口。

**起始版本：** 8

**废弃版本：** 14

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isBoxedPrimitive(value: Object): boolean--><!--Device-types-isBoxedPrimitive(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Boolean、Number、String 或 Symbol 类型，则返回 **true**；否则返回**false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isBoxedPrimitive(new Boolean(false));
console.info("result = " + result);
// 输出结果：result = true

```

## isDataView

```TypeScript
isDataView(value: Object): boolean
```

判断入参是否为 DataView 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isDataView(value: Object): boolean--><!--Device-types-isDataView(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 DataView 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
const ab = new ArrayBuffer(20);
let result = type.isDataView(new DataView(ab));
console.info("result = " + result);
// 输出结果：result = true

```

## isDate

```TypeScript
isDate(value: Object): boolean
```

判断入参是否为 Date 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isDate(value: Object): boolean--><!--Device-types-isDate(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Date 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isDate(new Date());
console.info("result = " + result);
// 输出结果：result = true

```

## isExternal

```TypeScript
isExternal(value: Object): boolean
```

判断入参是否为 native external 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isExternal(value: Object): boolean--><!--Device-types-isExternal(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 native external 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
// /entry/src/main/cpp/napi_init.cpp
#include "napi/native_api.h"
#include <js_native_api.h>
#include <stdlib.h>

napi_value result;
static napi_value Testexternal(napi_env env, napi_callback_info info) {
    int* raw = (int*) malloc(1024);
    napi_status status = napi_create_external(env, (void*) raw, NULL, NULL, &result);
    if (status != napi_ok) {
        napi_throw_error(env, NULL, "create external failed");
        return NULL;
    }
    return result;
}

EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        {"testexternal", nullptr, Testexternal, nullptr, nullptr, nullptr, napi_default, nullptr},
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END
// 此处已省略模块注册的代码, 你可能需要自行注册Testexternal方法
// ...


```

```TypeScript
import testNapi from 'libentry.so';

let type = new util.types();
const data = testNapi.testexternal();
let result = type.isExternal(data);

let result01 = type.isExternal(true);
console.info("result = " + result);
console.info("result01 = " + result01);
// 输出结果：result = true
// 输出结果：result01 = false

```

## isFloat32Array

```TypeScript
isFloat32Array(value: Object): boolean
```

判断入参是否为 Float32Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isFloat32Array(value: Object): boolean--><!--Device-types-isFloat32Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Float32Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isFloat32Array(new Float32Array());
console.info("result = " + result);
// 输出结果：result = true

```

## isFloat64Array

```TypeScript
isFloat64Array(value: Object): boolean
```

判断入参是否为 Float64Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isFloat64Array(value: Object): boolean--><!--Device-types-isFloat64Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Float64Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isFloat64Array(new Float64Array());
console.info("result = " + result);
// 输出结果：result = true

```

## isGeneratorFunction

```TypeScript
isGeneratorFunction(value: Object): boolean
```

判断入参是否为 generator 函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isGeneratorFunction(value: Object): boolean--><!--Device-types-isGeneratorFunction(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 generator 函数，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
// /entry/src/main/ets/pages/test.ts
export function* foo() {}

```

```TypeScript
import { foo } from './test'

let type = new util.types();
let result = type.isGeneratorFunction(foo);
console.info("result = " + result);
// 输出结果：result = true

```

该接口无法对AsyncGenerator Function进行有效判断，建议通过获取函数的属性与做判等的方式替代。

```TypeScript
// /entry/src/main/ets/pages/test.ts
export async function* asyncGeneratorFunc() {}

```

```TypeScript
import { asyncGeneratorFunc } from './test'

let type = new util.types();
let result = type.isGeneratorFunction(asyncGeneratorFunc);
console.info("result = " + result);
// 输出结果：result = false

console.info("asyncGeneratorFunc.constructor.name === AsyncGeneratorFunction : " +
  (asyncGeneratorFunc.constructor.name === 'AsyncGeneratorFunction'));
// 输出结果：asyncGeneratorFunc.constructor.name === AsyncGeneratorFunction : true

```

## isGeneratorObject

```TypeScript
isGeneratorObject(value: Object): boolean
```

判断入参是否为 generator 对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isGeneratorObject(value: Object): boolean--><!--Device-types-isGeneratorObject(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 generator 对象，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
// /entry/src/main/ets/pages/test.ts
function* foo() {}
export const generator = foo();

```

```TypeScript
import { generator } from './test'

let type = new util.types();
let result = type.isGeneratorObject(generator);
console.info("result = " + result);
// 输出结果：result = true

```

## isInt16Array

```TypeScript
isInt16Array(value: Object): boolean
```

判断入参是否为 Int16Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isInt16Array(value: Object): boolean--><!--Device-types-isInt16Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Int16Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isInt16Array(new Int16Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isInt32Array

```TypeScript
isInt32Array(value: Object): boolean
```

判断入参是否为 Int32Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isInt32Array(value: Object): boolean--><!--Device-types-isInt32Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Int32Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isInt32Array(new Int32Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isInt8Array

```TypeScript
isInt8Array(value: Object): boolean
```

判断入参是否为 Int8Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isInt8Array(value: Object): boolean--><!--Device-types-isInt8Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Int8Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isInt8Array(new Int8Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isMap

```TypeScript
isMap(value: Object): boolean
```

判断入参是否为 Map 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isMap(value: Object): boolean--><!--Device-types-isMap(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Map 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isMap(new Map());
console.info("result = " + result);
// 输出结果：result = true

```

## isMapIterator

```TypeScript
isMapIterator(value: Object): boolean
```

判断入参是否为 MapIterator 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isMapIterator(value: Object): boolean--><!--Device-types-isMapIterator(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 MapIterator 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
const map : Map<number,number> = new Map();
let result = type.isMapIterator(map.keys());
console.info("result = " + result);
// 输出结果：result = true

```

## isModuleNamespaceObject

```TypeScript
isModuleNamespaceObject(value: Object): boolean
```

判断入参是否为模块命名空间对象。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isModuleNamespaceObject(value: Object): boolean--><!--Device-types-isModuleNamespaceObject(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为模块命名空间对象，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
// /entry/src/main/ets/pages/test.ts
export function func() {
  console.info("hello world");
}

```

```TypeScript
import * as nameSpace from './test';

let type = new util.types();
let result = type.isModuleNamespaceObject(nameSpace);
console.info("result = " + result);
// 输出结果：result = true

```

## isNativeError

```TypeScript
isNativeError(value: Object): boolean
```

判断入参是否为 Error 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isNativeError(value: Object): boolean--><!--Device-types-isNativeError(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Error 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isNativeError(new TypeError());
console.info("result = " + result);
// 输出结果：result = true

```

## isNumberObject

```TypeScript
isNumberObject(value: Object): boolean
```

判断入参是否为 Number 类型。

> **NOTE**  
>  
> 本接口从 API version 8 起支持，从 API version 14 起废弃。无替代接口。

**起始版本：** 8

**废弃版本：** 14

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isNumberObject(value: Object): boolean--><!--Device-types-isNumberObject(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Number 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isNumberObject(new Number(0));
console.info("result = " + result);
// 输出结果：result = true

```

## isPromise

```TypeScript
isPromise(value: Object): boolean
```

判断入参是否为 promise。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isPromise(value: Object): boolean--><!--Device-types-isPromise(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 promise，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isPromise(Promise.resolve(1));
console.info("result = " + result);
// 输出结果：result = true

```

## isProxy

```TypeScript
isProxy(value: Object): boolean
```

判断入参是否为 proxy。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isProxy(value: Object): boolean--><!--Device-types-isProxy(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 proxy，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
class Target{
}
let type = new util.types();
const target : Target = {};
const proxy = new Proxy(target, target);
let result = type.isProxy(proxy);
console.info("result = " + result);
// 输出结果：result = true

```

## isRegExp

```TypeScript
isRegExp(value: Object): boolean
```

判断入参是否为 RegExp 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isRegExp(value: Object): boolean--><!--Device-types-isRegExp(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 RegExp 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isRegExp(new RegExp('abc'));
console.info("result = " + result);
// 输出结果：result = true

```

## isSet

```TypeScript
isSet(value: Object): boolean
```

判断入参是否为 Set 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isSet(value: Object): boolean--><!--Device-types-isSet(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Set 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let set : Set<number> = new Set();
let result = type.isSet(set);
console.info("result = " + result);
// 输出结果：result = true

```

## isSetIterator

```TypeScript
isSetIterator(value: Object): boolean
```

判断入参是否为 SetIterator 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isSetIterator(value: Object): boolean--><!--Device-types-isSetIterator(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 SetIterator 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
const set : Set<number> = new Set();
let result = type.isSetIterator(set.keys());
console.info("result = " + result);
// 输出结果：result = true

```

## isSharedArrayBuffer

```TypeScript
isSharedArrayBuffer(value: Object): boolean
```

判断入参是否为 SharedArrayBuffer 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isSharedArrayBuffer(value: Object): boolean--><!--Device-types-isSharedArrayBuffer(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 SharedArrayBuffer 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isSharedArrayBuffer(new SharedArrayBuffer(0));
console.info("result = " + result);
// 输出结果：result = true

```

## isStringObject

```TypeScript
isStringObject(value: Object): boolean
```

判断入参是否为字符串对象。

> **NOTE**  
>  
> 本接口从 API version 8 起支持，从 API version 14 起废弃。无替代接口。

**起始版本：** 8

**废弃版本：** 14

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isStringObject(value: Object): boolean--><!--Device-types-isStringObject(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为字符串对象，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isStringObject(new String('foo'));
console.info("result = " + result);
// 输出结果：result = true

```

## isSymbolObject

```TypeScript
isSymbolObject(value: Object): boolean
```

判断入参是否为 symbol 对象。

> **NOTE**  
>  
> 本接口从 API version 8 起支持，从 API version 14 起废弃。无替代接口。

**起始版本：** 8

**废弃版本：** 14

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isSymbolObject(value: Object): boolean--><!--Device-types-isSymbolObject(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 symbol 对象，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
// /entry/src/main/ets/pages/test.ts
export const symbols = Symbol('foo');

```

```TypeScript
import { symbols } from './test'

let type = new util.types();
let result = type.isSymbolObject(Object(symbols));
console.info("result = " + result);
// 输出结果：result = true

```

## isTypedArray

```TypeScript
isTypedArray(value: Object): boolean
```

判断入参是否为 TypedArray 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isTypedArray(value: Object): boolean--><!--Device-types-isTypedArray(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 TypedArray 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isTypedArray(new Float64Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isUint16Array

```TypeScript
isUint16Array(value: Object): boolean
```

判断入参是否为 Uint16Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isUint16Array(value: Object): boolean--><!--Device-types-isUint16Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Uint16Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isUint16Array(new Uint16Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isUint32Array

```TypeScript
isUint32Array(value: Object): boolean
```

判断入参是否为 Uint32Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isUint32Array(value: Object): boolean--><!--Device-types-isUint32Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Uint32Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isUint32Array(new Uint32Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isUint8Array

```TypeScript
isUint8Array(value: Object): boolean
```

判断入参是否为 Uint8Array 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isUint8Array(value: Object): boolean--><!--Device-types-isUint8Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Uint8Array 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isUint8Array(new Uint8Array([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isUint8ClampedArray

```TypeScript
isUint8ClampedArray(value: Object): boolean
```

判断入参是否为 Uint8ClampedArray 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isUint8ClampedArray(value: Object): boolean--><!--Device-types-isUint8ClampedArray(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 Uint8ClampedArray 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isUint8ClampedArray(new Uint8ClampedArray([]));
console.info("result = " + result);
// 输出结果：result = true

```

## isWeakMap

```TypeScript
isWeakMap(value: Object): boolean
```

判断入参是否为 WeakMap 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isWeakMap(value: Object): boolean--><!--Device-types-isWeakMap(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 WeakMap 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let value : WeakMap<object, number> = new WeakMap();
let result = type.isWeakMap(value);
console.info("result = " + result);
// 输出结果：result = true

```

## isWeakSet

```TypeScript
isWeakSet(value: Object): boolean
```

判断入参是否为 WeakSet 类型。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-types-isWeakSet(value: Object): boolean--><!--Device-types-isWeakSet(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | 要检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果入参为 WeakSet 类型，则返回 **true**；否则返回 **false**。 |

**示例：**

```TypeScript
let type = new util.types();
let result = type.isWeakSet(new WeakSet());
console.info("result = " + result);
// 输出结果：result = true

```

