# 通过用户首选项实现数据持久化 (C/C++)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 场景介绍
用户首选项（Preferences）模块主要提供轻量级Key-Value操作，支持本地存储少量数据，数据存储在文件和内存中，访问速度快。如果存在大量数据场景，请考虑使用键值型数据库或关系型数据库。

## 约束限制
- API version 18之前：ArkTS API仅支持[XML存储模式](./data-persistence-by-preferences.md#xml存储)；C API仅支持[GSKV存储模式](./data-persistence-by-preferences.md#gskv存储)；存储模式互不兼容，不支持ArkTS和C API操作同一个Preferences实例。
- API version 18及之后：ArkTS和C API均支持XML和GSKV双模式；ArkTS和C API使用相同的存储模式时，可以正常操作同一Preferences实例；禁止ArkTS和C API选择不同的存储模式，来操作同一个Preferences实例。
- Key的最大长度限制为1024个字节，Value的最大长度限制为16MB。


## 接口说明

详细的接口说明请参考[Preferences接口文档](../reference/apis-arkdata/capi-preferences.md)。

| 接口名称 | 描述 |
| -------- | -------- |
| OH_Preferences \* OH_Preferences_Open (OH_PreferencesOption \*option, int \*errCode) | 打开一个Preferences实例对象并创建指向它的指针。 当不再需要使用指针时，请使用OH_Preferences_Close关闭实例对象。 |
| int OH_Preferences_Close (OH_Preferences \*preference) | 关闭一个Preferences实例对象。 |
| int OH_Preferences_GetInt (OH_Preferences \*preference, const char \*key, int \*value) | 获取Preferences实例对象中Key对应的整型值。 |
| int OH_Preferences_GetBool (OH_Preferences \*preference, const char \*key, bool \*value) | 获取Preferences实例对象中Key对应的布尔值。 |
| int OH_Preferences_GetString (OH_Preferences \*preference, const char \*key, char \*\*value, uint32_t \*valueLen) | 获取Preferences实例对象中Key对应的字符串。 |
| void OH_Preferences_FreeString (char \*string) | 释放从Preferences实例对象中获取的字符串。 |
| int OH_Preferences_SetInt (OH_Preferences \*preference, const char \*key, int value) | 根据Key设置Preferences实例对象中的整型值。 |
| int OH_Preferences_SetBool (OH_Preferences \*preference, const char \*key, bool value) | 根据Key设置Preferences实例对象中的布尔值。 |
| int OH_Preferences_SetString (OH_Preferences \*preference, const char \*key, const char \*value) | 根据Key设置Preferences实例对象中的字符串。 |
| int OH_Preferences_Delete (OH_Preferences \*preference, const char \*key) | 在Preferences实例对象中删除Key对应的KV数据。 |
| int OH_Preferences_RegisterDataObserver (OH_Preferences \*preference, void \*context, OH_PreferencesDataObserver observer, const char \*keys[], uint32_t keyCount) | 对选取的Key注册数据变更订阅。订阅的Key的值发生变更后，在调用OH_Preferences_Close()后触发回调。 |
| int OH_Preferences_UnregisterDataObserver (OH_Preferences \*preference, void \*context, OH_PreferencesDataObserver observer, const char \*keys[], uint32_t keyCount) | 取消注册选取Key的数据变更订阅。 |
| int OH_Preferences_IsStorageTypeSupported (Preferences_StorageType type, bool \*isSupported) | 检查当前平台是否支持对应的存储模式。 |
| OH_PreferencesOption \* OH_PreferencesOption_Create (void) | 创建一个Preferences配置选项的OH_PreferencesOption实例对象以及指向它的指针。 当不再需要使用指针时，请使用OH_PreferencesOption_Destroy销毁实例对象，否则会导致内存泄漏。 |
| int OH_PreferencesOption_SetFileName (OH_PreferencesOption \*option, const char \*fileName) | 设置Preferences配置选项OH_PreferencesOption实例对象的文件名称。名称长度为0到255字节，其中不能包含'/'。 |
| int OH_PreferencesOption_SetBundleName (OH_PreferencesOption \*option, const char \*bundleName) | 设置Preferences配置选项OH_PreferencesOption实例对象的包名称。 |
| int OH_PreferencesOption_SetDataGroupId (OH_PreferencesOption \*option, const char \*dataGroupId) | 设置Preferences配置选项OH_PreferencesOption实例对象的应用组ID。 |
| int OH_PreferencesOption_SetStorageType (OH_PreferencesOption \*option, Preferences_StorageType type) | 设置Preferences配置选项 OH_PreferencesOption实例对象的存储模式。 |
| int OH_PreferencesOption_Destroy (OH_PreferencesOption \*option) | 销毁Preferences配置选项OH_PreferencesOption实例。 |
| const char \* OH_PreferencesPair_GetKey (const OH_PreferencesPair \*pairs, uint32_t index) | 获取KV数据中索引对应数据的键。 |
| const OH_PreferencesValue \* OH_PreferencesPair_GetPreferencesValue (const OH_PreferencesPair \*pairs, uint32_t index) | 获取KV数据数组中索引对应的值。 |
| Preference_ValueType OH_PreferencesValue_GetValueType (const OH_PreferencesValue \*object) | 获取PreferencesValue对象的数据类型。 |
| int OH_PreferencesValue_GetInt (const OH_PreferencesValue \*object, int \*value) | 从PreferencesValue对象OH_PreferencesValue中获取一个整型值。 |
| int OH_PreferencesValue_GetBool (const OH_PreferencesValue \*object, bool \*value) | 从PreferencesValue对象OH_PreferencesValue中获取一个布尔值。 |
| int OH_PreferencesValue_GetString (const OH_PreferencesValue \*object, char \*\*value, uint32_t \*valueLen) | 从PreferencesValue对象OH_PreferencesValue中获取字符串。 |
| int OH_Preferences_DeletePreferences(OH_PreferencesOption \*option) | 删除Preferences实例对象。 |
| int OH_Preferences_SetValue(OH_Preferences \*preference, const char \*key, OH_PreferencesValue \*value) | 根据Key设置Preferences实例对象中的值。 |
| int OH_Preferences_GetValue(OH_Preferences \*preference, const char \*key, OH_PreferencesValue \*\*value) | 根据Key获取Preferences实例对象中的值。 |
| int OH_Preferences_GetAll(OH_Preferences \*preference, OH_PreferencesPair \*\*pairs, uint32_t \*count) | 获取Preferences实例对象中的所有KV数据。 |
| bool OH_Preferences_HasKey(OH_Preferences \*preference, const char \*key) | 检查Preferences实例对象中是否包含指定的Key。 |
| int OH_Preferences_Flush(OH_Preferences \*preference) | 刷新Preferences实例对象中的数据到磁盘。 |
| int OH_Preferences_ClearCache(OH_Preferences \*preference) | 清除Preferences实例对象中的缓存数据。 |
| int OH_Preferences_RegisterMultiProcessDataObserver(OH_Preferences \*preference, void \*context, OH_PreferencesDataObserver observer) | 对选取的Key注册数据变更订阅。订阅的Key的值发生变更后，在调用OH_Preferences_Close()后触发回调。 |
| int OH_Preferences_UnregisterMultiProcessDataObserver(OH_Preferences \*preference, void \*context, OH_PreferencesDataObserver observer) | 取消注册选取Key的数据变更订阅。 |
| void OH_PreferencesPair_Destroy(OH_PreferencesPair \*pairs) | 销毁PreferencesPair实例对象。 |
| OH_PreferencesValue \* OH_PreferencesValue_Create(void) | 创建一个PreferencesValue实例对象以及指向它的指针。 当不再需要使用指针时，请使用OH_PreferencesValue_Destroy销毁实例对象，否则会导致内存泄漏。 |
| void OH_PreferencesValue_Destroy(OH_PreferencesValue \*value) | 销毁PreferencesValue实例对象。 |
| int OH_PreferencesValue_SetInt(OH_PreferencesValue \*value, int intValue) | 设置PreferencesValue实例对象中的整型值。 |
| int OH_PreferencesValue_SetBool(OH_PreferencesValue \*value, bool boolValue) | 设置PreferencesValue实例对象中的布尔值。 |
| int OH_PreferencesValue_SetString(OH_PreferencesValue \*value, const char \*stringValue) | 设置PreferencesValue实例对象中的字符串值。 |
| int OH_PreferencesValue_SetInt64(OH_PreferencesValue \*value, int64_t int64Value) | 设置PreferencesValue实例对象中的64位整型值。 |
| int OH_PreferencesValue_GetInt64(OH_PreferencesValue \*value, int64_t \*int64Value) | 获取PreferencesValue实例对象中的64位整型值。 |
| int OH_PreferencesValue_SetDouble(OH_PreferencesValue \*value, double doubleValue) | 设置PreferencesValue实例对象中的双精度浮点值。 |
| int OH_PreferencesValue_GetDouble(OH_PreferencesValue \*value, double \*doubleValue) | 获取PreferencesValue实例对象中的双精度浮点值。 |
| int OH_PreferencesValue_SetIntArray(OH_PreferencesValue \*value, const int \*intArray, uint32_t count) | 设置PreferencesValue实例对象中的整型数组值。 |
| int OH_PreferencesValue_GetIntArray(const OH_PreferencesValue \*object, int \*\*value, uint32_t \*count) | 获取PreferencesValue实例对象中的整型数组值。 |
| int OH_PreferencesValue_SetBoolArray(OH_PreferencesValue \*value, const bool \*boolArray, uint32_t count) | 设置PreferencesValue实例对象中的布尔数组值。 |
| int OH_PreferencesValue_GetBoolArray(const OH_PreferencesValue \*object, bool \*\*value, uint32_t \*count) | 获取PreferencesValue实例对象中的布尔数组值。 |
| int OH_PreferencesValue_SetStringArray(OH_PreferencesValue \*value, const char \*\*stringArray, uint32_t count) | 设置PreferencesValue实例对象中的字符串数组值。 |
| int OH_PreferencesValue_GetStringArray(const OH_PreferencesValue \*object, char \*\*\*value, uint32_t \*count) | 获取PreferencesValue实例对象中的字符串数组值。 |
| int OH_PreferencesValue_SetInt64Array(OH_PreferencesValue \*value, const int64_t \*int64Array, uint32_t count) | 设置PreferencesValue实例对象中的64位整型数组值。 |
| int OH_PreferencesValue_GetInt64Array(const OH_PreferencesValue \*object, int64_t \*\*value, uint32_t \*count) | 获取PreferencesValue实例对象中的64位整型数组值。 |
| int OH_PreferencesValue_SetDoubleArray(OH_PreferencesValue \*value, const double \*doubleArray, uint32_t count) | 设置PreferencesValue实例对象中的双精度浮点数组值。 |
| int OH_PreferencesValue_GetDoubleArray(const OH_PreferencesValue \*object, double \*\*value, uint32_t \*count) | 获取PreferencesValue实例对象中的双精度浮点数组值。 |
| int OH_PreferencesValue_SetBlob(OH_PreferencesValue \*value, const uint8_t \*blob, uint32_t count) | 设置PreferencesValue实例对象中的二进制数据值。 |
| int OH_PreferencesValue_GetBlob(const OH_PreferencesValue \*object, uint8_t \*\*blob, uint32_t *count) | 获取PreferencesValue实例对象中的二进制数据值。 |


## 添加动态链接库

CMakeLists.txt中添加以下lib。

```txt
libohpreferences.so
```

## 引用头文件

<!--@[preferences_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Preferences/PreferencesNDKSample/entry/src/main/cpp/napi_init.cpp)-->
``` C++
#include <database/preferences/oh_preferences.h>
#include <database/preferences/oh_preferences_err_code.h>
#include <database/preferences/oh_preferences_option.h>
#include <database/preferences/oh_preferences_value.h>
```

## 开发步骤
下列实例展示如何通过Preferences实现对键值数据的修改与持久化。
1. 创建Preferences配置选项（PreferencesOption）对象并设置配置选项成员（名称、应用组ID、包名、存储模式）。使用完毕后，调用OH_PreferencesOption_Destroy销毁配置选项实例。
2. 调用OH_Preferences_Open打开一个Preferences实例，该实例使用完后需要调用OH_Preferences_Close关闭。
   <!--@[PreferencesOpen](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Preferences/PreferencesNDKSample/entry/src/main/cpp/napi_init.cpp)-->
   
   ``` C++
   // 1. 创建Preferences配置选项。
   OH_PreferencesOption *option = OH_PreferencesOption_Create();
   if (option == nullptr) {
       // 错误处理
   }
   // 设置Preferences配置选项的文件名称。
   int ret = OH_PreferencesOption_SetFileName(option, "testdb");
   if (ret != PREFERENCES_OK) {
       (void)OH_PreferencesOption_Destroy(option);
       // 错误处理
   }
   // 设置Preferences配置选项的应用组ID。
   ret = OH_PreferencesOption_SetDataGroupId(option, "");
   if (ret != PREFERENCES_OK) {
       (void)OH_PreferencesOption_Destroy(option);
       // 错误处理
   }
   // 设置Preferences配置选项的包名称。
   ret = OH_PreferencesOption_SetBundleName(option, "com.example");
   if (ret != PREFERENCES_OK) {
       (void)OH_PreferencesOption_Destroy(option);
       // 错误处理
   }
   // 设置Preferences配置选项的存储模式，需要注意的是，设置之前需要调用OH_Preferences_IsStorageTypeSupported接口判断当前平台是否支持需要选择的模式。
   bool isGskvSupported = false;
   ret = OH_Preferences_IsStorageTypeSupported(Preferences_StorageType::PREFERENCES_STORAGE_GSKV, &isGskvSupported);
   if (ret != PREFERENCES_OK) {
       (void)OH_PreferencesOption_Destroy(option);
       // 错误处理
   }
   if (isGskvSupported) {
       ret = OH_PreferencesOption_SetStorageType(option, Preferences_StorageType::PREFERENCES_STORAGE_GSKV);
       if (ret != PREFERENCES_OK) {
           (void)OH_PreferencesOption_Destroy(option);
           // 错误处理
       }
   } else {
       ret = OH_PreferencesOption_SetStorageType(option, Preferences_StorageType::PREFERENCES_STORAGE_XML);
       if (ret != PREFERENCES_OK) {
           (void)OH_PreferencesOption_Destroy(option);
           // 错误处理
       }
   }
   // 2. 打开一个Preferences实例。
   int errCode = PREFERENCES_OK;
   OH_Preferences *preference = OH_Preferences_Open(option, &errCode);
   // option使用完毕后可直接释放，释放后需要将指针置空。
   (void)OH_PreferencesOption_Destroy(option);
   option = nullptr;
   if (preference == nullptr || errCode != PREFERENCES_OK) {
       // 错误处理
   }
   // option使用完毕后删除配置选项
   errCode = OH_Preferences_DeletePreferences(option);
   if (errCode != PREFERENCES_OK) {
       // 错误处理
   }
   ```
3. 订阅回调函数为DataChangeObserverCallback。
   <!--@[DataChangeObserverCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Preferences/PreferencesNDKSample/entry/src/main/cpp/napi_init.cpp)-->

``` C++
// 数据变更回调函数
void DataChangeObserverCallback(void *context, const OH_PreferencesPair *pairs, uint32_t count)
{
    for (uint32_t i = 0; i < count; i++) {
        // 获取索引i对应的PreferenceValue
        const OH_PreferencesValue *pValue = OH_PreferencesPair_GetPreferencesValue(pairs, i);
        // 获取PreferencesValue的数据类型
        Preference_ValueType type = OH_PreferencesValue_GetValueType(pValue);
        int ret = PREFERENCES_OK;
        if (type == PREFERENCE_TYPE_INT) {
            int intValue = 0;
            ret = OH_PreferencesValue_GetInt(pValue, &intValue);
            if (ret == PREFERENCES_OK) {
                // 业务逻辑
            }
        } else if (type == PREFERENCE_TYPE_BOOL) {
            bool boolValue = true;
            ret = OH_PreferencesValue_GetBool(pValue, &boolValue);
            if (ret == PREFERENCES_OK) {
                // 业务逻辑
            }
        } else if (type == PREFERENCE_TYPE_STRING) {
            char *stringValue = nullptr;
            uint32_t valueLen = 0;
            ret = OH_PreferencesValue_GetString(pValue, &stringValue, &valueLen);
            if (ret == PREFERENCES_OK) {
                // 业务逻辑
                OH_Preferences_FreeString(stringValue);
            }
        } else {
            // 无效类型
        }
    }
}
```
   调用OH_Preferences_RegisterDataObserver注册3个Key的数据变更订阅。
   <!--@[RegisterDataObserver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Preferences/PreferencesNDKSample/entry/src/main/cpp/napi_init.cpp)-->
   
   ``` C++
   // 3. 对key_int、key_bool和key_string注册数据变更订阅。
   const char *keys[] = {"key_int", "key_bool", "key_string"};
   int ret = OH_Preferences_RegisterDataObserver(preference, nullptr, DataChangeObserverCallback, keys, 3);
   if (ret != PREFERENCES_OK) {
       (void)OH_Preferences_Close(preference);
       // 错误处理
   }
   // 兼容多种类型的注册数据变更订阅。
   int contextData = 42;
   ret = OH_Preferences_RegisterMultiProcessDataObserver(preference, &contextData, DataChangeObserverCallback);
   if (ret != PREFERENCES_OK) {
       // 错误处理
   }
   // 取消兼容多种类型的注册数据变更订阅。
   ret = OH_Preferences_UnregisterMultiProcessDataObserver(preference, &contextData, DataChangeObserverCallback);
   if (ret != PREFERENCES_OK) {
       // 错误处理
   }
   ```
4. 设置Preferences实例中的键值数据。
   <!--@[PreferencesCrud](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Preferences/PreferencesNDKSample/entry/src/main/cpp/napi_init.cpp)-->
``` C++
// 3. 对key_int、key_bool和key_string注册数据变更订阅。
const char *keys[] = {"key_int", "key_bool", "key_string"};
ret = OH_Preferences_RegisterDataObserver(preference, nullptr, DataChangeObserverCallback, keys, 3);
if (ret != PREFERENCES_OK) {
    (void)OH_Preferences_Close(preference);
    // 错误处理
}

// 4. 设置Preferences实例中的KV数据。
ret = OH_Preferences_SetInt(preference, keys[0], 0);
if (ret != PREFERENCES_OK) {
    (void)OH_Preferences_Close(preference);
    // 错误处理
}
ret = OH_Preferences_SetBool(preference, keys[1], true);
if (ret != PREFERENCES_OK) {
    (void)OH_Preferences_Close(preference);
    // 错误处理
}
int32_t stringIndex = 2;
ret = OH_Preferences_SetString(preference, keys[stringIndex], "string value");
if (ret != PREFERENCES_OK) {
    (void)OH_Preferences_Close(preference);
    // 错误处理
}

// 5. 获取Preferences实例中的KV数据。
int intValue = 0;
ret = OH_Preferences_GetInt(preference, keys[0], &intValue);
if (ret == PREFERENCES_OK) {
    // 业务逻辑
}

bool boolValue = false;
ret = OH_Preferences_GetBool(preference, keys[1], &boolValue);
if (ret == PREFERENCES_OK) {
    // 业务逻辑
}

char *stringValue = nullptr;
uint32_t valueLen = 0;
ret = OH_Preferences_GetString(preference, keys[stringIndex], &stringValue, &valueLen);
if (ret == PREFERENCES_OK) {
    // 业务逻辑
    // 使用完OH_Preferences_GetString接口后，需要对字符串进行释放。
    OH_Preferences_FreeString(stringValue);
    stringValue = nullptr;
}
```
5. 获取Preferences实例中的键值数据。
   <!--@[PreferencesCrudGet](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Preferences/PreferencesNDKSample/entry/src/main/cpp/napi_init.cpp)-->

6. 调用OH_Preferences_Close关闭Preferences实例，关闭后需要将实例指针置空。
   <!--@[PreferencesClose](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Preferences/PreferencesNDKSample/entry/src/main/cpp/napi_init.cpp)-->
``` C++
// 6. 使用完Preferences实例后需要关闭实例，关闭后需要将指针置空。
(void)OH_Preferences_Close(preference);
preference = nullptr;

```
7. 设置和获取OH_PreferencesValue。
   <!--@[PreferencesValueSets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Preferences/PreferencesNDKSample/entry/src/main/cpp/napi_init.cpp)-->
