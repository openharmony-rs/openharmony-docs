# types

```TypeScript
class types
```

Provides APIs to check different types of built-in objects, such as ArrayBuffer, Map, and Set, so as to avoid exceptions caused by type errors.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Types** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let type = new util.types();
```

## isAnyArrayBuffer

```TypeScript
isAnyArrayBuffer(value: Object): boolean
```

Checks whether the value is of the ArrayBuffer or SharedArrayBuffer type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the ArrayBuffer or SharedArrayBuffer type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isAnyArrayBuffer(new ArrayBuffer(0));
console.info("result = " + result);
// Output: result = true
```

## isArgumentsObject

```TypeScript
isArgumentsObject(value: Object): boolean
```

Checks whether the value is an **arguments** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is an **arguments** object; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
function foo() {
    let result = type.isArgumentsObject(arguments);
    console.info("result = " + result);
}
let f = foo();
// Output: result = true
```

## isArrayBuffer

```TypeScript
isArrayBuffer(value: Object): boolean
```

Checks whether the value is of the ArrayBuffer type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the ArrayBuffer type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isArrayBuffer(new ArrayBuffer(0));
console.info("result = " + result);
// Output: result = true
```

## isArrayBufferView

```TypeScript
isArrayBufferView(value: Object): boolean
```

Checks whether the value is of the ArrayBufferView type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the ArrayBufferView type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isArrayBufferView(new Int8Array([]));
console.info("result = " + result);
// Output: result = true
```

## isAsyncFunction

```TypeScript
isAsyncFunction(value: Object): boolean
```

Checks whether the value is an asynchronous function.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is an asynchronous function; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isAsyncFunction(async () => {});
console.info("result = " + result);
// Output: result = true
```

## isBigInt64Array

```TypeScript
isBigInt64Array(value: Object): boolean
```

Checks whether the value is of the BigInt64Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the BigInt64Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isBigInt64Array(new BigInt64Array([]));
console.info("result = " + result);
// Output: result = true
```

## isBigUint64Array

```TypeScript
isBigUint64Array(value: Object): boolean
```

Checks whether the value is of the BigUint64Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the BigUint64Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isBigUint64Array(new BigUint64Array([]));
console.info("result = " + result);
// Output: result = true
```

## isBooleanObject

```TypeScript
isBooleanObject(value: Object): boolean
```

Checks whether the value is of the Boolean type.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 14. No substitute is provided.

**Since:** 8

**Deprecated since:** 14

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Boolean type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isBooleanObject(new Boolean(true));
console.info("result = " + result);
// Output: result = true
```

## isBoxedPrimitive

```TypeScript
isBoxedPrimitive(value: Object): boolean
```

Checks whether the value is of the Boolean, Number, String, or Symbol type.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 14. No substitute is provided.

**Since:** 8

**Deprecated since:** 14

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Boolean, Number, String, or Symbol type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isBoxedPrimitive(new Boolean(false));
console.info("result = " + result);
// Output: result = true
```

## isDataView

```TypeScript
isDataView(value: Object): boolean
```

Checks whether the value is of the DataView type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the DataView type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
const ab = new ArrayBuffer(20);
let result = type.isDataView(new DataView(ab));
console.info("result = " + result);
// Output: result = true
```

## isDate

```TypeScript
isDate(value: Object): boolean
```

Checks whether the value is of the Date type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Date type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isDate(new Date());
console.info("result = " + result);
// Output: result = true
```

## isExternal

```TypeScript
isExternal(value: Object): boolean
```

Checks whether the value is of the native external type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the native external type; otherwise, **false** is returned. |

**Examples**

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
// The code for module registration is omitted here. You may need to register the Testexternal method.
...
```

```TypeScript
import testNapi from 'libentry.so';

let type = new util.types();
const data = testNapi.testexternal();
let result = type.isExternal(data);

let result01 = type.isExternal(true);
console.info("result = " + result);
console.info("result01 = " + result01);
// Output: result = true
// Output: result01 = false
```

## isFloat32Array

```TypeScript
isFloat32Array(value: Object): boolean
```

Checks whether the value is of the Float32Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Float32Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isFloat32Array(new Float32Array());
console.info("result = " + result);
// Output: result = true
```

## isFloat64Array

```TypeScript
isFloat64Array(value: Object): boolean
```

Checks whether the value is of the Float64Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Float64Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isFloat64Array(new Float64Array());
console.info("result = " + result);
// Output: result = true
```

## isGeneratorFunction

```TypeScript
isGeneratorFunction(value: Object): boolean
```

Checks whether the value is a generator function.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is a generator function; otherwise, **false** is returned. |

**Examples**

```TypeScript
// /entry/src/main/ets/pages/test.ts
export function* foo() {}
```

```TypeScript
import { foo } from './test'

let type = new util.types();
let result = type.isGeneratorFunction(foo);
console.info("result = " + result);
// Output: result = true
```

## isGeneratorObject

```TypeScript
isGeneratorObject(value: Object): boolean
```

Checks whether the value is a generator object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is a generator object; otherwise, **false** is returned. |

**Examples**

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
// Output: result = true
```

## isInt16Array

```TypeScript
isInt16Array(value: Object): boolean
```

Checks whether the value is of the Int16Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Int16Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isInt16Array(new Int16Array([]));
console.info("result = " + result);
// Output: result = true
```

## isInt32Array

```TypeScript
isInt32Array(value: Object): boolean
```

Checks whether the value is of the Int32Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Int32Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isInt32Array(new Int32Array([]));
console.info("result = " + result);
// Output: result = true
```

## isInt8Array

```TypeScript
isInt8Array(value: Object): boolean
```

Checks whether the value is of the Int8Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Int8Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isInt8Array(new Int8Array([]));
console.info("result = " + result);
// Output: result = true
```

## isMap

```TypeScript
isMap(value: Object): boolean
```

Checks whether the value is of the Map type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Map type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isMap(new Map());
console.info("result = " + result);
// Output: result = true
```

## isMapIterator

```TypeScript
isMapIterator(value: Object): boolean
```

Checks whether the value is of the MapIterator type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the MapIterator type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
const map : Map<number,number> = new Map();
let result = type.isMapIterator(map.keys());
console.info("result = " + result);
// Output: result = true
```

## isModuleNamespaceObject

```TypeScript
isModuleNamespaceObject(value: Object): boolean
```

Checks whether the value is a module namespace object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is a module namespace object; otherwise, **false** is returned. |

**Examples**

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
// Output: result = true
```

## isNativeError

```TypeScript
isNativeError(value: Object): boolean
```

Checks whether the value is of the Error type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Error type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isNativeError(new TypeError());
console.info("result = " + result);
// Output: result = true
```

## isNumberObject

```TypeScript
isNumberObject(value: Object): boolean
```

Checks whether the value is of the Number type.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 14. No substitute is provided.

**Since:** 8

**Deprecated since:** 14

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Number type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isNumberObject(new Number(0));
console.info("result = " + result);
// Output: result = true
```

## isPromise

```TypeScript
isPromise(value: Object): boolean
```

Checks whether the value is a promise.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is a promise; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isPromise(Promise.resolve(1));
console.info("result = " + result);
// Output: result = true
```

## isProxy

```TypeScript
isProxy(value: Object): boolean
```

Checks whether the value is a proxy.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is a proxy; otherwise, **false** is returned. |

**Examples**

```TypeScript
class Target{
}
let type = new util.types();
const target : Target = {};
const proxy = new Proxy(target, target);
let result = type.isProxy(proxy);
console.info("result = " + result);
// Output: result = true
```

## isRegExp

```TypeScript
isRegExp(value: Object): boolean
```

Checks whether the value is of the RegExp type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the RegExp type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isRegExp(new RegExp('abc'));
console.info("result = " + result);
// Output: result = true
```

## isSet

```TypeScript
isSet(value: Object): boolean
```

Checks whether the value is of the Set type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Set type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let set : Set<number> = new Set();
let result = type.isSet(set);
console.info("result = " + result);
// Output: result = true
```

## isSetIterator

```TypeScript
isSetIterator(value: Object): boolean
```

Checks whether the value is of the SetIterator type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the SetIterator type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
const set : Set<number> = new Set();
let result = type.isSetIterator(set.keys());
console.info("result = " + result);
// Output: result = true
```

## isSharedArrayBuffer

```TypeScript
isSharedArrayBuffer(value: Object): boolean
```

Checks whether the value is of the SharedArrayBuffer type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the SharedArrayBuffer type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isSharedArrayBuffer(new SharedArrayBuffer(0));
console.info("result = " + result);
// Output: result = true
```

## isStringObject

```TypeScript
isStringObject(value: Object): boolean
```

Checks whether the value is a string object.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 14. No substitute is provided.

**Since:** 8

**Deprecated since:** 14

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is a string object; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isStringObject(new String('foo'));
console.info("result = " + result);
// Output: result = true
```

## isSymbolObject

```TypeScript
isSymbolObject(value: Object): boolean
```

Checks whether the value is a symbol object.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 14. No substitute is provided.

**Since:** 8

**Deprecated since:** 14

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is a symbol object; otherwise, **false** is returned. |

**Examples**

```TypeScript
// /entry/src/main/ets/pages/test.ts
export const symbols = Symbol('foo');
```

```TypeScript
import { symbols } from './test'

let type = new util.types();
let result = type.isSymbolObject(Object(symbols));
console.info("result = " + result);
// Output: result = true
```

## isTypedArray

```TypeScript
isTypedArray(value: Object): boolean
```

Checks whether the value is of the TypedArray type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the TypedArray type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isTypedArray(new Float64Array([]));
console.info("result = " + result);
// Output: result = true
```

## isUint16Array

```TypeScript
isUint16Array(value: Object): boolean
```

Checks whether the value is of the Uint16Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Uint16Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isUint16Array(new Uint16Array([]));
console.info("result = " + result);
// Output: result = true
```

## isUint32Array

```TypeScript
isUint32Array(value: Object): boolean
```

Checks whether the value is of the Uint32Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Uint32Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isUint32Array(new Uint32Array([]));
console.info("result = " + result);
// Output: result = true
```

## isUint8Array

```TypeScript
isUint8Array(value: Object): boolean
```

Checks whether the value is of the Uint8Array type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Uint8Array type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isUint8Array(new Uint8Array([]));
console.info("result = " + result);
// Output: result = true
```

## isUint8ClampedArray

```TypeScript
isUint8ClampedArray(value: Object): boolean
```

Checks whether the value is of the Uint8ClampedArray type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the Uint8ClampedArray type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isUint8ClampedArray(new Uint8ClampedArray([]));
console.info("result = " + result);
// Output: result = true
```

## isWeakMap

```TypeScript
isWeakMap(value: Object): boolean
```

Checks whether the value is of the WeakMap type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the WeakMap type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let value : WeakMap<object, number> = new WeakMap();
let result = type.isWeakMap(value);
console.info("result = " + result);
// Output: result = true
```

## isWeakSet

```TypeScript
isWeakSet(value: Object): boolean
```

Checks whether the value is of the WeakSet type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | Object to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the value is of the WeakSet type; otherwise, **false** is returned. |

**Examples**

```TypeScript
let type = new util.types();
let result = type.isWeakSet(new WeakSet());
console.info("result = " + result);
// Output: result = true
```
