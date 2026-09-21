# modular_object_dispatcher.h

## Overview

Declare common types and interfaces for modular object dispatcher.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md) | OH_AbilityRuntime_ModObjDispatcher_TypeInfo | Defines the parameter type descriptor for modular object dispatcher.<br> Describes the type of a parameter or return value using a tagged union. for array types, use u.arrayType.pElementType and u.arrayType.size; for vector/set types, use u.pElementType; for struct/proxy/stub/enum types, use u.idlType. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md) | OH_AbilityRuntime_ModObjDispatcher_Variant | Defines a variant structure using union + type tag for ABI compatibility. |
| [OH_AbilityRuntime_ModObjDispatcher_InputParams](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-inputparams.md) | OH_AbilityRuntime_ModObjDispatcher_InputParams | Defines a parameter structure for method invocation. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) | - | Defines a pointer to OH_AbilityRuntime_ModularObjectDispatcher_TypeDescriptor. |
| [OH_AbilityRuntime_ModularObjectDispatcher*](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md) | OH_AbilityRuntime_ModObjDispatcherHandle | Defines a pointer to OH_AbilityRuntime_ModularObjectDispatcher. |
| [OH_AbilityRuntime_ModularObjectDispatcher_Array*](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-array8h.md) | OH_AbilityRuntime_ModObjDispatcher_ArrayHandle | Defines a pointer to OH_AbilityRuntime_ModularObjectDispatcher_Array. |
| [OH_AbilityRuntime_ModularObjectDispatcher_Vector*](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md) | OH_AbilityRuntime_ModObjDispatcher_VectorHandle | Defines a pointer to OH_AbilityRuntime_ModularObjectDispatcher_Vector. |
| [OH_AbilityRuntime_ModularObjectDispatcher_Set*](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) | OH_AbilityRuntime_ModObjDispatcher_SetHandle | Defines a pointer to OH_AbilityRuntime_ModularObjectDispatcher_Set. |
| [OH_AbilityRuntime_ModularObjectDispatcher_Map*](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) | OH_AbilityRuntime_ModObjDispatcher_MapHandle | Defines a pointer to OH_AbilityRuntime_ModularObjectDispatcher_Map. |
| [OH_AbilityRuntime_ModularObjectDispatcher_Struct*](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-struct8h.md) | OH_AbilityRuntime_ModObjDispatcher_StructHandle | Defines a pointer to OH_AbilityRuntime_ModularObjectDispatcher_Struct. |

### Function

| Name | Description |
| -- | -- |
| [void OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear(OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pTypeInfo)](#oh_abilityruntime_modobjdispatcher_typeinfoclear) | Clear TypeInfo resources.<br> Recursively release any heap resources held by a TypeInfo struct (idlType strings, child TypeInfo nodes for map/array/vector/set types). After clearing, all pointers are set to NULL but the TypeInfo struct itself is not freed (it is typically stack-allocated by the caller).<br> TypeInfoClear must NOT be called on a shallow copy of another TypeInfo. If TypeInfo t2 = t1 is performed, only clear one of them. |
| [void OH_AbilityRuntime_ModObjDispatcher_VariantClear(OH_AbilityRuntime_ModObjDispatcher_Variant* pVariant)](#oh_abilityruntime_modobjdispatcher_variantclear) | Clear variant resources.<br> Release any resources held by the variant (strings, container handles, etc.). After clearing, the variant is reset to VT_EMPTY with all fields zeroed.<br> Ownership rules: - When a Variant is passed to a function (e.g. Array_Set, Map_Put), the function performs a deep copy. The caller retains ownership of the original Variant and is responsible for freeing its own resources (e.g. free(bstrVal) for strings, Release for container handles). - When a Variant is returned from a function (e.g. Array_Get, Map_Get, CallMethod), the function performs a deep copy and the caller owns the returned Variant. The caller must call VariantClear exactly once to release the resources. - Simple types (bool, i32, f64, etc.) do not hold heap resources and do not require VariantClear, though calling it is harmless. - VariantClear must NOT be called on a shallow copy of another Variant. If Variant v2 = v1 is performed, only clear one of them. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_CreateMainServiceInstance(OHIPCRemoteProxy* remoteProxy, OH_AbilityRuntime_ModObjDispatcherHandle* ppModObjDispatcher)](#oh_abilityruntime_modobjdispatcher_createmainserviceinstance) | Create a modular object dispatcher instance from an IPC remote proxy for the main service interface.<br> The type library metadata will be lazily loaded from the remote service on the first call that requires it, such as HasTypeDescriptor, QueryMainServiceInterfaceMemIDsOfNames, or CallMethod. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_CreateSubInstance(OH_AbilityRuntime_ModObjDispatcherHandle mainServiceDispatcher, OHIPCRemoteProxy* subProxy, OH_AbilityRuntime_ModObjDispatcherHandle* ppModObjDispatcher)](#oh_abilityruntime_modobjdispatcher_createsubinstance) | Create a sub-instance dispatcher bound to a mainService dispatcher.<br> The sub-instance shares the mainService dispatcher's metadata but uses its own IPC proxy. When CallMethod is invoked on the sub-instance, method metadata is resolved from the mainService dispatcher and the call is sent through subProxy. |
| [void OH_AbilityRuntime_ModObjDispatcher_Release(OH_AbilityRuntime_ModObjDispatcherHandle* ppModObjDispatcher)](#oh_abilityruntime_modobjdispatcher_release) | Release modular object dispatcher instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_HasTypeDescriptor(OH_AbilityRuntime_ModObjDispatcherHandle pModObjDispatcher, uint32_t* pctinfo)](#oh_abilityruntime_modobjdispatcher_hastypedescriptor) | Check if the type library metadata is available from the remote service. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor(OH_AbilityRuntime_ModObjDispatcherHandle pModObjDispatcher, OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle* ppTypeDescriptor)](#oh_abilityruntime_modobjdispatcher_gettypedescriptor) | Get type descriptor for querying interface metadata information.<br> The type descriptor provides access to type library metadata including interfaces, methods, enums, and structs defined in the remote service's type library. Must call [OH_AbilityRuntime_TypeDescriptor_Release](capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_release) to release the handle when no longer needed. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_QueryMainServiceInterfaceMemIDsOfNames(OH_AbilityRuntime_ModObjDispatcherHandle pModObjDispatcher, const char** rgszNames, uint32_t cNames, uint32_t* pMemID)](#oh_abilityruntime_modobjdispatcher_querymainserviceinterfacememidsofnames) | Query member IDs of method names in the main service interface.<br> The returned member IDs can be used as the memID parameter in [OH_AbilityRuntime_ModObjDispatcher_CallMethod](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_callmethod). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_CallMethod(OH_AbilityRuntime_ModObjDispatcherHandle pModObjDispatcher, uint32_t memID, OH_AbilityRuntime_ModObjDispatcher_InputParams* pInputParams, OH_AbilityRuntime_ModObjDispatcher_Variant* pResult, int32_t* pMethodErrCode)

// ========== TypeDescriptor Interfaces ==========](#oh_abilityruntime_modobjdispatcher_callmethod) | Call a method. |
| [void OH_AbilityRuntime_TypeDescriptor_Release(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle *pTypeDescriptor)](#oh_abilityruntime_typedescriptor_release) | Release TypeDescriptor instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetVersion(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, char* pbstrVersion, uint32_t cMaxVersion)](#oh_abilityruntime_typedescriptor_getversion) | Get version of the type library. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetInterfaceCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t* pcInterfaces)](#oh_abilityruntime_typedescriptor_getinterfacecount) | Get total number of interfaces. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetInterfaceName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t index, char* pbstrName, uint32_t cMaxName)](#oh_abilityruntime_typedescriptor_getinterfacename) | Get interface name by index. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetInterfaceIsCallback(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrName, bool* pIsCallback)](#oh_abilityruntime_typedescriptor_getinterfaceiscallback) | Check if interface is a callback type. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMainServiceInterfaceName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, char* pbstrName, uint32_t cMaxName)](#oh_abilityruntime_typedescriptor_getmainserviceinterfacename) | Get main service interface name. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, uint32_t* pcMethods)](#oh_abilityruntime_typedescriptor_getmethodcount) | Get method count from interface. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, uint32_t index, char* pbstrName, uint32_t cMaxName)](#oh_abilityruntime_typedescriptor_getmethodname) | Get method name by index from interface. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodMemberId(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, uint32_t* pMemID)](#oh_abilityruntime_typedescriptor_getmethodmemberid) | Get method MemberID by name from interface. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodReturnType(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pReturnType)](#oh_abilityruntime_typedescriptor_getmethodreturntype) | Get method return type by name from interface. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodParamCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, uint32_t* pcParams)](#oh_abilityruntime_typedescriptor_getmethodparamcount) | Get method parameter count by name from interface. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodParamType(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, uint32_t iParamIndex, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pParamType)](#oh_abilityruntime_typedescriptor_getmethodparamtype) | Get method parameter type by name and index from interface. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodParamName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, uint32_t iParamIndex, char* pbstrName, uint32_t cMaxName)

// ========== Enum Queries ==========](#oh_abilityruntime_typedescriptor_getmethodparamname) | Get method parameter name by name and index from interface. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t* pcEnums)](#oh_abilityruntime_typedescriptor_getenumcount) | Get enum count. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t index, char* pbstrName, uint32_t cMaxName)](#oh_abilityruntime_typedescriptor_getenumname) | Get enum name by index. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumValueCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrEnumName, uint32_t* pcValues)](#oh_abilityruntime_typedescriptor_getenumvaluecount) | Get enum value count by enum name. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumValueName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrEnumName, uint32_t iValueIndex, char* pbstrValueName, uint32_t cMaxName)](#oh_abilityruntime_typedescriptor_getenumvaluename) | Get enum value name by enum name and value index. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumValue(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrEnumName, const char* pbstrValueName, int32_t* pValue)](#oh_abilityruntime_typedescriptor_getenumvalue) | Get enum value by enum name and value name. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t* pcStructs)](#oh_abilityruntime_typedescriptor_getstructcount) | Get struct count. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t index, char* pbstrName, uint32_t cMaxName)](#oh_abilityruntime_typedescriptor_getstructname) | Get struct name by index. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructFieldCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrStructName, uint32_t* pcFields)](#oh_abilityruntime_typedescriptor_getstructfieldcount) | Get struct field count by struct name. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructFieldName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrStructName, uint32_t iFieldIndex, char* pbstrFieldName, uint32_t cMaxName)](#oh_abilityruntime_typedescriptor_getstructfieldname) | Get struct field name by struct name and field index. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructFieldType(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrStructName, const char* pbstrFieldName, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pFieldType)](#oh_abilityruntime_typedescriptor_getstructfieldtype) | Get struct field type by struct name and field name. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArrayCreate(OH_AbilityRuntime_ModObjDispatcher_TypeInfo *elementType, uint32_t size, OH_AbilityRuntime_ModObjDispatcher_ArrayHandle* ppArray)](#oh_abilityruntime_modobjdispatcher_arraycreate) | Create an array instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArrayGetElementType(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle pArray, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pElementType)](#oh_abilityruntime_modobjdispatcher_arraygetelementtype) | Get array element type. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArraySet(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle pArray, uint32_t index, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_arrayset) | Set an array element value. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArrayGet(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle pArray, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_arrayget) | Get an array element value. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArrayGetSize(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle pArray, uint32_t* pSize)](#oh_abilityruntime_modobjdispatcher_arraygetsize) | Get array size. |
| [void OH_AbilityRuntime_ModObjDispatcher_ArrayRelease(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle* ppArray)](#oh_abilityruntime_modobjdispatcher_arrayrelease) | Release array instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorCreate(OH_AbilityRuntime_ModObjDispatcher_TypeInfo *elementType, OH_AbilityRuntime_ModObjDispatcher_VectorHandle* ppVector)](#oh_abilityruntime_modobjdispatcher_vectorcreate) | Create a vector instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorGetElementType(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pElementType)](#oh_abilityruntime_modobjdispatcher_vectorgetelementtype) | Get vector element type. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorAdd(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_vectoradd) | Add an element to vector. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorGet(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_vectorget) | Get a vector element value. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorGetSize(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector, uint32_t* pSize)](#oh_abilityruntime_modobjdispatcher_vectorgetsize) | Get vector size. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorClear(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector)](#oh_abilityruntime_modobjdispatcher_vectorclear) | Clear vector. |
| [void OH_AbilityRuntime_ModObjDispatcher_VectorRelease(OH_AbilityRuntime_ModObjDispatcher_VectorHandle* ppVector)](#oh_abilityruntime_modobjdispatcher_vectorrelease) | Release vector instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetCreate(OH_AbilityRuntime_ModObjDispatcher_TypeInfo *elementType, OH_AbilityRuntime_ModObjDispatcher_SetHandle* ppSet)](#oh_abilityruntime_modobjdispatcher_setcreate) | Create a set instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetGetElementType(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pElementType)](#oh_abilityruntime_modobjdispatcher_setgetelementtype) | Get set element type. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetAdd(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_setadd) | Add an element to set. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetRemove(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_setremove) | Remove an element from set. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetContains(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue, bool* pExists)](#oh_abilityruntime_modobjdispatcher_setcontains) | Check if an element exists in set. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetGetSize(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, uint32_t* pSize)](#oh_abilityruntime_modobjdispatcher_setgetsize) | Get set size. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetGetAt(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_setgetat) | Get a set element value by index.<br> The returned variant is a deep copy owned by the caller. Caller must call [OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear) to release it. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetClear(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet)](#oh_abilityruntime_modobjdispatcher_setclear) | Clear set. |
| [void OH_AbilityRuntime_ModObjDispatcher_SetRelease(OH_AbilityRuntime_ModObjDispatcher_SetHandle* ppSet)](#oh_abilityruntime_modobjdispatcher_setrelease) | Release set instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapCreate(OH_AbilityRuntime_ModObjDispatcher_ValueType keyType, OH_AbilityRuntime_ModObjDispatcher_TypeInfo *valueType, OH_AbilityRuntime_ModObjDispatcher_MapHandle* ppMap)](#oh_abilityruntime_modobjdispatcher_mapcreate) | Create a map instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetKeyType(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, OH_AbilityRuntime_ModObjDispatcher_ValueType* pKeyType)](#oh_abilityruntime_modobjdispatcher_mapgetkeytype) | Get map key type. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetValueType(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pValueType)](#oh_abilityruntime_modobjdispatcher_mapgetvaluetype) | Get map value type. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapPut(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, const OH_AbilityRuntime_ModObjDispatcher_Variant* pKey, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_mapput) | Put a key-value pair into map. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGet(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, const OH_AbilityRuntime_ModObjDispatcher_Variant* pKey, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_mapget) | Get a value from map by key. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapRemove(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, const OH_AbilityRuntime_ModObjDispatcher_Variant* pKey)](#oh_abilityruntime_modobjdispatcher_mapremove) | Remove a key-value pair from map. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapContainsKey(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, const OH_AbilityRuntime_ModObjDispatcher_Variant* pKey, bool* pExists)](#oh_abilityruntime_modobjdispatcher_mapcontainskey) | Check if a key exists in map. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetSize(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, uint32_t* pSize)](#oh_abilityruntime_modobjdispatcher_mapgetsize) | Get map size. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetKeyAt(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pKey)](#oh_abilityruntime_modobjdispatcher_mapgetkeyat) | Get a map key by index.<br> The returned variant is a deep copy owned by the caller. Caller must call [OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear) to release it. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetValueAt(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_mapgetvalueat) | Get a map value by index.<br> The returned variant is a deep copy owned by the caller. Caller must call [OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear) to release it. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapClear(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap)](#oh_abilityruntime_modobjdispatcher_mapclear) | Clear map. |
| [void OH_AbilityRuntime_ModObjDispatcher_MapRelease(OH_AbilityRuntime_ModObjDispatcher_MapHandle* ppMap)](#oh_abilityruntime_modobjdispatcher_maprelease) | Release map instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_StructCreate(const char* structName, OH_AbilityRuntime_ModObjDispatcher_StructHandle* ppStruct)](#oh_abilityruntime_modobjdispatcher_structcreate) | Create a struct instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_StructGetName(OH_AbilityRuntime_ModObjDispatcher_StructHandle pStruct, char* pbstrName, uint32_t cMaxName)](#oh_abilityruntime_modobjdispatcher_structgetname) | Get struct name. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_StructSetField(OH_AbilityRuntime_ModObjDispatcher_StructHandle pStruct, const char* szName, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_structsetfield) | Set a struct field value. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_StructGetField(OH_AbilityRuntime_ModObjDispatcher_StructHandle pStruct, const char* szName, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)](#oh_abilityruntime_modobjdispatcher_structgetfield) | Get a struct field value. |
| [void OH_AbilityRuntime_ModObjDispatcher_StructRelease(OH_AbilityRuntime_ModObjDispatcher_StructHandle* ppStruct)](#oh_abilityruntime_modobjdispatcher_structrelease) | Release struct instance. |

## Function description

### OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear()

```c
void OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear(OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pTypeInfo)
```

**Description**

Clear TypeInfo resources.<br> Recursively release any heap resources held by a TypeInfo struct (idlType strings, child TypeInfo nodes for map/array/vector/set types). After clearing, all pointers are set to NULL but the TypeInfo struct itself is not freed (it is typically stack-allocated by the caller).<br> TypeInfoClear must NOT be called on a shallow copy of another TypeInfo. If TypeInfo t2 = t1 is performed, only clear one of them.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md)* pTypeInfo | Indicates a pointer to TypeInfo to clear. |

### OH_AbilityRuntime_ModObjDispatcher_VariantClear()

```c
void OH_AbilityRuntime_ModObjDispatcher_VariantClear(OH_AbilityRuntime_ModObjDispatcher_Variant* pVariant)
```

**Description**

Clear variant resources.<br> Release any resources held by the variant (strings, container handles, etc.). After clearing, the variant is reset to VT_EMPTY with all fields zeroed.<br> Ownership rules: - When a Variant is passed to a function (e.g. Array_Set, Map_Put), the function performs a deep copy. The caller retains ownership of the original Variant and is responsible for freeing its own resources (e.g. free(bstrVal) for strings, Release for container handles). - When a Variant is returned from a function (e.g. Array_Get, Map_Get, CallMethod), the function performs a deep copy and the caller owns the returned Variant. The caller must call VariantClear exactly once to release the resources. - Simple types (bool, i32, f64, etc.) do not hold heap resources and do not require VariantClear, though calling it is harmless. - VariantClear must NOT be called on a shallow copy of another Variant. If Variant v2 = v1 is performed, only clear one of them.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pVariant | Indicates a pointer to variant to clear. |

### OH_AbilityRuntime_ModObjDispatcher_CreateMainServiceInstance()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_CreateMainServiceInstance(OHIPCRemoteProxy* remoteProxy, OH_AbilityRuntime_ModObjDispatcherHandle* ppModObjDispatcher)
```

**Description**

Create a modular object dispatcher instance from an IPC remote proxy for the main service interface.<br> The type library metadata will be lazily loaded from the remote service on the first call that requires it, such as HasTypeDescriptor, QueryMainServiceInterfaceMemIDsOfNames, or CallMethod.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OHIPCRemoteProxy* remoteProxy | Indicates IPC remote proxy handle obtained from connectExtension. |
| [OH_AbilityRuntime_ModObjDispatcherHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md)* ppModObjDispatcher | Indicates a pointer to receive modular object dispatcher handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if remoteProxy or ppModObjDispatcher is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_CreateSubInstance()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_CreateSubInstance(OH_AbilityRuntime_ModObjDispatcherHandle mainServiceDispatcher, OHIPCRemoteProxy* subProxy, OH_AbilityRuntime_ModObjDispatcherHandle* ppModObjDispatcher)
```

**Description**

Create a sub-instance dispatcher bound to a mainService dispatcher.<br> The sub-instance shares the mainService dispatcher's metadata but uses its own IPC proxy. When CallMethod is invoked on the sub-instance, method metadata is resolved from the mainService dispatcher and the call is sent through subProxy.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcherHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md) mainServiceDispatcher | Indicates mainService dispatcher handle. |
| OHIPCRemoteProxy* subProxy | Indicates IPC remote proxy for the non-mainService interface. |
| [OH_AbilityRuntime_ModObjDispatcherHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md)* ppModObjDispatcher | Indicates a pointer to receive the created sub-instance dispatcher handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if mainServiceDispatcher or subProxy       or ppModObjDispatcher is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_Release()

```c
void OH_AbilityRuntime_ModObjDispatcher_Release(OH_AbilityRuntime_ModObjDispatcherHandle* ppModObjDispatcher)
```

**Description**

Release modular object dispatcher instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcherHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md)* ppModObjDispatcher | Indicates a pointer to modular object dispatcher handle to release. After release, handle will be set to NULL. |

### OH_AbilityRuntime_ModObjDispatcher_HasTypeDescriptor()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_HasTypeDescriptor(OH_AbilityRuntime_ModObjDispatcherHandle pModObjDispatcher, uint32_t* pctinfo)
```

**Description**

Check if the type library metadata is available from the remote service.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcherHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md) pModObjDispatcher | Indicates modular object dispatcher handle. |
| uint32_t* pctinfo | Indicates a pointer to receive support status (1 if supported, 0 if not supported). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pModObjDispatcher or pctinfo is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_SEND_REQUEST_FAILED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if send request failed.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_METADATA_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if type library metadata is invalid.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded from the remote service.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_GetTypeDescriptor(OH_AbilityRuntime_ModObjDispatcherHandle pModObjDispatcher, OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle* ppTypeDescriptor)
```

**Description**

Get type descriptor for querying interface metadata information.<br> The type descriptor provides access to type library metadata including interfaces, methods, enums, and structs defined in the remote service's type library. Must call [OH_AbilityRuntime_TypeDescriptor_Release](capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_release) to release the handle when no longer needed.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcherHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md) pModObjDispatcher | Indicates modular object dispatcher handle. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md)* ppTypeDescriptor | Indicates a pointer to receive type descriptor handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pModObjDispatcher or ppTypeDescriptor is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_SEND_REQUEST_FAILED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if send request failed.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_METADATA_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if type library metadata is invalid.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_QueryMainServiceInterfaceMemIDsOfNames()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_QueryMainServiceInterfaceMemIDsOfNames(OH_AbilityRuntime_ModObjDispatcherHandle pModObjDispatcher, const char** rgszNames, uint32_t cNames, uint32_t* pMemID)
```

**Description**

Query member IDs of method names in the main service interface.<br> The returned member IDs can be used as the memID parameter in [OH_AbilityRuntime_ModObjDispatcher_CallMethod](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_callmethod).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcherHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md) pModObjDispatcher | Indicates modular object dispatcher handle. |
| const char** rgszNames | Indicates array of method names. |
| uint32_t cNames | Indicates number of names. |
| uint32_t* pMemID | Indicates pointer to receive member IDs (MemberIDs). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pModObjDispatcher or rgszNames or pMemID is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_SEND_REQUEST_FAILED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if send request failed.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_METADATA_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if type library metadata is invalid.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if name not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded from the remote service.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_CallMethod()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_CallMethod(OH_AbilityRuntime_ModObjDispatcherHandle pModObjDispatcher, uint32_t memID, OH_AbilityRuntime_ModObjDispatcher_InputParams* pInputParams, OH_AbilityRuntime_ModObjDispatcher_Variant* pResult, int32_t* pMethodErrCode)

// ========== TypeDescriptor Interfaces ==========
```

**Description**

Call a method.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcherHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher8h.md) pModObjDispatcher | Indicates modular object dispatcher handle. |
| uint32_t memID | Indicates method member ID (MemberID). |
| [OH_AbilityRuntime_ModObjDispatcher_InputParams](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-inputparams.md)* pInputParams | Indicates parameter structure containing arguments. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pResult | Indicates pointer to receive result variant. |
| pMethodErrCode | Indicates a pointer to receive the error code returned by the remote method. 0 if the method executed successfully, non-zero if the method returned an error. This is independent of the framework-level return value. This parameter can be NULL if the caller does not need the method-level error code. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if IPC call is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pModObjDispatcher or pInputParams or       pResult is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if method not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if parameter type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_SEND_REQUEST_FAILED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if send request failed.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_METADATA_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if type library metadata is invalid.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed       when copying parameter or result.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_Release()

```c
void OH_AbilityRuntime_TypeDescriptor_Release(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle *pTypeDescriptor)
```

**Description**

Release TypeDescriptor instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) *pTypeDescriptor | Indicates TypeDescriptor handle to release. |

### OH_AbilityRuntime_TypeDescriptor_GetVersion()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetVersion(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, char* pbstrVersion, uint32_t cMaxVersion)
```

**Description**

Get version of the type library.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| char* pbstrVersion | Indicates a buffer to receive version string. |
| uint32_t cMaxVersion | Indicates size of buffer in bytes, including the null terminator. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or       pbstrVersion is null, or cMaxVersion is 0.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetInterfaceCount()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetInterfaceCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t* pcInterfaces)
```

**Description**

Get total number of interfaces.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| uint32_t* pcInterfaces | Indicates a pointer to receive interface count. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pcInterfaces is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetInterfaceName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetInterfaceName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t index, char* pbstrName, uint32_t cMaxName)
```

**Description**

Get interface name by index.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| uint32_t index | Indicates interface index, ranging from 0 to (interface count - 1) obtained from [OH_AbilityRuntime_TypeDescriptor_GetInterfaceCount](capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getinterfacecount). |
| char* pbstrName | Indicates a buffer to receive interface name. |
| uint32_t cMaxName | Indicates size of buffer in bytes, including the null terminator. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrName is null,       or cMaxName is 0, or index is out of range.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetInterfaceIsCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetInterfaceIsCallback(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrName, bool* pIsCallback)
```

**Description**

Check if interface is a callback type.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrName | Indicates interface name. |
| bool* pIsCallback | Indicates a pointer to receive callback flag (true if callback, false otherwise). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrName or       pIsCallback is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if interface not found.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetMainServiceInterfaceName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMainServiceInterfaceName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, char* pbstrName, uint32_t cMaxName)
```

**Description**

Get main service interface name.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| char* pbstrName | Indicates a buffer to receive main service interface name. |
| uint32_t cMaxName | Indicates size of buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrName is null,       or cMaxName is 0.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetMethodCount()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, uint32_t* pcMethods)
```

**Description**

Get method count from interface.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrInterfaceName | Indicates interface name. |
| uint32_t* pcMethods | Indicates a pointer to receive method count. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or       pbstrInterfaceName or pcMethods is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if interface not found.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetMethodName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, uint32_t index, char* pbstrName, uint32_t cMaxName)
```

**Description**

Get method name by index from interface.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrInterfaceName | Indicates interface name. |
| uint32_t index | Indicates method index, ranging from 0 to (method count - 1) obtained from [OH_AbilityRuntime_TypeDescriptor_GetMethodCount](capi-modular-object-dispatcher-h.md#oh_abilityruntime_typedescriptor_getmethodcount). |
| char* pbstrName | Indicates a buffer to receive method name. |
| uint32_t cMaxName | Indicates size of buffer in bytes, including the null terminator. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrInterfaceName or       pbstrName is null, or cMaxName is 0, or index is out of range.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if interface not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetMethodMemberId()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodMemberId(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, uint32_t* pMemID)
```

**Description**

Get method MemberID by name from interface.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrInterfaceName | Indicates interface name. |
| const char* pbstrMethodName | Indicates method name. |
| uint32_t* pMemID | Indicates a pointer to receive method MemberID. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrInterfaceName or       pbstrMethodName or pMemID is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if interface or method not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetMethodReturnType()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodReturnType(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pReturnType)
```

**Description**

Get method return type by name from interface.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrInterfaceName | Indicates interface name. |
| const char* pbstrMethodName | Indicates method name. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md)* pReturnType | Indicates a pointer to receive return type. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrInterfaceName or       pbstrMethodName or pReturnType is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if interface or method not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetMethodParamCount()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodParamCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, uint32_t* pcParams)
```

**Description**

Get method parameter count by name from interface.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrInterfaceName | Indicates interface name. |
| const char* pbstrMethodName | Indicates method name. |
| uint32_t* pcParams | Indicates a pointer to receive parameter count. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrInterfaceName or       pbstrMethodName or pcParams is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if interface or method not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetMethodParamType()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodParamType(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, uint32_t iParamIndex, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pParamType)
```

**Description**

Get method parameter type by name and index from interface.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrInterfaceName | Indicates interface name. |
| const char* pbstrMethodName | Indicates method name. |
| uint32_t iParamIndex | Indicates parameter index. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md)* pParamType | Indicates a pointer to receive parameter type. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrInterfaceName or       pbstrMethodName or pParamType is null, or iParamIndex is out of range.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if interface or method not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetMethodParamName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetMethodParamName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrInterfaceName, const char* pbstrMethodName, uint32_t iParamIndex, char* pbstrName, uint32_t cMaxName)

// ========== Enum Queries ==========
```

**Description**

Get method parameter name by name and index from interface.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrInterfaceName | Indicates interface name. |
| const char* pbstrMethodName | Indicates method name. |
| uint32_t iParamIndex | Indicates parameter index. |
| char* pbstrName | Indicates a buffer to receive parameter name. |
| cMaxName | Indicates size of buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrInterfaceName or       pbstrMethodName or pbstrName is null, or iParamIndex is out of range.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if interface or method not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetEnumCount()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t* pcEnums)
```

**Description**

Get enum count.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| uint32_t* pcEnums | Indicates a pointer to receive enum count. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pcEnums is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetEnumName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t index, char* pbstrName, uint32_t cMaxName)
```

**Description**

Get enum name by index.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| uint32_t index | Indicates enum index. |
| char* pbstrName | Indicates a buffer to receive enum name. |
| uint32_t cMaxName | Indicates size of buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrName is null,       or cMaxName is 0, or index is out of range.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetEnumValueCount()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumValueCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrEnumName, uint32_t* pcValues)
```

**Description**

Get enum value count by enum name.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrEnumName | Indicates enum name. |
| uint32_t* pcValues | Indicates a pointer to receive enum value count. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrEnumName or       pcValues is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if enum not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetEnumValueName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumValueName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrEnumName, uint32_t iValueIndex, char* pbstrValueName, uint32_t cMaxName)
```

**Description**

Get enum value name by enum name and value index.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrEnumName | Indicates enum name. |
| uint32_t iValueIndex | Indicates enum value index. |
| char* pbstrValueName | Indicates a buffer to receive enum value name. |
| uint32_t cMaxName | Indicates size of buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrEnumName or pbstrValueName       is null, or iValueIndex is out of range.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if enum not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetEnumValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetEnumValue(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrEnumName, const char* pbstrValueName, int32_t* pValue)
```

**Description**

Get enum value by enum name and value name.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrEnumName | Indicates enum name. |
| const char* pbstrValueName | Indicates enum value name. |
| int32_t* pValue | Indicates a pointer to receive enum value. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrEnumName or       pbstrValueName or pValue is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if enum value not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetStructCount()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t* pcStructs)
```

**Description**

Get struct count.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| uint32_t* pcStructs | Indicates a pointer to receive struct count. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pcStructs is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetStructName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, uint32_t index, char* pbstrName, uint32_t cMaxName)
```

**Description**

Get struct name by index.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| uint32_t index | Indicates struct index. |
| char* pbstrName | Indicates a buffer to receive struct name. |
| uint32_t cMaxName | Indicates size of buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrName is null, or cMaxName is 0,       or index is out of range.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetStructFieldCount()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructFieldCount(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrStructName, uint32_t* pcFields)
```

**Description**

Get struct field count by struct name.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrStructName | Indicates struct name. |
| uint32_t* pcFields | Indicates a pointer to receive field count. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrStructName or       pcFields is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if struct not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetStructFieldName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructFieldName(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrStructName, uint32_t iFieldIndex, char* pbstrFieldName, uint32_t cMaxName)
```

**Description**

Get struct field name by struct name and field index.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrStructName | Indicates struct name. |
| uint32_t iFieldIndex | Indicates field index. |
| char* pbstrFieldName | Indicates a buffer to receive field name. |
| uint32_t cMaxName | Indicates size of buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrStructName or       pbstrFieldName is null, or iFieldIndex is out of range.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if struct not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded, or memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_TypeDescriptor_GetStructFieldType()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_TypeDescriptor_GetStructFieldType(OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle pTypeDescriptor, const char* pbstrStructName, const char* pbstrFieldName, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pFieldType)
```

**Description**

Get struct field type by struct name and field name.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeDescriptorHandle](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typedescriptorhandle.md) pTypeDescriptor | Indicates TypeDescriptor handle. |
| const char* pbstrStructName | Indicates struct name. |
| const char* pbstrFieldName | Indicates field name. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md)* pFieldType | Indicates a pointer to receive field type. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pTypeDescriptor or pbstrStructName or       pbstrFieldName or pFieldType is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if field not found.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if metadata is not loaded.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_ArrayCreate()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArrayCreate(OH_AbilityRuntime_ModObjDispatcher_TypeInfo *elementType, uint32_t size, OH_AbilityRuntime_ModObjDispatcher_ArrayHandle* ppArray)
```

**Description**

Create an array instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md) *elementType | Indicates element type. |
| uint32_t size | Indicates initial array size. |
| [OH_AbilityRuntime_ModObjDispatcher_ArrayHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-array8h.md)* ppArray | Indicates a pointer to receive array handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if elementType or ppArray is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_ArrayGetElementType()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArrayGetElementType(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle pArray, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pElementType)
```

**Description**

Get array element type.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_ArrayHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-array8h.md) pArray | Indicates array handle. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md)* pElementType | Indicates a pointer to receive element type. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pArray or pElementType is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if internal element type info is not available.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_ArraySet()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArraySet(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle pArray, uint32_t index, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Set an array element value.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_ArrayHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-array8h.md) pArray | Indicates array handle. |
| uint32_t index | Indicates element index. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to element value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pArray or pValue is null,       or index is out of bounds.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if element type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_ArrayGet()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArrayGet(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle pArray, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Get an array element value.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_ArrayHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-array8h.md) pArray | Indicates array handle. |
| uint32_t index | Indicates element index. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to receive element value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pArray or pValue is null,       or index is out of bounds.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_ArrayGetSize()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_ArrayGetSize(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle pArray, uint32_t* pSize)
```

**Description**

Get array size.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_ArrayHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-array8h.md) pArray | Indicates array handle. |
| uint32_t* pSize | Indicates a pointer to receive array size. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pArray or pSize is null.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_ArrayRelease()

```c
void OH_AbilityRuntime_ModObjDispatcher_ArrayRelease(OH_AbilityRuntime_ModObjDispatcher_ArrayHandle* ppArray)
```

**Description**

Release array instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_ArrayHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-array8h.md)* ppArray | Indicates array handle to release. |

### OH_AbilityRuntime_ModObjDispatcher_VectorCreate()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorCreate(OH_AbilityRuntime_ModObjDispatcher_TypeInfo *elementType, OH_AbilityRuntime_ModObjDispatcher_VectorHandle* ppVector)
```

**Description**

Create a vector instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md) *elementType | Indicates element type. |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md)* ppVector | Indicates a pointer to receive vector handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if elementType or ppVector is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_VectorGetElementType()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorGetElementType(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pElementType)
```

**Description**

Get vector element type.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md) pVector | Indicates vector handle. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md)* pElementType | Indicates a pointer to receive element type. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pVector or pElementType is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if internal element type info is not available.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_VectorAdd()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorAdd(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Add an element to vector.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md) pVector | Indicates vector handle. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to element value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pVector or pValue is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if element type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_VectorGet()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorGet(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Get a vector element value.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md) pVector | Indicates vector handle. |
| uint32_t index | Indicates element index. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to receive element value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pVector or pValue is null,       or index is out of bounds.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_VectorGetSize()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorGetSize(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector, uint32_t* pSize)
```

**Description**

Get vector size.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md) pVector | Indicates vector handle. |
| uint32_t* pSize | Indicates a pointer to receive vector size. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pVector or pSize is null.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_VectorClear()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_VectorClear(OH_AbilityRuntime_ModObjDispatcher_VectorHandle pVector)
```

**Description**

Clear vector.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md) pVector | Indicates vector handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pVector is null.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_VectorRelease()

```c
void OH_AbilityRuntime_ModObjDispatcher_VectorRelease(OH_AbilityRuntime_ModObjDispatcher_VectorHandle* ppVector)
```

**Description**

Release vector instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md)* ppVector | Indicates vector handle to release. |

### OH_AbilityRuntime_ModObjDispatcher_SetCreate()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetCreate(OH_AbilityRuntime_ModObjDispatcher_TypeInfo *elementType, OH_AbilityRuntime_ModObjDispatcher_SetHandle* ppSet)
```

**Description**

Create a set instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md) *elementType | Indicates element type. |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md)* ppSet | Indicates a pointer to receive set handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if elementType or ppSet is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_SetGetElementType()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetGetElementType(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pElementType)
```

**Description**

Get set element type.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) pSet | Indicates set handle. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md)* pElementType | Indicates a pointer to receive element type. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pSet or pElementType is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if internal element type info is not available.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_SetAdd()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetAdd(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Add an element to set.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) pSet | Indicates set handle. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to element value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pSet or pValue is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if element type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_SetRemove()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetRemove(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Remove an element from set.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) pSet | Indicates set handle. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to element value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pSet or pValue is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if element type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if element is not found in set.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_SetContains()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetContains(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue, bool* pExists)
```

**Description**

Check if an element exists in set.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) pSet | Indicates set handle. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to element value variant. |
| bool* pExists | Indicates a pointer to receive existence flag. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pSet or pValue or pExists is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if element type mismatches.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_SetGetSize()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetGetSize(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, uint32_t* pSize)
```

**Description**

Get set size.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) pSet | Indicates set handle. |
| uint32_t* pSize | Indicates a pointer to receive set size. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pSet or pSize is null.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_SetGetAt()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetGetAt(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Get a set element value by index.<br> The returned variant is a deep copy owned by the caller. Caller must call [OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear) to release it.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) pSet | Indicates set handle. |
| uint32_t index | Indicates element index. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to receive element value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pSet or pValue is null, or index is out of bounds.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_SetClear()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_SetClear(OH_AbilityRuntime_ModObjDispatcher_SetHandle pSet)
```

**Description**

Clear set.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) pSet | Indicates set handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pSet is null.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_SetRelease()

```c
void OH_AbilityRuntime_ModObjDispatcher_SetRelease(OH_AbilityRuntime_ModObjDispatcher_SetHandle* ppSet)
```

**Description**

Release set instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md)* ppSet | Indicates set handle to release. |

### OH_AbilityRuntime_ModObjDispatcher_MapCreate()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapCreate(OH_AbilityRuntime_ModObjDispatcher_ValueType keyType, OH_AbilityRuntime_ModObjDispatcher_TypeInfo *valueType, OH_AbilityRuntime_ModObjDispatcher_MapHandle* ppMap)
```

**Description**

Create a map instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType keyType | Indicates key type. Only basic types are supported, such as {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_BOOL},<br>              {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_I32},<br>              {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_STRING},<br>              and {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ENUM}. Container types (ARRAY, VECTOR, SET, MAP) and complex types (STRUCT, IPC_REMOTE_PROXY, IPC_REMOTE_STUB) are not supported. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md) *valueType | Indicates value type. |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md)* ppMap | Indicates a pointer to receive map handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if valueType or ppMap is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapGetKeyType()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetKeyType(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, OH_AbilityRuntime_ModObjDispatcher_ValueType* pKeyType)
```

**Description**

Get map key type.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| OH_AbilityRuntime_ModObjDispatcher_ValueType* pKeyType | Indicates a pointer to receive key type. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pKeyType is null.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapGetValueType()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetValueType(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, OH_AbilityRuntime_ModObjDispatcher_TypeInfo* pValueType)
```

**Description**

Get map value type.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md)* pValueType | Indicates a pointer to receive value type. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pValueType is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if internal value type info is not available.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapPut()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapPut(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, const OH_AbilityRuntime_ModObjDispatcher_Variant* pKey, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Put a key-value pair into map.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pKey | Indicates a pointer to key variant. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pKey or pValue is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if key or value type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapGet()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGet(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, const OH_AbilityRuntime_ModObjDispatcher_Variant* pKey, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Get a value from map by key.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pKey | Indicates a pointer to key variant. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to receive value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pKey or pValue is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if key type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if key is not found in map.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapRemove()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapRemove(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, const OH_AbilityRuntime_ModObjDispatcher_Variant* pKey)
```

**Description**

Remove a key-value pair from map.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pKey | Indicates a pointer to key variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pKey is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if key type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if key is not found in map.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapContainsKey()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapContainsKey(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, const OH_AbilityRuntime_ModObjDispatcher_Variant* pKey, bool* pExists)
```

**Description**

Check if a key exists in map.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pKey | Indicates a pointer to key variant. |
| bool* pExists | Indicates a pointer to receive existence flag. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pKey or pExists is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if key type mismatches.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapGetSize()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetSize(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, uint32_t* pSize)
```

**Description**

Get map size.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| uint32_t* pSize | Indicates a pointer to receive map size. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pSize is null.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapGetKeyAt()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetKeyAt(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pKey)
```

**Description**

Get a map key by index.<br> The returned variant is a deep copy owned by the caller. Caller must call [OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear) to release it.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| uint32_t index | Indicates entry index. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pKey | Indicates a pointer to receive key variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pKey is null, or index is out of bounds.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapGetValueAt()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapGetValueAt(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap, uint32_t index, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Get a map value by index.<br> The returned variant is a deep copy owned by the caller. Caller must call [OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear) to release it.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |
| uint32_t index | Indicates entry index. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to receive value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap or pValue is null, or index is out of bounds.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapClear()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_MapClear(OH_AbilityRuntime_ModObjDispatcher_MapHandle pMap)
```

**Description**

Clear map.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pMap | Indicates map handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pMap is null.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_MapRelease()

```c
void OH_AbilityRuntime_ModObjDispatcher_MapRelease(OH_AbilityRuntime_ModObjDispatcher_MapHandle* ppMap)
```

**Description**

Release map instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md)* ppMap | Indicates map handle to release. |

### OH_AbilityRuntime_ModObjDispatcher_StructCreate()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_StructCreate(const char* structName, OH_AbilityRuntime_ModObjDispatcher_StructHandle* ppStruct)
```

**Description**

Create a struct instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* structName | Indicates struct name from type metadata. |
| [OH_AbilityRuntime_ModObjDispatcher_StructHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-struct8h.md)* ppStruct | Indicates a pointer to receive struct handle. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if structName or ppStruct is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if struct name is not found       in type metadata.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_StructGetName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_StructGetName(OH_AbilityRuntime_ModObjDispatcher_StructHandle pStruct, char* pbstrName, uint32_t cMaxName)
```

**Description**

Get struct name.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_StructHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-struct8h.md) pStruct | Indicates struct handle. |
| char* pbstrName | Indicates a buffer to receive struct name. |
| uint32_t cMaxName | Indicates size of buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pStruct or pbstrName is null,       or cMaxName is 0 or too small for struct name.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed or string copy failed.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_StructSetField()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_StructSetField(OH_AbilityRuntime_ModObjDispatcher_StructHandle pStruct, const char* szName, const OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Set a struct field value.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_StructHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-struct8h.md) pStruct | Indicates struct handle. |
| const char* szName | Indicates field name. |
| [const OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to field value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pStruct or szName or pValue is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if field is not found in struct.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_TYPE_MISMATCH](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if field type mismatches.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_StructGetField()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjDispatcher_StructGetField(OH_AbilityRuntime_ModObjDispatcher_StructHandle pStruct, const char* szName, OH_AbilityRuntime_ModObjDispatcher_Variant* pValue)
```

**Description**

Get a struct field value.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_StructHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-struct8h.md) pStruct | Indicates struct handle. |
| const char* szName | Indicates field name. |
| [OH_AbilityRuntime_ModObjDispatcher_Variant](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-variant.md)* pValue | Indicates a pointer to receive field value variant. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if operation is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if pStruct or szName or pValue is null.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PROPERTY_NOT_FOUND](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if field is not found in struct.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if memory allocation failed when copying variant value.</li>       </ul> |

### OH_AbilityRuntime_ModObjDispatcher_StructRelease()

```c
void OH_AbilityRuntime_ModObjDispatcher_StructRelease(OH_AbilityRuntime_ModObjDispatcher_StructHandle* ppStruct)
```

**Description**

Release struct instance.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_StructHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-struct8h.md)* ppStruct | Indicates struct handle to release. |


