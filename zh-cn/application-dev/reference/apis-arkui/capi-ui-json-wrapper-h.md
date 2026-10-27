# ui_json_wrapper.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202 -->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

声明UI感知与控制等接口共用的JSON数据对象。<br>接口通过返回值报告错误，具体含义参见各接口的返回值说明。这些接口不通过错误码变量errno报告错误，调用后该变量的取值未作规定，不得据此判断调用是否成功。<br>在满足对象生命周期要求的前提下，这些函数可在任意线程（包括UI线程）调用。对同一个有效对象的只读查询可并发执行，调用方必须确保销毁操作不会与该对象或其借用数据的访问同时进行。对独立对象的操作可并发执行。这些函数不触发应用回调；满足所有权和生命周期要求时，可在回调中调用。这些函数不具备异步信号安全性，不得在信号处理函数中调用。<br>查询函数以同步方式读取本地内存中的数据。创建和销毁对象还涉及内存分配或释放，这些内存操作的耗时上限不作保证。<br>这些接口不支持异步完成，也不提供取消操作。

**引用文件：** <arkui/ui_json_wrapper.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) | OH_ArkUI_NativeModule_UIJsonWrapper | 定义内部结构不对外公开的不可变JSON数据对象。<br>该对象保存一个JSON字符串，既用于承载框架传递的数据（UI感知），也用于承载应用注入的命令（UI控制）。JSON对象顶层必须包含schemaVersion字段，用于版本控制和后续兼容性维护。应用传入的JSON，以及框架通过接口返回或回调传递的JSON，均必须满足此要求；即使没有采集内容，返回的JSON也必须携带该字段。<br>该对象不使用引用计数。复制对象指针仅产生借用别名，不会创建独立对象或增加所有权。对象的所有者必须且只能销毁该对象一次。销毁后，所有别名及数据指针均失效，不得再次使用或销毁。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_NativeModule_UIJsonFormat](#oh_arkui_nativemodule_uijsonformat) | OH_ArkUI_NativeModule_UIJsonFormat | 定义JSON输出格式的枚举类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_UIJsonWrapperCreate(const char *data, uint32_t size, OH_ArkUI_NativeModule_UIJsonWrapper **outOwned)](#oh_arkui_nativemodule_uijsonwrappercreate) | 根据调用方提供的JSON字符串创建JSON数据对象。<br>传入的字符串会被复制到对象中。调用方拥有所创建对象的所有权，并且必须在不再使用时调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放该对象。复制返回的指针不会延长对象生命周期，也不会产生新的所有者。对象销毁后，该指针及其所有别名均失效，不得再次使用或销毁。<br>传入的字符串必须表示有效的JSON对象，且对象顶层必须包含schemaVersion字段。如果缺少该字段，或其值超出支持的版本范围，本函数返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，不使用默认版本。示例如下：{ "schemaVersion": 1, ... }<br>注意：传入的data字符串仍归调用方所有。销毁本接口返回的JSON封装对象，不会代替调用方释放data所指向的内存。参数错误需要修正输入后再重试。大小溢出或内存分配失败时，应减小输入或释放资源后再重试，避免忙循环。失败时不会转移任何对象的所有权。 |
| [const char *OH_ArkUI_NativeModule_UIJsonWrapperGetData(const OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrappergetdata) | 获取对象保存的JSON字符串。<br>返回的字符串为只读字符串，以空字符结尾。字符串所在的内存归JSON对象所有，在该对象销毁前一直有效。调用方不得修改或释放返回的字符串。JSON对象顶层包含schemaVersion字段。 |
| [uint32_t OH_ArkUI_NativeModule_UIJsonWrapperGetSize(const OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrappergetsize) | 获取JSON字符串的字节长度。<br>返回的长度不包含末尾的空字符，包含JSON字符串中schemaVersion字段所占的字节。<br>本查询不分配或释放资源。 |
| [void OH_ArkUI_NativeModule_UIJsonWrapperDestroy(OH_ArkUI_NativeModule_UIJsonWrapper *json)](#oh_arkui_nativemodule_uijsonwrapperdestroy) | 销毁JSON数据对象并释放其资源。<br>调用本函数后，[OH_ArkUI_NativeModule_UIJsonWrapperGetData](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)返回的所有指针均失效。<br>注意：调用方必须拥有JSON封装对象的所有权，才能调用本函数销毁该对象。例如通过[OH_ArkUI_NativeModule_UIJsonWrapperCreate](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)创建的对象，或通过所有权转移函数明确取得所有权的对象。不得使用本函数释放由系统构造并传出的JSON封装对象，例如通过[OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback)传入的对象。 |

## 枚举类型说明

### OH_ArkUI_NativeModule_UIJsonFormat

```c
enum OH_ArkUI_NativeModule_UIJsonFormat
```

**描述：**

定义JSON输出格式的枚举类型。

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_NATIVE_MODULE_UI_JSON_COMPACT = 0 | 输出不含多余空白字符的规范JSON。 |
| OH_ARKUI_NATIVE_MODULE_UI_JSON_PRETTY = 1 | 输出带有两个空格缩进和换行符的JSON。 |


## 函数说明

### OH_ArkUI_NativeModule_UIJsonWrapperCreate()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_UIJsonWrapperCreate(const char *data, uint32_t size, OH_ArkUI_NativeModule_UIJsonWrapper **outOwned)
```

**描述：**

根据调用方提供的JSON字符串创建JSON数据对象。<br>传入的字符串会被复制到对象中。调用方拥有所创建对象的所有权，并且必须在不再使用时调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放该对象。复制返回的指针不会延长对象生命周期，也不会产生新的所有者。对象销毁后，该指针及其所有别名均失效，不得再次使用或销毁。<br>传入的字符串必须表示有效的JSON对象，且对象顶层必须包含schemaVersion字段。如果缺少该字段，或其值超出支持的版本范围，本函数返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)，不使用默认版本。示例如下：{ "schemaVersion": 1, ... }<br>注意：传入的data字符串仍归调用方所有。销毁本接口返回的JSON封装对象，不会代替调用方释放data所指向的内存。参数错误需要修正输入后再重试。大小溢出或内存分配失败时，应减小输入或释放资源后再重试，避免忙循环。失败时不会转移任何对象的所有权。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *data | [入参] 指向UTF-8编码JSON字符串的指针。不能为NULL，且必须在整个调用期间保持有效。被调用方不会保留该指针。字符串必须包含有效的JSON对象，且schemaVersion必须为受支持的版本。空字符串无效。至少size个字节必须可读。输入无需以空字符结尾，创建的对象会追加自己的结束空字符。JSON文本中不得包含嵌入的空字节，U+0000应使用JSON转义表示。 |
| uint32_t size | [入参] 从data复制的字节数，不包括结尾的空字符。本函数按size复制字节，不校验实际字符串长度，并在副本末尾追加空字符。size必须大于0，传入0时返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。 |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) **outOwned | [出参] 用于接收创建成功的对象的输出参数。调用方拥有返回对象的所有权，必须调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)释放该对象。outOwned不能为NULL，其指向的对象指针无需初始化；创建失败时，该对象指针被设置为NULL。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)操作成功。<br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) data或outOwned为NULL、size为0、data不表示有效的JSON对象，或schemaVersion字段缺失、版本不受支持。<br>[ARKUI_ERROR_CODE_INTERNAL_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)包含结束空字符的缓冲区大小在当前架构上无法表示，或内存分配、数据复制失败。 |

### OH_ArkUI_NativeModule_UIJsonWrapperGetData()

```c
const char *OH_ArkUI_NativeModule_UIJsonWrapperGetData(const OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**描述：**

获取对象保存的JSON字符串。<br>返回的字符串为只读字符串，以空字符结尾。字符串所在的内存归JSON对象所有，在该对象销毁前一直有效。调用方不得修改或释放返回的字符串。JSON对象顶层包含schemaVersion字段。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [入参] JSON数据对象，不能为NULL。该对象为借用对象，必须在整个调用期间保持有效，被调用方不会保留该对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| const char * | 借用的JSON字符串指针，调用方不得修改或释放该指针。<br>json为NULL时返回NULL。 |

### OH_ArkUI_NativeModule_UIJsonWrapperGetSize()

```c
uint32_t OH_ArkUI_NativeModule_UIJsonWrapperGetSize(const OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**描述：**

获取JSON字符串的字节长度。<br>返回的长度不包含末尾的空字符，包含JSON字符串中schemaVersion字段所占的字节。<br>本查询不分配或释放资源。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [入参] JSON数据对象，不能为NULL。该对象为借用对象，必须在整个调用期间保持有效，被调用方不会保留该对象。传入NULL时无法获取对象的长度，应提供有效且尚未销毁的对象后再重试。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | JSON字符串的字节长度，不包含末尾的空字符。<br>json为NULL时返回0。 |

### OH_ArkUI_NativeModule_UIJsonWrapperDestroy()

```c
void OH_ArkUI_NativeModule_UIJsonWrapperDestroy(OH_ArkUI_NativeModule_UIJsonWrapper *json)
```

**描述：**

销毁JSON数据对象并释放其资源。<br>调用本函数后，[OH_ArkUI_NativeModule_UIJsonWrapperGetData](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata)返回的所有指针均失效。<br>注意：调用方必须拥有JSON封装对象的所有权，才能调用本函数销毁该对象。例如通过[OH_ArkUI_NativeModule_UIJsonWrapperCreate](capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappercreate)创建的对象，或通过所有权转移函数明确取得所有权的对象。不得使用本函数释放由系统构造并传出的JSON封装对象，例如通过[OH_ArkUI_NativeModule_UIInfoCollectionInteractionJsonCallback](capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiinfocollectioninteractionjsoncallback)传入的对象。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_NativeModule_UIJsonWrapper](capi-arkui-nativemodule-oh-arkui-nativemodule-uijsonwrapper.md) *json | [入参] 要销毁的JSON数据对象，可以为NULL；传入NULL时不执行任何操作。调用方必须拥有该对象的所有权。销毁后，对象及其所有别名立即失效，不得再次使用或销毁。不得将借用对象传给本函数。 |
