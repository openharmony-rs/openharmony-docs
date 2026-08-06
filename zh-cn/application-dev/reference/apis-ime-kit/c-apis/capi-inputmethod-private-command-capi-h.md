# inputmethod_private_command_capi.h

## 概述

提供私有数据对象的创建、销毁与读写方法。InputMethod_PrivateCommand采用key-value机制，支持输入法应用与编辑框客户端之间传递自定义私有数据，用于扩展输入法功能、传递特定场景指令或交换自定义配置信息。

**库：** libohinputmethod.so

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) | InputMethod_PrivateCommand | 私有命令结构体，采用key-value机制，作为输入框与输入法应用之间传递私有数据的载体。可用于传递自定义指令、扩展能力参数和特定场景数据，提升输入法功能的扩展性和兼容性。每个PrivateCommand实例包含一个key（标识符字符串）和一个value（布尔值、整数或字符串，三种类型只能选择一种），value的数据类型由InputMethod_CommandValueType标识。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)](#oh_privatecommand_create) | 创建一个新的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例。创建时需指定key值，key为私有命令的标识符，用于区分不同的私有数据项。创建后的实例value类型默认为IME_COMMAND_VALUE_TYPE_NONE，需后续通过SetBoolValue/SetIntValue/SetStrValue设置value值及其类型。 |
| [void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)](#oh_privatecommand_destroy) | 销毁一个[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例，释放其占用的内存资源，包括key值和value值（字符串类型value）所占用的内部内存。 |
| [InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)](#oh_privatecommand_setkey) | 设置[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)的key值。key值为私有命令的标识符，用于接收方区分不同含义的私有数据。 |
| [InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)](#oh_privatecommand_setboolvalue) | 设置[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)的布尔类型value值。调用此函数后，该PrivateCommand实例的value类型将变为IME_COMMAND_VALUE_TYPE_BOOL，之前已设置的其他类型value值（int32_t或string）将被覆盖。 |
| [InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)](#oh_privatecommand_setintvalue) | 设置[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)的整数类型value值。调用此函数后，该PrivateCommand实例的value类型将变为IME_COMMAND_VALUE_TYPE_INT32，之前已设置的其他类型value值（bool或string）将被覆盖。 |
| [InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)](#oh_privatecommand_setstrvalue) | 设置[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)的字符串类型value值。调用此函数后，该PrivateCommand实例的value类型将变为IME_COMMAND_VALUE_TYPE_STRING，之前已设置的其他类型value值（bool或int32_t）将被覆盖。 |
| [InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)](#oh_privatecommand_getkey) | 从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取key值。key值为私有命令的标识符。 |
| [InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)](#oh_privatecommand_getvaluetype) | 从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取value的数据类型。返回的类型指示了该实例当前存储的value值的类型，用于指导后续应调用哪个GetValue函数来获取实际的value值。 |
| [InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)](#oh_privatecommand_getboolvalue) | 从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取布尔类型的value的值。 |
| [InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)](#oh_privatecommand_getintvalue) | 从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取整数类型的value的值。 |
| [InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)](#oh_privatecommand_getstrvalue) | 从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取字符串类型的value的值。 |

## 函数说明

### OH_PrivateCommand_Create()

```c
InputMethod_PrivateCommand *OH_PrivateCommand_Create(char key[], size_t keyLength)
```

**描述**

创建一个新的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例。创建时需指定key值，key为私有命令的标识符，用于区分不同的私有数据项。创建后的实例value类型默认为IME_COMMAND_VALUE_TYPE_NONE，需后续通过SetBoolValue/SetIntValue/SetStrValue设置value值及其类型。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char key[] | The key of the private command. |
| size_t keyLength | key值的字节长度，不包括结尾空字符。必须大于0。单次所有私有数据与key值的大小限制32KB。若keyLength为0，创建行为未定义。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_PrivateCommand *](capi-inputmethod-inputmethod-privatecommand.md) | 如果创建成功，返回一个指向新创建的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。调用方必须负责该实例的生命周期管理，使用完毕后调用<br>     [OH_PrivateCommand_Destroy](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_destroy)销毁实例以释放内存。<br>     <br>如果创建失败，返回NULL。可能的失败原因：内存分配不足（应用地址空间满）。对NULL指针的后续操作（如Set/Get函数）将返回IME_ERR_NULL_POINTER。 |

### OH_PrivateCommand_Destroy()

```c
void OH_PrivateCommand_Destroy(InputMethod_PrivateCommand *command)
```

**描述**

销毁一个[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例，释放其占用的内存资源，包括key值和value值（字符串类型value）所占用的内部内存。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被销毁的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。若传入NULL，函数不执行任何操作，安全返回。建议销毁后将指针置为NULL以避免误用悬空指针。 |

### OH_PrivateCommand_SetKey()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetKey(InputMethod_PrivateCommand *command, char key[], size_t keyLength)
```

**描述**

设置[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)的key值。key值为私有命令的标识符，用于接收方区分不同含义的私有数据。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被设置的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| char key[] | Represents key value. |
| size_t keyLength | key值的字节长度，不包括结尾空字符。必须大于0。单次所有私有数据与key值的大小限制32KB。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 传入的command参数或key参数为空指针。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_PrivateCommand_SetBoolValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetBoolValue(InputMethod_PrivateCommand *command, bool value)
```

**描述**

设置[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)的布尔类型value值。调用此函数后，该PrivateCommand实例的value类型将变为IME_COMMAND_VALUE_TYPE_BOOL，之前已设置的其他类型value值（int32_t或string）将被覆盖。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被设置的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| bool value | 布尔类型value值，true或false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，value类型已设置为IME_COMMAND_VALUE_TYPE_BOOL。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，command参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_PrivateCommand_SetIntValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetIntValue(InputMethod_PrivateCommand *command, int32_t value)
```

**描述**

设置[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)的整数类型value值。调用此函数后，该PrivateCommand实例的value类型将变为IME_COMMAND_VALUE_TYPE_INT32，之前已设置的其他类型value值（bool或string）将被覆盖。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被设置的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| int32_t value | 整数类型的value值，32位带符号整数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，value类型已设置为IME_COMMAND_VALUE_TYPE_INT32。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，command参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_PrivateCommand_SetStrValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_SetStrValue(InputMethod_PrivateCommand *command, char value[], size_t valueLength)
```

**描述**

设置[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)的字符串类型value值。调用此函数后，该PrivateCommand实例的value类型将变为IME_COMMAND_VALUE_TYPE_STRING，之前已设置的其他类型value值（bool或int32_t）将被覆盖。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被设置的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| char value[] | Represents string data value. |
| size_t valueLength | 表示字符串数据值的字节长度，不包括结尾空字符。必须大于0。单次所有私有数据与key值的大小限制32KB。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，value类型已设置为IME_COMMAND_VALUE_TYPE_STRING。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，command参数或value参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_PrivateCommand_GetKey()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetKey(InputMethod_PrivateCommand *command, const char **key, size_t *keyLength)
```

**描述**

从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取key值。key值为私有命令的标识符。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被获取key值的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| const char **key | 输出参数，用于接收key值的字符串指针。key的生命周期和command一致，请勿直接保存key地址，也不应直接操作key内容；推荐先拷贝后再使用。command实例销毁后，key指针失效，不应再访问。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| size_t *keyLength | 输出参数，用于接收key值的字节长度。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，key和keyLength已被写入值。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，command、key或keyLength参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_PrivateCommand_GetValueType()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetValueType(InputMethod_PrivateCommand *command, InputMethod_CommandValueType *type)
```

**描述**

从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取value的数据类型。返回的类型指示了该实例当前存储的value值的类型，用于指导后续应调用哪个GetValue函数来获取实际的value值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被获取value类型的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| [InputMethod_CommandValueType](capi-inputmethod-types-capi-h.md#inputmethod_commandvaluetype) *type | 输出参数，用于获取value值的数据类型。返回值为[InputMethod_CommandValueType](capi-inputmethod-types-capi-h.md#inputmethod_commandvaluetype)枚举值：IME_COMMAND_VALUE_TYPE_NONE表示未设置value；IME_COMMAND_VALUE_TYPE_STRING表示字符串类型；IME_COMMAND_VALUE_TYPE_BOOL表示布尔类型；IME_COMMAND_VALUE_TYPE_INT32表示32位带符号整数类型。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，type已被写入当前value的数据类型。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，command或type参数为NULL。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_PrivateCommand_GetBoolValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetBoolValue(InputMethod_PrivateCommand *command, bool *value)
```

**描述**

从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取布尔类型的value的值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被获取value值的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| bool *value | 输出参数，用于接收布尔类型的value值。此参数为输出指针，调用方需分配bool类型变量的内存并将其地址传入。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，value指针指向的内存已被写入布尔值。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，command或value参数为NULL。<br>     <br>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 查询失败，命令中没有布尔值，即当前value类型不是IME_COMMAND_VALUE_TYPE_BOOL（类型不匹配）。<br>     建议先调用OH_PrivateCommand_GetValueType确认类型。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_PrivateCommand_GetIntValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetIntValue(InputMethod_PrivateCommand *command, int32_t *value)
```

**描述**

从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取整数类型的value的值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被获取value值的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| int32_t *value | 输出参数，用于接收整数类型的value值。此参数为输出指针，调用方需分配int32_t类型变量的内存并将其地址传入。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，value指针指向的内存已被写入整数值。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，command或value参数为NULL。<br>     <br>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 查询失败，命令中没有整数值，即当前value类型不是IME_COMMAND_VALUE_TYPE_INT32（类型不匹配）。<br>     建议先调用OH_PrivateCommand_GetValueType确认类型。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_PrivateCommand_GetStrValue()

```c
InputMethod_ErrorCode OH_PrivateCommand_GetStrValue(InputMethod_PrivateCommand *command, const char **value, size_t *valueLength)
```

**描述**

从[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)获取字符串类型的value的值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md) *command | 指向即将被获取value值的[InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md)实例的指针。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| const char **value | 输出参数，用于接收字符串类型value值的指针。value的生命周期和command一致，请勿直接保存value地址，也不应直接修改value内容；推荐先拷贝后再使用。command实例销毁后，value指针失效，不应再访问。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |
| size_t *valueLength | 输出参数，用于返回字符串类型value值的字节长度。不允许传入NULL指针，否则返回IME_ERR_NULL_POINTER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，value和valueLength已被写入值。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，command、value或valueLength参数为NULL。<br>     <br>[IME_ERR_QUERY_FAILED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 查询失败，命令中没有字符串值，即当前value类型不是IME_COMMAND_VALUE_TYPE_STRING（类型不匹配）。<br>     建议先调用OH_PrivateCommand_GetValueType确认类型。<br>     <br>具体错误码可以参考 [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |


