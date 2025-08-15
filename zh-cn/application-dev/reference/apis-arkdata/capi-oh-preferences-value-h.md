# oh_preferences_value.h
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @yanhuii-->
<!--Designer: @houpengtao1-->
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

## 枚举类型说明

### Preference_ValueType

```
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

```
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

```
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

```
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

```
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

```
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

```
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



