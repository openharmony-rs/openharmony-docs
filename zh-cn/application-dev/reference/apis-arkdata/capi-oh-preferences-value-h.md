# oh_preferences_value.h
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 概述

提供访问Preferences值（PreferencesValue）对象的接口、枚举类型与数据结构。

**引用文件：** <database/preferences/oh_preferences_value.h>

**库：** libohpreferences.so

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**起始版本：** 13

**相关模块：** [Preferences](capi-preferences.md)

## 汇总

### 结构体

| 名称                                               | typedef关键字       | 描述                                  |
| -------------------------------------------------- | ------------------- | ------------------------------------- |
| [OH_PreferencesPair](capi-preferences-oh-preferencespair.md)   | OH_PreferencesPair  | 定义Preferences使用的KV数据对象类型。 |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) | OH_PreferencesValue | 定义PreferencesValue对象类型。        |

### 枚举

| 名称                                          | typedef关键字        | 描述                             |
| --------------------------------------------- | -------------------- | -------------------------------- |
| [Preference_ValueType](#preference_valuetype) | Preference_ValueType | 定义PreferencesValue的数据类型。 |

### 函数

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [const char *OH_PreferencesPair_GetKey(const OH_PreferencesPair *pairs, uint32_t index)](#oh_preferencespair_getkey) | 获取KV数据中索引对应数据的键。                               |
| [const OH_PreferencesValue *OH_PreferencesPair_GetPreferencesValue(const OH_PreferencesPair *pairs, uint32_t index)](#oh_preferencespair_getpreferencesvalue) | 获取KV数据数组中索引对应的值。                               |
| [Preference_ValueType OH_PreferencesValue_GetValueType(const OH_PreferencesValue *object)](#oh_preferencesvalue_getvaluetype) | 获取PreferencesValue对象的数据类型。                         |
| [int OH_PreferencesValue_GetInt(const OH_PreferencesValue *object, int *value)](#oh_preferencesvalue_getint) | 从PreferencesValue对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)中获取一个整型值。 |
| [int OH_PreferencesValue_GetBool(const OH_PreferencesValue *object, bool *value)](#oh_preferencesvalue_getbool) | 从PreferencesValue对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)中获取一个布尔值。 |
| [int OH_PreferencesValue_GetString(const OH_PreferencesValue *object, char **value, uint32_t *valueLen)](#oh_preferencesvalue_getstring) | 从PreferencesValue对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)中获取字符串。 |
| [void OH_PreferencesPair_Destroy(OH_PreferencesPair *pair)](#oh_preferencespair_destroy) | 销毁PreferencesPair实例对象。 |
| [OH_PreferencesValue * OH_PreferencesValue_Create(void)](#oh_preferencesvalue_create) | 创建一个PreferencesValue实例对象以及指向它的指针。 当不再需要使用指针时，请使用OH_PreferencesValue_Destroy销毁实例对象，否则会导致内存泄漏。 |
| [void OH_PreferencesValue_Destroy(OH_PreferencesValue *value)](#oh_preferencesvalue_destroy) | 销毁PreferencesValue实例对象。 |
| [int OH_PreferencesValue_SetInt(OH_PreferencesValue *value, int intValue)](#oh_preferencesvalue_setint) | 设置PreferencesValue实例对象中的整型值。                     |
| [int OH_PreferencesValue_SetBool(OH_PreferencesValue *value, bool boolValue)](#oh_preferencesvalue_setbool) | 设置PreferencesValue实例对象中的布尔值。                     |
| [int OH_PreferencesValue_SetString(OH_PreferencesValue *value, const char *stringValue)](#oh_preferencesvalue_setstring) | 设置PreferencesValue实例对象中的字符串值。                   |
| [int OH_PreferencesValue_SetInt64(OH_PreferencesValue *value, int64_t int64Value)](#oh_preferencesvalue_setint64) | 设置PreferencesValue实例对象中的64位整型值。                 |
| [int OH_PreferencesValue_GetInt64(OH_PreferencesValue *value, int64_t *int64Value)](#oh_preferencesvalue_getint64) | 获取PreferencesValue实例对象中的64位整型值。                 |
| [int OH_PreferencesValue_SetDouble(OH_PreferencesValue *value, double doubleValue)](#oh_preferencesvalue_setdouble) | 设置PreferencesValue实例对象中的双精度浮点值。               |
| [int OH_PreferencesValue_GetDouble(OH_PreferencesValue *value, double *doubleValue)](#oh_preferencesvalue_getdouble) | 获取PreferencesValue实例对象中的双精度浮点值。               |
| [int OH_PreferencesValue_SetIntArray(OH_PreferencesValue *value, const int *intArray, uint32_t count)](#oh_preferencesvalue_setintarray) | 设置PreferencesValue实例对象中的整型数组值。                 |
| [int OH_PreferencesValue_GetIntArray(const OH_PreferencesValue *object, int **value, uint32_t *count)](#oh_preferencesvalue_getintarray) | 获取PreferencesValue实例对象中的整型数组值。                 |
| [int OH_PreferencesValue_SetBoolArray(OH_PreferencesValue *value, const bool *boolArray, uint32_t count)](#oh_preferencesvalue_setboolarray) | 设置PreferencesValue实例对象中的布尔数组值。                 |
| [int OH_PreferencesValue_GetBoolArray(const OH_PreferencesValue *object, bool **value, uint32_t *count)](#oh_preferencesvalue_getboolarray) | 获取PreferencesValue实例对象中的布尔数组值。                 |
| [int OH_PreferencesValue_SetStringArray(OH_PreferencesValue *value, const char **stringArray, uint32_t count)](#oh_preferencesvalue_setstringarray) | 设置PreferencesValue实例对象中的字符串数组值。               |
| [int OH_PreferencesValue_GetStringArray(const OH_PreferencesValue *object, const char ***value, uint32_t *count)](#oh_preferencesvalue_getstringarray) | 获取PreferencesValue实例对象中的字符串数组值。               |
| [int OH_PreferencesValue_SetInt64Array(OH_PreferencesValue *value, const int64_t *int64Array, uint32_t count)](#oh_preferencesvalue_setint64array) | 设置PreferencesValue实例对象中的64位整型数组值。             |
| [int OH_PreferencesValue_GetInt64Array(const OH_PreferencesValue *object, int64_t **value, uint32_t *count)](#oh_preferencesvalue_getint64array) | 获取PreferencesValue实例对象中的64位整型数组值。             |
| [int OH_PreferencesValue_SetDoubleArray(OH_PreferencesValue *value, const double *doubleArray, uint32_t count)](#oh_preferencesvalue_setdoublearray) | 设置PreferencesValue实例对象中的双精度浮点数组值。           |
| [int OH_PreferencesValue_GetDoubleArray(const OH_PreferencesValue *object, double **value, uint32_t *count)](#oh_preferencesvalue_getdoublearray) | 获取PreferencesValue实例对象中的双精度浮点数组值。           |
| [int OH_PreferencesValue_SetBlob(OH_PreferencesValue *value, const uint8_t *blob, uint32_t count) ](#oh_preferencesvalue_setblob) | 设置PreferencesValue实例对象中的二进制数据值。               |
| [int OH_PreferencesValue_GetBlob(const OH_PreferencesValue *object, uint8_t **blob, uint32_t *count)](#oh_preferencesvalue_getblob) | 获取PreferencesValue实例对象中的二进制数据值。               |

## 枚举类型说明

### Preference_ValueType

```c
enum Preference_ValueType
```

**描述**

定义PreferencesValue的数据类型。

**起始版本：** 13

| 枚举项                   | 描述         |
| ------------------------ | ------------ |
| PREFERENCE_TYPE_NULL = 0 | 空类型。     |
| PREFERENCE_TYPE_INT      | 整型类型。   |
| PREFERENCE_TYPE_BOOL     | 布尔类型。   |
| PREFERENCE_TYPE_STRING   | 字符串类型。 |
| PREFERENCE_TYPE_BUTT     | 结束类型。   |


## 函数说明

### OH_PreferencesPair_GetKey()

```c
const char *OH_PreferencesPair_GetKey(const OH_PreferencesPair *pairs, uint32_t index)
```

**描述**

获取KV数据中索引对应数据的键。

**起始版本：** 13


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) *pairs | 目标KV数据[OH_PreferencesPair](capi-preferences-oh-preferencespair.md)的指针。 |
| uint32_t index                                               | 目标KV数据[OH_PreferencesPair](capi-preferences-oh-preferencespair.md)的索引值。 |

**返回：**

| 类型         | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| const char * | 如果操作成功，返回获取到的键的指针。操作失败或传参不合法返回空指针。 |

### OH_PreferencesPair_GetPreferencesValue()

```c
const OH_PreferencesValue *OH_PreferencesPair_GetPreferencesValue(const OH_PreferencesPair *pairs, uint32_t index)
```

**描述**

获取KV数据数组中索引对应的值。

**起始版本：** 13


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) *pairs | 目标KV数据[OH_PreferencesPair](capi-preferences-oh-preferencespair.md)的指针。 |
| uint32_t index                                               | 目标KV数据[OH_PreferencesPair](capi-preferences-oh-preferencespair.md)的索引值。 |

**返回：**

| 类型                                                     | 说明                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) | 如果操作成功，返回获取到的值对象的指针。操作失败或传参不合法返回空指针。 |


### OH_PreferencesValue_GetValueType()

```c
Preference_ValueType OH_PreferencesValue_GetValueType(const OH_PreferencesValue *object)
```

**描述**

获取PreferencesValue对象的数据类型。

**起始版本：** 13


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)的指针。 |

**返回：**

| 类型                                          | 说明                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [Preference_ValueType](#preference_valuetype) | 返回获取到的数据类型枚举。若返回数据类型枚举为PREFERENCE_TYPE_NULL，代表传参不合法。 |

### OH_PreferencesValue_GetInt()

```c
int OH_PreferencesValue_GetInt(const OH_PreferencesValue *object, int *value)
```

**描述**

从PreferencesValue对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)中获取一个整型值。

**起始版本：** 13


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)的指针。 |
| int *value                                                   | 该参数作为出参使用，表示指向获取到的整型值的指针。           |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetBool()

```c
int OH_PreferencesValue_GetBool(const OH_PreferencesValue *object, bool *value)
```

**描述**

从PreferencesValue对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)中获取一个布尔值。

**起始版本：** 13


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)的指针。 |
| bool *value                                                  | 该参数作为出参使用，表示指向获取到的布尔值的指针。           |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetString()

```c
int OH_PreferencesValue_GetString(const OH_PreferencesValue *object, char **value, uint32_t *valueLen)
```

**描述**

从PreferencesValue对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)中获取字符串。

**起始版本：** 13


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 对象[OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md)的指针。 |
| char **value                                                 | 该参数作为出参使用，表示指向获取到的字符串的二级指针，使用完毕后需要调用释放函数[OH_Preferences_FreeString](capi-oh-preferences-h.md#oh_preferences_freestring)释放内存。 |
| uint32_t *valueLen                                           | 该参数作为出参使用，表示指向获取到的字符串长度的指针。       |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_Destroy()
```c
void OH_PreferencesValue_Destroy(OH_PreferencesValue *value)
```
**描述**

销毁PreferencesPair实例对象。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesPair](capi-preferences-oh-preferencespair.md) *pair | 指向目标PreferencesPair实例对象的指针。                     |

### OH_PreferencesValue_Create()

```c
OH_PreferencesValue* OH_PreferencesValue_Create(void);
```
**描述**

创建一个新的PreferencesValue实例对象。

**起始版本：** 23

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| OH_PreferencesValue*  | 返回指向新创建的PreferencesValue实例对象的指针。<br>若创建失败，则返回NULL。 |

### OH_PreferencesValue_Destroy()

```c
void OH_PreferencesValue_Destroy(OH_PreferencesValue *value)
```
**描述**

销毁PreferencesValue实例对象。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |

### OH_PreferencesValue_SetInt()

```c
int OH_PreferencesValue_SetInt(OH_PreferencesValue *value, int32_t intValue)
```
**描述**

设置PreferencesValue实例对象中的整数值。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| int32_t intValue                                            | 要设置的整数值。                                             |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetBool()

```c
int OH_PreferencesValue_SetBool(OH_PreferencesValue *value, bool boolValue)
```
**描述**

设置PreferencesValue实例对象中的布尔值。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| bool boolValue                                              | 要设置的布尔值。                                             |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetString()

```c
int OH_PreferencesValue_SetString(OH_PreferencesValue *value, const char *string)
```
**描述**

设置PreferencesValue实例对象中的字符串值。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| const char *string                                          | 要设置的字符串值。                                           |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetInt()

```c
int OH_PreferencesValue_GetInt(const OH_PreferencesValue *object, int32_t *intValue)
```
**描述**

获取PreferencesValue实例对象中的整数值。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| int32_t *intValue                                           | 指向存储获取到的整数值的指针。                               |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetBool()

```c
int OH_PreferencesValue_GetBool(const OH_PreferencesValue *object, bool *boolValue)
```
**描述**

获取PreferencesValue实例对象中的布尔值。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| bool *boolValue                                             | 指向存储获取到的布尔值的指针。                               |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetDouble()

```c
int OH_PreferencesValue_SetDouble(OH_PreferencesValue *value, double doubleValue)
```
**描述**

设置PreferencesValue实例对象中的双精度浮点数。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| double doubleValue                                          | 要设置的双精度浮点数。                                       |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetDouble()

```c
int OH_PreferencesValue_GetDouble(const OH_PreferencesValue *object, double *doubleValue)
```
**描述**

获取PreferencesValue实例对象中的双精度浮点数。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| double *doubleValue                                         | 指向存储获取到的双精度浮点数的指针。                         |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetIntArray()   

```c
int OH_PreferencesValue_SetIntArray(OH_PreferencesValue *value, const int32_t *intArray, size_t size)
```
**描述**

设置PreferencesValue实例对象中的整数数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| const int32_t *intArray                                     | 指向要设置的整数数组的指针。                                 |
| size_t size                                                 | 整数数组的元素数量。                                         |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetIntArray()   

```c
int OH_PreferencesValue_GetIntArray(const OH_PreferencesValue *object, int32_t *intArray, size_t *size)
```
**描述**

获取PreferencesValue实例对象中的整数数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| int32_t *intArray                                           | 指向存储获取到的整数数组的指针。                             |
| size_t *size                                                | 指向存储整数数组元素数量的指针。                             |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetBoolArray()   

```c
int OH_PreferencesValue_SetBoolArray(OH_PreferencesValue *value, const bool *boolArray, size_t size)
```
**描述**

设置PreferencesValue实例对象中的布尔数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| const bool *boolArray                                       | 指向要设置的布尔数组的指针。                                 |
| size_t size                                                 | 布尔数组的元素数量。                                         |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetBoolArray()   

```c
int OH_PreferencesValue_GetBoolArray(const OH_PreferencesValue *object, bool *boolArray, size_t *size)
```
**描述**

获取PreferencesValue实例对象中的布尔数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| bool *boolArray                                             | 指向存储获取到的布尔数组的指针。                             |
| size_t *size                                                | 指向存储布尔数组元素数量的指针。                             |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetStringArray()   

```c
int OH_PreferencesValue_SetStringArray(OH_PreferencesValue *value, const char *const *stringArray, size_t size)
```
**描述**

设置PreferencesValue实例对象中的字符串数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| const char *const *stringArray                              | 指向要设置的字符串数组的指针。                               |
| size_t size                                                 | 字符串数组的元素数量。                                       |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetStringArray()   

```c
int OH_PreferencesValue_GetStringArray(const OH_PreferencesValue *object, char *const *stringArray, size_t *size)
```
**描述**

获取PreferencesValue实例对象中的字符串数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| char *const *stringArray                                    | 指向存储获取到的字符串数组的指针。                           |
| size_t *size                                                | 指向存储字符串数组元素数量的指针。                           |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetInt64Array()
```c
int OH_PreferencesValue_SetInt64Array(OH_PreferencesValue *value, const int64_t *int64Array, size_t size)
```
**描述**

设置PreferencesValue实例对象中的64位整数数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| const int64_t *int64Array                                   | 指向要设置的64位整数数组的指针。                             |
| size_t size                                                 | 64位整数数组的元素数量。                                     |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetInt64Array()
```c
int OH_PreferencesValue_GetInt64Array(const OH_PreferencesValue *object, int64_t *int64Array, size_t *size)
```
**描述**

获取PreferencesValue实例对象中的64位整数数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| int64_t *int64Array                                        | 指向存储获取到的64位整数数组的指针。                         |
| size_t *size                                                | 指向存储64位整数数组元素数量的指针。                         |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetDoubleArray()
```c
int OH_PreferencesValue_SetDoubleArray(OH_PreferencesValue *value, const double *doubleArray, size_t size)
```
**描述**

设置PreferencesValue实例对象中的双精度浮点数数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| const double *doubleArray                                   | 指向要设置的双精度浮点数数组的指针。                         |
| size_t size                                                 | 双精度浮点数数组的元素数量。                                 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetDoubleArray()
```c
int OH_PreferencesValue_GetDoubleArray(const OH_PreferencesValue *object, double *doubleArray, size_t *size)
```
**描述**

获取PreferencesValue实例对象中的双精度浮点数数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| double *doubleArray                                        | 指向存储获取到的双精度浮点数数组的指针。                     |
| size_t *size                                                | 指向存储双精度浮点数数组元素数量的指针。                     |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetDoubleArray()
```c
int OH_PreferencesValue_GetDoubleArray(const OH_PreferencesValue *object, double **doubleArray, size_t *size)
```
**描述**

获取PreferencesValue实例对象中的双精度浮点数数组。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| double **doubleArray                                       | 指向存储获取到的双精度浮点数数组指针的指针。                 |
| size_t *size                                                | 指向存储双精度浮点数数组元素数量的指针。                     |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_SetBlob()
```c
int OH_PreferencesValue_SetBlob(OH_PreferencesValue *value, const uint8_t *blob, size_t size)
```
**描述**

设置PreferencesValue实例对象中的二进制数据。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *value | 指向目标PreferencesValue实例对象的指针。                     |
| const uint8_t *blob                                        | 指向要设置的二进制数据的指针。                               |
| size_t size                                                 | 二进制数据的字节数。                                       |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

### OH_PreferencesValue_GetBlob()
```c
int OH_PreferencesValue_GetBlob(const OH_PreferencesValue *object, uint8_t **blob, size_t *size)
```
**描述**

获取PreferencesValue实例对象中的二进制数据。

**起始版本：** 23


**参数：**

| 参数项                                                       | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| const [OH_PreferencesValue](capi-preferences-oh-preferencesvalue.md) *object | 指向目标PreferencesValue实例对象的指针。                     |
| uint8_t **blob                                             | 指向存储获取到的二进制数据指针的指针。                       |
| size_t *size                                                | 指向存储二进制数据字节数的指针。                             |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的错误码。<br>若错误码为PREFERENCES_OK，表示操作成功。<br>若错误码为PREFERENCES_ERROR_INVALID_PARAM，表示参数不合法。<br>若错误码为PREFERENCES_ERROR_STORAGE，表示存储异常。<br>若错误码为PREFERENCES_ERROR_MALLOC，表示内存分配失败。 |

