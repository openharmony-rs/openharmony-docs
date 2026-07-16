# 使用ModularObjectDispatcher实现动态接口调用 (C/C++)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

从API版本26.0.0开始，系统提供ModularObjectDispatcher（[modular_object_dispatcher.h](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md)）组件，支持客户端在运行时动态查询服务端的接口元数据，并通过成员ID（MemberID）动态调用远端方法，无需在编译期依赖服务端的接口定义。

> **说明**
>
> - 有关模块化对象的介绍、基本概念和运行机制，请参考[模块化对象模型概述 (C/C++)](./modular-object-extension-overview.md)。
> - 有关ModularObjectExtensionAbility服务端和客户端的基础开发流程（连接、Proxy通信、断开），请参考[使用ModularObjectExtensionAbility实现模块化对象 (C/C++)](./modular-object-extension-development.md)。
> - 有关Taihe工具自动生成服务侧的Proxy/Stub代码及类型库文件，请参考[使用Taihe实现ModularObjectExtensionAbility的IPC通信](modular-object-extension-ability-taihe.md)。
## 基本概念

- [ModularObjectDispatcher（分发器）](../reference/apis-ability-kit/capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md)：客户端侧的动态调用引擎，基于远端Proxy对象创建，提供类型库元数据查询和动态方法调用能力。
- [TypeDescriptor（类型描述符）](../reference/apis-ability-kit/capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-typedescriptor8h.md)：通过分发器获取的元数据访问句柄，用于查询远端服务定义的接口、方法、枚举和结构体等信息。
- 类型库元数据（Type Library Metadata）：服务端通过[Taihe工具](modular-object-extension-ability-taihe.md#基本概念)生成的类型描述文件（`.typelib.json`），定义了接口、方法签名、参数类型、枚举值和结构体字段。分发器在首次访问时从远端延迟加载该文件。
- [Variant（变体）](../reference/apis-ability-kit/capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)：一种能够存储多种不同类型值的通用数据容器，通过类型标签（vt字段）区分实际存储的数据类型，用于方法调用的参数传递和返回值接收。
- MemberID（成员ID）：方法在类型库中的唯一标识，客户端通过方法名解析出MemberID后，即可使用该ID发起动态调用。

## 运行机制

ModularObjectDispatcher与ModularObjectExtensionAbility的关系如下图所示：

![modular_object_dispatcher_architecture](figures/modular_object_dispatcher_architecture.png)

1. **创建分发器**：客户端通过连接ModularObjectExtensionAbility获取远端Proxy对象后，使用[OH_AbilityRuntime_ModObjDispatcher_CreateMainServiceInstance](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_createmainserviceinstance)接口从Proxy对象创建分发器实例。
2. **延迟加载元数据**：分发器在首次调用元数据查询或方法调用接口时，通过IPC从远端服务获取类型库元数据并缓存在本地，后续调用直接使用缓存，无需重复加载。
3. **查询接口信息**：通过[OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_gettypedescriptor)获取类型描述符，查询服务端定义的接口、方法、参数类型、枚举和结构体等元数据。
4. **动态方法调用**：通过[OH_AbilityRuntime_TypeDescriptor_GetMethodMemberId](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodmemberid)将方法名解析为MemberID，再通过[OH_AbilityRuntime_ModObjDispatcher_CallMethod](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_callmethod)发起调用。参数通过Variant封装，返回值也通过Variant接收。

与静态调用方式（编译期依赖服务端接口定义）相比，动态调用方式无需编译期绑定，适用于接口在运行时才能确定的场景，如通用调用框架、脚本引擎、动态测试工具等。

## 约束与限制

- 使用ModularObjectDispatcher前，需确保客户端已与ModularObjectExtensionAbility建立连接，连接相关约束与限制请参考[使用ModularObjectExtensionAbility实现模块化对象 (C/C++)](./modular-object-extension-development.md#约束与限制)。
- 使用动态调用前，需确保服务端的ModularObjectExtensionAbility已通过Taihe工具生成类型库元数据文件，否则动态调用将不可用。
- 方法的参数和返回值类型由服务端定义，客户端须通过元数据查询获取后，严格按照类型构造Variant，否则将返回类型不匹配错误。

## 开发步骤

### 前提条件

已完成客户端连接ModularObjectExtensionAbility并获取Proxy对象，请参考[使用ModularObjectExtensionAbility实现模块化对象 (C/C++)](./modular-object-extension-development.md)中的"连接ModularObjectExtensionAbility"和"通过Proxy与服务端通信"章节。

以下步骤假设已通过连接回调获取到类型为`OHIPCRemoteProxy*`的`g_remoteProxy`对象，以及保存分发器、类型描述符的全局变量`g_ModObjDispatcher`、`g_TypeDescriptor`。

### 创建分发器实例

通过Proxy对象创建主服务接口的分发器实例。类型库元数据将在首次需要时从远端延迟加载。

<!-- @[modular_object_extension_dispatcher_createMainServiceInstance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
AbilityRuntime_ErrorCode err =
    OH_AbilityRuntime_ModObjDispatcher_CreateMainServiceInstance(g_remoteProxy, &g_ModObjDispatcher);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "CreateMainServiceInstance err:%{public}d", err);
    return nullptr;
}
```

如果服务端定义了多个非主服务接口，可通过[OH_AbilityRuntime_ModObjDispatcher_CreateSubInstance](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_createsubinstance)创建子实例分发器。子实例共享主服务分发器的类型库元数据，但使用独立的IPC代理发送请求。

### 获取类型描述符

通过[OH_AbilityRuntime_ModObjDispatcher_HasTypeDescriptor](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_hastypedescriptor)接口判断远端服务是否提供了类型库元数据。只有支持动态接口的服务端才能进行后续的元数据查询和动态调用。

<!-- @[modular_object_extension_dispatcher_hasTypeDescriptor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
uint32_t hasTypeDescriptor = 0;
AbilityRuntime_ErrorCode err =
    OH_AbilityRuntime_ModObjDispatcher_HasTypeDescriptor(g_ModObjDispatcher, &hasTypeDescriptor);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR || hasTypeDescriptor == 0) {
    // 查询失败处理
    // 服务端未提供类型库元数据，不支持动态接口
    OH_LOG_ERROR(LOG_APP, "The type library metadata is not available from the remote service err:%{public}d",
        err);
    return nullptr;
}
```

确认远端支持类型库元数据后，通过[OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_gettypedescriptor)获取类型描述符句柄。

<!-- @[modular_object_extension_dispatcher_getTypeDescriptor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
err = OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor(g_ModObjDispatcher, &g_TypeDescriptor);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "GetTypeDescriptor err:%{public}d", err);
    return nullptr;
}
```

### 查询接口信息说明书

通过分发器获取TypeDescriptor句柄，查询服务端定义的接口、方法、枚举和结构体等元数据信息。

**查询类型库版本**

通过[OH_AbilityRuntime_TypeDescriptor_GetVersion](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getversion)获取类型库版本号字符串。

<!-- @[modular_object_extension_dispatcher_getVersion](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
char version[256];
AbilityRuntime_ErrorCode err =
    OH_AbilityRuntime_TypeDescriptor_GetVersion(g_TypeDescriptor, version, sizeof(version));
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "GetVersion err:%{public}d", err);
    return nullptr;
}
OH_LOG_INFO(LOG_APP, "Version:%{public}s", version);
```

**查询主服务接口名称**

通过[OH_AbilityRuntime_TypeDescriptor_GetMainServiceInterfaceName](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmainserviceinterfacename)获取主服务接口名称。

<!-- @[modular_object_extension_dispatcher_getMainServiceInterfaceName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
char mainServiceInterfaceName[256];
err = OH_AbilityRuntime_TypeDescriptor_GetMainServiceInterfaceName(g_TypeDescriptor, mainServiceInterfaceName,
    sizeof(mainServiceInterfaceName));
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "GetMainServiceInterfaceName err:%{public}d", err);
    return nullptr;
}
OH_LOG_INFO(LOG_APP, "MainServiceInterfaceName:%{public}s", mainServiceInterfaceName);
```

**查询所有接口名称**

通过[OH_AbilityRuntime_TypeDescriptor_GetInterfaceCount](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getinterfacecount)获取接口数量，再通过[OH_AbilityRuntime_TypeDescriptor_GetInterfaceName](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getinterfacename)逐个获取接口名称。

<!-- @[modular_object_extension_dispatcher_getInterface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
uint32_t interfaceCount = 0;
AbilityRuntime_ErrorCode err =
    OH_AbilityRuntime_TypeDescriptor_GetInterfaceCount(g_TypeDescriptor, &interfaceCount);
if (!CheckApiErr(err, "GetInterfaceCount")) {
    return nullptr;
}
OH_LOG_INFO(LOG_APP, "InterfaceCount:%{public}d", interfaceCount);

for (uint32_t interfaceIndex = 0; interfaceIndex < interfaceCount; interfaceIndex++) {
    char interfaceName[256];
    err = OH_AbilityRuntime_TypeDescriptor_GetInterfaceName(g_TypeDescriptor, interfaceIndex, interfaceName,
        sizeof(interfaceName));
    if (!CheckApiErr(err, "GetInterfaceName")) {
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "InterfaceName:%{public}s", interfaceName);

    // ...
}
```

**遍历接口下的方法名称**

针对每个接口，通过[OH_AbilityRuntime_TypeDescriptor_GetMethodCount](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodcount)获取方法数量，再通过[OH_AbilityRuntime_TypeDescriptor_GetMethodName](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodname)和[OH_AbilityRuntime_TypeDescriptor_GetMethodMemberId](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodmemberid)获取方法名称及其MemberID。

<!-- @[modular_object_extension_dispatcher_getMethod](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static void QueryMethodMetadata(const char *interfaceName)
{
    // 获取接口下的方法数量，逐个遍历方法名并解析对应的MemberID
    uint32_t methodCount = 0;
    AbilityRuntime_ErrorCode err =
        OH_AbilityRuntime_TypeDescriptor_GetMethodCount(g_TypeDescriptor, interfaceName, &methodCount);
    if (!CheckApiErr(err, "GetMethodCount")) {
        return;
    }
    OH_LOG_INFO(LOG_APP, "MethodCount:%{public}d", methodCount);
    // 遍历每个方法，获取方法名和MemberID
    for (uint32_t methodIndex = 0; methodIndex < methodCount; methodIndex++) {
        char methodName[256];
        err = OH_AbilityRuntime_TypeDescriptor_GetMethodName(g_TypeDescriptor, interfaceName, methodIndex,
            methodName, sizeof(methodName));
        if (!CheckApiErr(err, "GetMethodName")) {
            return;
        }
        OH_LOG_INFO(LOG_APP, "MethodName:%{public}s", methodName);

        uint32_t memId = 0;
        err = OH_AbilityRuntime_TypeDescriptor_GetMethodMemberId(g_TypeDescriptor, interfaceName, methodName,
            &memId);
        if (!CheckApiErr(err, "GetMethodMemberId")) {
            return;
        }
        OH_LOG_INFO(LOG_APP, "MethodMemberId:%{public}d", memId);

        // ...
    }
}
```

**查询所有结构体名称**

通过[OH_AbilityRuntime_TypeDescriptor_GetStructCount](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getstructcount)获取结构体数量，再通过[OH_AbilityRuntime_TypeDescriptor_GetStructName](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getstructname)逐个获取结构体名称。

<!-- @[modular_object_extension_dispatcher_getStructName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
uint32_t structCount = 0;
AbilityRuntime_ErrorCode err = OH_AbilityRuntime_TypeDescriptor_GetStructCount(g_TypeDescriptor, &structCount);
if (!CheckApiErr(err, "GetStructCount")) {
    return nullptr;
}
OH_LOG_INFO(LOG_APP, "StructCount:%{public}d", structCount);

for (uint32_t structIndex = 0; structIndex < structCount; structIndex++) {
    char structName[256];
    err = OH_AbilityRuntime_TypeDescriptor_GetStructName(g_TypeDescriptor, structIndex, structName,
        sizeof(structName));
    if (!CheckApiErr(err, "GetStructName")) {
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "StructName:%{public}s", structName);

    // ...
}
```

**遍历结构体的字段名称和类型**

针对每个结构体，通过[OH_AbilityRuntime_TypeDescriptor_GetStructFieldCount](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getstructfieldcount)获取字段数量，再通过[OH_AbilityRuntime_TypeDescriptor_GetStructFieldName](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getstructfieldname)和[OH_AbilityRuntime_TypeDescriptor_GetStructFieldType](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getstructfieldtype)逐个获取字段名称和类型。

<!-- @[modular_object_extension_dispatcher_getStructField](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
// 获取结构体的字段数量，逐个遍历字段名和字段类型
uint32_t fieldCount = 0;
err = OH_AbilityRuntime_TypeDescriptor_GetStructFieldCount(g_TypeDescriptor, structName, &fieldCount);
if (!CheckApiErr(err, "GetStructFieldCount")) {
    return nullptr;
}
OH_LOG_INFO(LOG_APP, "FieldCount:%{public}d", fieldCount);
// 遍历每个字段，获取字段名和字段类型
for (uint32_t fieldIndex = 0; fieldIndex < fieldCount; fieldIndex++) {
    char fieldName[256];
    err = OH_AbilityRuntime_TypeDescriptor_GetStructFieldName(g_TypeDescriptor, structName, fieldIndex,
        fieldName, sizeof(fieldName));
    if (!CheckApiErr(err, "GetStructFieldName")) {
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "FieldName:%{public}s", fieldName);
    OH_AbilityRuntime_ModObjDispatcher_TypeInfo typeInfo = {
        .vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
    err = OH_AbilityRuntime_TypeDescriptor_GetStructFieldType(g_TypeDescriptor, structName, fieldName,
        &typeInfo);
    if (!CheckApiErr(err, "GetStructFieldType")) {
        return nullptr;
    }
    //...
    OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear(&typeInfo);
}
```

**查询所有枚举名称**

通过[OH_AbilityRuntime_TypeDescriptor_GetEnumCount](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getenumcount)获取枚举数量，再通过[OH_AbilityRuntime_TypeDescriptor_GetEnumName](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getenumname)逐个获取枚举名称。

<!-- @[modular_object_extension_dispatcher_getEnumName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
uint32_t enumCount = 0;
AbilityRuntime_ErrorCode err = OH_AbilityRuntime_TypeDescriptor_GetEnumCount(g_TypeDescriptor, &enumCount);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "GetEnumCount err:%{public}d", err);
    return nullptr;
}
OH_LOG_INFO(LOG_APP, "EnumCount:%{public}d", enumCount);

for (uint32_t enumIndex = 0; enumIndex < enumCount; enumIndex++) {
    char enumName[256];
    err = OH_AbilityRuntime_TypeDescriptor_GetEnumName(g_TypeDescriptor, enumIndex, enumName, sizeof(enumName));
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        OH_LOG_ERROR(LOG_APP, "GetEnumName err:%{public}d", err);
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "EnumName:%{public}s", enumName);

    // ...
}
```

**遍历所有枚举值名称和枚举值**

针对每个枚举，通过[OH_AbilityRuntime_TypeDescriptor_GetEnumValueCount](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getenumvaluecount)获取枚举值数量，再通过[OH_AbilityRuntime_TypeDescriptor_GetEnumValueName](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getenumvaluename)和[OH_AbilityRuntime_TypeDescriptor_GetEnumValue](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getenumvalue)逐个获取枚举值名称和枚举值。

<!-- @[modular_object_extension_dispatcher_getEnumValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
// 遍历枚举的所有枚举值名称和对应的枚举值
uint32_t valueCount = 0;
err = OH_AbilityRuntime_TypeDescriptor_GetEnumValueCount(g_TypeDescriptor, enumName, &valueCount);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "GetEnumValueCount err:%{public}d", err);
    return nullptr;
}
OH_LOG_INFO(LOG_APP, "valueCount:%{public}d", valueCount);
for (uint32_t valueIndex = 0; valueIndex < valueCount; valueIndex++) {
    char valueName[256];
    err = OH_AbilityRuntime_TypeDescriptor_GetEnumValueName(g_TypeDescriptor, enumName, valueIndex, valueName,
        sizeof(valueName));
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        OH_LOG_ERROR(LOG_APP, "GetEnumValueName err:%{public}d", err);
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "ValueName:%{public}s", valueName);

    int32_t value = 0;
    err = OH_AbilityRuntime_TypeDescriptor_GetEnumValue(g_TypeDescriptor, enumName, valueName, &value);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        OH_LOG_ERROR(LOG_APP, "GetEnumValue err:%{public}d", err);
        return nullptr;
    }
    OH_LOG_INFO(LOG_APP, "value:%{public}d", value);
}
```

### 获取方法的参数类型

在动态调用前，需获取方法的返回值类型和参数类型，确保构造的Variant与期望类型匹配。

**获取方法返回值类型**

通过[OH_AbilityRuntime_TypeDescriptor_GetMethodReturnType](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodreturntype)获取方法的返回值类型信息。TypeInfo中的`vt`字段标识数据类型。

<!-- @[modular_object_extension_dispatcher_getMethodReturnType](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static void QueryMethodReturnType(const char *interfaceName, const char *methodName)
{
    OH_AbilityRuntime_ModObjDispatcher_TypeInfo returnTypeInfo = {
        .vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
    AbilityRuntime_ErrorCode err =
        OH_AbilityRuntime_TypeDescriptor_GetMethodReturnType(g_TypeDescriptor, interfaceName, methodName,
            &returnTypeInfo);
    if (!CheckApiErr(err, "GetMethodReturnType")) {
        return;
    }
    //...
    OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear(&returnTypeInfo);
}
```

**获取方法入参类型和名称**

通过[OH_AbilityRuntime_TypeDescriptor_GetMethodParamCount](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodparamcount)获取方法参数数量，再通过[OH_AbilityRuntime_TypeDescriptor_GetMethodParamName](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodparamname)和[OH_AbilityRuntime_TypeDescriptor_GetMethodParamType](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodparamtype)逐个获取参数名称和类型。

<!-- @[modular_object_extension_dispatcher_getMethodParam](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static void QueryMethodParamInfo(const char *interfaceName, const char *methodName)
{
    // 获取方法的参数数量，逐个遍历参数名和参数类型
    uint32_t paramCount = 0;
    AbilityRuntime_ErrorCode err =
        OH_AbilityRuntime_TypeDescriptor_GetMethodParamCount(g_TypeDescriptor, interfaceName, methodName,
            &paramCount);
    if (!CheckApiErr(err, "GetMethodParamCount")) {
        return;
    }
    OH_LOG_INFO(LOG_APP, "MethodParamCount:%{public}d", paramCount);

    // 遍历每个参数，获取参数名和参数类型
    for (uint32_t paramIndex = 0; paramIndex < paramCount; paramIndex++) {
        char methodParamName[256];
        err = OH_AbilityRuntime_TypeDescriptor_GetMethodParamName(
            g_TypeDescriptor, interfaceName, methodName, paramIndex, methodParamName, sizeof(methodParamName));
        if (!CheckApiErr(err, "GetMethodParamName")) {
            return;
        }
        OH_LOG_INFO(LOG_APP, "GetMethodParamName:%{public}s", methodParamName);

        OH_AbilityRuntime_ModObjDispatcher_TypeInfo paramTypeInfo = {
            .vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
        err = OH_AbilityRuntime_TypeDescriptor_GetMethodParamType(g_TypeDescriptor, interfaceName, methodName,
            paramIndex, &paramTypeInfo);
        if (!CheckApiErr(err, "GetMethodParamType")) {
            return;
        }
        //...
        OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear(&paramTypeInfo);
    }
}
```

TypeInfo中的`vt`字段表示数据类型，常见类型如下表所示：

| vt值 | 类型 | 说明 |
| --- | --- | --- |
| VT_I32 | int32_t | 32位有符号整数 |
| VT_I64 | int64_t | 64位有符号整数 |
| VT_F64 | double | 64位浮点数 |
| VT_BOOL | bool | 布尔值 |
| VT_STRING | char* | UTF-8字符串 |
| VT_ARRAY | Array | 定长数组 |
| VT_VECTOR | Vector | 动态向量 |
| VT_SET | Set | 不重复元素集合 |
| VT_MAP | Map | 键值对映射 |
| VT_STRUCT | Struct | 结构体 |
| VT_ENUM | enum | 枚举值（存储为int32_t） |

### 通过动态接口执行动态调用

通过方法名解析MemberID，构造参数后发起动态调用。MemberID可通过[OH_AbilityRuntime_TypeDescriptor_GetMethodMemberId](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodmemberid)接口从TypeDescriptor查询，具体参见[遍历接口下的方法名称](#遍历接口下的方法名称)。

**构造参数并调用**

以调用`Add(int32_t a, int32_t b)`方法为例，将参数封装为Variant数组，通过[OH_AbilityRuntime_ModObjDispatcher_CallMethod](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_callmethod)发起调用。

<!-- @[modular_object_extension_dispatcher_callMethod](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
// 构造参数
OH_AbilityRuntime_ModObjDispatcher_Variant params[2] = {
    {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32, .u.i32Val = 10},
    {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32, .u.i32Val = 20},
};

OH_AbilityRuntime_ModObjDispatcher_InputParams inputParams = {.rgvarg = params, .cArgs = 2};

// 调用方法，memberId 17 为 Add 方法对应的 MemberID，可通过 OH_AbilityRuntime_TypeDescriptor_GetMethodMemberId 获取
OH_AbilityRuntime_ModObjDispatcher_Variant result = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
int32_t methodErrCode = 0;
uint32_t memID = 17;
AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjDispatcher_CallMethod(g_ModObjDispatcher, memID,
    &inputParams, &result, &methodErrCode);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    // 框架级错误：IPC通信失败、参数类型不匹配等
    OH_LOG_ERROR(LOG_APP, "add err:%{public}d", err);
    return nullptr;
}
if (methodErrCode != 0) {
    // 方法级错误：远端方法执行返回的业务错误码
    OH_LOG_ERROR(LOG_APP, "methodErrCode:%{public}d", methodErrCode);
    return nullptr;
}
// result.u.i32Val 为返回值（30）
int32_t addResult = result.u.i32Val;
OH_LOG_INFO(LOG_APP, "addResult :%{public}d", addResult);
// 简单类型不需要清理
```

> **说明**
>
> CallMethod采用双层错误处理机制：
> - **框架级错误**（返回值）：IPC通信、元数据加载、参数类型校验等框架层面的问题。
> - **方法级错误**（pMethodErrCode输出参数）：远端方法执行返回的业务错误码，0表示方法执行成功。

### 传递复杂类型参数

当方法参数包含容器类型（数组、向量、集合、映射）或结构体时，需先创建对应的容器实例并填充数据，再将容器句柄包装为Variant参数。

**传递数组参数**

通过[OH_AbilityRuntime_ModObjDispatcher_ArrayCreate](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_arraycreate)创建数组，使用[OH_AbilityRuntime_ModObjDispatcher_ArraySet](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_arrayset)填充元素。下方示例以二维数组`array<array<i32,5>,5>`为例，分为创建数组、调用方法、解析结果三步。

创建并填充二维数组：先构造嵌套的TypeInfo（内层`array<i32,5>`，外层`array<inner,5>`），再用`ArrayCreate`创建外层数组，逐行创建内层数组并填充元素后设入外层。

<!-- @[modular_object_extension_dispatcher_callTypeArray_build](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static OH_AbilityRuntime_ModObjDispatcher_ArrayHandle BuildMatrixArray(uint32_t arrSize)
{
    // 构造嵌套数组类型信息：内层 array<i32,size>，外层 array<inner,size>
    OH_AbilityRuntime_ModObjDispatcher_TypeInfo elemType = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
    OH_AbilityRuntime_ModObjDispatcher_TypeInfo innerType = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ARRAY};
    innerType.u.arrayType.pElementType = &elemType;
    innerType.u.arrayType.size = arrSize;

    // 创建外层数组，逐行创建内层数组、填充元素后设入外层
    OH_AbilityRuntime_ModObjDispatcher_ArrayHandle matrixArray = NULL;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjDispatcher_ArrayCreate(&innerType, arrSize, &matrixArray);
    if (!CheckApiErr(err, "ArrayCreate outer")) {
        return NULL;
    }
    for (uint32_t i = 0; i < arrSize; i++) {
        OH_AbilityRuntime_ModObjDispatcher_ArrayHandle rowArray = NULL;
        err = OH_AbilityRuntime_ModObjDispatcher_ArrayCreate(&elemType, arrSize, &rowArray);
        if (!CheckApiErr(err, "ArrayCreate inner")) {
            OH_AbilityRuntime_ModObjDispatcher_ArrayRelease(&matrixArray);
            return NULL;
        }
        for (uint32_t j = 0; j < arrSize; j++) {
            // 填充内层数组元素
            OH_AbilityRuntime_ModObjDispatcher_Variant cell = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
            uint32_t multiply = 10;
            cell.u.i32Val = static_cast<int32_t>(i * multiply + j);
            OH_AbilityRuntime_ModObjDispatcher_ArraySet(rowArray, j, &cell);
        }
        // 将内层数组设入外层对应位置
        OH_AbilityRuntime_ModObjDispatcher_Variant rowVar = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ARRAY};
        rowVar.u.parrayVal = rowArray;
        OH_AbilityRuntime_ModObjDispatcher_ArraySet(matrixArray, i, &rowVar);
        OH_AbilityRuntime_ModObjDispatcher_ArrayRelease(&rowArray);
    }
    return matrixArray;
}
```

组装参数并调用方法：将数组句柄包装为Variant参数，通过`CallMethod`发起调用。

<!-- @[modular_object_extension_dispatcher_callTypeArray](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
uint32_t arrSize = 5;
OH_AbilityRuntime_ModObjDispatcher_ArrayHandle matrixArray = BuildMatrixArray(arrSize);
if (matrixArray == NULL) {
    return nullptr;
}
OH_AbilityRuntime_ModObjDispatcher_Variant param = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ARRAY};
param.u.parrayVal = matrixArray;
OH_AbilityRuntime_ModObjDispatcher_InputParams inputParams = {.rgvarg = &param, .cArgs = 1};
OH_AbilityRuntime_ModObjDispatcher_Variant result = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
int32_t methodErrCode = 0;
uint32_t memID = 19;
AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjDispatcher_CallMethod(g_ModObjDispatcher, memID,
    &inputParams, &result, &methodErrCode);
OH_AbilityRuntime_ModObjDispatcher_ArrayRelease(&matrixArray);
if (!CheckCallResult(err, methodErrCode, "TestType_Array")) {
    return nullptr;
}
ParseArrayResult(&result);
OH_AbilityRuntime_ModObjDispatcher_VariantClear(&result);
```

解析返回的二维数组：通过`ArrayGetSize`获取行列数，用`ArrayGet`逐层读取元素。

<!-- @[modular_object_extension_dispatcher_callTypeArray_parse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static void ParseArrayResult(OH_AbilityRuntime_ModObjDispatcher_Variant *result)
{
    // 校验返回类型，嵌套遍历二维数组读取每个元素
    if (result->vt != OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ARRAY || result->u.parrayVal == NULL) {
        OH_LOG_ERROR(LOG_APP, "TestType_Array result type unexpected");
        return;
    }
    // 逐行遍历，每行再逐列读取元素值
    uint32_t rowCount = 0;
    OH_AbilityRuntime_ModObjDispatcher_ArrayGetSize(result->u.parrayVal, &rowCount);
    for (uint32_t i = 0; i < rowCount; i++) {
        OH_AbilityRuntime_ModObjDispatcher_Variant rowVar = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
        OH_AbilityRuntime_ModObjDispatcher_ArrayGet(result->u.parrayVal, i, &rowVar);
        uint32_t colCount = 0;
        if (rowVar.u.parrayVal != NULL) {
            OH_AbilityRuntime_ModObjDispatcher_ArrayGetSize(rowVar.u.parrayVal, &colCount);
            for (uint32_t j = 0; j < colCount; j++) {
                OH_AbilityRuntime_ModObjDispatcher_Variant cell = {
                    .vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
                OH_AbilityRuntime_ModObjDispatcher_ArrayGet(rowVar.u.parrayVal, j, &cell);
                OH_LOG_INFO(LOG_APP, "array[%{public}u][%{public}u]=%{public}d", i, j, cell.u.i32Val);
            }
        }
        OH_AbilityRuntime_ModObjDispatcher_VariantClear(&rowVar);
    }
}
```

**传递向量参数**

通过[OH_AbilityRuntime_ModObjDispatcher_VectorCreate](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_vectorcreate)创建向量，使用[OH_AbilityRuntime_ModObjDispatcher_VectorAdd](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_vectoradd)添加元素。向量为动态长度容器。

<!-- @[modular_object_extension_dispatcher_callTypeVector](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
// 创建 vector<i32> 并添加元素
OH_AbilityRuntime_ModObjDispatcher_TypeInfo elemType = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
OH_AbilityRuntime_ModObjDispatcher_VectorHandle vec = NULL;
AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjDispatcher_VectorCreate(&elemType, &vec);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "VectorCreate err:%{public}d", err);
    return nullptr;
}
// 添加元素到向量
int32_t arrSize = 5;
for (int32_t i = 1; i <= arrSize; i++) {
    OH_AbilityRuntime_ModObjDispatcher_Variant v = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
    v.u.i32Val = i;
    OH_AbilityRuntime_ModObjDispatcher_VectorAdd(vec, &v);
}
// 组装参数并调用方法
OH_AbilityRuntime_ModObjDispatcher_Variant param = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_VECTOR};
param.u.pvectorVal = vec;
OH_AbilityRuntime_ModObjDispatcher_InputParams inputParams = {.rgvarg = &param, .cArgs = 1};
OH_AbilityRuntime_ModObjDispatcher_Variant result = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
int32_t methodErrCode = 0;
uint32_t memID = 21;
err = OH_AbilityRuntime_ModObjDispatcher_CallMethod(g_ModObjDispatcher, memID, &inputParams, &result,
    &methodErrCode);
OH_AbilityRuntime_ModObjDispatcher_VectorRelease(&vec);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "TestType_Vector err:%{public}d", err);
    return nullptr;
}
if (methodErrCode != 0) {
    OH_LOG_ERROR(LOG_APP, "TestType_Vector methodErrCode:%{public}d", methodErrCode);
    return nullptr;
}
// 解析返回的 vector
if (result.vt != OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_VECTOR || result.u.pvectorVal == NULL) {
    OH_LOG_ERROR(LOG_APP, "TestType_Vector result type unexpected");
    return nullptr;
}
uint32_t size = 0;
OH_AbilityRuntime_ModObjDispatcher_VectorGetSize(result.u.pvectorVal, &size);
for (uint32_t i = 0; i < size; i++) {
    OH_AbilityRuntime_ModObjDispatcher_Variant v = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
    OH_AbilityRuntime_ModObjDispatcher_VectorGet(result.u.pvectorVal, i, &v);
    OH_LOG_INFO(LOG_APP, "vector[%{public}u]=%{public}d", i, v.u.i32Val);
}
OH_AbilityRuntime_ModObjDispatcher_VariantClear(&result);
```

**传递集合参数**

通过[OH_AbilityRuntime_ModObjDispatcher_SetCreate](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_setcreate)创建集合，使用[OH_AbilityRuntime_ModObjDispatcher_SetAdd](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_setadd)添加元素。集合中的元素不重复。

<!-- @[modular_object_extension_dispatcher_callTypeSet](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
// 创建 set<i32> 并添加元素
OH_AbilityRuntime_ModObjDispatcher_TypeInfo elemType = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
OH_AbilityRuntime_ModObjDispatcher_SetHandle set = NULL;
AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjDispatcher_SetCreate(&elemType, &set);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "SetCreate err:%{public}d", err);
    return nullptr;
}
// 添加元素到集合
int32_t values[] = {11, 22, 33};
for (int32_t v : values) {
    OH_AbilityRuntime_ModObjDispatcher_Variant item = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
    item.u.i32Val = v;
    OH_AbilityRuntime_ModObjDispatcher_SetAdd(set, &item);
}
// 组装参数并调用方法
OH_AbilityRuntime_ModObjDispatcher_Variant param = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_SET};
param.u.psetVal = set;
OH_AbilityRuntime_ModObjDispatcher_InputParams inputParams = {.rgvarg = &param, .cArgs = 1};
OH_AbilityRuntime_ModObjDispatcher_Variant result = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
int32_t methodErrCode = 0;
uint32_t memID = 23;
err = OH_AbilityRuntime_ModObjDispatcher_CallMethod(g_ModObjDispatcher, memID, &inputParams, &result,
    &methodErrCode);
OH_AbilityRuntime_ModObjDispatcher_SetRelease(&set);
if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
    OH_LOG_ERROR(LOG_APP, "TestType_Set err:%{public}d", err);
    return nullptr;
}
if (methodErrCode != 0) {
    OH_LOG_ERROR(LOG_APP, "TestType_Set methodErrCode:%{public}d", methodErrCode);
    return nullptr;
}
// 解析返回的 set
if (result.vt != OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_SET || result.u.psetVal == NULL) {
    OH_LOG_ERROR(LOG_APP, "TestType_Set result type unexpected");
    return nullptr;
}
uint32_t size = 0;
OH_AbilityRuntime_ModObjDispatcher_SetGetSize(result.u.psetVal, &size);
for (uint32_t i = 0; i < size; i++) {
    OH_AbilityRuntime_ModObjDispatcher_Variant v = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
    OH_AbilityRuntime_ModObjDispatcher_SetGetAt(result.u.psetVal, i, &v);
    OH_LOG_INFO(LOG_APP, "set[%{public}u]=%{public}d", i, v.u.i32Val);
}
OH_AbilityRuntime_ModObjDispatcher_VariantClear(&result);
```

**传递映射参数**

通过[OH_AbilityRuntime_ModObjDispatcher_MapCreate](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_mapcreate)创建映射，使用[OH_AbilityRuntime_ModObjDispatcher_MapPut](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_mapput)添加键值对。

创建映射并填充键值对：通过`MapCreate`指定键值类型后，构造key和value的Variant调用`MapPut`逐条添加。

<!-- @[modular_object_extension_dispatcher_callTypeMap_fill](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static void FillMapEntries(OH_AbilityRuntime_ModObjDispatcher_MapHandle map)
{
    const char *keys[] = {"cn", "us", "jp"};
    int32_t values[] = {86, 1, 81};
    const int32_t length = sizeof(values) / sizeof(values[0]);
    for (int32_t i = 0; i < length; i++) {
        OH_AbilityRuntime_ModObjDispatcher_Variant key = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_STRING};
        key.u.bstrVal = strdup(keys[i]);
        OH_AbilityRuntime_ModObjDispatcher_Variant val = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
        val.u.i32Val = values[i];
        OH_AbilityRuntime_ModObjDispatcher_MapPut(map, &key, &val);
        free(key.u.bstrVal);
    }
}
```

组装参数并调用方法：将映射句柄包装为Variant参数，通过`CallMethod`发起调用。

<!-- @[modular_object_extension_dispatcher_callTypeMap](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
// 创建 map<String,i32>，填充键值对后调用方法
OH_AbilityRuntime_ModObjDispatcher_TypeInfo valType = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
OH_AbilityRuntime_ModObjDispatcher_MapHandle map = NULL;
AbilityRuntime_ErrorCode err =
    OH_AbilityRuntime_ModObjDispatcher_MapCreate(OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_STRING, &valType, &map);
if (!CheckApiErr(err, "MapCreate")) {
    return nullptr;
}
FillMapEntries(map);
// 组装参数并调用方法
OH_AbilityRuntime_ModObjDispatcher_Variant param = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_MAP};
param.u.pmapVal = map;
OH_AbilityRuntime_ModObjDispatcher_InputParams inputParams = {.rgvarg = &param, .cArgs = 1};
OH_AbilityRuntime_ModObjDispatcher_Variant result = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
int32_t methodErrCode = 0;
uint32_t memID = 25;
err = OH_AbilityRuntime_ModObjDispatcher_CallMethod(g_ModObjDispatcher, memID, &inputParams, &result,
    &methodErrCode);
OH_AbilityRuntime_ModObjDispatcher_MapRelease(&map);
if (!CheckCallResult(err, methodErrCode, "TestType_Map")) {
    return nullptr;
}
ParseMapResult(&result);
OH_AbilityRuntime_ModObjDispatcher_VariantClear(&result);
```

解析返回的映射：通过`MapGetSize`获取元素数量，用`MapGetKeyAt`和`MapGetValueAt`逐条读取键值。

<!-- @[modular_object_extension_dispatcher_callTypeMap_parse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static void ParseMapResult(OH_AbilityRuntime_ModObjDispatcher_Variant *result)
{
    if (result->vt != OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_MAP || result->u.pmapVal == NULL) {
        OH_LOG_ERROR(LOG_APP, "TestType_Map result type unexpected");
        return;
    }
    uint32_t size = 0;
    OH_AbilityRuntime_ModObjDispatcher_MapGetSize(result->u.pmapVal, &size);
    OH_LOG_INFO(LOG_APP, "result map size:%{public}u", size);
    for (uint32_t i = 0; i < size; i++) {
        OH_AbilityRuntime_ModObjDispatcher_Variant k = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
        OH_AbilityRuntime_ModObjDispatcher_Variant v = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
        OH_AbilityRuntime_ModObjDispatcher_MapGetKeyAt(result->u.pmapVal, i, &k);
        OH_AbilityRuntime_ModObjDispatcher_MapGetValueAt(result->u.pmapVal, i, &v);
        OH_LOG_INFO(LOG_APP, "map[%{public}s]=%{public}d", (k.u.bstrVal != NULL) ? k.u.bstrVal : "(null)", v.u.i32Val);
        OH_AbilityRuntime_ModObjDispatcher_VariantClear(&k);
    }
}
```

**传递结构体参数**

通过[OH_AbilityRuntime_ModObjDispatcher_StructCreate](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_structcreate)按结构体名称创建实例，使用[OH_AbilityRuntime_ModObjDispatcher_StructSetField](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_structsetfield)填充字段值。

创建结构体并设置字段：通过`StructCreate`按名称创建实例，再用`StructSetField`逐个设置字段值。

<!-- @[modular_object_extension_dispatcher_callTypeStruct_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static OH_AbilityRuntime_ModObjDispatcher_StructHandle CreatePointStruct(int32_t x, int32_t y)
{
    OH_AbilityRuntime_ModObjDispatcher_StructHandle handle = NULL;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjDispatcher_StructCreate("Point", &handle);
    if (!CheckApiErr(err, "StructCreate")) {
        return NULL;
    }
    OH_AbilityRuntime_ModObjDispatcher_Variant vx = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
    vx.u.i32Val = x;
    OH_AbilityRuntime_ModObjDispatcher_Variant vy = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32};
    vy.u.i32Val = y;
    OH_AbilityRuntime_ModObjDispatcher_StructSetField(handle, "x", &vx);
    OH_AbilityRuntime_ModObjDispatcher_StructSetField(handle, "y", &vy);
    return handle;
}
```

组装参数并调用方法：将结构体句柄包装为Variant参数，通过`CallMethod`发起调用。

<!-- @[modular_object_extension_dispatcher_callTypeStruct](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
// 创建 Point 结构体入参，组装参数后调用方法
OH_AbilityRuntime_ModObjDispatcher_StructHandle structA = CreatePointStruct(10, 20);
if (structA == NULL) {
    return nullptr;
}
int32_t idx = 5;
int32_t idy = 8;
// 组装入参：结构体 a、idx、idy
OH_AbilityRuntime_ModObjDispatcher_Variant params[3] = {
    {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_STRUCT, .u.pstructVal = structA},
    {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32, .u.i32Val = idx},
    {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32, .u.i32Val = idy},
};

OH_AbilityRuntime_ModObjDispatcher_InputParams inputParams = {.rgvarg = params, .cArgs = 3};
OH_AbilityRuntime_ModObjDispatcher_Variant result = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
int32_t methodErrCode = 0;
uint32_t memID = 29;
AbilityRuntime_ErrorCode err = OH_AbilityRuntime_ModObjDispatcher_CallMethod(g_ModObjDispatcher, memID,
    &inputParams, &result, &methodErrCode);
OH_AbilityRuntime_ModObjDispatcher_StructRelease(&structA);
if (!CheckCallResult(err, methodErrCode, "TestType_Struct")) {
    return nullptr;
}
ParseStructResult(&result);
OH_AbilityRuntime_ModObjDispatcher_VariantClear(&result);
```

解析返回的结构体：通过`StructGetField`按字段名读取返回结构体中的字段值。

<!-- @[modular_object_extension_dispatcher_callTypeStruct_parse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ModularObjectExtensionDispatcherClient/entry/src/main/cpp/napi_init.cpp) -->

``` C
static void ParseStructResult(OH_AbilityRuntime_ModObjDispatcher_Variant *result)
{
    if (result->vt != OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_STRUCT || result->u.pstructVal == NULL) {
        OH_LOG_ERROR(LOG_APP, "TestType_Struct result type unexpected, vt:%{public}d", result->vt);
        return;
    }
    OH_AbilityRuntime_ModObjDispatcher_Variant outX = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
    OH_AbilityRuntime_ModObjDispatcher_Variant outY = {.vt = OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_EMPTY};
    OH_AbilityRuntime_ModObjDispatcher_StructGetField(result->u.pstructVal, "x", &outX);
    OH_AbilityRuntime_ModObjDispatcher_StructGetField(result->u.pstructVal, "y", &outY);
    OH_LOG_INFO(LOG_APP, "Point b: x=%{public}d, y=%{public}d", outX.u.i32Val, outY.u.i32Val);
    OH_AbilityRuntime_ModObjDispatcher_VariantClear(&outX);
    OH_AbilityRuntime_ModObjDispatcher_VariantClear(&outY);
}
```

### 资源释放

所有通过Create接口获取的句柄和通过Get接口返回的Variant/TypeInfo均需在不再使用时释放，避免内存泄漏。

``` C
// 释放TypeDescriptor
if (g_TypeDescriptor != NULL) {
    OH_AbilityRuntime_TypeDescriptor_Release(&g_TypeDescriptor);
}

// 释放分发器
if (g_ModObjDispatcher != NULL) {
    OH_AbilityRuntime_ModObjDispatcher_Release(&g_ModObjDispatcher);
}
```

资源释放需遵循以下规则：

- 通过[OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear)清理TypeInfo持有的堆资源，清理后内部指针置为NULL，vt重置为VT_EMPTY。
- 通过[OH_AbilityRuntime_ModObjDispatcher_VariantClear](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear)清理Variant持有的堆资源（字符串、容器句柄等），清理后变体重置为VT_EMPTY。简单类型（布尔、整数、浮点数）不持有堆资源，无需清理。
- 所有容器的Release接口会将句柄指针置为NULL，支持传入NULL指针。
- Variant传入容器函数（如ArraySet、MapPut）时执行深拷贝，调用方保留原始Variant的所有权，需自行释放。
- 从容器函数返回的Variant（如ArrayGet、MapGet、CallMethod返回值）为深拷贝，调用方获得所有权，需调用VariantClear释放。
- 禁止对Variant或TypeInfo的浅拷贝调用Clear，只能清理其中一个。

## 相关文档

- [模块化对象模型概述 (C/C++)](./modular-object-extension-overview.md)
- [使用ModularObjectExtensionAbility实现模块化对象 (C/C++)](./modular-object-extension-development.md)
- [使用Taihe实现ModularObjectExtensionAbility的IPC通信](./modular-object-extension-ability-taihe.md)
- [ModularObjectDispatcher API参考](../reference/apis-ability-kit/capi-modular-object-dispatcher-h.md)
