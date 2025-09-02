# Working with Arrays Using JSVM-API

## Introduction

JSVM-API provides APIs for directly managing JavaScript (JS) arrays.

## Basic Concepts

JSVM-API can be used to create, access, modify, and traverse arrays. Before using JSVM-API to work with arrays, it is helpful if you understand the following concepts:

- Array creation: You can use **OH_JSVM_CreateArray** to create an array and pass it to the JS layer.
- Array-related operations: You can use the APIs provides by the JSVM module to obtain the length of a JS array, retrieve the element at the specified index, and set the element value at the specified index.
- **TypedArray**: A **TypedArray** object in JS is an array-like view of an underlying binary data buffer. It can be simply understood as an array of elements of the specified type. There is no constructor for **TypedArray** objects, but its child class constructor can be used to construct **TypedArray** data. The child classes of **TypedArray** include **Int8Array**, **Uint8Array**, **Uint8ClampedArray**, **Int16Array**, and **Int32Array**.
- **ArrayBuffer**: **ArrayBuffer** is a data struct used to represent a binary data buffer of fixed length.
- **DataView**: **DataView** is a JS view that allows a variety of number types to be read and written in an **ArrayBuffer** object.


## Available APIs

| API                        | Description                                  |
| ---------------------------- | ------------------------------------------ |
|OH_JSVM_CreateArray | Creates a JS array object.|
|OH_JSVM_CreateArrayWithLength | Creates a JS array object of the specified length.|
|OH_JSVM_CreateTypedarray | Creates a JS **TypedArray** object for an **ArrayBuffer**. The **TypedArray** object provides an array-like view over an underlying data buffer, where each element has the same underlying binary scalar data type. <br/>The parameters specified must meet the following:<br>(**length** x **size_of_element**) + **byte_offset** ≤ Array size (in bytes)<br>Otherwise, a **RangeError** exception will be thrown.<br>**size_of_element** specifies the size of the data type of the elements in the array. |
|OH_JSVM_CreateDataview | Creates a JS **DataView** object based on an existing **ArrayBuffer**. The **DataView** object provides an array-like view on the underlying data buffer. The **ArrayBuffer** allows elements of different sizes and types. <br/>The sum of **byte_length** and **byte_offset** must be less than or equal to the array size (in bytes). Otherwise, a **RangeError** exception will be thrown. |
|OH_JSVM_GetArrayLength | Obtains the length of an array.|
|OH_JSVM_GetTypedarrayInfo | Obtains information about a **TypedArray** object.|
|OH_JSVM_GetDataviewInfo | Obtains information of a **DataView** object.|
|OH_JSVM_IsArray | Checks whether a JS object is an array.|
|OH_JSVM_SetElement | Sets an element at the specified index for a JS object.|
|OH_JSVM_GetElement | Obtains the element at the specified index of a JS object.|
|OH_JSVM_HasElement | Checks whether a JS object has an element at the specified index.|
|OH_JSVM_DeleteElement | Deletes the element at the specified index from a JS object.|
|OH_JSVM_IsDataview | Checks whether a JS object is a **DataView** object.|
|OH_JSVM_IsTypedarray | Checks whether a JS object is a **TypedArray** object.|

## Example

If you are just starting out with JSVM-API, see [JSVM-API Development Process](use-jsvm-process.md). The following demonstrates only the C++ code involved in array development.

### OH_JSVM_CreateArray

Use **OH_JSVM_CreateArray** to create a JS array object.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Register the CreateArray callback.
static int DIFF_VALUE_FIVE = 5;
// Define OH_JSVM_CreateArray. 
static JSVM_Value CreateArray(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Create an empty array.
    JSVM_Value array = nullptr;
    JSVM_Status status = OH_JSVM_CreateArray(env, &array);
    // Assign values to the created array.
    for (int i = 0; i < DIFF_VALUE_FIVE; i++) {
        JSVM_Value element;
        OH_JSVM_CreateInt32(env, i, &element);
        OH_JSVM_SetElement(env, array, i, element);
    }
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM CreateArray fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM CreateArray success");
    }
    return array;
}
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = CreateArray},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named createArray and associate it with a callback. This allows the CreateArray callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"createArray", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
  function testCreateArray() {
    return createArray();
  }
  testCreateArray();
)JS";
```
### OH_JSVM_CreateArrayWithLength

Use **OH_JSVM_CreateArrayWithLength** to create a JS array object of the specified length.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_CreateArrayWithLength.
static JSVM_Value CreateArrayWithLength(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value argv[1] = {nullptr};
    JSVM_Value result = nullptr;
    // Obtain the callback information.
    OH_JSVM_GetCbInfo(env, info, &argc, argv, nullptr, nullptr);
    // Obtain the array length passed.
    int32_t length;
    OH_JSVM_GetValueInt32(env, argv[0], &length);
    // Call OH_JSVM_CreateArrayWithLength to create an array with the specified length.
    JSVM_Status status = OH_JSVM_CreateArrayWithLength(env, length, &result);
    if (status == JSVM_OK) {
        // Set an element in the created array.
        for (int32_t i = 0; i < length; i++) {
            JSVM_Value value;
            OH_JSVM_CreateInt32(env, i, &value);
            OH_JSVM_SetElement(env, result, i, value);
        }
        OH_LOG_INFO(LOG_APP, "JSVM CreateArrayWithLength success");
    } else {
        OH_LOG_ERROR(LOG_APP, "JSVM CreateArrayWithLength fail");
    }
    return result;
}
// Register the CreateArrayWithLength callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = CreateArrayWithLength},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named createArrayWithLength and associate it with a callback. This allows the CreateArrayWithLength callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"createArrayWithLength", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
let num = 7;
function testCreateArrayWithLength(num){
    return createArrayWithLength(num);
}
testCreateArrayWithLength(num);
)JS";
```

### OH_JSVM_CreateTypedarray

Use **OH_JSVM_CreateTypedarray** to create a JS **TypedArray** object based on an **ArrayBuffer**. The **TypedArray** object provides an array-like view over an underlying data buffer, where each element has the same underlying binary scalar data type.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_CreateTypedarray.
static int DIFF_VALUE_THREE = 3;
static JSVM_Value CreateTypedArray(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    int32_t typeNum;
    OH_JSVM_GetValueInt32(env, args[0], &typeNum);
    JSVM_TypedarrayType arrayType;
    // Set the element size.
    size_t elementSize = 0;
    // Convert the value to the JSVM_TypedarrayType type.
    arrayType = static_cast<JSVM_TypedarrayType>(typeNum);
    switch (typeNum) {
    case JSVM_INT8_ARRAY:
    case JSVM_UINT8_ARRAY:
    case JSVM_UINT8_CLAMPED_ARRAY:
        elementSize = sizeof(int8_t);
        break;
    case JSVM_INT16_ARRAY:
    case JSVM_UINT16_ARRAY:
        elementSize = sizeof(int16_t);
        break;
    case JSVM_INT32_ARRAY:
    case JSVM_UINT32_ARRAY:
        elementSize = sizeof(int32_t);
        break;
    case JSVM_FLOAT32_ARRAY:
        elementSize = sizeof(float);
        break;
    case JSVM_FLOAT64_ARRAY:
        elementSize = sizeof(double);
        break;
    case JSVM_BIGINT64_ARRAY:
    case JSVM_BIGUINT64_ARRAY:
        elementSize = sizeof(int64_t);
        break;
    default:
        // By default, an array of the JSVM_INT8_ARRAY type is created.
        arrayType = JSVM_INT8_ARRAY;
        elementSize = sizeof(int8_t);
        break;
    }
    size_t length = DIFF_VALUE_THREE;
    JSVM_Value arrayBuffer = nullptr;
    JSVM_Value typedArray = nullptr;
    void *data;
    // Create an ArrayBuffer object.
    OH_JSVM_CreateArraybuffer(env, length * elementSize, (void **)&data, &arrayBuffer);
    // Create a TypedArray object of the specified type.
    JSVM_Status status = OH_JSVM_CreateTypedarray(env, arrayType, length, arrayBuffer, 0, &typedArray);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM CreateTypedArray fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM CreateTypedArray success");
    }
    return typedArray;
}
// Register the CreateTypedArray callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = CreateTypedArray},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named createTypedArray and associate it with a callback. This allows the CreateTypedArray callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"createTypedArray", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
const type = {
    INT8_ARRAY: 0,
    UINT8_ARRAY: 1,
    UINT8_CLAMPED_ARRAY: 2,
    INT16_ARRAY: 3,
    UINT16_ARRAY: 4,
    INT32_ARRAY: 5,
    UINT32_ARRAY: 6,
    FLOAT32_ARRAY: 7,
    FLOAT64_ARRAY: 8,
    BIGINT64_ARRAY: 9,
    BIGUINT64_ARRAY: 10
};
createTypedArray(type.INT8_ARRAY);
createTypedArray(type.INT32_ARRAY);
)JS";
```

### OH_JSVM_CreateDataview

Use **OH_JSVM_CreateDataview** to create a JS **DataView** object based on an **ArrayBuffer**. The **DataView** object provides an array-like view over an underlying data buffer.

CPP code:

```cpp
static int DIFF_VALUE_FOUR = 4;
static int DIFF_VALUE_TWELVE = 12;
// Define OH_JSVM_CreateDataview.
static JSVM_Value CreateDataView(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Obtain the two parameters passed from JS.
    size_t argc = 2;
    JSVM_Value args[2] = {nullptr};
    JSVM_Value arrayBuffer = nullptr;
    JSVM_Value result = nullptr;
    // Byte length of DataView.
    size_t byteLength = DIFF_VALUE_TWELVE;
    // Offset of the byte.
    size_t byteOffset = DIFF_VALUE_FOUR;
    // Obtain the parameters of the callback.
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // Convert the parameter into the object type.
    OH_JSVM_CoerceToObject(env, args[0], &arrayBuffer);
    // Create a DataView object with the specified byte length and offset.
    JSVM_Status status = OH_JSVM_CreateDataview(env, byteLength, arrayBuffer, byteOffset, &result);
    // Obtain the pointer to the DataView object and the length.
    uint8_t *data = nullptr;
    size_t length = 0;
    // Assign values to DataView.
    for (size_t i = 0; i < length; i++) {
        data[i] = static_cast<uint8_t>(i + 1);
    }
    int32_t infoType;
    OH_JSVM_GetValueInt32(env, args[1], &infoType);
    size_t returnLength;
    JSVM_Value returnArrayBuffer = nullptr;
    size_t returnOffset;
    enum InfoType { BYTE_LENGTHE, ARRAY_BUFFERE, BYTE_OFFSET };
    // Obtain DataView information.
    OH_JSVM_GetDataviewInfo(env, result, &returnLength, (void **)&data, &returnArrayBuffer, &returnOffset);
    JSVM_Value returnResult = nullptr;
    switch (infoType) {
    case BYTE_LENGTHE:
        JSVM_Value len;
        OH_JSVM_CreateInt32(env, returnLength, &len);
        returnResult = len;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM CreateDataView fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM CreateDataView success, returnLength: %{public}d", returnLength);
        }
        break;
    case ARRAY_BUFFERE:
        bool isArraybuffer;
        OH_JSVM_IsArraybuffer(env, returnArrayBuffer, &isArraybuffer);
        JSVM_Value isArray;
        OH_JSVM_GetBoolean(env, isArraybuffer, &isArray);
        returnResult = isArray;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM CreateDataView fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM CreateDataView success, isArraybuffer: %{public}d", isArraybuffer);
        }
        break;
    case BYTE_OFFSET:
        JSVM_Value offset;
        OH_JSVM_CreateInt32(env, returnOffset, &offset);
        returnResult = offset;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM CreateDataView fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM CreateDataView success, returnOffset: %{public}d", returnOffset);
        }
        break;
    default:
        break;
    }
    return returnResult;
}
// Register the CreateDataView callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = CreateDataView},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named createDataView and associate it with a callback. This allows the CreateDataView callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"createDataView", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
 let BYTE_LENGTH = 0;
 createDataView(new ArrayBuffer(16), BYTE_LENGTH);
 let IS_ARRAYBUFFER = 1;
 createDataView(new ArrayBuffer(16), IS_ARRAYBUFFER);
 let BYTE_OFFSET = 2;
 createDataView(new ArrayBuffer(16), BYTE_OFFSET);
)JS";
```

### OH_JSVM_GetArrayLength

Use **OH_JSVM_GetArrayLength** to obtain the length of an array.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_GetArrayLength.
static JSVM_Value GetArrayLength(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    JSVM_Value result = nullptr;
    uint32_t length;
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // Check whether the parameter is an array.
    bool isArray = false;
    OH_JSVM_IsArray(env, args[0], &isArray);
    if (!isArray) {
        OH_LOG_INFO(LOG_APP, "JSVM Argument must be an array");
        return nullptr;
    }
    OH_JSVM_GetArrayLength(env, args[0], &length);
    // Create a return value.
    OH_JSVM_CreateInt32(env, length, &result);
    OH_LOG_INFO(LOG_APP, "JSVM length: %{public}d", length);
    return result;
}
// Register the GetArrayLength callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = GetArrayLength},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named getArrayLength and associate it with a callback. This allows the GetArrayLength callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"getArrayLength", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
let data = [0, 1, 2, 3, 4, 5];
getArrayLength(data);
)JS";
```

### OH_JSVM_GetTypedarrayInfo

Use **OH_JSVM_GetTypedarrayInfo** to obtain information about a **TypedArray** object.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_GetTypedarrayInfo.
static JSVM_Value GetTypedArrayInfo(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Obtain and parse the parameters passed to a JS callback within a JSVM. The first parameter is the TypedArray type of the information to obtain, and the second parameter is the enums of the information type to obtain.
    size_t argc = 2;
    JSVM_Value args[2] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);

    // Convert the second parameter to the int32 type for comparison.
    int32_t infoTypeParam;
    OH_JSVM_GetValueInt32(env, args[1], &infoTypeParam);
    // Define the infoType enums in the same sequence as those in ArkTS.
    enum InfoType { INFO_TYPE, INFO_LENGTH, INFO_ARRAY_BUFFER, INFO_BYTE_OFFSET };
    void *data;
    JSVM_TypedarrayType type;
    size_t byteOffset, length;
    JSVM_Value arrayBuffer = nullptr;
    // Call OH_JSVM_GetTypedarrayInfo to obtain TypedArray information.
    JSVM_Status status = OH_JSVM_GetTypedarrayInfo(env, args[0], &type, &length, &data, &arrayBuffer, &byteOffset);
    JSVM_Value result = nullptr;
    // Return the property value based on the property name.
    switch (infoTypeParam) {
    case INFO_TYPE:
        // If the input parameter is TypedArray data of the int8 type, the value type is JSVM_INT8_ARRAY.
        JSVM_Value int8_type;
        OH_JSVM_GetBoolean(env, type == JSVM_INT8_ARRAY, &int8_type);
        result = int8_type;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM GetTypedArrayInfo fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM GetTypedArrayInfo success, JSVM_INT8_ARRAY: %{public}d", type == JSVM_INT8_ARRAY);
        }
        break;
    case INFO_LENGTH:
        // Number of elements in the TypedArray object.
        JSVM_Value jsvmLength;
        OH_JSVM_CreateInt32(env, length, &jsvmLength);
        result = jsvmLength;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM GetTypedArrayInfo fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM GetTypedArrayInfo success, length: %{public}d", length);
        }
        break;
    case INFO_BYTE_OFFSET:
        // Byte offset of the first TypedArray element in the native array.
        JSVM_Value jsvmOffset;
        OH_JSVM_CreateInt32(env, byteOffset, &jsvmOffset);
        result = jsvmOffset;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM GetTypedArrayInfo fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM GetTypedArrayInfo success, byteOffset: %{public}d", byteOffset);
        }
        break;
    case INFO_ARRAY_BUFFER:
        // ArrayBuffer under TypedArray.
        bool isArrayBuffer;
        OH_JSVM_IsArraybuffer(env, arrayBuffer, &isArrayBuffer);
        JSVM_Value isArray;
        OH_JSVM_GetBoolean(env, isArrayBuffer, &isArray);
        result = isArray;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM GetTypedArrayInfo fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM GetTypedArrayInfo success, isArrayBuffer: %{public}d", isArrayBuffer);
        }
        break;
    default:
        break;
    }
    return result;
}
// Register the GetTypedArrayInfo callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = GetTypedArrayInfo},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named getTypedArrayInfo and associate it with a callback. This allows the GetTypedArrayInfo callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"getTypedArrayInfo", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
// is JSVM_INT8_ARRAY
getTypedArrayInfo(new Int8Array(3), 0);
// Length
getTypedArrayInfo(new Int8Array(5), 1);
// is_arraybuffer
getTypedArrayInfo(new Int8Array(5), 2);
// Byte offset.
getTypedArrayInfo(new Int8Array(1), 3);
)JS";
```

### OH_JSVM_GetDataviewInfo

Use **OH_JSVM_GetDataviewInfo** to obtain information about a **DataView** object.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_GetDataviewInfo.
static JSVM_Value GetDataViewInfo(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Obtain and parse the parameters passed to a JS callback within a JSVM. The first parameter is the DataView type of the information to obtain, and the second parameter is the enums of the information type to obtain.
    size_t argc = 2;
    JSVM_Value args[2] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // Convert the second parameter to an int32 number.
    int32_t infoType;
    OH_JSVM_GetValueInt32(env, args[1], &infoType);
    size_t byteLength;
    void *data;
    JSVM_Value arrayBuffer = nullptr;
    size_t byteOffset;
    // Define the infoType enums in the same sequence as those in ArkTS.
    enum infoTypeEnum { BYTE_LENGTHE, ARRAY_BUFFERE, BYTE_OFFSET };
    // Obtain DataView information.
    JSVM_Status status = OH_JSVM_GetDataviewInfo(env, args[0], &byteLength, &data, &arrayBuffer, &byteOffset);
    JSVM_Value result = nullptr;
    switch (infoType) {
    case BYTE_LENGTHE:
        // Return the length of DataView.
        JSVM_Value len;
        OH_JSVM_CreateInt32(env, byteLength, &len);
        result = len;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM GetDataViewInfo fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM GetDataViewInfo success, byteLength: %{public}d", byteLength);
        }
        break;
    case ARRAY_BUFFERE:
        // Check whether data in Info of DataView is an ArrayBuffer object.
        bool isArrayBuffer;
        OH_JSVM_IsArraybuffer(env, arrayBuffer, &isArrayBuffer);
        JSVM_Value isArray;
        OH_JSVM_GetBoolean(env, isArrayBuffer, &isArray);
        result = isArray;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM GetDataViewInfo fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM GetDataViewInfo success, isArrayBuffer: %{public}d", isArrayBuffer);
        }
        break;
    case BYTE_OFFSET:
        // Return the offset of DataView.
        JSVM_Value offset;
        OH_JSVM_CreateInt32(env, byteOffset, &offset);
        result = offset;
        if (status != JSVM_OK) {
            OH_LOG_ERROR(LOG_APP, "JSVM GetDataViewInfo fail");
        } else {
            OH_LOG_INFO(LOG_APP, "JSVM GetDataViewInfo success, byteOffset: %{public}d", byteOffset);
        }
        break;
    default:
        break;
    }
    return result;
}
// Register the GetDataViewInfo callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = GetDataViewInfo},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named getDataViewInfo and associate it with a callback. This allows the GetDataViewInfo callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"getDataViewInfo", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
// Byte length.
getDataViewInfo(new DataView(new Int8Array([2,5]).buffer), 0);
// Check whether the data is an ArrayBuffer object.
let data = 'a';
let isarraybuffer = 1;
getDataViewInfo(data, isarraybuffer);
// Check whether the data is an ArrayBuffer object.
data = new DataView(new Int8Array([2,5,3]).buffer);
isarraybuffer = 1;
getDataViewInfo(data, isarraybuffer);
// byte_offset
data = new DataView(new Int8Array([2,5,3]).buffer);
isarraybuffer = 2;
getDataViewInfo(data, isarraybuffer);
)JS";
```

### OH_JSVM_IsArray

Use **OH_JSVM_IsArray** to check whether a JS object is an array.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_IsArray.
static JSVM_Value IsArray(JSVM_Env env, JSVM_CallbackInfo info)
{
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    bool result = false;
    JSVM_Status status = OH_JSVM_IsArray(env, args[0], &result);
    JSVM_Value returnValue = nullptr;
    OH_JSVM_GetBoolean(env, result, &returnValue);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM IsArray fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM IsArray success, IsArray: %{public}d", result);
    }
    return returnValue;
}
// Register the IsArray callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = IsArray},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named isArray and associate it with a callback. This allows the IsArray callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"isArray", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
let data = [1, 2, 3, 4, 5];
isArray(data);
)JS";
```

### OH_JSVM_SetElement

Use **OH_JSVM_SetElement** to set an element at the specified index for a JS object.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_SetElement.
static int DIFF_VALUE_THREE = 3;
static JSVM_Value SetElement(JSVM_Env env, JSVM_CallbackInfo info) {
    size_t argc = DIFF_VALUE_THREE;
    JSVM_Value args[3] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    int32_t index = 0;
    OH_JSVM_GetValueInt32(env, args[1], &index);
    JSVM_Status status = OH_JSVM_SetElement(env, args[0], index, args[2]);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM SetElement fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM SetElement success");
    }
    return args[0];
}
// Register the SetElement callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = SetElement},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named setElement and associate it with a callback. This allows the SetElement callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"setElement", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
setElement(3);
)JS";
```

### OH_JSVM_GetElement

Use **OH_JSVM_GetElement** to obtain the element at the specified index of a JS object.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_GetElement.
static JSVM_Value GetElement(JSVM_Env env, JSVM_CallbackInfo info) {
    // Obtain the two parameters passed from JS.
    size_t argc = 2;
    JSVM_Value args[2] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // Obtain the index value of the element.
    uint32_t index;
    OH_JSVM_GetValueUint32(env, args[1], &index);
    // Obtain the element value at the index and store it in result.
    JSVM_Value result = nullptr;
    JSVM_Status status = OH_JSVM_GetElement(env, args[0], index, &result);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM GetElement fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM GetElement success");
    }
    return result;
}
// Register the GetElement callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = GetElement},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named getElement and associate it with a callback. This allows the GetElement callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"getElement", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
let arr = [10, 'hello', null, true];
getElement(arr, 3);
)JS";
```

### OH_JSVM_HasElement

Use **OH_JSVM_HasElement** to check whether a JS object has an element at the specified index.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_HasElement.
static JSVM_Value HasElement(JSVM_Env env, JSVM_CallbackInfo info)
{
    // Obtain the two parameters passed from JS.
    size_t argc = 2;
    JSVM_Value args[2] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // Obtain the index of the element to be checked.
    uint32_t index;
    OH_JSVM_GetValueUint32(env, args[1], &index);
    // Check whether the element exists based on the given index.
    bool hasElement = true;
    JSVM_Status status = OH_JSVM_HasElement(env, args[0], index, &hasElement);
    // Convert the boolean value to JSVM_Value and return it.
    JSVM_Value result = nullptr;
    OH_JSVM_GetBoolean(env, hasElement, &result);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM hasElement fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM hasElement: %{public}d", hasElement);
    }
    return result;
}
// Register the HasElement callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = HasElement},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named hasElement and associate it with a callback. This allows the HasElement callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"hasElement", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
let arr = [10, 'hello', null, true];
hasElement(arr, 0);
hasElement(arr, 4);
)JS";
```

### OH_JSVM_DeleteElement

Use **OH_JSVM_DeleteElement** to delete the element at the specified index from a JS object.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_DeleteElement.
static JSVM_Value DeleteElement(JSVM_Env env, JSVM_CallbackInfo info) {
    // Obtain the two parameters passed from JS.
    size_t argc = 2;
    JSVM_Value args[2] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // Obtain the index of the element to delete.
    uint32_t index;
    OH_JSVM_GetValueUint32(env, args[1], &index);
    // Delete the element at the specified index.
    bool deleted = true;
    JSVM_Status status = OH_JSVM_DeleteElement(env, args[0], index, &deleted);
    // Convert the boolean value to JSVM_Value and return it.
    JSVM_Value result = nullptr;
    OH_JSVM_GetBoolean(env, deleted, &result);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM DeleteElement fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM DeleteElement: %{public}d", deleted);
    }
    return result;
}
// Register the DeleteElement callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = DeleteElement},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named deleteElement and associate it with a callback. This allows the DeleteElement callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"deleteElement", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
let arr = [10, 'hello', null, true];
deleteElement(arr, 0);
)JS";
```

### OH_JSVM_IsDataview

Use **OH_JSVM_IsDataview** to check whether a JS object is a **DataView** object.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_IsDataview.
static JSVM_Value IsDataView(JSVM_Env env, JSVM_CallbackInfo info) {
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    // Call OH_JSVM_IsDataview to check whether the input parameter is a DataView object.
    bool result = false;
    JSVM_Status status = OH_JSVM_IsDataview(env, args[0], &result);
    JSVM_Value isDateView = nullptr;
    OH_JSVM_GetBoolean(env, result, &isDateView);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM IsDataView fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM IsDataView: %{public}d", result);
    }
    return isDateView;
}
// Register the IsDataView callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = IsDataView},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named isDataView and associate it with a callback. This allows the IsDataView callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"isDataView", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
let buffer = new ArrayBuffer(16);
let dataView = new DataView(buffer);
isDataView(dataView);
)JS";
```

### OH_JSVM_IsTypedarray

Use **OH_JSVM_IsTypedarray** to check whether a JS object is a **TypedArray** object.

CPP code:

```cpp
// hello.cpp
#include "napi/native_api.h"
#include "ark_runtime/jsvm.h"
#include <hilog/log.h>
// Define OH_JSVM_IsTypedarray.
static JSVM_Value IsTypedarray(JSVM_Env env, JSVM_CallbackInfo info) {
    size_t argc = 1;
    JSVM_Value args[1] = {nullptr};
    OH_JSVM_GetCbInfo(env, info, &argc, args, nullptr, nullptr);
    bool result = false;
    JSVM_Status status = OH_JSVM_IsTypedarray(env, args[0], &result);
    JSVM_Value isTypedArray = nullptr;
    OH_JSVM_GetBoolean(env, result, &isTypedArray);
    if (status != JSVM_OK) {
        OH_LOG_ERROR(LOG_APP, "JSVM IsTypedarray fail");
    } else {
        OH_LOG_INFO(LOG_APP, "JSVM IsTypedarray: %{public}d", result);
    }
    return isTypedArray;
}
// Register the IsTypedarray callback.
static JSVM_CallbackStruct param[] = {
    {.data = nullptr, .callback = IsTypedarray},
};
static JSVM_CallbackStruct *method = param;
// Set a property descriptor named isTypedarray and associate it with a callback. This allows the IsTypedarray callback to be called from JS.
static JSVM_PropertyDescriptor descriptor[] = {
    {"isTypedarray", nullptr, method++, nullptr, nullptr, nullptr, JSVM_DEFAULT},
};
// Call the C++ code from JS.
const char *srcCallNative = R"JS(
isTypedarray(new Uint16Array([1, 2, 3, 4]));
)JS";
```
