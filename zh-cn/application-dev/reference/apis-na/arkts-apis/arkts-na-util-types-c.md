# types

Check the type of parameter.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-util-class types--><!--Device-util-class types-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor()
```

The types constructor

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-constructor()--><!--Device-types-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## isAnyArrayBuffer

```TypeScript
isAnyArrayBuffer(value: Object): boolean
```

Check whether the entered value is of arraybuffer or sharedarraybuffer type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isAnyArrayBuffer(value: Object): boolean--><!--Device-types-isAnyArrayBuffer(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A ArrayBuffer or SharedArrayBuffer value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in ArrayBuffer or SharedArrayBuffer instance. |

## isArrayBuffer

```TypeScript
isArrayBuffer(value: Object): boolean
```

Check whether the entered value is of arraybuffer type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isArrayBuffer(value: Object): boolean--><!--Device-types-isArrayBuffer(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A arraybuffer value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in ArrayBuffer instance. This does not include SharedArrayBuffer instances. Usually, it is desirable to test for both; See isAnyArrayBuffer() for that. |

## isArrayBufferView

```TypeScript
isArrayBufferView(value: Object): boolean
```

Check whether the type is included in the isAnyArrayBuffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isArrayBufferView(value: Object): boolean--><!--Device-types-isArrayBufferView(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A included in the isAnyArrayBuffer value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is an instance of one of the ArrayBuffer views, such as typed array objects or DataView. |

## isAsyncFunction

```TypeScript
isAsyncFunction(value: Object): boolean
```

Check whether the value entered is an asynchronous function type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isAsyncFunction(value: Object): boolean--><!--Device-types-isAsyncFunction(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A async function value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is an async function. This only reports back what the JavaScript engine is seeing; in particular, the return value may not match the original source code if a transpilation tool was used. |

## isBigInt64Array

```TypeScript
isBigInt64Array(value: Object): boolean
```

Check whether the entered value is of bigint64array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isBigInt64Array(value: Object): boolean--><!--Device-types-isBigInt64Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A BigInt64Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a BigInt64Array instance. |

## isBigUint64Array

```TypeScript
isBigUint64Array(value: Object): boolean
```

Check whether the entered value is of biguint64array array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isBigUint64Array(value: Object): boolean--><!--Device-types-isBigUint64Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A BigUint64Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a BigUint64Array instance. |

## isDataView

```TypeScript
isDataView(value: Object): boolean
```

Check whether the entered value is of DataView type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isDataView(value: Object): boolean--><!--Device-types-isDataView(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A DataView value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in DataView instance. |

## isDate

```TypeScript
isDate(value: Object): boolean
```

Check whether the entered value is of type date.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isDate(value: Object): boolean--><!--Device-types-isDate(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Date value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Date instance. |

## isFloat32Array

```TypeScript
isFloat32Array(value: Object): boolean
```

Check whether the entered value is of float32array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isFloat32Array(value: Object): boolean--><!--Device-types-isFloat32Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Float32Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Float32Array instance. |

## isFloat64Array

```TypeScript
isFloat64Array(value: Object): boolean
```

Check whether the entered value is of float64array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isFloat64Array(value: Object): boolean--><!--Device-types-isFloat64Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Float64Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Float64Array instance. |

## isInt16Array

```TypeScript
isInt16Array(value: Object): boolean
```

Check whether the entered value is the int16array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isInt16Array(value: Object): boolean--><!--Device-types-isInt16Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Int16Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Int16Array instance. |

## isInt32Array

```TypeScript
isInt32Array(value: Object): boolean
```

Check whether the entered value is the int32array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isInt32Array(value: Object): boolean--><!--Device-types-isInt32Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Int32Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Int32Array instance. |

## isInt8Array

```TypeScript
isInt8Array(value: Object): boolean
```

Check whether the entered value is of int8array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isInt8Array(value: Object): boolean--><!--Device-types-isInt8Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Int8Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Int8Array instance. |

## isMap

```TypeScript
isMap(value: Object): boolean
```

Check whether the entered value is of map type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isMap(value: Object): boolean--><!--Device-types-isMap(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Map value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Map instance. |

## isMapIterator

```TypeScript
isMapIterator(value: Object): boolean
```

Check whether the entered value is the iterator type of map.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isMapIterator(value: Object): boolean--><!--Device-types-isMapIterator(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Map iterator value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is an iterator returned for a built-in Map instance. |

## isNativeError

```TypeScript
isNativeError(value: Object): boolean
```

Check whether the value entered is of type error.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isNativeError(value: Object): boolean--><!--Device-types-isNativeError(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Error value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is an instance of a built-in Error type. |

## isPromise

```TypeScript
isPromise(value: Object): boolean
```

Check whether the entered value is of promise type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isPromise(value: Object): boolean--><!--Device-types-isPromise(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Promise value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Promise. |

## isRegExp

```TypeScript
isRegExp(value: Object): boolean
```

Check whether the entered value is of type regexp.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isRegExp(value: Object): boolean--><!--Device-types-isRegExp(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A regular expression object value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a regular expression object. |

## isSet

```TypeScript
isSet(value: Object): boolean
```

Check whether the entered value is of type set.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isSet(value: Object): boolean--><!--Device-types-isSet(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Set instance value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Set instance. |

## isSetIterator

```TypeScript
isSetIterator(value: Object): boolean
```

Check whether the entered value is the iterator type of set.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isSetIterator(value: Object): boolean--><!--Device-types-isSetIterator(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Set iterator value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is an iterator returned for a built-in Set instance. |

## isTypedArray

```TypeScript
isTypedArray(value: Object): boolean
```

Check whether the entered value is a type contained in typedarray.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isTypedArray(value: Object): boolean--><!--Device-types-isTypedArray(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A TypedArray instance value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in TypedArray instance. |

## isUint16Array

```TypeScript
isUint16Array(value: Object): boolean
```

Check whether the entered value is the uint16array array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isUint16Array(value: Object): boolean--><!--Device-types-isUint16Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Uint16Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Uint16Array instance. |

## isUint32Array

```TypeScript
isUint32Array(value: Object): boolean
```

Check whether the entered value is the uint32array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isUint32Array(value: Object): boolean--><!--Device-types-isUint32Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Uint32Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Uint32Array instance. |

## isUint8Array

```TypeScript
isUint8Array(value: Object): boolean
```

Check whether the entered value is the uint8array array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isUint8Array(value: Object): boolean--><!--Device-types-isUint8Array(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Uint8Array value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Uint8Array instance. |

## isUint8ClampedArray

```TypeScript
isUint8ClampedArray(value: Object): boolean
```

Check whether the entered value is the uint8clapedarray array type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isUint8ClampedArray(value: Object): boolean--><!--Device-types-isUint8ClampedArray(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A Uint8ClampedArray value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in Uint8ClampedArray instance. |

## isWeakMap

```TypeScript
isWeakMap(value: Object): boolean
```

Check whether the entered value is of type weakmap.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isWeakMap(value: Object): boolean--><!--Device-types-isWeakMap(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A WeakMap value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in WeakMap instance. |

## isWeakSet

```TypeScript
isWeakSet(value: Object): boolean
```

Check whether the entered value is of type weakset.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-types-isWeakSet(value: Object): boolean--><!--Device-types-isWeakSet(value: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | A WeakSet value |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the value is a built-in WeakSet instance. |

