# __ani_env

## Overview

**System capability**: SystemCapability.ArkCompiler.ANI

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const struct \_\_ani_interaction_api *c_api |  |
| ani_status GetVersion(uint32_t *result)
    {
        return c_api->GetVersion(this, result);
    }
    ani_status GetVM(ani_vm **result)
    {
        return c_api->GetVM(this, result);
    }
    ani_status Object_New(ani_class cls, ani_method ctor, ani_object *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_New_V(this, cls, ctor, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_New_A(ani_class cls, ani_method ctor, ani_object *result, const ani_value *args)
    {
        return c_api->Object_New_A(this, cls, ctor, result, args);
    }
    ani_status Object_New_V(ani_class cls, ani_method ctor, ani_object *result, va_list args)
    {
        return c_api->Object_New_V(this, cls, ctor, result, args);
    }
    ani_status Object_GetType(ani_object object, ani_type *result)
    {
        return c_api->Object_GetType(this, object, result);
    }
    ani_status Object_InstanceOf(ani_object object, ani_type type, ani_boolean *result)
    {
        return c_api->Object_InstanceOf(this, object, type, result);
    }
    ani_status Type_GetSuperClass(ani_type type, ani_class *result)
    {
        return c_api->Type_GetSuperClass(this, type, result);
    }
    ani_status Type_IsAssignableFrom(ani_type from_type, ani_type to_type, ani_boolean *result)
    {
        return c_api->Type_IsAssignableFrom(this, from_type, to_type, result);
    }
    ani_status FindModule(const char *module_descriptor, ani_module *result)
    {
        return c_api->FindModule(this, module_descriptor, result);
    }
    ani_status FindNamespace(const char *namespace_descriptor, ani_namespace *result)
    {
        return c_api->FindNamespace(this, namespace_descriptor, result);
    }
    ani_status FindClass(const char *class_descriptor, ani_class *result)
    {
        return c_api->FindClass(this, class_descriptor, result);
    }
    ani_status FindEnum(const char *enum_descriptor, ani_enum *result)
    {
        return c_api->FindEnum(this, enum_descriptor, result);
    }
    ani_status Module_FindFunction(ani_module module, const char *name, const char *signature, ani_function *result)
    {
        return c_api->Module_FindFunction(this, module, name, signature, result);
    }
    ani_status Module_FindVariable(ani_module module, const char *name, ani_variable *result)
    {
        return c_api->Module_FindVariable(this, module, name, result);
    }
    ani_status Namespace_FindFunction(ani_namespace ns, const char *name, const char *signature, ani_function *result)
    {
        return c_api->Namespace_FindFunction(this, ns, name, signature, result);
    }
    ani_status Namespace_FindVariable(ani_namespace ns, const char *name, ani_variable *result)
    {
        return c_api->Namespace_FindVariable(this, ns, name, result);
    }
    ani_status Module_BindNativeFunctions(ani_module module, const ani_native_function *functions,
                                          ani_size nr_functions)
    {
        return c_api->Module_BindNativeFunctions(this, module, functions, nr_functions);
    }
    ani_status Namespace_BindNativeFunctions(ani_namespace ns, const ani_native_function *functions,
                                             ani_size nr_functions)
    {
        return c_api->Namespace_BindNativeFunctions(this, ns, functions, nr_functions);
    }
    ani_status Class_BindNativeMethods(ani_class cls, const ani_native_function *methods, ani_size nr_methods)
    {
        return c_api->Class_BindNativeMethods(this, cls, methods, nr_methods);
    }
    ani_status Reference_Delete(ani_ref lref)
    {
        return c_api->Reference_Delete(this, lref);
    }
    ani_status EnsureEnoughReferences(ani_size nr_refs)
    {
        return c_api->EnsureEnoughReferences(this, nr_refs);
    }
    ani_status CreateLocalScope(ani_size nr_refs)
    {
        return c_api->CreateLocalScope(this, nr_refs);
    }
    ani_status DestroyLocalScope()
    {
        return c_api->DestroyLocalScope(this);
    }
    ani_status CreateEscapeLocalScope(ani_size nr_refs)
    {
        return c_api->CreateEscapeLocalScope(this, nr_refs);
    }
    ani_status DestroyEscapeLocalScope(ani_ref ref, ani_ref *result)
    {
        return c_api->DestroyEscapeLocalScope(this, ref, result);
    }
    ani_status ThrowError(ani_error err)
    {
        return c_api->ThrowError(this, err);
    }
    ani_status ExistUnhandledError(ani_boolean *result)
    {
        return c_api->ExistUnhandledError(this, result);
    }
    ani_status GetUnhandledError(ani_error *result)
    {
        return c_api->GetUnhandledError(this, result);
    }
    ani_status ResetError()
    {
        return c_api->ResetError(this);
    }
    ani_status DescribeError()
    {
        return c_api->DescribeError(this);
    }
    ani_status Abort(const char *message)
    {
        return c_api->Abort(this, message);
    }
    ani_status GetNull(ani_ref *result)
    {
        return c_api->GetNull(this, result);
    }
    ani_status GetUndefined(ani_ref *result)
    {
        return c_api->GetUndefined(this, result);
    }
    ani_status Reference_IsNull(ani_ref ref, ani_boolean *result)
    {
        return c_api->Reference_IsNull(this, ref, result);
    }
    ani_status Reference_IsUndefined(ani_ref ref, ani_boolean *result)
    {
        return c_api->Reference_IsUndefined(this, ref, result);
    }
    ani_status Reference_IsNullishValue(ani_ref ref, ani_boolean *result)
    {
        return c_api->Reference_IsNullishValue(this, ref, result);
    }
    ani_status Reference_Equals(ani_ref ref0, ani_ref ref1, ani_boolean *result)
    {
        return c_api->Reference_Equals(this, ref0, ref1, result);
    }
    ani_status Reference_StrictEquals(ani_ref ref0, ani_ref ref1, ani_boolean *result)
    {
        return c_api->Reference_StrictEquals(this, ref0, ref1, result);
    }
    ani_status String_NewUTF16(const uint16_t *utf16_string, ani_size utf16_size, ani_string *result)
    {
        return c_api->String_NewUTF16(this, utf16_string, utf16_size, result);
    }
    ani_status String_GetUTF16Size(ani_string string, ani_size *result)
    {
        return c_api->String_GetUTF16Size(this, string, result);
    }
    ani_status String_GetUTF16(ani_string string, uint16_t *utf16_buffer, ani_size utf16_buffer_size, ani_size *result)
    {
        return c_api->String_GetUTF16(this, string, utf16_buffer, utf16_buffer_size, result);
    }
    ani_status String_GetUTF16SubString(ani_string string, ani_size substr_offset, ani_size substr_size,
                                        uint16_t *utf16_buffer, ani_size utf16_buffer_size, ani_size *result)
    {
        return c_api->String_GetUTF16SubString(this, string, substr_offset, substr_size, utf16_buffer,
                                               utf16_buffer_size, result);
    }
    ani_status String_NewUTF8(const char *utf8_string, ani_size utf8_size, ani_string *result)
    {
        return c_api->String_NewUTF8(this, utf8_string, utf8_size, result);
    }
    ani_status String_GetUTF8Size(ani_string string, ani_size *result)
    {
        return c_api->String_GetUTF8Size(this, string, result);
    }
    ani_status String_GetUTF8(ani_string string, char *utf8_buffer, ani_size utf8_buffer_size, ani_size *result)
    {
        return c_api->String_GetUTF8(this, string, utf8_buffer, utf8_buffer_size, result);
    }
    ani_status String_GetUTF8SubString(ani_string string, ani_size substr_offset, ani_size substr_size,
                                       char *utf8_buffer, ani_size utf8_buffer_size, ani_size *result)
    {
        return c_api->String_GetUTF8SubString(this, string, substr_offset, substr_size, utf8_buffer, utf8_buffer_size,
                                              result);
    }
    ani_status Array_GetLength(ani_array array, ani_size *result)
    {
        return c_api->Array_GetLength(this, array, result);
    }
    ani_status Array_New(ani_size length, ani_ref initial_element, ani_array *result)
    {
        return c_api->Array_New(this, length, initial_element, result);
    }
    ani_status Array_Set(ani_array array, ani_size index, ani_ref ref)
    {
        return c_api->Array_Set(this, array, index, ref);
    }
    ani_status Array_Get(ani_array array, ani_size index, ani_ref *result)
    {
        return c_api->Array_Get(this, array, index, result);
    }
    ani_status Array_Push(ani_array array, ani_ref ref)
    {
        return c_api->Array_Push(this, array, ref);
    }
    ani_status Array_Pop(ani_array array, ani_ref *result)
    {
        return c_api->Array_Pop(this, array, result);
    }
    ani_status FixedArray_GetLength(ani_fixedarray array, ani_size *result)
    {
        return c_api->FixedArray_GetLength(this, array, result);
    }
    ani_status ValueArray_New_Boolean(ani_size length, ani_valuearray_boolean *result)
    {
        return c_api->ValueArray_New_Boolean(this, length, result);
    }
    ani_status ValueArray_New_Char(ani_size length, ani_valuearray_char *result)
    {
        return c_api->ValueArray_New_Char(this, length, result);
    }
    ani_status ValueArray_New_Byte(ani_size length, ani_valuearray_byte *result)
    {
        return c_api->ValueArray_New_Byte(this, length, result);
    }
    ani_status ValueArray_New_Short(ani_size length, ani_valuearray_short *result)
    {
        return c_api->ValueArray_New_Short(this, length, result);
    }
    ani_status ValueArray_New_Int(ani_size length, ani_valuearray_int *result)
    {
        return c_api->ValueArray_New_Int(this, length, result);
    }
    ani_status ValueArray_New_Long(ani_size length, ani_valuearray_long *result)
    {
        return c_api->ValueArray_New_Long(this, length, result);
    }
    ani_status ValueArray_New_Float(ani_size length, ani_valuearray_float *result)
    {
        return c_api->ValueArray_New_Float(this, length, result);
    }
    ani_status ValueArray_New_Double(ani_size length, ani_valuearray_double *result)
    {
        return c_api->ValueArray_New_Double(this, length, result);
    }
    ani_status ValueArray_GetRegion_Boolean(ani_valuearray_boolean array, ani_size offset, ani_size length,
                                            ani_boolean *native_buffer)
    {
        return c_api->ValueArray_GetRegion_Boolean(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_GetRegion_Char(ani_valuearray_char array, ani_size offset, ani_size length,
                                         ani_char *native_buffer)
    {
        return c_api->ValueArray_GetRegion_Char(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_GetRegion_Byte(ani_valuearray_byte array, ani_size offset, ani_size length,
                                         ani_byte *native_buffer)
    {
        return c_api->ValueArray_GetRegion_Byte(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_GetRegion_Short(ani_valuearray_short array, ani_size offset, ani_size length,
                                          ani_short *native_buffer)
    {
        return c_api->ValueArray_GetRegion_Short(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_GetRegion_Int(ani_valuearray_int array, ani_size offset, ani_size length,
                                        ani_int *native_buffer)
    {
        return c_api->ValueArray_GetRegion_Int(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_GetRegion_Long(ani_valuearray_long array, ani_size offset, ani_size length,
                                         ani_long *native_buffer)
    {
        return c_api->ValueArray_GetRegion_Long(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_GetRegion_Float(ani_valuearray_float array, ani_size offset, ani_size length,
                                          ani_float *native_buffer)
    {
        return c_api->ValueArray_GetRegion_Float(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_GetRegion_Double(ani_valuearray_double array, ani_size offset, ani_size length,
                                           ani_double *native_buffer)
    {
        return c_api->ValueArray_GetRegion_Double(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_SetRegion_Boolean(ani_valuearray_boolean array, ani_size offset, ani_size length,
                                            const ani_boolean *native_buffer)
    {
        return c_api->ValueArray_SetRegion_Boolean(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_SetRegion_Char(ani_valuearray_char array, ani_size offset, ani_size length,
                                         const ani_char *native_buffer)
    {
        return c_api->ValueArray_SetRegion_Char(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_SetRegion_Byte(ani_valuearray_byte array, ani_size offset, ani_size length,
                                         const ani_byte *native_buffer)
    {
        return c_api->ValueArray_SetRegion_Byte(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_SetRegion_Short(ani_valuearray_short array, ani_size offset, ani_size length,
                                          const ani_short *native_buffer)
    {
        return c_api->ValueArray_SetRegion_Short(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_SetRegion_Int(ani_valuearray_int array, ani_size offset, ani_size length,
                                        const ani_int *native_buffer)
    {
        return c_api->ValueArray_SetRegion_Int(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_SetRegion_Long(ani_valuearray_long array, ani_size offset, ani_size length,
                                         const ani_long *native_buffer)
    {
        return c_api->ValueArray_SetRegion_Long(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_SetRegion_Float(ani_valuearray_float array, ani_size offset, ani_size length,
                                          const ani_float *native_buffer)
    {
        return c_api->ValueArray_SetRegion_Float(this, array, offset, length, native_buffer);
    }
    ani_status ValueArray_SetRegion_Double(ani_valuearray_double array, ani_size offset, ani_size length,
                                           const ani_double *native_buffer)
    {
        return c_api->ValueArray_SetRegion_Double(this, array, offset, length, native_buffer);
    }
    ani_status FixedArray_New(ani_type type, ani_size length, ani_ref initial_element, ani_fixedarray *result)
    {
        return c_api->FixedArray_New(this, type, length, initial_element, result);
    }
    ani_status FixedArray_Set(ani_fixedarray array, ani_size index, ani_ref ref)
    {
        return c_api->FixedArray_Set(this, array, index, ref);
    }
    ani_status FixedArray_Get(ani_fixedarray array, ani_size index, ani_ref *result)
    {
        return c_api->FixedArray_Get(this, array, index, result);
    }
    ani_status Enum_GetEnumItemByName(ani_enum enm, const char *name, ani_enum_item *result)
    {
        return c_api->Enum_GetEnumItemByName(this, enm, name, result);
    }
    ani_status Enum_GetEnumItemByIndex(ani_enum enm, ani_size index, ani_enum_item *result)
    {
        return c_api->Enum_GetEnumItemByIndex(this, enm, index, result);
    }
    ani_status EnumItem_GetEnum(ani_enum_item enum_item, ani_enum *result)
    {
        return c_api->EnumItem_GetEnum(this, enum_item, result);
    }
    ani_status EnumItem_GetValue_Int(ani_enum_item enum_item, ani_int *result)
    {
        return c_api->EnumItem_GetValue_Int(this, enum_item, result);
    }
    ani_status EnumItem_GetValue_String(ani_enum_item enum_item, ani_string *result)
    {
        return c_api->EnumItem_GetValue_String(this, enum_item, result);
    }
    ani_status EnumItem_GetName(ani_enum_item enum_item, ani_string *result)
    {
        return c_api->EnumItem_GetName(this, enum_item, result);
    }
    ani_status EnumItem_GetIndex(ani_enum_item enum_item, ani_size *result)
    {
        return c_api->EnumItem_GetIndex(this, enum_item, result);
    }
    ani_status FunctionalObject_Call(ani_fn_object fn, ani_size argc, ani_ref *argv, ani_ref *result)
    {
        return c_api->FunctionalObject_Call(this, fn, argc, argv, result);
    }
    ani_status Variable_SetValue_Boolean(ani_variable variable, ani_boolean value)
    {
        return c_api->Variable_SetValue_Boolean(this, variable, value);
    }
    ani_status Variable_SetValue_Char(ani_variable variable, ani_char value)
    {
        return c_api->Variable_SetValue_Char(this, variable, value);
    }
    ani_status Variable_SetValue_Byte(ani_variable variable, ani_byte value)
    {
        return c_api->Variable_SetValue_Byte(this, variable, value);
    }
    ani_status Variable_SetValue_Short(ani_variable variable, ani_short value)
    {
        return c_api->Variable_SetValue_Short(this, variable, value);
    }
    ani_status Variable_SetValue_Int(ani_variable variable, ani_int value)
    {
        return c_api->Variable_SetValue_Int(this, variable, value);
    }
    ani_status Variable_SetValue_Long(ani_variable variable, ani_long value)
    {
        return c_api->Variable_SetValue_Long(this, variable, value);
    }
    ani_status Variable_SetValue_Float(ani_variable variable, ani_float value)
    {
        return c_api->Variable_SetValue_Float(this, variable, value);
    }
    ani_status Variable_SetValue_Double(ani_variable variable, ani_double value)
    {
        return c_api->Variable_SetValue_Double(this, variable, value);
    }
    ani_status Variable_SetValue_Ref(ani_variable variable, ani_ref value)
    {
        return c_api->Variable_SetValue_Ref(this, variable, value);
    }
    ani_status Variable_GetValue_Boolean(ani_variable variable, ani_boolean *result)
    {
        return c_api->Variable_GetValue_Boolean(this, variable, result);
    }
    ani_status Variable_GetValue_Char(ani_variable variable, ani_char *result)
    {
        return c_api->Variable_GetValue_Char(this, variable, result);
    }
    ani_status Variable_GetValue_Byte(ani_variable variable, ani_byte *result)
    {
        return c_api->Variable_GetValue_Byte(this, variable, result);
    }
    ani_status Variable_GetValue_Short(ani_variable variable, ani_short *result)
    {
        return c_api->Variable_GetValue_Short(this, variable, result);
    }
    ani_status Variable_GetValue_Int(ani_variable variable, ani_int *result)
    {
        return c_api->Variable_GetValue_Int(this, variable, result);
    }
    ani_status Variable_GetValue_Long(ani_variable variable, ani_long *result)
    {
        return c_api->Variable_GetValue_Long(this, variable, result);
    }
    ani_status Variable_GetValue_Float(ani_variable variable, ani_float *result)
    {
        return c_api->Variable_GetValue_Float(this, variable, result);
    }
    ani_status Variable_GetValue_Double(ani_variable variable, ani_double *result)
    {
        return c_api->Variable_GetValue_Double(this, variable, result);
    }
    ani_status Variable_GetValue_Ref(ani_variable variable, ani_ref *result)
    {
        return c_api->Variable_GetValue_Ref(this, variable, result);
    }
    ani_status Function_Call_Boolean(ani_function fn, ani_boolean *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Boolean_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Boolean_A(ani_function fn, ani_boolean *result, const ani_value *args)
    {
        return c_api->Function_Call_Boolean_A(this, fn, result, args);
    }
    ani_status Function_Call_Boolean_V(ani_function fn, ani_boolean *result, va_list args)
    {
        return c_api->Function_Call_Boolean_V(this, fn, result, args);
    }
    ani_status Function_Call_Char(ani_function fn, ani_char *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Char_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Char_A(ani_function fn, ani_char *result, const ani_value *args)
    {
        return c_api->Function_Call_Char_A(this, fn, result, args);
    }
    ani_status Function_Call_Char_V(ani_function fn, ani_char *result, va_list args)
    {
        return c_api->Function_Call_Char_V(this, fn, result, args);
    }
    ani_status Function_Call_Byte(ani_function fn, ani_byte *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Byte_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Byte_A(ani_function fn, ani_byte *result, const ani_value *args)
    {
        return c_api->Function_Call_Byte_A(this, fn, result, args);
    }
    ani_status Function_Call_Byte_V(ani_function fn, ani_byte *result, va_list args)
    {
        return c_api->Function_Call_Byte_V(this, fn, result, args);
    }
    ani_status Function_Call_Short(ani_function fn, ani_short *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Short_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Short_A(ani_function fn, ani_short *result, const ani_value *args)
    {
        return c_api->Function_Call_Short_A(this, fn, result, args);
    }
    ani_status Function_Call_Short_V(ani_function fn, ani_short *result, va_list args)
    {
        return c_api->Function_Call_Short_V(this, fn, result, args);
    }
    ani_status Function_Call_Int(ani_function fn, ani_int *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Int_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Int_A(ani_function fn, ani_int *result, const ani_value *args)
    {
        return c_api->Function_Call_Int_A(this, fn, result, args);
    }
    ani_status Function_Call_Int_V(ani_function fn, ani_int *result, va_list args)
    {
        return c_api->Function_Call_Int_V(this, fn, result, args);
    }
    ani_status Function_Call_Long(ani_function fn, ani_long *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Long_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Long_A(ani_function fn, ani_long *result, const ani_value *args)
    {
        return c_api->Function_Call_Long_A(this, fn, result, args);
    }
    ani_status Function_Call_Long_V(ani_function fn, ani_long *result, va_list args)
    {
        return c_api->Function_Call_Long_V(this, fn, result, args);
    }
    ani_status Function_Call_Float(ani_function fn, ani_float *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Float_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Float_A(ani_function fn, ani_float *result, const ani_value *args)
    {
        return c_api->Function_Call_Float_A(this, fn, result, args);
    }
    ani_status Function_Call_Float_V(ani_function fn, ani_float *result, va_list args)
    {
        return c_api->Function_Call_Float_V(this, fn, result, args);
    }
    ani_status Function_Call_Double(ani_function fn, ani_double *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Double_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Double_A(ani_function fn, ani_double *result, const ani_value *args)
    {
        return c_api->Function_Call_Double_A(this, fn, result, args);
    }
    ani_status Function_Call_Double_V(ani_function fn, ani_double *result, va_list args)
    {
        return c_api->Function_Call_Double_V(this, fn, result, args);
    }
    ani_status Function_Call_Ref(ani_function fn, ani_ref *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Function_Call_Ref_V(this, fn, result, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Ref_A(ani_function fn, ani_ref *result, const ani_value *args)
    {
        return c_api->Function_Call_Ref_A(this, fn, result, args);
    }
    ani_status Function_Call_Ref_V(ani_function fn, ani_ref *result, va_list args)
    {
        return c_api->Function_Call_Ref_V(this, fn, result, args);
    }
    ani_status Function_Call_Void(ani_function fn, ...)
    {
        va_list args;
        va_start(args, fn);
        ani_status status = c_api->Function_Call_Void_V(this, fn, args);
        va_end(args);
        return status;
    }
    ani_status Function_Call_Void_A(ani_function fn, const ani_value *args)
    {
        return c_api->Function_Call_Void_A(this, fn, args);
    }
    ani_status Function_Call_Void_V(ani_function fn, va_list args)
    {
        return c_api->Function_Call_Void_V(this, fn, args);
    }
    ani_status Class_FindField(ani_class cls, const char *name, ani_field *result)
    {
        return c_api->Class_FindField(this, cls, name, result);
    }
    ani_status Class_FindStaticField(ani_class cls, const char *name, ani_static_field *result)
    {
        return c_api->Class_FindStaticField(this, cls, name, result);
    }
    ani_status Class_FindMethod(ani_class cls, const char *name, const char *signature, ani_method *result)
    {
        return c_api->Class_FindMethod(this, cls, name, signature, result);
    }
    ani_status Class_FindStaticMethod(ani_class cls, const char *name, const char *signature, ani_static_method *result)
    {
        return c_api->Class_FindStaticMethod(this, cls, name, signature, result);
    }
    ani_status Class_FindSetter(ani_class cls, const char *name, ani_method *result)
    {
        return c_api->Class_FindSetter(this, cls, name, result);
    }
    ani_status Class_FindGetter(ani_class cls, const char *name, ani_method *result)
    {
        return c_api->Class_FindGetter(this, cls, name, result);
    }
    ani_status Class_FindIndexableGetter(ani_class cls, const char *signature, ani_method *result)
    {
        return c_api->Class_FindIndexableGetter(this, cls, signature, result);
    }
    ani_status Class_FindIndexableSetter(ani_class cls, const char *signature, ani_method *result)
    {
        return c_api->Class_FindIndexableSetter(this, cls, signature, result);
    }
    ani_status Class_FindIterator(ani_class cls, ani_method *result)
    {
        return c_api->Class_FindIterator(this, cls, result);
    }
    ani_status Class_GetStaticField_Boolean(ani_class cls, ani_static_field field, ani_boolean *result)
    {
        return c_api->Class_GetStaticField_Boolean(this, cls, field, result);
    }
    ani_status Class_GetStaticField_Char(ani_class cls, ani_static_field field, ani_char *result)
    {
        return c_api->Class_GetStaticField_Char(this, cls, field, result);
    }
    ani_status Class_GetStaticField_Byte(ani_class cls, ani_static_field field, ani_byte *result)
    {
        return c_api->Class_GetStaticField_Byte(this, cls, field, result);
    }
    ani_status Class_GetStaticField_Short(ani_class cls, ani_static_field field, ani_short *result)
    {
        return c_api->Class_GetStaticField_Short(this, cls, field, result);
    }
    ani_status Class_GetStaticField_Int(ani_class cls, ani_static_field field, ani_int *result)
    {
        return c_api->Class_GetStaticField_Int(this, cls, field, result);
    }
    ani_status Class_GetStaticField_Long(ani_class cls, ani_static_field field, ani_long *result)
    {
        return c_api->Class_GetStaticField_Long(this, cls, field, result);
    }
    ani_status Class_GetStaticField_Float(ani_class cls, ani_static_field field, ani_float *result)
    {
        return c_api->Class_GetStaticField_Float(this, cls, field, result);
    }
    ani_status Class_GetStaticField_Double(ani_class cls, ani_static_field field, ani_double *result)
    {
        return c_api->Class_GetStaticField_Double(this, cls, field, result);
    }
    ani_status Class_GetStaticField_Ref(ani_class cls, ani_static_field field, ani_ref *result)
    {
        return c_api->Class_GetStaticField_Ref(this, cls, field, result);
    }
    ani_status Class_SetStaticField_Boolean(ani_class cls, ani_static_field field, ani_boolean value)
    {
        return c_api->Class_SetStaticField_Boolean(this, cls, field, value);
    }
    ani_status Class_SetStaticField_Char(ani_class cls, ani_static_field field, ani_char value)
    {
        return c_api->Class_SetStaticField_Char(this, cls, field, value);
    }
    ani_status Class_SetStaticField_Byte(ani_class cls, ani_static_field field, ani_byte value)
    {
        return c_api->Class_SetStaticField_Byte(this, cls, field, value);
    }
    ani_status Class_SetStaticField_Short(ani_class cls, ani_static_field field, ani_short value)
    {
        return c_api->Class_SetStaticField_Short(this, cls, field, value);
    }
    ani_status Class_SetStaticField_Int(ani_class cls, ani_static_field field, ani_int value)
    {
        return c_api->Class_SetStaticField_Int(this, cls, field, value);
    }
    ani_status Class_SetStaticField_Long(ani_class cls, ani_static_field field, ani_long value)
    {
        return c_api->Class_SetStaticField_Long(this, cls, field, value);
    }
    ani_status Class_SetStaticField_Float(ani_class cls, ani_static_field field, ani_float value)
    {
        return c_api->Class_SetStaticField_Float(this, cls, field, value);
    }
    ani_status Class_SetStaticField_Double(ani_class cls, ani_static_field field, ani_double value)
    {
        return c_api->Class_SetStaticField_Double(this, cls, field, value);
    }
    ani_status Class_SetStaticField_Ref(ani_class cls, ani_static_field field, ani_ref value)
    {
        return c_api->Class_SetStaticField_Ref(this, cls, field, value);
    }
    ani_status Class_GetStaticFieldByName_Boolean(ani_class cls, const char *name, ani_boolean *result)
    {
        return c_api->Class_GetStaticFieldByName_Boolean(this, cls, name, result);
    }
    ani_status Class_GetStaticFieldByName_Char(ani_class cls, const char *name, ani_char *result)
    {
        return c_api->Class_GetStaticFieldByName_Char(this, cls, name, result);
    }
    ani_status Class_GetStaticFieldByName_Byte(ani_class cls, const char *name, ani_byte *result)
    {
        return c_api->Class_GetStaticFieldByName_Byte(this, cls, name, result);
    }
    ani_status Class_GetStaticFieldByName_Short(ani_class cls, const char *name, ani_short *result)
    {
        return c_api->Class_GetStaticFieldByName_Short(this, cls, name, result);
    }
    ani_status Class_GetStaticFieldByName_Int(ani_class cls, const char *name, ani_int *result)
    {
        return c_api->Class_GetStaticFieldByName_Int(this, cls, name, result);
    }
    ani_status Class_GetStaticFieldByName_Long(ani_class cls, const char *name, ani_long *result)
    {
        return c_api->Class_GetStaticFieldByName_Long(this, cls, name, result);
    }
    ani_status Class_GetStaticFieldByName_Float(ani_class cls, const char *name, ani_float *result)
    {
        return c_api->Class_GetStaticFieldByName_Float(this, cls, name, result);
    }
    ani_status Class_GetStaticFieldByName_Double(ani_class cls, const char *name, ani_double *result)
    {
        return c_api->Class_GetStaticFieldByName_Double(this, cls, name, result);
    }
    ani_status Class_GetStaticFieldByName_Ref(ani_class cls, const char *name, ani_ref *result)
    {
        return c_api->Class_GetStaticFieldByName_Ref(this, cls, name, result);
    }
    ani_status Class_SetStaticFieldByName_Boolean(ani_class cls, const char *name, ani_boolean value)
    {
        return c_api->Class_SetStaticFieldByName_Boolean(this, cls, name, value);
    }
    ani_status Class_SetStaticFieldByName_Char(ani_class cls, const char *name, ani_char value)
    {
        return c_api->Class_SetStaticFieldByName_Char(this, cls, name, value);
    }
    ani_status Class_SetStaticFieldByName_Byte(ani_class cls, const char *name, ani_byte value)
    {
        return c_api->Class_SetStaticFieldByName_Byte(this, cls, name, value);
    }
    ani_status Class_SetStaticFieldByName_Short(ani_class cls, const char *name, ani_short value)
    {
        return c_api->Class_SetStaticFieldByName_Short(this, cls, name, value);
    }
    ani_status Class_SetStaticFieldByName_Int(ani_class cls, const char *name, ani_int value)
    {
        return c_api->Class_SetStaticFieldByName_Int(this, cls, name, value);
    }
    ani_status Class_SetStaticFieldByName_Long(ani_class cls, const char *name, ani_long value)
    {
        return c_api->Class_SetStaticFieldByName_Long(this, cls, name, value);
    }
    ani_status Class_SetStaticFieldByName_Float(ani_class cls, const char *name, ani_float value)
    {
        return c_api->Class_SetStaticFieldByName_Float(this, cls, name, value);
    }
    ani_status Class_SetStaticFieldByName_Double(ani_class cls, const char *name, ani_double value)
    {
        return c_api->Class_SetStaticFieldByName_Double(this, cls, name, value);
    }
    ani_status Class_SetStaticFieldByName_Ref(ani_class cls, const char *name, ani_ref value)
    {
        return c_api->Class_SetStaticFieldByName_Ref(this, cls, name, value);
    }
    ani_status Class_CallStaticMethod_Boolean(ani_class cls, ani_static_method method, ani_boolean *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Boolean_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Boolean_A(ani_class cls, ani_static_method method, ani_boolean *result,
                                                const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Boolean_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Boolean_V(ani_class cls, ani_static_method method, ani_boolean *result,
                                                va_list args)
    {
        return c_api->Class_CallStaticMethod_Boolean_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Char(ani_class cls, ani_static_method method, ani_char *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Char_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Char_A(ani_class cls, ani_static_method method, ani_char *result,
                                             const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Char_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Char_V(ani_class cls, ani_static_method method, ani_char *result, va_list args)
    {
        return c_api->Class_CallStaticMethod_Char_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Byte(ani_class cls, ani_static_method method, ani_byte *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Byte_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Byte_A(ani_class cls, ani_static_method method, ani_byte *result,
                                             const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Byte_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Byte_V(ani_class cls, ani_static_method method, ani_byte *result, va_list args)
    {
        return c_api->Class_CallStaticMethod_Byte_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Short(ani_class cls, ani_static_method method, ani_short *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Short_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Short_A(ani_class cls, ani_static_method method, ani_short *result,
                                              const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Short_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Short_V(ani_class cls, ani_static_method method, ani_short *result, va_list args)
    {
        return c_api->Class_CallStaticMethod_Short_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Int(ani_class cls, ani_static_method method, ani_int *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Int_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Int_A(ani_class cls, ani_static_method method, ani_int *result,
                                            const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Int_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Int_V(ani_class cls, ani_static_method method, ani_int *result, va_list args)
    {
        return c_api->Class_CallStaticMethod_Int_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Long(ani_class cls, ani_static_method method, ani_long *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Long_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Long_A(ani_class cls, ani_static_method method, ani_long *result,
                                             const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Long_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Long_V(ani_class cls, ani_static_method method, ani_long *result, va_list args)
    {
        return c_api->Class_CallStaticMethod_Long_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Float(ani_class cls, ani_static_method method, ani_float *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Float_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Float_A(ani_class cls, ani_static_method method, ani_float *result,
                                              const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Float_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Float_V(ani_class cls, ani_static_method method, ani_float *result, va_list args)
    {
        return c_api->Class_CallStaticMethod_Float_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Double(ani_class cls, ani_static_method method, ani_double *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Double_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Double_A(ani_class cls, ani_static_method method, ani_double *result,
                                               const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Double_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Double_V(ani_class cls, ani_static_method method, ani_double *result,
                                               va_list args)
    {
        return c_api->Class_CallStaticMethod_Double_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Ref(ani_class cls, ani_static_method method, ani_ref *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethod_Ref_V(this, cls, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Ref_A(ani_class cls, ani_static_method method, ani_ref *result,
                                            const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Ref_A(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Ref_V(ani_class cls, ani_static_method method, ani_ref *result, va_list args)
    {
        return c_api->Class_CallStaticMethod_Ref_V(this, cls, method, result, args);
    }
    ani_status Class_CallStaticMethod_Void(ani_class cls, ani_static_method method, ...)
    {
        va_list args;
        va_start(args, method);
        ani_status status = c_api->Class_CallStaticMethod_Void_V(this, cls, method, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethod_Void_A(ani_class cls, ani_static_method method, const ani_value *args)
    {
        return c_api->Class_CallStaticMethod_Void_A(this, cls, method, args);
    }
    ani_status Class_CallStaticMethod_Void_V(ani_class cls, ani_static_method method, va_list args)
    {
        return c_api->Class_CallStaticMethod_Void_V(this, cls, method, args);
    }
    ani_status Class_CallStaticMethodByName_Boolean(ani_class cls, const char *name, const char *signature,
                                                    ani_boolean *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Boolean_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Boolean_A(ani_class cls, const char *name, const char *signature,
                                                      ani_boolean *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Boolean_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Boolean_V(ani_class cls, const char *name, const char *signature,
                                                      ani_boolean *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Boolean_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Char(ani_class cls, const char *name, const char *signature,
                                                 ani_char *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Char_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Char_A(ani_class cls, const char *name, const char *signature,
                                                   ani_char *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Char_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Char_V(ani_class cls, const char *name, const char *signature,
                                                   ani_char *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Char_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Byte(ani_class cls, const char *name, const char *signature,
                                                 ani_byte *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Byte_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Byte_A(ani_class cls, const char *name, const char *signature,
                                                   ani_byte *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Byte_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Byte_V(ani_class cls, const char *name, const char *signature,
                                                   ani_byte *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Byte_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Short(ani_class cls, const char *name, const char *signature,
                                                  ani_short *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Short_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Short_A(ani_class cls, const char *name, const char *signature,
                                                    ani_short *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Short_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Short_V(ani_class cls, const char *name, const char *signature,
                                                    ani_short *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Short_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Int(ani_class cls, const char *name, const char *signature, ani_int *result,
                                                ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Int_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Int_A(ani_class cls, const char *name, const char *signature,
                                                  ani_int *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Int_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Int_V(ani_class cls, const char *name, const char *signature,
                                                  ani_int *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Int_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Long(ani_class cls, const char *name, const char *signature,
                                                 ani_long *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Long_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Long_A(ani_class cls, const char *name, const char *signature,
                                                   ani_long *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Long_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Long_V(ani_class cls, const char *name, const char *signature,
                                                   ani_long *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Long_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Float(ani_class cls, const char *name, const char *signature,
                                                  ani_float *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Float_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Float_A(ani_class cls, const char *name, const char *signature,
                                                    ani_float *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Float_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Float_V(ani_class cls, const char *name, const char *signature,
                                                    ani_float *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Float_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Double(ani_class cls, const char *name, const char *signature,
                                                   ani_double *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Double_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Double_A(ani_class cls, const char *name, const char *signature,
                                                     ani_double *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Double_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Double_V(ani_class cls, const char *name, const char *signature,
                                                     ani_double *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Double_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Ref(ani_class cls, const char *name, const char *signature, ani_ref *result,
                                                ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Class_CallStaticMethodByName_Ref_V(this, cls, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Ref_A(ani_class cls, const char *name, const char *signature,
                                                  ani_ref *result, const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Ref_A(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Ref_V(ani_class cls, const char *name, const char *signature,
                                                  ani_ref *result, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Ref_V(this, cls, name, signature, result, args);
    }
    ani_status Class_CallStaticMethodByName_Void(ani_class cls, const char *name, const char *signature, ...)
    {
        va_list args;
        va_start(args, signature);
        ani_status status = c_api->Class_CallStaticMethodByName_Void_V(this, cls, name, signature, args);
        va_end(args);
        return status;
    }
    ani_status Class_CallStaticMethodByName_Void_A(ani_class cls, const char *name, const char *signature,
                                                   const ani_value *args)
    {
        return c_api->Class_CallStaticMethodByName_Void_A(this, cls, name, signature, args);
    }
    ani_status Class_CallStaticMethodByName_Void_V(ani_class cls, const char *name, const char *signature, va_list args)
    {
        return c_api->Class_CallStaticMethodByName_Void_V(this, cls, name, signature, args);
    }
    ani_status Object_GetField_Boolean(ani_object object, ani_field field, ani_boolean *result)
    {
        return c_api->Object_GetField_Boolean(this, object, field, result);
    }
    ani_status Object_GetField_Char(ani_object object, ani_field field, ani_char *result)
    {
        return c_api->Object_GetField_Char(this, object, field, result);
    }
    ani_status Object_GetField_Byte(ani_object object, ani_field field, ani_byte *result)
    {
        return c_api->Object_GetField_Byte(this, object, field, result);
    }
    ani_status Object_GetField_Short(ani_object object, ani_field field, ani_short *result)
    {
        return c_api->Object_GetField_Short(this, object, field, result);
    }
    ani_status Object_GetField_Int(ani_object object, ani_field field, ani_int *result)
    {
        return c_api->Object_GetField_Int(this, object, field, result);
    }
    ani_status Object_GetField_Long(ani_object object, ani_field field, ani_long *result)
    {
        return c_api->Object_GetField_Long(this, object, field, result);
    }
    ani_status Object_GetField_Float(ani_object object, ani_field field, ani_float *result)
    {
        return c_api->Object_GetField_Float(this, object, field, result);
    }
    ani_status Object_GetField_Double(ani_object object, ani_field field, ani_double *result)
    {
        return c_api->Object_GetField_Double(this, object, field, result);
    }
    ani_status Object_GetField_Ref(ani_object object, ani_field field, ani_ref *result)
    {
        return c_api->Object_GetField_Ref(this, object, field, result);
    }
    ani_status Object_SetField_Boolean(ani_object object, ani_field field, ani_boolean value)
    {
        return c_api->Object_SetField_Boolean(this, object, field, value);
    }
    ani_status Object_SetField_Char(ani_object object, ani_field field, ani_char value)
    {
        return c_api->Object_SetField_Char(this, object, field, value);
    }
    ani_status Object_SetField_Byte(ani_object object, ani_field field, ani_byte value)
    {
        return c_api->Object_SetField_Byte(this, object, field, value);
    }
    ani_status Object_SetField_Short(ani_object object, ani_field field, ani_short value)
    {
        return c_api->Object_SetField_Short(this, object, field, value);
    }
    ani_status Object_SetField_Int(ani_object object, ani_field field, ani_int value)
    {
        return c_api->Object_SetField_Int(this, object, field, value);
    }
    ani_status Object_SetField_Long(ani_object object, ani_field field, ani_long value)
    {
        return c_api->Object_SetField_Long(this, object, field, value);
    }
    ani_status Object_SetField_Float(ani_object object, ani_field field, ani_float value)
    {
        return c_api->Object_SetField_Float(this, object, field, value);
    }
    ani_status Object_SetField_Double(ani_object object, ani_field field, ani_double value)
    {
        return c_api->Object_SetField_Double(this, object, field, value);
    }
    ani_status Object_SetField_Ref(ani_object object, ani_field field, ani_ref value)
    {
        return c_api->Object_SetField_Ref(this, object, field, value);
    }
    ani_status Object_GetFieldByName_Boolean(ani_object object, const char *name, ani_boolean *result)
    {
        return c_api->Object_GetFieldByName_Boolean(this, object, name, result);
    }
    ani_status Object_GetFieldByName_Char(ani_object object, const char *name, ani_char *result)
    {
        return c_api->Object_GetFieldByName_Char(this, object, name, result);
    }
    ani_status Object_GetFieldByName_Byte(ani_object object, const char *name, ani_byte *result)
    {
        return c_api->Object_GetFieldByName_Byte(this, object, name, result);
    }
    ani_status Object_GetFieldByName_Short(ani_object object, const char *name, ani_short *result)
    {
        return c_api->Object_GetFieldByName_Short(this, object, name, result);
    }
    ani_status Object_GetFieldByName_Int(ani_object object, const char *name, ani_int *result)
    {
        return c_api->Object_GetFieldByName_Int(this, object, name, result);
    }
    ani_status Object_GetFieldByName_Long(ani_object object, const char *name, ani_long *result)
    {
        return c_api->Object_GetFieldByName_Long(this, object, name, result);
    }
    ani_status Object_GetFieldByName_Float(ani_object object, const char *name, ani_float *result)
    {
        return c_api->Object_GetFieldByName_Float(this, object, name, result);
    }
    ani_status Object_GetFieldByName_Double(ani_object object, const char *name, ani_double *result)
    {
        return c_api->Object_GetFieldByName_Double(this, object, name, result);
    }
    ani_status Object_GetFieldByName_Ref(ani_object object, const char *name, ani_ref *result)
    {
        return c_api->Object_GetFieldByName_Ref(this, object, name, result);
    }
    ani_status Object_SetFieldByName_Boolean(ani_object object, const char *name, ani_boolean value)
    {
        return c_api->Object_SetFieldByName_Boolean(this, object, name, value);
    }
    ani_status Object_SetFieldByName_Char(ani_object object, const char *name, ani_char value)
    {
        return c_api->Object_SetFieldByName_Char(this, object, name, value);
    }
    ani_status Object_SetFieldByName_Byte(ani_object object, const char *name, ani_byte value)
    {
        return c_api->Object_SetFieldByName_Byte(this, object, name, value);
    }
    ani_status Object_SetFieldByName_Short(ani_object object, const char *name, ani_short value)
    {
        return c_api->Object_SetFieldByName_Short(this, object, name, value);
    }
    ani_status Object_SetFieldByName_Int(ani_object object, const char *name, ani_int value)
    {
        return c_api->Object_SetFieldByName_Int(this, object, name, value);
    }
    ani_status Object_SetFieldByName_Long(ani_object object, const char *name, ani_long value)
    {
        return c_api->Object_SetFieldByName_Long(this, object, name, value);
    }
    ani_status Object_SetFieldByName_Float(ani_object object, const char *name, ani_float value)
    {
        return c_api->Object_SetFieldByName_Float(this, object, name, value);
    }
    ani_status Object_SetFieldByName_Double(ani_object object, const char *name, ani_double value)
    {
        return c_api->Object_SetFieldByName_Double(this, object, name, value);
    }
    ani_status Object_SetFieldByName_Ref(ani_object object, const char *name, ani_ref value)
    {
        return c_api->Object_SetFieldByName_Ref(this, object, name, value);
    }
    ani_status Object_GetPropertyByName_Boolean(ani_object object, const char *name, ani_boolean *result)
    {
        return c_api->Object_GetPropertyByName_Boolean(this, object, name, result);
    }
    ani_status Object_GetPropertyByName_Char(ani_object object, const char *name, ani_char *result)
    {
        return c_api->Object_GetPropertyByName_Char(this, object, name, result);
    }
    ani_status Object_GetPropertyByName_Byte(ani_object object, const char *name, ani_byte *result)
    {
        return c_api->Object_GetPropertyByName_Byte(this, object, name, result);
    }
    ani_status Object_GetPropertyByName_Short(ani_object object, const char *name, ani_short *result)
    {
        return c_api->Object_GetPropertyByName_Short(this, object, name, result);
    }
    ani_status Object_GetPropertyByName_Int(ani_object object, const char *name, ani_int *result)
    {
        return c_api->Object_GetPropertyByName_Int(this, object, name, result);
    }
    ani_status Object_GetPropertyByName_Long(ani_object object, const char *name, ani_long *result)
    {
        return c_api->Object_GetPropertyByName_Long(this, object, name, result);
    }
    ani_status Object_GetPropertyByName_Float(ani_object object, const char *name, ani_float *result)
    {
        return c_api->Object_GetPropertyByName_Float(this, object, name, result);
    }
    ani_status Object_GetPropertyByName_Double(ani_object object, const char *name, ani_double *result)
    {
        return c_api->Object_GetPropertyByName_Double(this, object, name, result);
    }
    ani_status Object_GetPropertyByName_Ref(ani_object object, const char *name, ani_ref *result)
    {
        return c_api->Object_GetPropertyByName_Ref(this, object, name, result);
    }
    ani_status Object_SetPropertyByName_Boolean(ani_object object, const char *name, ani_boolean value)
    {
        return c_api->Object_SetPropertyByName_Boolean(this, object, name, value);
    }
    ani_status Object_SetPropertyByName_Char(ani_object object, const char *name, ani_char value)
    {
        return c_api->Object_SetPropertyByName_Char(this, object, name, value);
    }
    ani_status Object_SetPropertyByName_Byte(ani_object object, const char *name, ani_byte value)
    {
        return c_api->Object_SetPropertyByName_Byte(this, object, name, value);
    }
    ani_status Object_SetPropertyByName_Short(ani_object object, const char *name, ani_short value)
    {
        return c_api->Object_SetPropertyByName_Short(this, object, name, value);
    }
    ani_status Object_SetPropertyByName_Int(ani_object object, const char *name, ani_int value)
    {
        return c_api->Object_SetPropertyByName_Int(this, object, name, value);
    }
    ani_status Object_SetPropertyByName_Long(ani_object object, const char *name, ani_long value)
    {
        return c_api->Object_SetPropertyByName_Long(this, object, name, value);
    }
    ani_status Object_SetPropertyByName_Float(ani_object object, const char *name, ani_float value)
    {
        return c_api->Object_SetPropertyByName_Float(this, object, name, value);
    }
    ani_status Object_SetPropertyByName_Double(ani_object object, const char *name, ani_double value)
    {
        return c_api->Object_SetPropertyByName_Double(this, object, name, value);
    }
    ani_status Object_SetPropertyByName_Ref(ani_object object, const char *name, ani_ref value)
    {
        return c_api->Object_SetPropertyByName_Ref(this, object, name, value);
    }
    ani_status Object_CallMethod_Boolean(ani_object object, ani_method method, ani_boolean *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Boolean_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Boolean_A(ani_object object, ani_method method, ani_boolean *result,
                                           const ani_value *args)
    {
        return c_api->Object_CallMethod_Boolean_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Boolean_V(ani_object object, ani_method method, ani_boolean *result, va_list args)
    {
        return c_api->Object_CallMethod_Boolean_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Char(ani_object object, ani_method method, ani_char *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Char_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Char_A(ani_object object, ani_method method, ani_char *result, const ani_value *args)
    {
        return c_api->Object_CallMethod_Char_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Char_V(ani_object object, ani_method method, ani_char *result, va_list args)
    {
        return c_api->Object_CallMethod_Char_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Byte(ani_object object, ani_method method, ani_byte *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Byte_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Byte_A(ani_object object, ani_method method, ani_byte *result, const ani_value *args)
    {
        return c_api->Object_CallMethod_Byte_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Byte_V(ani_object object, ani_method method, ani_byte *result, va_list args)
    {
        return c_api->Object_CallMethod_Byte_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Short(ani_object object, ani_method method, ani_short *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Short_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Short_A(ani_object object, ani_method method, ani_short *result, const ani_value *args)
    {
        return c_api->Object_CallMethod_Short_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Short_V(ani_object object, ani_method method, ani_short *result, va_list args)
    {
        return c_api->Object_CallMethod_Short_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Int(ani_object object, ani_method method, ani_int *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Int_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Int_A(ani_object object, ani_method method, ani_int *result, const ani_value *args)
    {
        return c_api->Object_CallMethod_Int_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Int_V(ani_object object, ani_method method, ani_int *result, va_list args)
    {
        return c_api->Object_CallMethod_Int_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Long(ani_object object, ani_method method, ani_long *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Long_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Long_A(ani_object object, ani_method method, ani_long *result, const ani_value *args)
    {
        return c_api->Object_CallMethod_Long_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Long_V(ani_object object, ani_method method, ani_long *result, va_list args)
    {
        return c_api->Object_CallMethod_Long_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Float(ani_object object, ani_method method, ani_float *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Float_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Float_A(ani_object object, ani_method method, ani_float *result, const ani_value *args)
    {
        return c_api->Object_CallMethod_Float_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Float_V(ani_object object, ani_method method, ani_float *result, va_list args)
    {
        return c_api->Object_CallMethod_Float_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Double(ani_object object, ani_method method, ani_double *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Double_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Double_A(ani_object object, ani_method method, ani_double *result,
                                          const ani_value *args)
    {
        return c_api->Object_CallMethod_Double_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Double_V(ani_object object, ani_method method, ani_double *result, va_list args)
    {
        return c_api->Object_CallMethod_Double_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Ref(ani_object object, ani_method method, ani_ref *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethod_Ref_V(this, object, method, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Ref_A(ani_object object, ani_method method, ani_ref *result, const ani_value *args)
    {
        return c_api->Object_CallMethod_Ref_A(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Ref_V(ani_object object, ani_method method, ani_ref *result, va_list args)
    {
        return c_api->Object_CallMethod_Ref_V(this, object, method, result, args);
    }
    ani_status Object_CallMethod_Void(ani_object object, ani_method method, ...)
    {
        va_list args;
        va_start(args, method);
        ani_status status = c_api->Object_CallMethod_Void_V(this, object, method, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethod_Void_A(ani_object object, ani_method method, const ani_value *args)
    {
        return c_api->Object_CallMethod_Void_A(this, object, method, args);
    }
    ani_status Object_CallMethod_Void_V(ani_object object, ani_method method, va_list args)
    {
        return c_api->Object_CallMethod_Void_V(this, object, method, args);
    }
    ani_status Object_CallMethodByName_Boolean(ani_object object, const char *name, const char *signature,
                                               ani_boolean *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Boolean_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Boolean_A(ani_object object, const char *name, const char *signature,
                                                 ani_boolean *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Boolean_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Boolean_V(ani_object object, const char *name, const char *signature,
                                                 ani_boolean *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Boolean_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Char(ani_object object, const char *name, const char *signature,
                                            ani_char *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Char_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Char_A(ani_object object, const char *name, const char *signature,
                                              ani_char *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Char_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Char_V(ani_object object, const char *name, const char *signature,
                                              ani_char *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Char_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Byte(ani_object object, const char *name, const char *signature,
                                            ani_byte *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Byte_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Byte_A(ani_object object, const char *name, const char *signature,
                                              ani_byte *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Byte_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Byte_V(ani_object object, const char *name, const char *signature,
                                              ani_byte *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Byte_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Short(ani_object object, const char *name, const char *signature,
                                             ani_short *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Short_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Short_A(ani_object object, const char *name, const char *signature,
                                               ani_short *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Short_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Short_V(ani_object object, const char *name, const char *signature,
                                               ani_short *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Short_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Int(ani_object object, const char *name, const char *signature, ani_int *result,
                                           ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Int_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Int_A(ani_object object, const char *name, const char *signature,
                                             ani_int *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Int_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Int_V(ani_object object, const char *name, const char *signature,
                                             ani_int *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Int_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Long(ani_object object, const char *name, const char *signature,
                                            ani_long *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Long_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Long_A(ani_object object, const char *name, const char *signature,
                                              ani_long *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Long_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Long_V(ani_object object, const char *name, const char *signature,
                                              ani_long *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Long_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Float(ani_object object, const char *name, const char *signature,
                                             ani_float *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Float_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Float_A(ani_object object, const char *name, const char *signature,
                                               ani_float *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Float_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Float_V(ani_object object, const char *name, const char *signature,
                                               ani_float *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Float_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Double(ani_object object, const char *name, const char *signature,
                                              ani_double *result, ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Double_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Double_A(ani_object object, const char *name, const char *signature,
                                                ani_double *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Double_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Double_V(ani_object object, const char *name, const char *signature,
                                                ani_double *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Double_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Ref(ani_object object, const char *name, const char *signature, ani_ref *result,
                                           ...)
    {
        va_list args;
        va_start(args, result);
        ani_status status = c_api->Object_CallMethodByName_Ref_V(this, object, name, signature, result, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Ref_A(ani_object object, const char *name, const char *signature,
                                             ani_ref *result, const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Ref_A(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Ref_V(ani_object object, const char *name, const char *signature,
                                             ani_ref *result, va_list args)
    {
        return c_api->Object_CallMethodByName_Ref_V(this, object, name, signature, result, args);
    }
    ani_status Object_CallMethodByName_Void(ani_object object, const char *name, const char *signature, ...)
    {
        va_list args;
        va_start(args, signature);
        ani_status status = c_api->Object_CallMethodByName_Void_V(this, object, name, signature, args);
        va_end(args);
        return status;
    }
    ani_status Object_CallMethodByName_Void_A(ani_object object, const char *name, const char *signature,
                                              const ani_value *args)
    {
        return c_api->Object_CallMethodByName_Void_A(this, object, name, signature, args);
    }
    ani_status Object_CallMethodByName_Void_V(ani_object object, const char *name, const char *signature, va_list args)
    {
        return c_api->Object_CallMethodByName_Void_V(this, object, name, signature, args);
    }
    ani_status TupleValue_GetNumberOfItems(ani_tuple_value tuple_value, ani_size *result)
    {
        return c_api->TupleValue_GetNumberOfItems(this, tuple_value, result);
    }
    ani_status TupleValue_GetItem_Boolean(ani_tuple_value tuple_value, ani_size index, ani_boolean *result)
    {
        return c_api->TupleValue_GetItem_Boolean(this, tuple_value, index, result);
    }
    ani_status TupleValue_GetItem_Char(ani_tuple_value tuple_value, ani_size index, ani_char *result)
    {
        return c_api->TupleValue_GetItem_Char(this, tuple_value, index, result);
    }
    ani_status TupleValue_GetItem_Byte(ani_tuple_value tuple_value, ani_size index, ani_byte *result)
    {
        return c_api->TupleValue_GetItem_Byte(this, tuple_value, index, result);
    }
    ani_status TupleValue_GetItem_Short(ani_tuple_value tuple_value, ani_size index, ani_short *result)
    {
        return c_api->TupleValue_GetItem_Short(this, tuple_value, index, result);
    }
    ani_status TupleValue_GetItem_Int(ani_tuple_value tuple_value, ani_size index, ani_int *result)
    {
        return c_api->TupleValue_GetItem_Int(this, tuple_value, index, result);
    }
    ani_status TupleValue_GetItem_Long(ani_tuple_value tuple_value, ani_size index, ani_long *result)
    {
        return c_api->TupleValue_GetItem_Long(this, tuple_value, index, result);
    }
    ani_status TupleValue_GetItem_Float(ani_tuple_value tuple_value, ani_size index, ani_float *result)
    {
        return c_api->TupleValue_GetItem_Float(this, tuple_value, index, result);
    }
    ani_status TupleValue_GetItem_Double(ani_tuple_value tuple_value, ani_size index, ani_double *result)
    {
        return c_api->TupleValue_GetItem_Double(this, tuple_value, index, result);
    }
    ani_status TupleValue_GetItem_Ref(ani_tuple_value tuple_value, ani_size index, ani_ref *result)
    {
        return c_api->TupleValue_GetItem_Ref(this, tuple_value, index, result);
    }
    ani_status TupleValue_SetItem_Boolean(ani_tuple_value tuple_value, ani_size index, ani_boolean value)
    {
        return c_api->TupleValue_SetItem_Boolean(this, tuple_value, index, value);
    }
    ani_status TupleValue_SetItem_Char(ani_tuple_value tuple_value, ani_size index, ani_char value)
    {
        return c_api->TupleValue_SetItem_Char(this, tuple_value, index, value);
    }
    ani_status TupleValue_SetItem_Byte(ani_tuple_value tuple_value, ani_size index, ani_byte value)
    {
        return c_api->TupleValue_SetItem_Byte(this, tuple_value, index, value);
    }
    ani_status TupleValue_SetItem_Short(ani_tuple_value tuple_value, ani_size index, ani_short value)
    {
        return c_api->TupleValue_SetItem_Short(this, tuple_value, index, value);
    }
    ani_status TupleValue_SetItem_Int(ani_tuple_value tuple_value, ani_size index, ani_int value)
    {
        return c_api->TupleValue_SetItem_Int(this, tuple_value, index, value);
    }
    ani_status TupleValue_SetItem_Long(ani_tuple_value tuple_value, ani_size index, ani_long value)
    {
        return c_api->TupleValue_SetItem_Long(this, tuple_value, index, value);
    }
    ani_status TupleValue_SetItem_Float(ani_tuple_value tuple_value, ani_size index, ani_float value)
    {
        return c_api->TupleValue_SetItem_Float(this, tuple_value, index, value);
    }
    ani_status TupleValue_SetItem_Double(ani_tuple_value tuple_value, ani_size index, ani_double value)
    {
        return c_api->TupleValue_SetItem_Double(this, tuple_value, index, value);
    }
    ani_status TupleValue_SetItem_Ref(ani_tuple_value tuple_value, ani_size index, ani_ref value)
    {
        return c_api->TupleValue_SetItem_Ref(this, tuple_value, index, value);
    }
    ani_status GlobalReference_Create(ani_ref ref, ani_ref *result)
    {
        return c_api->GlobalReference_Create(this, ref, result);
    }
    ani_status GlobalReference_Delete(ani_ref ref)
    {
        return c_api->GlobalReference_Delete(this, ref);
    }
    ani_status WeakReference_Create(ani_ref ref, ani_wref *result)
    {
        return c_api->WeakReference_Create(this, ref, result);
    }
    ani_status WeakReference_Delete(ani_wref wref)
    {
        return c_api->WeakReference_Delete(this, wref);
    }
    ani_status WeakReference_GetReference(ani_wref wref, ani_boolean *was_released_result, ani_ref *ref_result)
    {
        return c_api->WeakReference_GetReference(this, wref, was_released_result, ref_result);
    }
    ani_status CreateArrayBuffer(size_t length, void **data_result, ani_arraybuffer *arraybuffer_result)
    {
        return c_api->CreateArrayBuffer(this, length, data_result, arraybuffer_result);
    }
    ani_status ArrayBuffer_GetInfo(ani_arraybuffer arraybuffer, void **data_result, size_t *length_result)
    {
        return c_api->ArrayBuffer_GetInfo(this, arraybuffer, data_result, length_result);
    }
    ani_status Promise_New(ani_resolver *result_resolver, ani_object *result_promise)
    {
        return c_api->Promise_New(this, result_resolver, result_promise);
    }
    ani_status PromiseResolver_Resolve(ani_resolver resolver, ani_ref resolution)
    {
        return c_api->PromiseResolver_Resolve(this, resolver, resolution);
    }
    ani_status PromiseResolver_Reject(ani_resolver resolver, ani_error rejection)
    {
        return c_api->PromiseResolver_Reject(this, resolver, rejection);
    }
    ani_status Class_BindStaticNativeMethods(ani_class cls, const ani_native_function *methods, ani_size nr_methods)
    {
        return c_api->Class_BindStaticNativeMethods(this, cls, methods, nr_methods);
    }
    ani_status Primitive_Box_Boolean(ani_boolean value, ani_object *result)
    {
        return c_api->Primitive_Box_Boolean(this, value, result);
    }
    ani_status Primitive_Unbox_Boolean(ani_object obj, ani_boolean *result)
    {
        return c_api->Primitive_Unbox_Boolean(this, obj, result);
    }
    ani_status Primitive_Box_Byte(ani_byte value, ani_object *result)
    {
        return c_api->Primitive_Box_Byte(this, value, result);
    }
    ani_status Primitive_Unbox_Byte(ani_object obj, ani_byte *result)
    {
        return c_api->Primitive_Unbox_Byte(this, obj, result);
    }
    ani_status Primitive_Box_Char(ani_char value, ani_object *result)
    {
        return c_api->Primitive_Box_Char(this, value, result);
    }
    ani_status Primitive_Unbox_Char(ani_object obj, ani_char *result)
    {
        return c_api->Primitive_Unbox_Char(this, obj, result);
    }
    ani_status Primitive_Box_Short(ani_short value, ani_object *result)
    {
        return c_api->Primitive_Box_Short(this, value, result);
    }
    ani_status Primitive_Unbox_Short(ani_object obj, ani_short *result)
    {
        return c_api->Primitive_Unbox_Short(this, obj, result);
    }
    ani_status Primitive_Box_Int(ani_int value, ani_object *result)
    {
        return c_api->Primitive_Box_Int(this, value, result);
    }
    ani_status Primitive_Unbox_Int(ani_object obj, ani_int *result)
    {
        return c_api->Primitive_Unbox_Int(this, obj, result);
    }
    ani_status Primitive_Box_Long(ani_long value, ani_object *result)
    {
        return c_api->Primitive_Box_Long(this, value, result);
    }
    ani_status Primitive_Unbox_Long(ani_object obj, ani_long *result)
    {
        return c_api->Primitive_Unbox_Long(this, obj, result);
    }
    ani_status Primitive_Box_Float(ani_float value, ani_object *result)
    {
        return c_api->Primitive_Box_Float(this, value, result);
    }
    ani_status Primitive_Unbox_Float(ani_object obj, ani_float *result)
    {
        return c_api->Primitive_Unbox_Float(this, obj, result);
    }
    ani_status Primitive_Box_Double(ani_double value, ani_object *result)
    {
        return c_api->Primitive_Box_Double(this, value, result);
    }
    ani_status Primitive_Unbox_Double(ani_object obj, ani_double *result)
    {
        return c_api->Primitive_Unbox_Double(this, obj, result);
    }
    ani_status ValueArray_GetLength(ani_valuearray array, ani_size *result)
    {
        return c_api->ValueArray_GetLength(this, array, result);
    } |  |


