# __ani_interaction_api

## Overview

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [ani_status (\*GetVersion)(ani_env *env, uint32_t *result)](#getversion) | Retrieves the version information.<br> This function retrieves the version information and stores it in the result parameter. |
| [ani_status (\*GetVM)(ani_env *env, ani_vm **result)](#getvm) | Retrieves the Virtual Machine (VM) instance.<br> This function retrieves the VM instance and stores it in the result parameter. |
| [ani_status (\*Object_New)(ani_env *env, ani_class cls, ani_method ctor, ani_object *result, ...)](#object_new) | Creates a new object of a specified class using a constructor method.<br> This function creates a new object of the given class and calls the specified constructor method with variadic arguments. |
| [ani_status (\*Object_New_A)(ani_env *env, ani_class cls, ani_method ctor, ani_object *result, const ani_value *args)](#object_new_a) | Creates a new object of a specified class using a constructor method (array-based).<br> This function creates a new object of the given class and calls the specified constructor method with arguments provided in an array. |
| [ani_status (\*Object_New_V)(ani_env *env, ani_class cls, ani_method ctor, ani_object *result, va_list args)](#object_new_v) | Creates a new object of a specified class using a constructor method (variadic arguments).<br> This function creates a new object of the given class and calls the specified constructor method with a `va_list` of arguments. |
| [ani_status (\*Object_GetType)(ani_env *env, ani_object object, ani_type *result)](#object_gettype) | Retrieves the type of a given object.<br> This function retrieves the type of the specified object. |
| [ani_status (\*Object_InstanceOf)(ani_env *env, ani_object object, ani_type type, ani_boolean *result)](#object_instanceof) | Checks if an object is an instance of a specified type.<br> This function checks whether the given object is an instance of the specified type. |
| [ani_status (\*Type_GetSuperClass)(ani_env *env, ani_type type, ani_class *result)](#type_getsuperclass) | Retrieves the superclass of a specified type.<br> This function retrieves the superclass of a given type and stores it in the result parameter. |
| [ani_status (\*Type_IsAssignableFrom)(ani_env *env, ani_type from_type, ani_type to_type, ani_boolean *result)](#type_isassignablefrom) | Determines if one type is assignable from another.<br> This function checks if a type is assignable from another and stores the result in the output parameter. |
| [ani_status (\*FindModule)(ani_env *env, const char *module_descriptor, ani_module *result)](#findmodule) | Finds a module by its descriptor.<br> This function locates a module based on its descriptor and stores it in the result parameter. |
| [ani_status (\*FindNamespace)(ani_env *env, const char *namespace_descriptor, ani_namespace *result)](#findnamespace) | Finds a namespace by its descriptor.<br> This function locates a namespace based on its descriptor and stores it in the result parameter. |
| [ani_status (\*FindClass)(ani_env *env, const char *class_descriptor, ani_class *result)](#findclass) | Finds a class by its descriptor.<br> This function locates a class based on its descriptor and stores it in the result parameter. |
| [ani_status (\*FindEnum)(ani_env *env, const char *enum_descriptor, ani_enum *result)](#findenum) | Finds an enum by its descriptor.<br> This function locates an enum based on its descriptor and stores it in the result parameter. |
| [ani_status (\*Module_FindFunction)(ani_env *env, ani_module module, const char *name, const char *signature,ani_function *result)](#module_findfunction) | Finds a function within a module by its name and signature.<br> This function locates a function within the specified module based on its name and signature. |
| [ani_status (\*Module_FindVariable)(ani_env *env, ani_module module, const char *name, ani_variable *result)](#module_findvariable) | Finds a variable within a module by its name.<br> This function locates a variable within the specified module based on its name. |
| [ani_status (\*Namespace_FindFunction)(ani_env *env, ani_namespace ns, const char *name, const char *signature,ani_function *result)](#namespace_findfunction) | Finds a function within a namespace by its name and signature.<br> This function locates a function within the specified namespace based on its name and signature. |
| [ani_status (\*Namespace_FindVariable)(ani_env *env, ani_namespace ns, const char *name, ani_variable *result)](#namespace_findvariable) | Finds a variable within a namespace by its name.<br> This function locates a variable within the specified namespace based on its name. |
| [ani_status (\*Module_BindNativeFunctions)(ani_env *env, ani_module module, const ani_native_function *functions,ani_size nr_functions)](#module_bindnativefunctions) | Binds native functions to a module.<br> This function binds an array of native functions to the specified module. |
| [ani_status (\*Namespace_BindNativeFunctions)(ani_env *env, ani_namespace ns, const ani_native_function *functions,ani_size nr_functions)](#namespace_bindnativefunctions) | Binds native functions to a namespace.<br> This function binds an array of native functions to the specified namespace. |
| [ani_status (\*Class_BindNativeMethods)(ani_env *env, ani_class cls, const ani_native_function *methods,ani_size nr_methods)](#class_bindnativemethods) | Binds native methods to a class.<br> This function binds an array of native instance methods to the specified class. |
| [ani_status (\*Reference_Delete)(ani_env *env, ani_ref lref)](#reference_delete) | Deletes a local reference.<br> This function deletes a specified local reference to free up resources. |
| [ani_status (\*EnsureEnoughReferences)(ani_env *env, ani_size nr_refs)](#ensureenoughreferences) | Ensures enough local references are available.<br> This function checks and ensures that the specified number of local references can be created. |
| [ani_status (\*CreateLocalScope)(ani_env *env, ani_size nr_refs)](#createlocalscope) | Creates a new local scope for references.<br> This function creates a local scope for references with a specified capacity. |
| [ani_status (\*DestroyLocalScope)(ani_env *env)](#destroylocalscope) | Destroys the current local scope.<br> This function destroys the current local scope and frees all references within it. |
| [ani_status (\*CreateEscapeLocalScope)(ani_env *env, ani_size nr_refs)](#createescapelocalscope) | Creates a new escape local scope.<br> This function creates a local scope for references with escape functionality, allowing objects to escape this scope. |
| [ani_status (\*DestroyEscapeLocalScope)(ani_env *env, ani_ref ref, ani_ref *result)](#destroyescapelocalscope) | Destroys the current escape local scope.<br> This function destroys the current escape local scope and allows escaping references to be retrieved. |
| [ani_status (\*ThrowError)(ani_env *env, ani_error err)](#throwerror) | Throws an error.<br> This function throws the specified error in the current environment. |
| [ani_status (\*ExistUnhandledError)(ani_env *env, ani_boolean *result)](#existunhandlederror) | Checks if there are unhandled errors.<br> This function determines if there are unhandled errors in the current environment. |
| [ani_status (\*GetUnhandledError)(ani_env *env, ani_error *result)](#getunhandlederror) | Retrieves the current unhandled error.<br> This function fetches the unhandled error in the environment. |
| [ani_status (\*ResetError)(ani_env *env)](#reseterror) | Resets the current error state.<br> This function clears the error state in the current environment. |
| [ani_status (\*DescribeError)(ani_env *env)  // NOTE: Print stacktrace for debugging?](#describeerror) | Provides a description of the current error.<br> This function prints the stack trace or other debug information for the current error. Printing is done via invocation of `console.error` provided by standard library. |
| [ani_status (\*Abort)(ani_env *env, const char *message)](#abort) | Aborts execution with a message.<br> This function terminates execution with the specified error message. |
| [ani_status (\*GetNull)(ani_env *env, ani_ref *result)](#getnull) | Retrieves a null reference.<br> This function provides a null reference in the specified result. |
| [ani_status (\*GetUndefined)(ani_env *env, ani_ref *result)](#getundefined) | Retrieves an undefined reference.<br> This function provides an undefined reference in the specified result. |
| [ani_status (\*Reference_IsNull)(ani_env *env, ani_ref ref, ani_boolean *result)](#reference_isnull) | Checks if a reference is null.<br> This function determines if the specified reference is null. |
| [ani_status (\*Reference_IsUndefined)(ani_env *env, ani_ref ref, ani_boolean *result)](#reference_isundefined) | Checks if a reference is undefined.<br> This function determines if the specified reference is undefined. |
| [ani_status (\*Reference_IsNullishValue)(ani_env *env, ani_ref ref, ani_boolean *result)](#reference_isnullishvalue) | Checks if a reference is nullish value (null or undefined).<br> This function determines if the specified reference is either null or undefined. |
| [ani_status (\*Reference_Equals)(ani_env *env, ani_ref ref0, ani_ref ref1, ani_boolean *result)](#reference_equals) | Compares two references for equality.<br> This function checks if two references are equal. |
| [ani_status (\*Reference_StrictEquals)(ani_env *env, ani_ref ref0, ani_ref ref1, ani_boolean *result)](#reference_strictequals) | Compares two references for strict equality.<br> This function checks if two references are strictly equal. |
| [ani_status (\*String_NewUTF16)(ani_env *env, const uint16_t *utf16_string, ani_size utf16_size, ani_string *result)](#string_newutf16) | Creates a new UTF-16 string.<br> This function creates a new string from the provided UTF-16 encoded data. |
| [ani_status (\*String_GetUTF16Size)(ani_env *env, ani_string string, ani_size *result)](#string_getutf16size) | Retrieves the size of a UTF-16 string.<br> This function retrieves the size (in code units) of the specified UTF-16 string. |
| [ani_status (\*String_GetUTF16)(ani_env *env, ani_string string, uint16_t *utf16_buffer, ani_size utf16_buffer_size,ani_size *result)](#string_getutf16) | Retrieves the UTF-16 encoded data of a string.<br> This function copies the UTF-16 encoded data of the string into the provided buffer. |
| [ani_status (\*String_GetUTF16SubString)(ani_env *env, ani_string string, ani_size substr_offset,ani_size substr_size, uint16_t *utf16_buffer, ani_size utf16_buffer_size,ani_size *result)](#string_getutf16substring) | Retrieves a substring of a UTF-16 string.<br> This function copies a portion of the UTF-16 string into the provided buffer. |
| [ani_status (\*String_NewUTF8)(ani_env *env, const char *utf8_string, ani_size utf8_size, ani_string *result)](#string_newutf8) | Creates a new UTF-8 string.<br> This function creates a new string from the provided UTF-8 encoded data. |
| [ani_status (\*String_GetUTF8Size)(ani_env *env, ani_string string, ani_size *result)](#string_getutf8size) | Retrieves the size of a UTF-8 string.<br> This function retrieves the size (in bytes) of the specified UTF-8 string. |
| [ani_status (\*String_GetUTF8)(ani_env *env, ani_string string, char *utf8_buffer, ani_size utf8_buffer_size,ani_size *result)](#string_getutf8) | Retrieves the UTF-8 encoded data of a string.<br> This function copies the UTF-8 encoded data of the string into the provided buffer. |
| [ani_status (\*String_GetUTF8SubString)(ani_env *env, ani_string string, ani_size substr_offset, ani_size substr_size,char *utf8_buffer, ani_size utf8_buffer_size, ani_size *result)](#string_getutf8substring) | Retrieves a substring of a UTF-8 string.<br> This function copies a portion of the UTF-8 string into the provided buffer. |
| [ani_status (\*Array_GetLength)(ani_env *env, ani_array array, ani_size *result)](#array_getlength) | Retrieves the length of an Array.<br> This function retrieves the length of the specified Array object with respect to possible override of the managed method. |
| [ani_status (\*Array_New)(ani_env *env, ani_size length, ani_ref initial_element, ani_array *result)](#array_new) | This function creates a new Array of the specified length. |
| [ani_status (\*Array_Set)(ani_env *env, ani_array array, ani_size index, ani_ref ref)](#array_set) | Sets a value to an Array.<br> This function sets a value at a given index in Array with respect to possible override of the managed method. |
| [ani_status (\*Array_Get)(ani_env *env, ani_array array, ani_size index, ani_ref *result)](#array_get) | Retrieves a value from an Array.<br> This function retrieves a value at a given index from Array with respect to possible override of the managed method. |
| [ani_status (\*Array_Push)(ani_env *env, ani_array array, ani_ref ref)](#array_push) | Push a value to the end of Array.<br> This function pushes a value to the end of Array with respect to possible override of the managed method. |
| [ani_status (\*Array_Pop)(ani_env *env, ani_array array, ani_ref *result)](#array_pop) | Retrieves the last element and erases it from array.<br> This function retrieves the last element and erases it from Array with respect to possible override of the managed method. |
| [ani_status (\*FixedArray_GetLength)(ani_env *env, ani_fixedarray array, ani_size *result)](#fixedarray_getlength) | Retrieves the length of a FixedArray.<br> This function retrieves the length of the specified FixedArray. |
| [ani_status (\*ValueArray_New_Boolean)(ani_env *env, ani_size length, ani_valuearray_boolean *result)](#valuearray_new_boolean) | Creates a new ValueArray of booleans.<br> This function creates a new ValueArray of the specified length for boolean values. |
| [ani_status (\*ValueArray_New_Char)(ani_env *env, ani_size length, ani_valuearray_char *result)](#valuearray_new_char) | Creates a new ValueArray of characters.<br> This function creates a new ValueArray of the specified length for character values. |
| [ani_status (\*ValueArray_New_Byte)(ani_env *env, ani_size length, ani_valuearray_byte *result)](#valuearray_new_byte) | Creates a new ValueArray of bytes.<br> This function creates a new ValueArray of the specified length for byte values. |
| [ani_status (\*ValueArray_New_Short)(ani_env *env, ani_size length, ani_valuearray_short *result)](#valuearray_new_short) | Creates a new ValueArray of shorts.<br> This function creates a new ValueArray of the specified length for short integer values. |
| [ani_status (\*ValueArray_New_Int)(ani_env *env, ani_size length, ani_valuearray_int *result)](#valuearray_new_int) | Creates a new ValueArray of integers.<br> This function creates a new ValueArray of the specified length for integer values. |
| [ani_status (\*ValueArray_New_Long)(ani_env *env, ani_size length, ani_valuearray_long *result)](#valuearray_new_long) | Creates a new ValueArray of long integers.<br> This function creates a new ValueArray of the specified length for long integer values. |
| [ani_status (\*ValueArray_New_Float)(ani_env *env, ani_size length, ani_valuearray_float *result)](#valuearray_new_float) | Creates a new ValueArray of floats.<br> This function creates a new ValueArray of the specified length for float values. |
| [ani_status (\*ValueArray_New_Double)(ani_env *env, ani_size length, ani_valuearray_double *result)](#valuearray_new_double) | Creates a new ValueArray of doubles.<br> This function creates a new ValueArray of the specified length for double values. |
| [ani_status (\*ValueArray_GetRegion_Boolean)(ani_env *env, ani_valuearray_boolean array, ani_size offset,ani_size length, ani_boolean *native_buffer)](#valuearray_getregion_boolean) | Retrieves a region of boolean values from a ValueArray.<br> This function retrieves a portion of the specified boolean ValueArray into a native buffer. |
| [ani_status (\*ValueArray_GetRegion_Char)(ani_env *env, ani_valuearray_char array, ani_size offset, ani_size length,ani_char *native_buffer)](#valuearray_getregion_char) | Retrieves a region of character values from a ValueArray.<br> This function retrieves a portion of the specified character ValueArray into a native buffer. |
| [ani_status (\*ValueArray_GetRegion_Byte)(ani_env *env, ani_valuearray_byte array, ani_size offset, ani_size length,ani_byte *native_buffer)](#valuearray_getregion_byte) | Retrieves a region of byte values from a ValueArray.<br> This function retrieves a portion of the specified byte ValueArray into a native buffer. |
| [ani_status (\*ValueArray_GetRegion_Short)(ani_env *env, ani_valuearray_short array, ani_size offset, ani_size length,ani_short *native_buffer)](#valuearray_getregion_short) | Retrieves a region of short values from a ValueArray.<br> This function retrieves a portion of the specified short ValueArray into a native buffer. |
| [ani_status (\*ValueArray_GetRegion_Int)(ani_env *env, ani_valuearray_int array, ani_size offset, ani_size length,ani_int *native_buffer)](#valuearray_getregion_int) | Retrieves a region of integer values from a ValueArray.<br> This function retrieves a portion of the specified integer ValueArray into a native buffer. |
| [ani_status (\*ValueArray_GetRegion_Long)(ani_env *env, ani_valuearray_long array, ani_size offset, ani_size length,ani_long *native_buffer)](#valuearray_getregion_long) | Retrieves a region of long integer values from a ValueArray.<br> This function retrieves a portion of the specified long integer ValueArray into a native buffer. |
| [ani_status (\*ValueArray_GetRegion_Float)(ani_env *env, ani_valuearray_float array, ani_size offset, ani_size length,ani_float *native_buffer)](#valuearray_getregion_float) | Retrieves a region of float values from a ValueArray.<br> This function retrieves a portion of the specified float ValueArray into a native buffer. |
| [ani_status (\*ValueArray_GetRegion_Double)(ani_env *env, ani_valuearray_double array, ani_size offset,ani_size length, ani_double *native_buffer)](#valuearray_getregion_double) | Retrieves a region of double values from a ValueArray.<br> This function retrieves a portion of the specified double ValueArray into a native buffer. |
| [ani_status (\*ValueArray_SetRegion_Boolean)(ani_env *env, ani_valuearray_boolean array, ani_size offset,ani_size length, const ani_boolean *native_buffer)](#valuearray_setregion_boolean) | Sets a region of boolean values in a ValueArray.<br> This function sets a portion of the specified boolean ValueArray using a native buffer. |
| [ani_status (\*ValueArray_SetRegion_Char)(ani_env *env, ani_valuearray_char array, ani_size offset, ani_size length,const ani_char *native_buffer)](#valuearray_setregion_char) | Sets a region of character values in a ValueArray.<br> This function sets a portion of the specified character ValueArray using a native buffer. |
| [ani_status (\*ValueArray_SetRegion_Byte)(ani_env *env, ani_valuearray_byte array, ani_size offset, ani_size length,const ani_byte *native_buffer)](#valuearray_setregion_byte) | Sets a region of byte values in a ValueArray.<br> This function sets a portion of the specified byte ValueArray using a native buffer. |
| [ani_status (\*ValueArray_SetRegion_Short)(ani_env *env, ani_valuearray_short array, ani_size offset, ani_size length,const ani_short *native_buffer)](#valuearray_setregion_short) | Sets a region of short values in a ValueArray.<br> This function sets a portion of the specified short ValueArray using a native buffer. |
| [ani_status (\*ValueArray_SetRegion_Int)(ani_env *env, ani_valuearray_int array, ani_size offset, ani_size length,const ani_int *native_buffer)](#valuearray_setregion_int) | Sets a region of integer values in a ValueArray.<br> This function sets a portion of the specified integer ValueArray using a native buffer. |
| [ani_status (\*ValueArray_SetRegion_Long)(ani_env *env, ani_valuearray_long array, ani_size offset, ani_size length,const ani_long *native_buffer)](#valuearray_setregion_long) | Sets a region of long integer values in a ValueArray.<br> This function sets a portion of the specified long integer ValueArray using a native buffer. |
| [ani_status (\*ValueArray_SetRegion_Float)(ani_env *env, ani_valuearray_float array, ani_size offset, ani_size length,const ani_float *native_buffer)](#valuearray_setregion_float) | Sets a region of float values in a ValueArray.<br> This function sets a portion of the specified float ValueArray using a native buffer. |
| [ani_status (\*ValueArray_SetRegion_Double)(ani_env *env, ani_valuearray_double array, ani_size offset,ani_size length, const ani_double *native_buffer)](#valuearray_setregion_double) | Sets a region of double values in a ValueArray.<br> This function sets a portion of the specified double ValueArray using a native buffer. |
| [ani_status (\*FixedArray_New)(ani_env *env, ani_type type, ani_size length, ani_ref initial_element,ani_fixedarray *result)](#fixedarray_new) | Creates a new FixedArray of references.<br> This function creates a new FixedArray of references, optionally initializing it with an initial_element ref. |
| [ani_status (\*FixedArray_Set)(ani_env *env, ani_fixedarray array, ani_size index, ani_ref ref)](#fixedarray_set) | Sets a reference at a specific index in a FixedArray.<br> This function sets the value of a reference at the specified index in the FixedArray. |
| [ani_status (\*FixedArray_Get)(ani_env *env, ani_fixedarray array, ani_size index, ani_ref *result)](#fixedarray_get) | Retrieves a reference from a specific index in a FixedArray.<br> This function retrieves the value of a reference at the specified index in the FixedArray. |
| [ani_status (\*Enum_GetEnumItemByName)(ani_env *env, ani_enum enm, const char *name, ani_enum_item *result)](#enum_getenumitembyname) | Retrieves an enum item by its name.<br> This function retrieves an enum item associated with the specified name. |
| [ani_status (\*Enum_GetEnumItemByIndex)(ani_env *env, ani_enum enm, ani_size index, ani_enum_item *result)](#enum_getenumitembyindex) | Retrieves an enum item by its index.<br> This function retrieves an enum item located at the specified index. |
| [ani_status (\*EnumItem_GetEnum)(ani_env *env, ani_enum_item enum_item, ani_enum *result)](#enumitem_getenum) | Retrieves the enum associated with an enum item.<br> This function retrieves the enum to which the specified enum item belongs. |
| [ani_status (\*EnumItem_GetValue_Int)(ani_env *env, ani_enum_item enum_item, ani_int *result)](#enumitem_getvalue_int) | Retrieves the integer value of an enum item.<br> This function retrieves the integer representing the value of the specified enum item. |
| [ani_status (\*EnumItem_GetValue_String)(ani_env *env, ani_enum_item enum_item, ani_string *result)](#enumitem_getvalue_string) | Retrieves the string value of an enum item.<br> This function retrieves the string representing the value of the specified enum item. |
| [ani_status (\*EnumItem_GetName)(ani_env *env, ani_enum_item enum_item, ani_string *result)](#enumitem_getname) | Retrieves the name of an enum item.<br> This function retrieves the name associated with the specified enum item. |
| [ani_status (\*EnumItem_GetIndex)(ani_env *env, ani_enum_item enum_item, ani_size *result)](#enumitem_getindex) | Retrieves the index of an enum item.<br> This function retrieves the index of the specified enum item within its enum. |
| [ani_status (\*FunctionalObject_Call)(ani_env *env, ani_fn_object fn, ani_size argc, ani_ref *argv, ani_ref *result)](#functionalobject_call) | Invokes an object of function type.<br> This function invokes an object of function type with the specified arguments. |
| [ani_status (\*Variable_SetValue_Boolean)(ani_env *env, ani_variable variable, ani_boolean value)](#variable_setvalue_boolean) | Sets a boolean value to a variable.<br> This function assigns a boolean value to the specified variable. |
| [ani_status (\*Variable_SetValue_Char)(ani_env *env, ani_variable variable, ani_char value)](#variable_setvalue_char) | Sets a character value to a variable.<br> This function assigns a character value to the specified variable. |
| [ani_status (\*Variable_SetValue_Byte)(ani_env *env, ani_variable variable, ani_byte value)](#variable_setvalue_byte) | Sets a byte value to a variable.<br> This function assigns a byte value to the specified variable. |
| [ani_status (\*Variable_SetValue_Short)(ani_env *env, ani_variable variable, ani_short value)](#variable_setvalue_short) | Sets a short value to a variable.<br> This function assigns a short integer value to the specified variable. |
| [ani_status (\*Variable_SetValue_Int)(ani_env *env, ani_variable variable, ani_int value)](#variable_setvalue_int) | Sets an integer value to a variable.<br> This function assigns an integer value to the specified variable. |
| [ani_status (\*Variable_SetValue_Long)(ani_env *env, ani_variable variable, ani_long value)](#variable_setvalue_long) | Sets a long value to a variable.<br> This function assigns a long integer value to the specified variable. |
| [ani_status (\*Variable_SetValue_Float)(ani_env *env, ani_variable variable, ani_float value)](#variable_setvalue_float) | Sets a float value to a variable.<br> This function assigns a float value to the specified variable. |
| [ani_status (\*Variable_SetValue_Double)(ani_env *env, ani_variable variable, ani_double value)](#variable_setvalue_double) | Sets a double value to a variable.<br> This function assigns a double value to the specified variable. |
| [ani_status (\*Variable_SetValue_Ref)(ani_env *env, ani_variable variable, ani_ref value)](#variable_setvalue_ref) | Sets a reference value to a variable.<br> This function assigns a reference value to the specified variable. |
| [ani_status (\*Variable_GetValue_Boolean)(ani_env *env, ani_variable variable, ani_boolean *result)](#variable_getvalue_boolean) | Retrieves a boolean value from a variable.<br> This function fetches a boolean value from the specified variable. |
| [ani_status (\*Variable_GetValue_Char)(ani_env *env, ani_variable variable, ani_char *result)](#variable_getvalue_char) | Retrieves a character value from a variable.<br> This function fetches a character value from the specified variable. |
| [ani_status (\*Variable_GetValue_Byte)(ani_env *env, ani_variable variable, ani_byte *result)](#variable_getvalue_byte) | Retrieves a byte value from a variable.<br> This function fetches a byte value from the specified variable. |
| [ani_status (\*Variable_GetValue_Short)(ani_env *env, ani_variable variable, ani_short *result)](#variable_getvalue_short) | Retrieves a short value from a variable.<br> This function fetches a short integer value from the specified variable. |
| [ani_status (\*Variable_GetValue_Int)(ani_env *env, ani_variable variable, ani_int *result)](#variable_getvalue_int) | Retrieves an integer value from a variable.<br> This function fetches an integer value from the specified variable. |
| [ani_status (\*Variable_GetValue_Long)(ani_env *env, ani_variable variable, ani_long *result)](#variable_getvalue_long) | Retrieves a long value from a variable.<br> This function fetches a long integer value from the specified variable. |
| [ani_status (\*Variable_GetValue_Float)(ani_env *env, ani_variable variable, ani_float *result)](#variable_getvalue_float) | Retrieves a float value from a variable.<br> This function fetches a float value from the specified variable. |
| [ani_status (\*Variable_GetValue_Double)(ani_env *env, ani_variable variable, ani_double *result)](#variable_getvalue_double) | Retrieves a double value from a variable.<br> This function fetches a double value from the specified variable. |
| [ani_status (\*Variable_GetValue_Ref)(ani_env *env, ani_variable variable, ani_ref *result)](#variable_getvalue_ref) | Retrieves a reference value from a variable.<br> This function fetches a reference value from the specified variable. |
| [ani_status (\*Function_Call_Boolean)(ani_env *env, ani_function fn, ani_boolean *result, ...)](#function_call_boolean) | Calls a function and retrieves a boolean result.<br> This function calls the specified function with variadic arguments and retrieves a boolean result. |
| [ani_status (\*Function_Call_Boolean_A)(ani_env *env, ani_function fn, ani_boolean *result, const ani_value *args)](#function_call_boolean_a) | Calls a function and retrieves a boolean result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a boolean result. |
| [ani_status (\*Function_Call_Boolean_V)(ani_env *env, ani_function fn, ani_boolean *result, va_list args)](#function_call_boolean_v) | Calls a function and retrieves a boolean result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a boolean result. |
| [ani_status (\*Function_Call_Char)(ani_env *env, ani_function fn, ani_char *result, ...)](#function_call_char) | Calls a function and retrieves a character result.<br> This function calls the specified function with variadic arguments and retrieves a character result. |
| [ani_status (\*Function_Call_Char_A)(ani_env *env, ani_function fn, ani_char *result, const ani_value *args)](#function_call_char_a) | Calls a function and retrieves a character result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a character result. |
| [ani_status (\*Function_Call_Char_V)(ani_env *env, ani_function fn, ani_char *result, va_list args)](#function_call_char_v) | Calls a function and retrieves a character result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a character result. |
| [ani_status (\*Function_Call_Byte)(ani_env *env, ani_function fn, ani_byte *result, ...)](#function_call_byte) | Calls a function and retrieves a byte result.<br> This function calls the specified function with variadic arguments and retrieves a byte result. |
| [ani_status (\*Function_Call_Byte_A)(ani_env *env, ani_function fn, ani_byte *result, const ani_value *args)](#function_call_byte_a) | Calls a function and retrieves a byte result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a byte result. |
| [ani_status (\*Function_Call_Byte_V)(ani_env *env, ani_function fn, ani_byte *result, va_list args)](#function_call_byte_v) | Calls a function and retrieves a byte result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a byte result. |
| [ani_status (\*Function_Call_Short)(ani_env *env, ani_function fn, ani_short *result, ...)](#function_call_short) | Calls a function and retrieves a short result.<br> This function calls the specified function with variadic arguments and retrieves a short result. |
| [ani_status (\*Function_Call_Short_A)(ani_env *env, ani_function fn, ani_short *result, const ani_value *args)](#function_call_short_a) | Calls a function and retrieves a short result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a short result. |
| [ani_status (\*Function_Call_Short_V)(ani_env *env, ani_function fn, ani_short *result, va_list args)](#function_call_short_v) | Calls a function and retrieves a short result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a short result. |
| [ani_status (\*Function_Call_Int)(ani_env *env, ani_function fn, ani_int *result, ...)](#function_call_int) | Calls a function and retrieves an integer result.<br> This function calls the specified function with variadic arguments and retrieves an integer result. |
| [ani_status (\*Function_Call_Int_A)(ani_env *env, ani_function fn, ani_int *result, const ani_value *args)](#function_call_int_a) | Calls a function and retrieves an integer result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves an integer result. |
| [ani_status (\*Function_Call_Int_V)(ani_env *env, ani_function fn, ani_int *result, va_list args)](#function_call_int_v) | Calls a function and retrieves an integer result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves an integer result. |
| [ani_status (\*Function_Call_Long)(ani_env *env, ani_function fn, ani_long *result, ...)](#function_call_long) | Calls a function and retrieves a long result.<br> This function calls the specified function with variadic arguments and retrieves a long result. |
| [ani_status (\*Function_Call_Long_A)(ani_env *env, ani_function fn, ani_long *result, const ani_value *args)](#function_call_long_a) | Calls a function and retrieves a long result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a long result. |
| [ani_status (\*Function_Call_Long_V)(ani_env *env, ani_function fn, ani_long *result, va_list args)](#function_call_long_v) | Calls a function and retrieves a long result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a long result. |
| [ani_status (\*Function_Call_Float)(ani_env *env, ani_function fn, ani_float *result, ...)](#function_call_float) | Calls a function and retrieves a float result.<br> This function calls the specified function with variadic arguments and retrieves a float result. |
| [ani_status (\*Function_Call_Float_A)(ani_env *env, ani_function fn, ani_float *result, const ani_value *args)](#function_call_float_a) | Calls a function and retrieves a float result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a float result. |
| [ani_status (\*Function_Call_Float_V)(ani_env *env, ani_function fn, ani_float *result, va_list args)](#function_call_float_v) | Calls a function and retrieves a float result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a float result. |
| [ani_status (\*Function_Call_Double)(ani_env *env, ani_function fn, ani_double *result, ...)](#function_call_double) | Calls a function and retrieves a double result.<br> This function calls the specified function with variadic arguments and retrieves a double result. |
| [ani_status (\*Function_Call_Double_A)(ani_env *env, ani_function fn, ani_double *result, const ani_value *args)](#function_call_double_a) | Calls a function and retrieves a double result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a double result. |
| [ani_status (\*Function_Call_Double_V)(ani_env *env, ani_function fn, ani_double *result, va_list args)](#function_call_double_v) | Calls a function and retrieves a double result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a double result. |
| [ani_status (\*Function_Call_Ref)(ani_env *env, ani_function fn, ani_ref *result, ...)](#function_call_ref) | Calls a function and retrieves a reference result.<br> This function calls the specified function with variadic arguments and retrieves a reference result. |
| [ani_status (\*Function_Call_Ref_A)(ani_env *env, ani_function fn, ani_ref *result, const ani_value *args)](#function_call_ref_a) | Calls a function and retrieves a reference result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a reference result. |
| [ani_status (\*Function_Call_Ref_V)(ani_env *env, ani_function fn, ani_ref *result, va_list args)](#function_call_ref_v) | Calls a function and retrieves a reference result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a reference result. |
| [ani_status (\*Function_Call_Void)(ani_env *env, ani_function fn, ...)](#function_call_void) | Calls a function without returning a result.<br> This function calls the specified function with variadic arguments and does not return a result. |
| [ani_status (\*Function_Call_Void_A)(ani_env *env, ani_function fn, const ani_value *args)](#function_call_void_a) | Calls a function without returning a result (array-based).<br> This function calls the specified function with arguments provided in an array and does not return a result. |
| [ani_status (\*Function_Call_Void_V)(ani_env *env, ani_function fn, va_list args)](#function_call_void_v) | Calls a function without returning a result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and does not return a result. |
| [ani_status (\*Class_FindField)(ani_env *env, ani_class cls, const char *name, ani_field *result)](#class_findfield) | Finds a field from by its name.<br> This function locates a field based on its name and stores it in the result parameter. |
| [ani_status (\*Class_FindStaticField)(ani_env *env, ani_class cls, const char *name, ani_static_field *result)](#class_findstaticfield) | Finds a static field by its name.<br> This function locates a static field based on its name and stores it in the result parameter. |
| [ani_status (\*Class_FindMethod)(ani_env *env, ani_class cls, const char *name, const char *signature,ani_method *result)](#class_findmethod) | Finds a method from by its name and signature.<br> This function locates a method based on its name and signature and stores it in the result parameter. |
| [ani_status (\*Class_FindStaticMethod)(ani_env *env, ani_class cls, const char *name, const char *signature,ani_static_method *result)](#class_findstaticmethod) | Finds a static method from by its name and signature.<br> This function locates a static method based on its name and signature and stores it in the result parameter. |
| [ani_status (\*Class_FindSetter)(ani_env *env, ani_class cls, const char *name, ani_method *result)](#class_findsetter) | Finds a setter method from by its name.<br> This function locates a setter method based on its name and stores it in the result parameter. |
| [ani_status (\*Class_FindGetter)(ani_env *env, ani_class cls, const char *name, ani_method *result)](#class_findgetter) | Finds a getter method from by its name.<br> This function locates a getter method based on its name and stores it in the result parameter. |
| [ani_status (\*Class_FindIndexableGetter)(ani_env *env, ani_class cls, const char *signature, ani_method *result)](#class_findindexablegetter) | Finds an indexable getter method from by its signature.<br> This function locates an indexable getter method based on its signature and stores it in the result parameter. |
| [ani_status (\*Class_FindIndexableSetter)(ani_env *env, ani_class cls, const char *signature, ani_method *result)](#class_findindexablesetter) | Finds an indexable setter method from by its signature.<br> This function locates an indexable setter method based on its signature and stores it in the result parameter. |
| [ani_status (\*Class_FindIterator)(ani_env *env, ani_class cls, ani_method *result)](#class_finditerator) | Finds an iterator method.<br> This function locates an iterator method |
| [ani_status (\*Class_GetStaticField_Boolean)(ani_env *env, ani_class cls, ani_static_field field,ani_boolean *result)](#class_getstaticfield_boolean) | Retrieves a boolean value from a static field of a class.<br> This function retrieves the boolean value of the specified static field from the given class. |
| [ani_status (\*Class_GetStaticField_Char)(ani_env *env, ani_class cls, ani_static_field field, ani_char *result)](#class_getstaticfield_char) | Retrieves a character value from a static field of a class.<br> This function retrieves the character value of the specified static field from the given class. |
| [ani_status (\*Class_GetStaticField_Byte)(ani_env *env, ani_class cls, ani_static_field field, ani_byte *result)](#class_getstaticfield_byte) | Retrieves a byte value from a static field of a class.<br> This function retrieves the byte value of the specified static field from the given class. |
| [ani_status (\*Class_GetStaticField_Short)(ani_env *env, ani_class cls, ani_static_field field, ani_short *result)](#class_getstaticfield_short) | Retrieves a short value from a static field of a class.<br> This function retrieves the short value of the specified static field from the given class. |
| [ani_status (\*Class_GetStaticField_Int)(ani_env *env, ani_class cls, ani_static_field field, ani_int *result)](#class_getstaticfield_int) | Retrieves an integer value from a static field of a class.<br> This function retrieves the integer value of the specified static field from the given class. |
| [ani_status (\*Class_GetStaticField_Long)(ani_env *env, ani_class cls, ani_static_field field, ani_long *result)](#class_getstaticfield_long) | Retrieves a long value from a static field of a class.<br> This function retrieves the long value of the specified static field from the given class. |
| [ani_status (\*Class_GetStaticField_Float)(ani_env *env, ani_class cls, ani_static_field field, ani_float *result)](#class_getstaticfield_float) | Retrieves a float value from a static field of a class.<br> This function retrieves the float value of the specified static field from the given class. |
| [ani_status (\*Class_GetStaticField_Double)(ani_env *env, ani_class cls, ani_static_field field, ani_double *result)](#class_getstaticfield_double) | Retrieves a double value from a static field of a class.<br> This function retrieves the double value of the specified static field from the given class. |
| [ani_status (\*Class_GetStaticField_Ref)(ani_env *env, ani_class cls, ani_static_field field, ani_ref *result)](#class_getstaticfield_ref) | Retrieves a reference value from a static field of a class.<br> This function retrieves the reference value of the specified static field from the given class. |
| [ani_status (\*Class_SetStaticField_Boolean)(ani_env *env, ani_class cls, ani_static_field field, ani_boolean value)](#class_setstaticfield_boolean) | Sets a boolean value to a static field of a class.<br> This function assigns a boolean value to the specified static field of the given class. |
| [ani_status (\*Class_SetStaticField_Char)(ani_env *env, ani_class cls, ani_static_field field, ani_char value)](#class_setstaticfield_char) | Sets a character value to a static field of a class.<br> This function assigns a character value to the specified static field of the given class. |
| [ani_status (\*Class_SetStaticField_Byte)(ani_env *env, ani_class cls, ani_static_field field, ani_byte value)](#class_setstaticfield_byte) | Sets a byte value to a static field of a class.<br> This function assigns a byte value to the specified static field of the given class. |
| [ani_status (\*Class_SetStaticField_Short)(ani_env *env, ani_class cls, ani_static_field field, ani_short value)](#class_setstaticfield_short) | Sets a short value to a static field of a class.<br> This function assigns a short value to the specified static field of the given class. |
| [ani_status (\*Class_SetStaticField_Int)(ani_env *env, ani_class cls, ani_static_field field, ani_int value)](#class_setstaticfield_int) | Sets an integer value to a static field of a class.<br> This function assigns an integer value to the specified static field of the given class. |
| [ani_status (\*Class_SetStaticField_Long)(ani_env *env, ani_class cls, ani_static_field field, ani_long value)](#class_setstaticfield_long) | Sets a long value to a static field of a class.<br> This function assigns a long value to the specified static field of the given class. |
| [ani_status (\*Class_SetStaticField_Float)(ani_env *env, ani_class cls, ani_static_field field, ani_float value)](#class_setstaticfield_float) | Sets a float value to a static field of a class.<br> This function assigns a float value to the specified static field of the given class. |
| [ani_status (\*Class_SetStaticField_Double)(ani_env *env, ani_class cls, ani_static_field field, ani_double value)](#class_setstaticfield_double) | Sets a double value to a static field of a class.<br> This function assigns a double value to the specified static field of the given class. |
| [ani_status (\*Class_SetStaticField_Ref)(ani_env *env, ani_class cls, ani_static_field field, ani_ref value)](#class_setstaticfield_ref) | Sets a reference value to a static field of a class.<br> This function assigns a reference value to the specified static field of the given class. |
| [ani_status (\*Class_GetStaticFieldByName_Boolean)(ani_env *env, ani_class cls, const char *name,ani_boolean *result)](#class_getstaticfieldbyname_boolean) | Retrieves a boolean value from a static field of a class by its name.<br> This function retrieves the boolean value of the specified static field from the given class by its name. |
| [ani_status (\*Class_GetStaticFieldByName_Char)(ani_env *env, ani_class cls, const char *name, ani_char *result)](#class_getstaticfieldbyname_char) | Retrieves a character value from a static field of a class by its name.<br> This function retrieves the character value of the specified static field from the given class by its name. |
| [ani_status (\*Class_GetStaticFieldByName_Byte)(ani_env *env, ani_class cls, const char *name, ani_byte *result)](#class_getstaticfieldbyname_byte) | Retrieves a byte value from a static field of a class by its name.<br> This function retrieves the byte value of the specified static field from the given class by its name. |
| [ani_status (\*Class_GetStaticFieldByName_Short)(ani_env *env, ani_class cls, const char *name, ani_short *result)](#class_getstaticfieldbyname_short) | Retrieves a short value from a static field of a class by its name.<br> This function retrieves the short value of the specified static field from the given class by its name. |
| [ani_status (\*Class_GetStaticFieldByName_Int)(ani_env *env, ani_class cls, const char *name, ani_int *result)](#class_getstaticfieldbyname_int) | Retrieves an integer value from a static field of a class by its name.<br> This function retrieves the integer value of the specified static field from the given class by its name. |
| [ani_status (\*Class_GetStaticFieldByName_Long)(ani_env *env, ani_class cls, const char *name, ani_long *result)](#class_getstaticfieldbyname_long) | Retrieves a long value from a static field of a class by its name.<br> This function retrieves the long value of the specified static field from the given class by its name. |
| [ani_status (\*Class_GetStaticFieldByName_Float)(ani_env *env, ani_class cls, const char *name, ani_float *result)](#class_getstaticfieldbyname_float) | Retrieves a float value from a static field of a class by its name.<br> This function retrieves the float value of the specified static field from the given class by its name. |
| [ani_status (\*Class_GetStaticFieldByName_Double)(ani_env *env, ani_class cls, const char *name, ani_double *result)](#class_getstaticfieldbyname_double) | Retrieves a double value from a static field of a class by its name.<br> This function retrieves the double value of the specified static field from the given class by its name. |
| [ani_status (\*Class_GetStaticFieldByName_Ref)(ani_env *env, ani_class cls, const char *name, ani_ref *result)](#class_getstaticfieldbyname_ref) | Retrieves a reference value from a static field of a class by its name.<br> This function retrieves the reference value of the specified static field from the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Boolean)(ani_env *env, ani_class cls, const char *name, ani_boolean value)](#class_setstaticfieldbyname_boolean) | Sets a boolean value to a static field of a class by its name.<br> This function assigns a boolean value to the specified static field of the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Char)(ani_env *env, ani_class cls, const char *name, ani_char value)](#class_setstaticfieldbyname_char) | Sets a character value to a static field of a class by its name.<br> This function assigns a character value to the specified static field of the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Byte)(ani_env *env, ani_class cls, const char *name, ani_byte value)](#class_setstaticfieldbyname_byte) | Sets a byte value to a static field of a class by its name.<br> This function assigns a byte value to the specified static field of the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Short)(ani_env *env, ani_class cls, const char *name, ani_short value)](#class_setstaticfieldbyname_short) | Sets a short value to a static field of a class by its name.<br> This function assigns a short value to the specified static field of the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Int)(ani_env *env, ani_class cls, const char *name, ani_int value)](#class_setstaticfieldbyname_int) | Sets an integer value to a static field of a class by its name.<br> This function assigns an integer value to the specified static field of the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Long)(ani_env *env, ani_class cls, const char *name, ani_long value)](#class_setstaticfieldbyname_long) | Sets a long value to a static field of a class by its name.<br> This function assigns a long value to the specified static field of the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Float)(ani_env *env, ani_class cls, const char *name, ani_float value)](#class_setstaticfieldbyname_float) | Sets a float value to a static field of a class by its name.<br> This function assigns a float value to the specified static field of the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Double)(ani_env *env, ani_class cls, const char *name, ani_double value)](#class_setstaticfieldbyname_double) | Sets a double value to a static field of a class by its name.<br> This function assigns a double value to the specified static field of the given class by its name. |
| [ani_status (\*Class_SetStaticFieldByName_Ref)(ani_env *env, ani_class cls, const char *name, ani_ref value)](#class_setstaticfieldbyname_ref) | Sets a reference value to a static field of a class by its name.<br> This function assigns a reference value to the specified static field of the given class by its name. |
| [ani_status (\*Class_CallStaticMethod_Boolean)(ani_env *env, ani_class cls, ani_static_method method,ani_boolean *result, ...)](#class_callstaticmethod_boolean) | Calls a static method with a boolean return type.<br> This function calls the specified static method of a class and retrieves a boolean result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Boolean_A)(ani_env *env, ani_class cls, ani_static_method method,ani_boolean *result, const ani_value *args)](#class_callstaticmethod_boolean_a) | Calls a static method with a boolean return type (array-based).<br> This function calls the specified static method of a class and retrieves a boolean result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Boolean_V)(ani_env *env, ani_class cls, ani_static_method method,ani_boolean *result, va_list args)](#class_callstaticmethod_boolean_v) | Calls a static method with a boolean return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a boolean result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Char)(ani_env *env, ani_class cls, ani_static_method method, ani_char *result,...)](#class_callstaticmethod_char) | Calls a static method with a character return type.<br> This function calls the specified static method of a class and retrieves a character result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Char_A)(ani_env *env, ani_class cls, ani_static_method method, ani_char *result,const ani_value *args)](#class_callstaticmethod_char_a) | Calls a static method with a character return type (array-based).<br> This function calls the specified static method of a class and retrieves a character result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Char_V)(ani_env *env, ani_class cls, ani_static_method method, ani_char *result,va_list args)](#class_callstaticmethod_char_v) | Calls a static method with a character return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a character result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Byte)(ani_env *env, ani_class cls, ani_static_method method, ani_byte *result,...)](#class_callstaticmethod_byte) | Calls a static method with a byte return type.<br> This function calls the specified static method of a class and retrieves a byte result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Byte_A)(ani_env *env, ani_class cls, ani_static_method method, ani_byte *result,const ani_value *args)](#class_callstaticmethod_byte_a) | Calls a static method with a byte return type (array-based).<br> This function calls the specified static method of a class and retrieves a byte result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Byte_V)(ani_env *env, ani_class cls, ani_static_method method, ani_byte *result,va_list args)](#class_callstaticmethod_byte_v) | Calls a static method with a byte return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a byte result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Short)(ani_env *env, ani_class cls, ani_static_method method, ani_short *result,...)](#class_callstaticmethod_short) | Calls a static method with a short return type.<br> This function calls the specified static method of a class and retrieves a short result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Short_A)(ani_env *env, ani_class cls, ani_static_method method,ani_short *result, const ani_value *args)](#class_callstaticmethod_short_a) | Calls a static method with a short return type (array-based).<br> This function calls the specified static method of a class and retrieves a short result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Short_V)(ani_env *env, ani_class cls, ani_static_method method,ani_short *result, va_list args)](#class_callstaticmethod_short_v) | Calls a static method with a short return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a short result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Int)(ani_env *env, ani_class cls, ani_static_method method, ani_int *result,...)](#class_callstaticmethod_int) | Calls a static method with an integer return type.<br> This function calls the specified static method of a class and retrieves an integer result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Int_A)(ani_env *env, ani_class cls, ani_static_method method, ani_int *result,const ani_value *args)](#class_callstaticmethod_int_a) | Calls a static method with an integer return type (array-based).<br> This function calls the specified static method of a class and retrieves an integer result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Int_V)(ani_env *env, ani_class cls, ani_static_method method, ani_int *result,va_list args)](#class_callstaticmethod_int_v) | Calls a static method with an integer return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves an integer result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Long)(ani_env *env, ani_class cls, ani_static_method method, ani_long *result,...)](#class_callstaticmethod_long) | Calls a static method with a long return type.<br> This function calls the specified static method of a class and retrieves a long result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Long_A)(ani_env *env, ani_class cls, ani_static_method method, ani_long *result,const ani_value *args)](#class_callstaticmethod_long_a) | Calls a static method with a long return type (array-based).<br> This function calls the specified static method of a class and retrieves a long result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Long_V)(ani_env *env, ani_class cls, ani_static_method method, ani_long *result,va_list args)](#class_callstaticmethod_long_v) | Calls a static method with a long return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a long result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Float)(ani_env *env, ani_class cls, ani_static_method method, ani_float *result,...)](#class_callstaticmethod_float) | Calls a static method with a float return type.<br> This function calls the specified static method of a class and retrieves a float result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Float_A)(ani_env *env, ani_class cls, ani_static_method method,ani_float *result, const ani_value *args)](#class_callstaticmethod_float_a) | Calls a static method with a float return type (array-based).<br> This function calls the specified static method of a class and retrieves a float result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Float_V)(ani_env *env, ani_class cls, ani_static_method method,ani_float *result, va_list args)](#class_callstaticmethod_float_v) | Calls a static method with a float return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a float result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Double)(ani_env *env, ani_class cls, ani_static_method method,ani_double *result, ...)](#class_callstaticmethod_double) | Calls a static method with a double return type.<br> This function calls the specified static method of a class and retrieves a double result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Double_A)(ani_env *env, ani_class cls, ani_static_method method,ani_double *result, const ani_value *args)](#class_callstaticmethod_double_a) | Calls a static method with a double return type (array-based).<br> This function calls the specified static method of a class and retrieves a double result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Double_V)(ani_env *env, ani_class cls, ani_static_method method,ani_double *result, va_list args)](#class_callstaticmethod_double_v) | Calls a static method with a double return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a double result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Ref)(ani_env *env, ani_class cls, ani_static_method method, ani_ref *result,...)](#class_callstaticmethod_ref) | Calls a static method with a reference return type.<br> This function calls the specified static method of a class and retrieves a reference result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethod_Ref_A)(ani_env *env, ani_class cls, ani_static_method method, ani_ref *result,const ani_value *args)](#class_callstaticmethod_ref_a) | Calls a static method with a reference return type (array-based).<br> This function calls the specified static method of a class and retrieves a reference result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethod_Ref_V)(ani_env *env, ani_class cls, ani_static_method method, ani_ref *result,va_list args)](#class_callstaticmethod_ref_v) | Calls a static method with a reference return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a reference result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethod_Void)(ani_env *env, ani_class cls, ani_static_method method, ...)](#class_callstaticmethod_void) | Calls a static method with no return value.<br> This function calls the specified static method of a class using variadic arguments. The method does not return a value. |
| [ani_status (\*Class_CallStaticMethod_Void_A)(ani_env *env, ani_class cls, ani_static_method method,const ani_value *args)](#class_callstaticmethod_void_a) | Calls a static method with no return value (array-based).<br> This function calls the specified static method of a class using arguments from an array. The method does not return a value. |
| [ani_status (\*Class_CallStaticMethod_Void_V)(ani_env *env, ani_class cls, ani_static_method method, va_list args)](#class_callstaticmethod_void_v) | Calls a static method with no return value (variadic arguments).<br> This function calls the specified static method of a class using a `va_list`. The method does not return a value. |
| [ani_status (\*Class_CallStaticMethodByName_Boolean)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_boolean *result, ...)](#class_callstaticmethodbyname_boolean) | Calls a static method by name with a boolean return type.<br> This function calls the specified static method of a class by its name and retrieves a boolean result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Boolean_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_boolean *result,const ani_value *args)](#class_callstaticmethodbyname_boolean_a) | Calls a static method by name with a boolean return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a boolean result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Boolean_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_boolean *result, va_list args)](#class_callstaticmethodbyname_boolean_v) | Calls a static method by name with a boolean return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a boolean result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Char)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_char *result, ...)](#class_callstaticmethodbyname_char) | Calls a static method by name with a char return type.<br> This function calls the specified static method of a class by its name and retrieves a char result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Char_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_char *result, const ani_value *args)](#class_callstaticmethodbyname_char_a) | Calls a static method by name with a char return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a char result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Char_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_char *result, va_list args)](#class_callstaticmethodbyname_char_v) | Calls a static method by name with a char return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a char result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Byte)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_byte *result, ...)](#class_callstaticmethodbyname_byte) | Calls a static method by name with a byte return type.<br> This function calls the specified static method of a class by its name and retrieves a byte result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Byte_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_byte *result, const ani_value *args)](#class_callstaticmethodbyname_byte_a) | Calls a static method by name with a byte return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a byte result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Byte_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_byte *result, va_list args)](#class_callstaticmethodbyname_byte_v) | Calls a static method by name with a byte return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a byte result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Short)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_short *result, ...)](#class_callstaticmethodbyname_short) | Calls a static method by name with a short return type.<br> This function calls the specified static method of a class by its name and retrieves a short result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Short_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_short *result, const ani_value *args)](#class_callstaticmethodbyname_short_a) | Calls a static method by name with a short return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a short result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Short_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_short *result, va_list args)](#class_callstaticmethodbyname_short_v) | Calls a static method by name with a short return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a short result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Int)(ani_env *env, ani_class cls, const char *name, const char *signature,ani_int *result, ...)](#class_callstaticmethodbyname_int) | Calls a static method by name with a integer return type.<br> This function calls the specified static method of a class by its name and retrieves a integer result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Int_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_int *result, const ani_value *args)](#class_callstaticmethodbyname_int_a) | Calls a static method by name with a integer return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a integer result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Int_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_int *result, va_list args)](#class_callstaticmethodbyname_int_v) | Calls a static method by name with a integer return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a integer result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Long)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_long *result, ...)](#class_callstaticmethodbyname_long) | Calls a static method by name with a long return type.<br> This function calls the specified static method of a class by its name and retrieves a long result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Long_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_long *result, const ani_value *args)](#class_callstaticmethodbyname_long_a) | Calls a static method by name with a long return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a long result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Long_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_long *result, va_list args)](#class_callstaticmethodbyname_long_v) | Calls a static method by name with a long return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a long result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Float)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_float *result, ...)](#class_callstaticmethodbyname_float) | Calls a static method by name with a float return type.<br> This function calls the specified static method of a class by its name and retrieves a float result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Float_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_float *result, const ani_value *args)](#class_callstaticmethodbyname_float_a) | Calls a static method by name with a float return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a float result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Float_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_float *result, va_list args)](#class_callstaticmethodbyname_float_v) | Calls a static method by name with a float return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a float result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Double)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_double *result, ...)](#class_callstaticmethodbyname_double) | Calls a static method by name with a double return type.<br> This function calls the specified static method of a class by its name and retrieves a double result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Double_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_double *result,const ani_value *args)](#class_callstaticmethodbyname_double_a) | Calls a static method by name with a double return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a double result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Double_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_double *result, va_list args)](#class_callstaticmethodbyname_double_v) | Calls a static method by name with a double return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a double result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Ref)(ani_env *env, ani_class cls, const char *name, const char *signature,ani_ref *result, ...)](#class_callstaticmethodbyname_ref) | Calls a static method by name with a reference return type.<br> This function calls the specified static method of a class by its name and retrieves a reference result using variadic arguments. |
| [ani_status (\*Class_CallStaticMethodByName_Ref_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_ref *result, const ani_value *args)](#class_callstaticmethodbyname_ref_a) | Calls a static method by name with a reference return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a reference result using arguments from an array. |
| [ani_status (\*Class_CallStaticMethodByName_Ref_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_ref *result, va_list args)](#class_callstaticmethodbyname_ref_v) | Calls a static method by name with a reference return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a reference result using a `va_list`. |
| [ani_status (\*Class_CallStaticMethodByName_Void)(ani_env *env, ani_class cls, const char *name,const char *signature, ...)](#class_callstaticmethodbyname_void) | Calls a static method by name with no return value.<br> This function calls the specified static method of a class by its name using variadic arguments. The method does not return a value. |
| [ani_status (\*Class_CallStaticMethodByName_Void_A)(ani_env *env, ani_class cls, const char *name,const char *signature, const ani_value *args)](#class_callstaticmethodbyname_void_a) | Calls a static method by name with no return value (array-based).<br> This function calls the specified static method of a class by its name using arguments from an array. The method does not return a value. |
| [ani_status (\*Class_CallStaticMethodByName_Void_V)(ani_env *env, ani_class cls, const char *name,const char *signature, va_list args)](#class_callstaticmethodbyname_void_v) | Calls a static method by name with no return value (variadic arguments).<br> This function calls the specified static method of a class by its name using a `va_list`. The method does not return a value. |
| [ani_status (\*Object_GetField_Boolean)(ani_env *env, ani_object object, ani_field field, ani_boolean *result)](#object_getfield_boolean) | Retrieves a boolean value from a field of an object.<br> This function retrieves the boolean value of the specified field from the given object. |
| [ani_status (\*Object_GetField_Char)(ani_env *env, ani_object object, ani_field field, ani_char *result)](#object_getfield_char) | Retrieves a char value from a field of an object.<br> This function retrieves the char value of the specified field from the given object. |
| [ani_status (\*Object_GetField_Byte)(ani_env *env, ani_object object, ani_field field, ani_byte *result)](#object_getfield_byte) | Retrieves a byte value from a field of an object.<br> This function retrieves the byte value of the specified field from the given object. |
| [ani_status (\*Object_GetField_Short)(ani_env *env, ani_object object, ani_field field, ani_short *result)](#object_getfield_short) | Retrieves a short value from a field of an object.<br> This function retrieves the short value of the specified field from the given object. |
| [ani_status (\*Object_GetField_Int)(ani_env *env, ani_object object, ani_field field, ani_int *result)](#object_getfield_int) | Retrieves a integer value from a field of an object.<br> This function retrieves the integer value of the specified field from the given object. |
| [ani_status (\*Object_GetField_Long)(ani_env *env, ani_object object, ani_field field, ani_long *result)](#object_getfield_long) | Retrieves a long value from a field of an object.<br> This function retrieves the long value of the specified field from the given object. |
| [ani_status (\*Object_GetField_Float)(ani_env *env, ani_object object, ani_field field, ani_float *result)](#object_getfield_float) | Retrieves a float value from a field of an object.<br> This function retrieves the float value of the specified field from the given object. |
| [ani_status (\*Object_GetField_Double)(ani_env *env, ani_object object, ani_field field, ani_double *result)](#object_getfield_double) | Retrieves a double value from a field of an object.<br> This function retrieves the double value of the specified field from the given object. |
| [ani_status (\*Object_GetField_Ref)(ani_env *env, ani_object object, ani_field field, ani_ref *result)](#object_getfield_ref) | Retrieves a reference value from a field of an object.<br> This function retrieves the reference value of the specified field from the given object. |
| [ani_status (\*Object_SetField_Boolean)(ani_env *env, ani_object object, ani_field field, ani_boolean value)](#object_setfield_boolean) | Sets a boolean value to a field of an object.<br> This function assigns a boolean value to the specified field of the given object. |
| [ani_status (\*Object_SetField_Char)(ani_env *env, ani_object object, ani_field field, ani_char value)](#object_setfield_char) | Sets a char value to a field of an object.<br> This function assigns a char value to the specified field of the given object. |
| [ani_status (\*Object_SetField_Byte)(ani_env *env, ani_object object, ani_field field, ani_byte value)](#object_setfield_byte) | Sets a byte value to a field of an object.<br> This function assigns a byte value to the specified field of the given object. |
| [ani_status (\*Object_SetField_Short)(ani_env *env, ani_object object, ani_field field, ani_short value)](#object_setfield_short) | Sets a short value to a field of an object.<br> This function assigns a short value to the specified field of the given object. |
| [ani_status (\*Object_SetField_Int)(ani_env *env, ani_object object, ani_field field, ani_int value)](#object_setfield_int) | Sets a integer value to a field of an object.<br> This function assigns a integer value to the specified field of the given object. |
| [ani_status (\*Object_SetField_Long)(ani_env *env, ani_object object, ani_field field, ani_long value)](#object_setfield_long) | Sets a long value to a field of an object.<br> This function assigns a long value to the specified field of the given object. |
| [ani_status (\*Object_SetField_Float)(ani_env *env, ani_object object, ani_field field, ani_float value)](#object_setfield_float) | Sets a float value to a field of an object.<br> This function assigns a float value to the specified field of the given object. |
| [ani_status (\*Object_SetField_Double)(ani_env *env, ani_object object, ani_field field, ani_double value)](#object_setfield_double) | Sets a double value to a field of an object.<br> This function assigns a double value to the specified field of the given object. |
| [ani_status (\*Object_SetField_Ref)(ani_env *env, ani_object object, ani_field field, ani_ref value)](#object_setfield_ref) | Sets a reference value to a field of an object.<br> This function assigns a reference value to the specified field of the given object. |
| [ani_status (\*Object_GetFieldByName_Boolean)(ani_env *env, ani_object object, const char *name, ani_boolean *result)](#object_getfieldbyname_boolean) | Retrieves a boolean value from a field of an object by its name.<br> This function retrieves the boolean value of the specified field from the given object by its name. |
| [ani_status (\*Object_GetFieldByName_Char)(ani_env *env, ani_object object, const char *name, ani_char *result)](#object_getfieldbyname_char) | Retrieves a char value from a field of an object by its name.<br> This function retrieves the char value of the specified field from the given object by its name. |
| [ani_status (\*Object_GetFieldByName_Byte)(ani_env *env, ani_object object, const char *name, ani_byte *result)](#object_getfieldbyname_byte) | Retrieves a byte value from a field of an object by its name.<br> This function retrieves the byte value of the specified field from the given object by its name. |
| [ani_status (\*Object_GetFieldByName_Short)(ani_env *env, ani_object object, const char *name, ani_short *result)](#object_getfieldbyname_short) | Retrieves a short value from a field of an object by its name.<br> This function retrieves the short value of the specified field from the given object by its name. |
| [ani_status (\*Object_GetFieldByName_Int)(ani_env *env, ani_object object, const char *name, ani_int *result)](#object_getfieldbyname_int) | Retrieves a integer value from a field of an object by its name.<br> This function retrieves the integer value of the specified field from the given object by its name. |
| [ani_status (\*Object_GetFieldByName_Long)(ani_env *env, ani_object object, const char *name, ani_long *result)](#object_getfieldbyname_long) | Retrieves a long value from a field of an object by its name.<br> This function retrieves the long value of the specified field from the given object by its name. |
| [ani_status (\*Object_GetFieldByName_Float)(ani_env *env, ani_object object, const char *name, ani_float *result)](#object_getfieldbyname_float) | Retrieves a float value from a field of an object by its name.<br> This function retrieves the float value of the specified field from the given object by its name. |
| [ani_status (\*Object_GetFieldByName_Double)(ani_env *env, ani_object object, const char *name, ani_double *result)](#object_getfieldbyname_double) | Retrieves a double value from a field of an object by its name.<br> This function retrieves the double value of the specified field from the given object by its name. |
| [ani_status (\*Object_GetFieldByName_Ref)(ani_env *env, ani_object object, const char *name, ani_ref *result)](#object_getfieldbyname_ref) | Retrieves a reference value from a field of an object by its name.<br> This function retrieves the reference value of the specified field from the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Boolean)(ani_env *env, ani_object object, const char *name, ani_boolean value)](#object_setfieldbyname_boolean) | Sets a boolean value to a field of an object by its name.<br> This function assigns a boolean value to the specified field of the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Char)(ani_env *env, ani_object object, const char *name, ani_char value)](#object_setfieldbyname_char) | Sets a char value to a field of an object by its name.<br> This function assigns a char value to the specified field of the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Byte)(ani_env *env, ani_object object, const char *name, ani_byte value)](#object_setfieldbyname_byte) | Sets a byte value to a field of an object by its name.<br> This function assigns a byte value to the specified field of the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Short)(ani_env *env, ani_object object, const char *name, ani_short value)](#object_setfieldbyname_short) | Sets a short value to a field of an object by its name.<br> This function assigns a short value to the specified field of the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Int)(ani_env *env, ani_object object, const char *name, ani_int value)](#object_setfieldbyname_int) | Sets a integer value to a field of an object by its name.<br> This function assigns a integer value to the specified field of the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Long)(ani_env *env, ani_object object, const char *name, ani_long value)](#object_setfieldbyname_long) | Sets a long value to a field of an object by its name.<br> This function assigns a long value to the specified field of the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Float)(ani_env *env, ani_object object, const char *name, ani_float value)](#object_setfieldbyname_float) | Sets a float value to a field of an object by its name.<br> This function assigns a float value to the specified field of the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Double)(ani_env *env, ani_object object, const char *name, ani_double value)](#object_setfieldbyname_double) | Sets a double value to a field of an object by its name.<br> This function assigns a double value to the specified field of the given object by its name. |
| [ani_status (\*Object_SetFieldByName_Ref)(ani_env *env, ani_object object, const char *name, ani_ref value)](#object_setfieldbyname_ref) | Sets a reference value to a field of an object by its name.<br> This function assigns a reference value to the specified field of the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Boolean)(ani_env *env, ani_object object, const char *name,ani_boolean *result)](#object_getpropertybyname_boolean) | Retrieves a boolean value from a property of an object by its name.<br> This function retrieves the boolean value of the specified property from the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Char)(ani_env *env, ani_object object, const char *name, ani_char *result)](#object_getpropertybyname_char) | Retrieves a char value from a property of an object by its name.<br> This function retrieves the char value of the specified property from the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Byte)(ani_env *env, ani_object object, const char *name, ani_byte *result)](#object_getpropertybyname_byte) | Retrieves a byte value from a property of an object by its name.<br> This function retrieves the byte value of the specified property from the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Short)(ani_env *env, ani_object object, const char *name, ani_short *result)](#object_getpropertybyname_short) | Retrieves a short value from a property of an object by its name.<br> This function retrieves the short value of the specified property from the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Int)(ani_env *env, ani_object object, const char *name, ani_int *result)](#object_getpropertybyname_int) | Retrieves a integer value from a property of an object by its name.<br> This function retrieves the integer value of the specified property from the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Long)(ani_env *env, ani_object object, const char *name, ani_long *result)](#object_getpropertybyname_long) | Retrieves a long value from a property of an object by its name.<br> This function retrieves the long value of the specified property from the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Float)(ani_env *env, ani_object object, const char *name, ani_float *result)](#object_getpropertybyname_float) | Retrieves a float value from a property of an object by its name.<br> This function retrieves the float value of the specified property from the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Double)(ani_env *env, ani_object object, const char *name,ani_double *result)](#object_getpropertybyname_double) | Retrieves a double value from a property of an object by its name.<br> This function retrieves the double value of the specified property from the given object by its name. |
| [ani_status (\*Object_GetPropertyByName_Ref)(ani_env *env, ani_object object, const char *name, ani_ref *result)](#object_getpropertybyname_ref) | Retrieves a reference value from a property of an object by its name.<br> This function retrieves the reference value of the specified property from the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Boolean)(ani_env *env, ani_object object, const char *name,ani_boolean value)](#object_setpropertybyname_boolean) | Sets a boolean value to a property of an object by its name.<br> This function assigns a boolean value to the specified property of the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Char)(ani_env *env, ani_object object, const char *name, ani_char value)](#object_setpropertybyname_char) | Sets a char value to a property of an object by its name.<br> This function assigns a char value to the specified property of the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Byte)(ani_env *env, ani_object object, const char *name, ani_byte value)](#object_setpropertybyname_byte) | Sets a byte value to a property of an object by its name.<br> This function assigns a byte value to the specified property of the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Short)(ani_env *env, ani_object object, const char *name, ani_short value)](#object_setpropertybyname_short) | Sets a short value to a property of an object by its name.<br> This function assigns a short value to the specified property of the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Int)(ani_env *env, ani_object object, const char *name, ani_int value)](#object_setpropertybyname_int) | Sets a integer value to a property of an object by its name.<br> This function assigns a integer value to the specified property of the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Long)(ani_env *env, ani_object object, const char *name, ani_long value)](#object_setpropertybyname_long) | Sets a long value to a property of an object by its name.<br> This function assigns a long value to the specified property of the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Float)(ani_env *env, ani_object object, const char *name, ani_float value)](#object_setpropertybyname_float) | Sets a float value to a property of an object by its name.<br> This function assigns a float value to the specified property of the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Double)(ani_env *env, ani_object object, const char *name, ani_double value)](#object_setpropertybyname_double) | Sets a double value to a property of an object by its name.<br> This function assigns a double value to the specified property of the given object by its name. |
| [ani_status (\*Object_SetPropertyByName_Ref)(ani_env *env, ani_object object, const char *name, ani_ref value)](#object_setpropertybyname_ref) | Sets a reference value to a property of an object by its name.<br> This function assigns a reference value to the specified property of the given object by its name. |
| [ani_status (\*Object_CallMethod_Boolean)(ani_env *env, ani_object object, ani_method method, ani_boolean *result,...)](#object_callmethod_boolean) | Calls a method on an object and retrieves a boolean return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a boolean result. |
| [ani_status (\*Object_CallMethod_Boolean_A)(ani_env *env, ani_object object, ani_method method, ani_boolean *result,const ani_value *args)](#object_callmethod_boolean_a) | Calls a method on an object and retrieves a boolean return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a boolean result. |
| [ani_status (\*Object_CallMethod_Boolean_V)(ani_env *env, ani_object object, ani_method method, ani_boolean *result,va_list args)](#object_callmethod_boolean_v) | Calls a method on an object and retrieves a boolean return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a boolean result. |
| [ani_status (\*Object_CallMethod_Char)(ani_env *env, ani_object object, ani_method method, ani_char *result, ...)](#object_callmethod_char) | Calls a method on an object and retrieves a char return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a char result. |
| [ani_status (\*Object_CallMethod_Char_A)(ani_env *env, ani_object object, ani_method method, ani_char *result,const ani_value *args)](#object_callmethod_char_a) | Calls a method on an object and retrieves a char return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a char result. |
| [ani_status (\*Object_CallMethod_Char_V)(ani_env *env, ani_object object, ani_method method, ani_char *result,va_list args)](#object_callmethod_char_v) | Calls a method on an object and retrieves a char return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a char result. |
| [ani_status (\*Object_CallMethod_Byte)(ani_env *env, ani_object object, ani_method method, ani_byte *result, ...)](#object_callmethod_byte) | Calls a method on an object and retrieves a byte return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a byte result. |
| [ani_status (\*Object_CallMethod_Byte_A)(ani_env *env, ani_object object, ani_method method, ani_byte *result,const ani_value *args)](#object_callmethod_byte_a) | Calls a method on an object and retrieves a byte return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a byte result. |
| [ani_status (\*Object_CallMethod_Byte_V)(ani_env *env, ani_object object, ani_method method, ani_byte *result,va_list args)](#object_callmethod_byte_v) | Calls a method on an object and retrieves a byte return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a byte result. |
| [ani_status (\*Object_CallMethod_Short)(ani_env *env, ani_object object, ani_method method, ani_short *result, ...)](#object_callmethod_short) | Calls a method on an object and retrieves a short return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a short result. |
| [ani_status (\*Object_CallMethod_Short_A)(ani_env *env, ani_object object, ani_method method, ani_short *result,const ani_value *args)](#object_callmethod_short_a) | Calls a method on an object and retrieves a short return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a short result. |
| [ani_status (\*Object_CallMethod_Short_V)(ani_env *env, ani_object object, ani_method method, ani_short *result,va_list args)](#object_callmethod_short_v) | Calls a method on an object and retrieves a short return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a short result. |
| [ani_status (\*Object_CallMethod_Int)(ani_env *env, ani_object object, ani_method method, ani_int *result, ...)](#object_callmethod_int) | Calls a method on an object and retrieves a integer return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a integer result. |
| [ani_status (\*Object_CallMethod_Int_A)(ani_env *env, ani_object object, ani_method method, ani_int *result,const ani_value *args)](#object_callmethod_int_a) | Calls a method on an object and retrieves a integer return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a integer result. |
| [ani_status (\*Object_CallMethod_Int_V)(ani_env *env, ani_object object, ani_method method, ani_int *result,va_list args)](#object_callmethod_int_v) | Calls a method on an object and retrieves a integer return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a integer result. |
| [ani_status (\*Object_CallMethod_Long)(ani_env *env, ani_object object, ani_method method, ani_long *result, ...)](#object_callmethod_long) | Calls a method on an object and retrieves a long return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a long result. |
| [ani_status (\*Object_CallMethod_Long_A)(ani_env *env, ani_object object, ani_method method, ani_long *result,const ani_value *args)](#object_callmethod_long_a) | Calls a method on an object and retrieves a long return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a long result. |
| [ani_status (\*Object_CallMethod_Long_V)(ani_env *env, ani_object object, ani_method method, ani_long *result,va_list args)](#object_callmethod_long_v) | Calls a method on an object and retrieves a long return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a long result. |
| [ani_status (\*Object_CallMethod_Float)(ani_env *env, ani_object object, ani_method method, ani_float *result, ...)](#object_callmethod_float) | Calls a method on an object and retrieves a float return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a float result. |
| [ani_status (\*Object_CallMethod_Float_A)(ani_env *env, ani_object object, ani_method method, ani_float *result,const ani_value *args)](#object_callmethod_float_a) | Calls a method on an object and retrieves a float return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a float result. |
| [ani_status (\*Object_CallMethod_Float_V)(ani_env *env, ani_object object, ani_method method, ani_float *result,va_list args)](#object_callmethod_float_v) | Calls a method on an object and retrieves a float return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a float result. |
| [ani_status (\*Object_CallMethod_Double)(ani_env *env, ani_object object, ani_method method, ani_double *result, ...)](#object_callmethod_double) | Calls a method on an object and retrieves a double return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a double result. |
| [ani_status (\*Object_CallMethod_Double_A)(ani_env *env, ani_object object, ani_method method, ani_double *result,const ani_value *args)](#object_callmethod_double_a) | Calls a method on an object and retrieves a double return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a double result. |
| [ani_status (\*Object_CallMethod_Double_V)(ani_env *env, ani_object object, ani_method method, ani_double *result,va_list args)](#object_callmethod_double_v) | Calls a method on an object and retrieves a double return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a double result. |
| [ani_status (\*Object_CallMethod_Ref)(ani_env *env, ani_object object, ani_method method, ani_ref *result, ...)](#object_callmethod_ref) | Calls a method on an object and retrieves a reference return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a reference result. |
| [ani_status (\*Object_CallMethod_Ref_A)(ani_env *env, ani_object object, ani_method method, ani_ref *result,const ani_value *args)](#object_callmethod_ref_a) | Calls a method on an object and retrieves a reference return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a reference result. |
| [ani_status (\*Object_CallMethod_Ref_V)(ani_env *env, ani_object object, ani_method method, ani_ref *result,va_list args)](#object_callmethod_ref_v) | Calls a method on an object and retrieves a reference return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a reference result. |
| [ani_status (\*Object_CallMethod_Void)(ani_env *env, ani_object object, ani_method method, ...)](#object_callmethod_void) | Calls a method on an object with no return value.<br> This function calls the specified method of an object using variadic arguments. The method does not return a value. |
| [ani_status (\*Object_CallMethod_Void_A)(ani_env *env, ani_object object, ani_method method, const ani_value *args)](#object_callmethod_void_a) | Calls a method on an object with no return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array. The method does not return a value. |
| [ani_status (\*Object_CallMethod_Void_V)(ani_env *env, ani_object object, ani_method method, va_list args)](#object_callmethod_void_v) | Calls a method on an object with no return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list`. The method does not return a value. |
| [ani_status (\*Object_CallMethodByName_Boolean)(ani_env *env, ani_object object, const char *name,const char *signature, ani_boolean *result, ...)](#object_callmethodbyname_boolean) | Calls a method by name on an object and retrieves a boolean return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a boolean result. |
| [ani_status (\*Object_CallMethodByName_Boolean_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_boolean *result, const ani_value *args)](#object_callmethodbyname_boolean_a) | Calls a method by name on an object and retrieves a boolean return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a boolean result. |
| [ani_status (\*Object_CallMethodByName_Boolean_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_boolean *result, va_list args)](#object_callmethodbyname_boolean_v) | Calls a method by name on an object and retrieves a boolean return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a boolean result. |
| [ani_status (\*Object_CallMethodByName_Char)(ani_env *env, ani_object object, const char *name, const char *signature,ani_char *result, ...)](#object_callmethodbyname_char) | Calls a method by name on an object and retrieves a char return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a char result. |
| [ani_status (\*Object_CallMethodByName_Char_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_char *result, const ani_value *args)](#object_callmethodbyname_char_a) | Calls a method by name on an object and retrieves a char return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a char result. |
| [ani_status (\*Object_CallMethodByName_Char_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_char *result, va_list args)](#object_callmethodbyname_char_v) | Calls a method by name on an object and retrieves a char return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a char result. |
| [ani_status (\*Object_CallMethodByName_Byte)(ani_env *env, ani_object object, const char *name, const char *signature,ani_byte *result, ...)](#object_callmethodbyname_byte) | Calls a method by name on an object and retrieves a byte return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a byte result. |
| [ani_status (\*Object_CallMethodByName_Byte_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_byte *result, const ani_value *args)](#object_callmethodbyname_byte_a) | Calls a method by name on an object and retrieves a byte return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a byte result. |
| [ani_status (\*Object_CallMethodByName_Byte_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_byte *result, va_list args)](#object_callmethodbyname_byte_v) | Calls a method by name on an object and retrieves a byte return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a byte result. |
| [ani_status (\*Object_CallMethodByName_Short)(ani_env *env, ani_object object, const char *name,const char *signature, ani_short *result, ...)](#object_callmethodbyname_short) | Calls a method by name on an object and retrieves a short return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a short result. |
| [ani_status (\*Object_CallMethodByName_Short_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_short *result, const ani_value *args)](#object_callmethodbyname_short_a) | Calls a method by name on an object and retrieves a short return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a short result. |
| [ani_status (\*Object_CallMethodByName_Short_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_short *result, va_list args)](#object_callmethodbyname_short_v) | Calls a method by name on an object and retrieves a short return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a short result. |
| [ani_status (\*Object_CallMethodByName_Int)(ani_env *env, ani_object object, const char *name, const char *signature,ani_int *result, ...)](#object_callmethodbyname_int) | Calls a method by name on an object and retrieves a integer return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a integer result. |
| [ani_status (\*Object_CallMethodByName_Int_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_int *result, const ani_value *args)](#object_callmethodbyname_int_a) | Calls a method by name on an object and retrieves a integer return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a integer result. |
| [ani_status (\*Object_CallMethodByName_Int_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_int *result, va_list args)](#object_callmethodbyname_int_v) | Calls a method by name on an object and retrieves a integer return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a integer result. |
| [ani_status (\*Object_CallMethodByName_Long)(ani_env *env, ani_object object, const char *name, const char *signature,ani_long *result, ...)](#object_callmethodbyname_long) | Calls a method by name on an object and retrieves a long return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a long result. |
| [ani_status (\*Object_CallMethodByName_Long_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_long *result, const ani_value *args)](#object_callmethodbyname_long_a) | Calls a method by name on an object and retrieves a long return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a long result. |
| [ani_status (\*Object_CallMethodByName_Long_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_long *result, va_list args)](#object_callmethodbyname_long_v) | Calls a method by name on an object and retrieves a long return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a long result. |
| [ani_status (\*Object_CallMethodByName_Float)(ani_env *env, ani_object object, const char *name,const char *signature, ani_float *result, ...)](#object_callmethodbyname_float) | Calls a method by name on an object and retrieves a float return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a float result. |
| [ani_status (\*Object_CallMethodByName_Float_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_float *result, const ani_value *args)](#object_callmethodbyname_float_a) | Calls a method by name on an object and retrieves a float return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a float result. |
| [ani_status (\*Object_CallMethodByName_Float_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_float *result, va_list args)](#object_callmethodbyname_float_v) | Calls a method by name on an object and retrieves a float return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a float result. |
| [ani_status (\*Object_CallMethodByName_Double)(ani_env *env, ani_object object, const char *name,const char *signature, ani_double *result, ...)](#object_callmethodbyname_double) | Calls a method by name on an object and retrieves a double return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a double result. |
| [ani_status (\*Object_CallMethodByName_Double_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_double *result, const ani_value *args)](#object_callmethodbyname_double_a) | Calls a method by name on an object and retrieves a double return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a double result. |
| [ani_status (\*Object_CallMethodByName_Double_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_double *result, va_list args)](#object_callmethodbyname_double_v) | Calls a method by name on an object and retrieves a double return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a double result. |
| [ani_status (\*Object_CallMethodByName_Ref)(ani_env *env, ani_object object, const char *name, const char *signature,ani_ref *result, ...)](#object_callmethodbyname_ref) | Calls a method by name on an object and retrieves a reference return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a reference result. |
| [ani_status (\*Object_CallMethodByName_Ref_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_ref *result, const ani_value *args)](#object_callmethodbyname_ref_a) | Calls a method by name on an object and retrieves a reference return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a reference result. |
| [ani_status (\*Object_CallMethodByName_Ref_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_ref *result, va_list args)](#object_callmethodbyname_ref_v) | Calls a method by name on an object and retrieves a reference return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a reference result. |
| [ani_status (\*Object_CallMethodByName_Void)(ani_env *env, ani_object object, const char *name, const char *signature,...)](#object_callmethodbyname_void) | Calls a method by name on an object with no return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments. The method does not return a value. |
| [ani_status (\*Object_CallMethodByName_Void_A)(ani_env *env, ani_object object, const char *name,const char *signature, const ani_value *args)](#object_callmethodbyname_void_a) | Calls a method by name on an object with no return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array. The method does not return a value. |
| [ani_status (\*Object_CallMethodByName_Void_V)(ani_env *env, ani_object object, const char *name,const char *signature, va_list args)](#object_callmethodbyname_void_v) | Calls a method by name on an object with no return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list`. The method does not return a value. |
| [ani_status (\*TupleValue_GetNumberOfItems)(ani_env *env, ani_tuple_value tuple_value, ani_size *result)](#tuplevalue_getnumberofitems) | Retrieves the number of items in a tuple value.<br> This function retrieves the total number of items in the specified tuple value. |
| [ani_status (\*TupleValue_GetItem_Boolean)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_boolean *result)](#tuplevalue_getitem_boolean) | Retrieves a boolean item from a tuple value.<br> This function retrieves the boolean value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_GetItem_Char)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_char *result)](#tuplevalue_getitem_char) | Retrieves a char item from a tuple value.<br> This function retrieves the char value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_GetItem_Byte)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_byte *result)](#tuplevalue_getitem_byte) | Retrieves a byte item from a tuple value.<br> This function retrieves the byte value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_GetItem_Short)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_short *result)](#tuplevalue_getitem_short) | Retrieves a short item from a tuple value.<br> This function retrieves the short value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_GetItem_Int)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_int *result)](#tuplevalue_getitem_int) | Retrieves a integer item from a tuple value.<br> This function retrieves the integer value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_GetItem_Long)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_long *result)](#tuplevalue_getitem_long) | Retrieves a long item from a tuple value.<br> This function retrieves the long value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_GetItem_Float)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_float *result)](#tuplevalue_getitem_float) | Retrieves a float item from a tuple value.<br> This function retrieves the float value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_GetItem_Double)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_double *result)](#tuplevalue_getitem_double) | Retrieves a double item from a tuple value.<br> This function retrieves the double value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_GetItem_Ref)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_ref *result)](#tuplevalue_getitem_ref) | Retrieves a reference item from a tuple value.<br> This function retrieves the reference value of the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Boolean)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_boolean value)](#tuplevalue_setitem_boolean) | Sets a boolean value to an item in a tuple value.<br> This function assigns a boolean value to the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Char)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_char value)](#tuplevalue_setitem_char) | Sets a char value to an item in a tuple value.<br> This function assigns a char value to the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Byte)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_byte value)](#tuplevalue_setitem_byte) | Sets a byte value to an item in a tuple value.<br> This function assigns a byte value to the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Short)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_short value)](#tuplevalue_setitem_short) | Sets a short value to an item in a tuple value.<br> This function assigns a short value to the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Int)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_int value)](#tuplevalue_setitem_int) | Sets a integer value to an item in a tuple value.<br> This function assigns a integer value to the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Long)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_long value)](#tuplevalue_setitem_long) | Sets a long value to an item in a tuple value.<br> This function assigns a long value to the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Float)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_float value)](#tuplevalue_setitem_float) | Sets a float value to an item in a tuple value.<br> This function assigns a float value to the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Double)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_double value)](#tuplevalue_setitem_double) | Sets a double value to an item in a tuple value.<br> This function assigns a double value to the item at the specified index in the tuple value. |
| [ani_status (\*TupleValue_SetItem_Ref)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_ref value)](#tuplevalue_setitem_ref) | Sets a reference value to an item in a tuple value.<br> This function assigns a reference value to the item at the specified index in the tuple value. |
| [ani_status (\*GlobalReference_Create)(ani_env *env, ani_ref ref, ani_ref *result)](#globalreference_create) | Creates a global reference.<br> This function creates a global reference from a local reference. |
| [ani_status (\*GlobalReference_Delete)(ani_env *env, ani_ref gref)](#globalreference_delete) | Deletes a global reference.<br> This function deletes the specified global reference, releasing all associated resources. |
| [ani_status (\*WeakReference_Create)(ani_env *env, ani_ref ref, ani_wref *result)](#weakreference_create) | Creates a weak reference.<br> This function creates a weak reference from a local reference. |
| [ani_status (\*WeakReference_Delete)(ani_env *env, ani_wref wref)](#weakreference_delete) | Deletes a weak reference.<br> This function deletes the specified weak reference, releasing all associated resources. |
| [ani_status (\*WeakReference_GetReference)(ani_env *env, ani_wref wref, ani_boolean *was_released_result,ani_ref *ref_result)](#weakreference_getreference) | Retrieves the local reference associated with a weak reference.<br> This function retrieves the local reference that corresponds to the specified weak reference. |
| [ani_status (\*CreateArrayBuffer)(ani_env *env, size_t length, void **data_result,ani_arraybuffer *arraybuffer_result)](#createarraybuffer) | Creates a new array buffer.<br> This function creates a new array buffer with the specified length and returns a pointer to the allocated data. |
| [ani_status (\*ArrayBuffer_GetInfo)(ani_env *env, ani_arraybuffer arraybuffer, void **data_result,size_t *length_result)](#arraybuffer_getinfo) | Retrieves information about an array buffer.<br> This function retrieves the data pointer and length of the specified array buffer. |
| [ani_status (\*Promise_New)(ani_env *env, ani_resolver *result_resolver, ani_object *result_promise)](#promise_new) | Creates a new Promise.<br> This function creates a new promise and a resolver to manage it. |
| [ani_status (\*PromiseResolver_Resolve)(ani_env *env, ani_resolver resolver, ani_ref resolution)](#promiseresolver_resolve) | Resolves a promise.<br> This function resolves a promise by way of the resolver with which it is associated and queues promise `then` callbacks. |
| [ani_status (\*PromiseResolver_Reject)(ani_env *env, ani_resolver resolver, ani_error rejection)
void *reserved4void *reserved5void *reserved6void *reserved7void *reserved8void *reserved9void *reserved10void *reserved11void *reserved12void *reserved13](#promiseresolver_reject) | Rejects a promise.<br> This function rejects a promise by way of the resolver with which it is associated and queues promise `catch` callbacks. |
| [ani_status (\*Class_BindStaticNativeMethods)(ani_env *env, ani_class cls, const ani_native_function *methods,ani_size nr_methods)](#class_bindstaticnativemethods) | Binds static native methods to a class.<br> This function binds an array of static native methods to the specified class. |
| [ani_status (\*Primitive_Box_Boolean)(ani_env *env, ani_boolean value, ani_object *result)](#primitive_box_boolean) | Box a boolean value into an object.<br> This function boxes a boolean value into an object. |
| [ani_status (\*Primitive_Unbox_Boolean)(ani_env *env, ani_object obj, ani_boolean *result)](#primitive_unbox_boolean) | Unbox a boolean object into a boolean value.<br> This function unboxes a boolean object into a boolean value. |
| [ani_status (\*Primitive_Box_Byte)(ani_env *env, ani_byte value, ani_object *result)](#primitive_box_byte) | Box a byte value into an object.<br> This function boxes a byte value into an object. |
| [ani_status (\*Primitive_Unbox_Byte)(ani_env *env, ani_object obj, ani_byte *result)](#primitive_unbox_byte) | Unbox a byte object into a byte value.<br> This function unboxes a byte object into a byte value. |
| [ani_status (\*Primitive_Box_Char)(ani_env *env, ani_char value, ani_object *result)](#primitive_box_char) | Box a char value into an object.<br> This function boxes a char value into an object. |
| [ani_status (\*Primitive_Unbox_Char)(ani_env *env, ani_object obj, ani_char *result)](#primitive_unbox_char) | Unbox a char object into a char value.<br> This function unboxes a char object into a char value. |
| [ani_status (\*Primitive_Box_Short)(ani_env *env, ani_short value, ani_object *result)](#primitive_box_short) | Box a short value into an object.<br> This function boxes a short value into an object. |
| [ani_status (\*Primitive_Unbox_Short)(ani_env *env, ani_object obj, ani_short *result)](#primitive_unbox_short) | Unbox a short object into a short value.<br> This function unboxes a short object into a short value. |
| [ani_status (\*Primitive_Box_Int)(ani_env *env, ani_int value, ani_object *result)](#primitive_box_int) | Box a int value into an object.<br> This function boxes a int value into an object. |
| [ani_status (\*Primitive_Unbox_Int)(ani_env *env, ani_object obj, ani_int *result)](#primitive_unbox_int) | Unbox a int object into a int value.<br> This function unboxes a int object into a int value. |
| [ani_status (\*Primitive_Box_Long)(ani_env *env, ani_long value, ani_object *result)](#primitive_box_long) | Box a long value into an object.<br> This function boxes a long value into an object. |
| [ani_status (\*Primitive_Unbox_Long)(ani_env *env, ani_object obj, ani_long *result)](#primitive_unbox_long) | Unbox a long object into a long value.<br> This function unboxes a long object into a long value. |
| [ani_status (\*Primitive_Box_Float)(ani_env *env, ani_float value, ani_object *result)](#primitive_box_float) | Box a float value into an object.<br> This function boxes a float value into an object. |
| [ani_status (\*Primitive_Unbox_Float)(ani_env *env, ani_object obj, ani_float *result)](#primitive_unbox_float) | Unbox a float object into a float value.<br> This function unboxes a float object into a float value. |
| [ani_status (\*Primitive_Box_Double)(ani_env *env, ani_double value, ani_object *result)](#primitive_box_double) | Box a double value into an object.<br> This function boxes a double value into an object. |
| [ani_status (\*Primitive_Unbox_Double)(ani_env *env, ani_object obj, ani_double *result)](#primitive_unbox_double) | Unbox a double object into a double value.<br> This function unboxes a double object into a double value. |
| [ani_status (\*ValueArray_GetLength)(ani_env *env, ani_valuearray array, ani_size *result)](#valuearray_getlength) | Retrieves the length of a ValueArray.<br> This function retrieves the length of the specified ValueArray. |

## Member function description

### GetVersion()

```c
ani_status (*GetVersion)(ani_env *env, uint32_t *result)
```

**Description**

Retrieves the version information.<br> This function retrieves the version information and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [out] | result A pointer to a variable where the version information will be stored. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### GetVM()

```c
ani_status (*GetVM)(ani_env *env, ani_vm **result)
```

**Description**

Retrieves the Virtual Machine (VM) instance.<br> This function retrieves the VM instance and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [out] | result A pointer to the VM instance to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_New()

```c
ani_status (*Object_New)(ani_env *env, ani_class cls, ani_method ctor, ani_object *result, ...)
```

**Description**

Creates a new object of a specified class using a constructor method.<br> This function creates a new object of the given class and calls the specified constructor method with variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class of the object to create. |
| [in] | ctor The constructor method to invoke. |
| [out] | result A pointer to store the object return value. |
| [in] | ... Variadic arguments to pass to the constructor method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_New_A()

```c
ani_status (*Object_New_A)(ani_env *env, ani_class cls, ani_method ctor, ani_object *result, const ani_value *args)
```

**Description**

Creates a new object of a specified class using a constructor method (array-based).<br> This function creates a new object of the given class and calls the specified constructor method with arguments provided in an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class of the object to create. |
| [in] | ctor The constructor method to invoke. |
| [out] | result A pointer to store the object return value. |
| [in] | args An array of arguments to pass to the constructor method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_New_V()

```c
ani_status (*Object_New_V)(ani_env *env, ani_class cls, ani_method ctor, ani_object *result, va_list args)
```

**Description**

Creates a new object of a specified class using a constructor method (variadic arguments).<br> This function creates a new object of the given class and calls the specified constructor method with a `va_list` of arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class of the object to create. |
| [in] | ctor The constructor method to invoke. |
| [out] | result A pointer to store the object return value. |
| [in] | args A `va_list` of arguments to pass to the constructor method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetType()

```c
ani_status (*Object_GetType)(ani_env *env, ani_object object, ani_type *result)
```

**Description**

Retrieves the type of a given object.<br> This function retrieves the type of the specified object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object whose type is to be retrieved. |
| [out] | result A pointer to store the retrieved type. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_InstanceOf()

```c
ani_status (*Object_InstanceOf)(ani_env *env, ani_object object, ani_type type, ani_boolean *result)
```

**Description**

Checks if an object is an instance of a specified type.<br> This function checks whether the given object is an instance of the specified type.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object to check. |
| [in] | type The type to compare against. |
| [out] | result A pointer to store the boolean result (true if the object is an instance of the type, false otherwise). |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Type_GetSuperClass()

```c
ani_status (*Type_GetSuperClass)(ani_env *env, ani_type type, ani_class *result)
```

**Description**

Retrieves the superclass of a specified type.<br> This function retrieves the superclass of a given type and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | type The type for which to retrieve the superclass. |
| [out] | result A pointer to the superclass to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Type_IsAssignableFrom()

```c
ani_status (*Type_IsAssignableFrom)(ani_env *env, ani_type from_type, ani_type to_type, ani_boolean *result)
```

**Description**

Determines if one type is assignable from another.<br> This function checks if a type is assignable from another and stores the result in the output parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | from_type The source type. |
| [in] | to_type The target type. |
| [out] | result A pointer to a boolean indicating assignability. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FindModule()

```c
ani_status (*FindModule)(ani_env *env, const char *module_descriptor, ani_module *result)
```

**Description**

Finds a module by its descriptor.<br> This function locates a module based on its descriptor and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | module_descriptor The descriptor of the module to find. |
| [out] | result A pointer to the module to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FindNamespace()

```c
ani_status (*FindNamespace)(ani_env *env, const char *namespace_descriptor, ani_namespace *result)
```

**Description**

Finds a namespace by its descriptor.<br> This function locates a namespace based on its descriptor and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | namespace_descriptor The descriptor of the namespace to find. |
| [out] | result A pointer to the namespace to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FindClass()

```c
ani_status (*FindClass)(ani_env *env, const char *class_descriptor, ani_class *result)
```

**Description**

Finds a class by its descriptor.<br> This function locates a class based on its descriptor and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | class_descriptor The descriptor of the class to find. |
| [out] | result A pointer to the class to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FindEnum()

```c
ani_status (*FindEnum)(ani_env *env, const char *enum_descriptor, ani_enum *result)
```

**Description**

Finds an enum by its descriptor.<br> This function locates an enum based on its descriptor and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | enum_descriptor The descriptor of the enum to find. |
| [out] | result A pointer to the enum to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Module_FindFunction()

```c
ani_status (*Module_FindFunction)(ani_env *env, ani_module module, const char *name, const char *signature,ani_function *result)
```

**Description**

Finds a function within a module by its name and signature.<br> This function locates a function within the specified module based on its name and signature.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | module The module to search within. |
| [in] | name The name of the function to find. |
| [in] | signature The signature of the function to find. |
| [out] | result A pointer to the function object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Module_FindVariable()

```c
ani_status (*Module_FindVariable)(ani_env *env, ani_module module, const char *name, ani_variable *result)
```

**Description**

Finds a variable within a module by its name.<br> This function locates a variable within the specified module based on its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | module The module to search within. |
| [in] | name The name of the variable to find. |
| [out] | result A pointer to the variable object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Namespace_FindFunction()

```c
ani_status (*Namespace_FindFunction)(ani_env *env, ani_namespace ns, const char *name, const char *signature,ani_function *result)
```

**Description**

Finds a function within a namespace by its name and signature.<br> This function locates a function within the specified namespace based on its name and signature.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ns The namespace to search within. |
| [in] | name The name of the function to find. |
| [in] | signature The signature of the function to find. |
| [out] | result A pointer to the function object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Namespace_FindVariable()

```c
ani_status (*Namespace_FindVariable)(ani_env *env, ani_namespace ns, const char *name, ani_variable *result)
```

**Description**

Finds a variable within a namespace by its name.<br> This function locates a variable within the specified namespace based on its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ns The namespace to search within. |
| [in] | name The name of the variable to find. |
| [out] | result A pointer to the variable object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Module_BindNativeFunctions()

```c
ani_status (*Module_BindNativeFunctions)(ani_env *env, ani_module module, const ani_native_function *functions,ani_size nr_functions)
```

**Description**

Binds native functions to a module.<br> This function binds an array of native functions to the specified module.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | module The module to which the native functions will be bound. |
| [in] | functions A pointer to an array of native functions to bind. |
| [in] | nr_functions The number of native functions in the array. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Namespace_BindNativeFunctions()

```c
ani_status (*Namespace_BindNativeFunctions)(ani_env *env, ani_namespace ns, const ani_native_function *functions,ani_size nr_functions)
```

**Description**

Binds native functions to a namespace.<br> This function binds an array of native functions to the specified namespace.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ns The namespace to which the native functions will be bound. |
| [in] | functions A pointer to an array of native functions to bind. |
| [in] | nr_functions The number of native functions in the array. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_BindNativeMethods()

```c
ani_status (*Class_BindNativeMethods)(ani_env *env, ani_class cls, const ani_native_function *methods,ani_size nr_methods)
```

**Description**

Binds native methods to a class.<br> This function binds an array of native instance methods to the specified class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to which the native methods will be bound. |
| [in] | methods A pointer to an array of native methods to bind. |
| [in] | nr_methods The number of native methods in the array. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Reference_Delete()

```c
ani_status (*Reference_Delete)(ani_env *env, ani_ref lref)
```

**Description**

Deletes a local reference.<br> This function deletes a specified local reference to free up resources.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | lref The local reference to be deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### EnsureEnoughReferences()

```c
ani_status (*EnsureEnoughReferences)(ani_env *env, ani_size nr_refs)
```

**Description**

Ensures enough local references are available.<br> This function checks and ensures that the specified number of local references can be created.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | nr_refs The number of local references to ensure availability for. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### CreateLocalScope()

```c
ani_status (*CreateLocalScope)(ani_env *env, ani_size nr_refs)
```

**Description**

Creates a new local scope for references.<br> This function creates a local scope for references with a specified capacity.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | nr_refs The maximum number of references that can be created in this scope. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### DestroyLocalScope()

```c
ani_status (*DestroyLocalScope)(ani_env *env)
```

**Description**

Destroys the current local scope.<br> This function destroys the current local scope and frees all references within it.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### CreateEscapeLocalScope()

```c
ani_status (*CreateEscapeLocalScope)(ani_env *env, ani_size nr_refs)
```

**Description**

Creates a new escape local scope.<br> This function creates a local scope for references with escape functionality, allowing objects to escape this scope.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | nr_refs The maximum number of references that can be created in this scope. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### DestroyEscapeLocalScope()

```c
ani_status (*DestroyEscapeLocalScope)(ani_env *env, ani_ref ref, ani_ref *result)
```

**Description**

Destroys the current escape local scope.<br> This function destroys the current escape local scope and allows escaping references to be retrieved.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ref The reference to be escaped from the current scope. |
| [out] | result A pointer to the resulting reference that has escaped the scope. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ThrowError()

```c
ani_status (*ThrowError)(ani_env *env, ani_error err)
```

**Description**

Throws an error.<br> This function throws the specified error in the current environment.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | err The error to throw. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ExistUnhandledError()

```c
ani_status (*ExistUnhandledError)(ani_env *env, ani_boolean *result)
```

**Description**

Checks if there are unhandled errors.<br> This function determines if there are unhandled errors in the current environment.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [out] | result A pointer to a boolean indicating if unhandled errors exist. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### GetUnhandledError()

```c
ani_status (*GetUnhandledError)(ani_env *env, ani_error *result)
```

**Description**

Retrieves the current unhandled error.<br> This function fetches the unhandled error in the environment.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [out] | result A pointer to store the unhandled error. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ResetError()

```c
ani_status (*ResetError)(ani_env *env)
```

**Description**

Resets the current error state.<br> This function clears the error state in the current environment.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### DescribeError()

```c
ani_status (*DescribeError)(ani_env *env)  // NOTE: Print stacktrace for debugging?
```

**Description**

Provides a description of the current error.<br> This function prints the stack trace or other debug information for the current error. Printing is done via invocation of `console.error` provided by standard library.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Abort()

```c
ani_status (*Abort)(ani_env *env, const char *message)
```

**Description**

Aborts execution with a message.<br> This function terminates execution with the specified error message.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | message The error message to display on termination. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Does not return; the process terminates. |

### GetNull()

```c
ani_status (*GetNull)(ani_env *env, ani_ref *result)
```

**Description**

Retrieves a null reference.<br> This function provides a null reference in the specified result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [out] | result A pointer to store the null reference. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### GetUndefined()

```c
ani_status (*GetUndefined)(ani_env *env, ani_ref *result)
```

**Description**

Retrieves an undefined reference.<br> This function provides an undefined reference in the specified result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [out] | result A pointer to store the undefined reference. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Reference_IsNull()

```c
ani_status (*Reference_IsNull)(ani_env *env, ani_ref ref, ani_boolean *result)
```

**Description**

Checks if a reference is null.<br> This function determines if the specified reference is null.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ref The reference to check. |
| [out] | result A pointer to a boolean indicating if the reference is null. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Reference_IsUndefined()

```c
ani_status (*Reference_IsUndefined)(ani_env *env, ani_ref ref, ani_boolean *result)
```

**Description**

Checks if a reference is undefined.<br> This function determines if the specified reference is undefined.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ref The reference to check. |
| [out] | result A pointer to a boolean indicating if the reference is undefined. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Reference_IsNullishValue()

```c
ani_status (*Reference_IsNullishValue)(ani_env *env, ani_ref ref, ani_boolean *result)
```

**Description**

Checks if a reference is nullish value (null or undefined).<br> This function determines if the specified reference is either null or undefined.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ref The reference to check. |
| [out] | result A pointer to a boolean indicating if the reference is nullish value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Reference_Equals()

```c
ani_status (*Reference_Equals)(ani_env *env, ani_ref ref0, ani_ref ref1, ani_boolean *result)
```

**Description**

Compares two references for equality.<br> This function checks if two references are equal.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ref0 The first reference to compare. |
| [in] | ref1 The second reference to compare. |
| [out] | result A pointer to a boolean indicating if the references are equal. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Reference_StrictEquals()

```c
ani_status (*Reference_StrictEquals)(ani_env *env, ani_ref ref0, ani_ref ref1, ani_boolean *result)
```

**Description**

Compares two references for strict equality.<br> This function checks if two references are strictly equal.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ref0 The first reference to compare. |
| [in] | ref1 The second reference to compare. |
| [out] | result A pointer to a boolean indicating if the references are strictly equal. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### String_NewUTF16()

```c
ani_status (*String_NewUTF16)(ani_env *env, const uint16_t *utf16_string, ani_size utf16_size, ani_string *result)
```

**Description**

Creates a new UTF-16 string.<br> This function creates a new string from the provided UTF-16 encoded data.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | utf16_string A pointer to the UTF-16 encoded string data. |
| [in] | utf16_size The size of the UTF-16 string in code units. |
| [out] | result A pointer to store the created string. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### String_GetUTF16Size()

```c
ani_status (*String_GetUTF16Size)(ani_env *env, ani_string string, ani_size *result)
```

**Description**

Retrieves the size of a UTF-16 string.<br> This function retrieves the size (in code units) of the specified UTF-16 string.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | string The UTF-16 string to measure. |
| [out] | result A pointer to store the size of the string. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### String_GetUTF16()

```c
ani_status (*String_GetUTF16)(ani_env *env, ani_string string, uint16_t *utf16_buffer, ani_size utf16_buffer_size,ani_size *result)
```

**Description**

Retrieves the UTF-16 encoded data of a string.<br> This function copies the UTF-16 encoded data of the string into the provided buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | string The string to retrieve data from. |
| [out] | utf16_buffer A buffer to store the UTF-16 encoded data. |
| [in] | utf16_buffer_size The size of the buffer in code units. |
| [out] | result A pointer to store the number of code units written. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### String_GetUTF16SubString()

```c
ani_status (*String_GetUTF16SubString)(ani_env *env, ani_string string, ani_size substr_offset,ani_size substr_size, uint16_t *utf16_buffer, ani_size utf16_buffer_size,ani_size *result)
```

**Description**

Retrieves a substring of a UTF-16 string.<br> This function copies a portion of the UTF-16 string into the provided buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | string The string to retrieve data from. |
| [in] | substr_offset The starting offset of the substring. |
| [in] | substr_size The size of the substring in code units. |
| [out] | utf16_buffer A buffer to store the substring. |
| [in] | utf16_buffer_size The size of the buffer in code units. |
| [out] | result A pointer to store the number of code units written. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### String_NewUTF8()

```c
ani_status (*String_NewUTF8)(ani_env *env, const char *utf8_string, ani_size utf8_size, ani_string *result)
```

**Description**

Creates a new UTF-8 string.<br> This function creates a new string from the provided UTF-8 encoded data.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | utf8_string A pointer to the UTF-8 encoded string data. |
| [in] | utf8_size The size of the UTF-8 string in bytes. |
| [out] | result A pointer to store the created string. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### String_GetUTF8Size()

```c
ani_status (*String_GetUTF8Size)(ani_env *env, ani_string string, ani_size *result)
```

**Description**

Retrieves the size of a UTF-8 string.<br> This function retrieves the size (in bytes) of the specified UTF-8 string.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | string The UTF-8 string to measure. |
| [out] | result A pointer to store the size of the string. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### String_GetUTF8()

```c
ani_status (*String_GetUTF8)(ani_env *env, ani_string string, char *utf8_buffer, ani_size utf8_buffer_size,ani_size *result)
```

**Description**

Retrieves the UTF-8 encoded data of a string.<br> This function copies the UTF-8 encoded data of the string into the provided buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | string The string to retrieve data from. |
| [out] | utf8_buffer A buffer to store the UTF-8 encoded data. |
| [in] | utf8_buffer_size The size of the buffer in bytes. |
| [out] | result A pointer to store the number of bytes written. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### String_GetUTF8SubString()

```c
ani_status (*String_GetUTF8SubString)(ani_env *env, ani_string string, ani_size substr_offset, ani_size substr_size,char *utf8_buffer, ani_size utf8_buffer_size, ani_size *result)
```

**Description**

Retrieves a substring of a UTF-8 string.<br> This function copies a portion of the UTF-8 string into the provided buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | string The string to retrieve data from. |
| [in] | substr_offset The starting offset of the substring. |
| [in] | substr_size The size of the substring in bytes. |
| [out] | utf8_buffer A buffer to store the substring. |
| [in] | utf8_buffer_size The size of the buffer in bytes. |
| [out] | result A pointer to store the number of bytes written. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Array_GetLength()

```c
ani_status (*Array_GetLength)(ani_env *env, ani_array array, ani_size *result)
```

**Description**

Retrieves the length of an Array.<br> This function retrieves the length of the specified Array object with respect to possible override of the managed method.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The Array whose length is to be retrieved. |
| [out] | result A pointer to store the length of the Array. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Array_New()

```c
ani_status (*Array_New)(ani_env *env, ani_size length, ani_ref initial_element, ani_array *result)
```

**Description**

This function creates a new Array of the specified length.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the Array to be created. |
| [out] | result A pointer to store the created Array. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Array_Set()

```c
ani_status (*Array_Set)(ani_env *env, ani_array array, ani_size index, ani_ref ref)
```

**Description**

Sets a value to an Array.<br> This function sets a value at a given index in Array with respect to possible override of the managed method.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The Array to retrieve values from. |
| [in] | index The index of element to retrieve. |
| [in] | ref Value to set |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Array_Get()

```c
ani_status (*Array_Get)(ani_env *env, ani_array array, ani_size index, ani_ref *result)
```

**Description**

Retrieves a value from an Array.<br> This function retrieves a value at a given index from Array with respect to possible override of the managed method.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The Array to retrieve values from. |
| [in] | index The index of element to retrieve. |
| [out] | result A pointer to store the retrieved value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Array_Push()

```c
ani_status (*Array_Push)(ani_env *env, ani_array array, ani_ref ref)
```

**Description**

Push a value to the end of Array.<br> This function pushes a value to the end of Array with respect to possible override of the managed method.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The array to retrieve values from. |
| [in] | ref Value to set |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Array_Pop()

```c
ani_status (*Array_Pop)(ani_env *env, ani_array array, ani_ref *result)
```

**Description**

Retrieves the last element and erases it from array.<br> This function retrieves the last element and erases it from Array with respect to possible override of the managed method.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The array whose last element is to be retrieved. |
| [out] | result A pointer to store the last element of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FixedArray_GetLength()

```c
ani_status (*FixedArray_GetLength)(ani_env *env, ani_fixedarray array, ani_size *result)
```

**Description**

Retrieves the length of a FixedArray.<br> This function retrieves the length of the specified FixedArray.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The FixedArray whose length is to be retrieved. |
| [out] | result A pointer to store the length of the FixedArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_New_Boolean()

```c
ani_status (*ValueArray_New_Boolean)(ani_env *env, ani_size length, ani_valuearray_boolean *result)
```

**Description**

Creates a new ValueArray of booleans.<br> This function creates a new ValueArray of the specified length for boolean values.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the ValueArray to be created. |
| [out] | result A pointer to store the created ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_New_Char()

```c
ani_status (*ValueArray_New_Char)(ani_env *env, ani_size length, ani_valuearray_char *result)
```

**Description**

Creates a new ValueArray of characters.<br> This function creates a new ValueArray of the specified length for character values.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the ValueArray to be created. |
| [out] | result A pointer to store the created ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_New_Byte()

```c
ani_status (*ValueArray_New_Byte)(ani_env *env, ani_size length, ani_valuearray_byte *result)
```

**Description**

Creates a new ValueArray of bytes.<br> This function creates a new ValueArray of the specified length for byte values.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the ValueArray to be created. |
| [out] | result A pointer to store the created ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_New_Short()

```c
ani_status (*ValueArray_New_Short)(ani_env *env, ani_size length, ani_valuearray_short *result)
```

**Description**

Creates a new ValueArray of shorts.<br> This function creates a new ValueArray of the specified length for short integer values.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the ValueArray to be created. |
| [out] | result A pointer to store the created ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_New_Int()

```c
ani_status (*ValueArray_New_Int)(ani_env *env, ani_size length, ani_valuearray_int *result)
```

**Description**

Creates a new ValueArray of integers.<br> This function creates a new ValueArray of the specified length for integer values.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the ValueArray to be created. |
| [out] | result A pointer to store the created ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_New_Long()

```c
ani_status (*ValueArray_New_Long)(ani_env *env, ani_size length, ani_valuearray_long *result)
```

**Description**

Creates a new ValueArray of long integers.<br> This function creates a new ValueArray of the specified length for long integer values.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the ValueArray to be created. |
| [out] | result A pointer to store the created ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_New_Float()

```c
ani_status (*ValueArray_New_Float)(ani_env *env, ani_size length, ani_valuearray_float *result)
```

**Description**

Creates a new ValueArray of floats.<br> This function creates a new ValueArray of the specified length for float values.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the ValueArray to be created. |
| [out] | result A pointer to store the created ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_New_Double()

```c
ani_status (*ValueArray_New_Double)(ani_env *env, ani_size length, ani_valuearray_double *result)
```

**Description**

Creates a new ValueArray of doubles.<br> This function creates a new ValueArray of the specified length for double values.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the ValueArray to be created. |
| [out] | result A pointer to store the created ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetRegion_Boolean()

```c
ani_status (*ValueArray_GetRegion_Boolean)(ani_env *env, ani_valuearray_boolean array, ani_size offset,ani_size length, ani_boolean *native_buffer)
```

**Description**

Retrieves a region of boolean values from a ValueArray.<br> This function retrieves a portion of the specified boolean ValueArray into a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to retrieve values from. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to retrieve. |
| [out] | native_buffer A buffer to store the retrieved boolean values. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetRegion_Char()

```c
ani_status (*ValueArray_GetRegion_Char)(ani_env *env, ani_valuearray_char array, ani_size offset, ani_size length,ani_char *native_buffer)
```

**Description**

Retrieves a region of character values from a ValueArray.<br> This function retrieves a portion of the specified character ValueArray into a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to retrieve values from. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to retrieve. |
| [out] | native_buffer A buffer to store the retrieved character values. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetRegion_Byte()

```c
ani_status (*ValueArray_GetRegion_Byte)(ani_env *env, ani_valuearray_byte array, ani_size offset, ani_size length,ani_byte *native_buffer)
```

**Description**

Retrieves a region of byte values from a ValueArray.<br> This function retrieves a portion of the specified byte ValueArray into a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to retrieve values from. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to retrieve. |
| [out] | native_buffer A buffer to store the retrieved byte values. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetRegion_Short()

```c
ani_status (*ValueArray_GetRegion_Short)(ani_env *env, ani_valuearray_short array, ani_size offset, ani_size length,ani_short *native_buffer)
```

**Description**

Retrieves a region of short values from a ValueArray.<br> This function retrieves a portion of the specified short ValueArray into a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to retrieve values from. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to retrieve. |
| [out] | native_buffer A buffer to store the retrieved short values. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetRegion_Int()

```c
ani_status (*ValueArray_GetRegion_Int)(ani_env *env, ani_valuearray_int array, ani_size offset, ani_size length,ani_int *native_buffer)
```

**Description**

Retrieves a region of integer values from a ValueArray.<br> This function retrieves a portion of the specified integer ValueArray into a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to retrieve values from. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to retrieve. |
| [out] | native_buffer A buffer to store the retrieved integer values. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetRegion_Long()

```c
ani_status (*ValueArray_GetRegion_Long)(ani_env *env, ani_valuearray_long array, ani_size offset, ani_size length,ani_long *native_buffer)
```

**Description**

Retrieves a region of long integer values from a ValueArray.<br> This function retrieves a portion of the specified long integer ValueArray into a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to retrieve values from. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to retrieve. |
| [out] | native_buffer A buffer to store the retrieved long integer values. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetRegion_Float()

```c
ani_status (*ValueArray_GetRegion_Float)(ani_env *env, ani_valuearray_float array, ani_size offset, ani_size length,ani_float *native_buffer)
```

**Description**

Retrieves a region of float values from a ValueArray.<br> This function retrieves a portion of the specified float ValueArray into a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to retrieve values from. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to retrieve. |
| [out] | native_buffer A buffer to store the retrieved float values. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetRegion_Double()

```c
ani_status (*ValueArray_GetRegion_Double)(ani_env *env, ani_valuearray_double array, ani_size offset,ani_size length, ani_double *native_buffer)
```

**Description**

Retrieves a region of double values from a ValueArray.<br> This function retrieves a portion of the specified double ValueArray into a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to retrieve values from. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to retrieve. |
| [out] | native_buffer A buffer to store the retrieved double values. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_SetRegion_Boolean()

```c
ani_status (*ValueArray_SetRegion_Boolean)(ani_env *env, ani_valuearray_boolean array, ani_size offset,ani_size length, const ani_boolean *native_buffer)
```

**Description**

Sets a region of boolean values in a ValueArray.<br> This function sets a portion of the specified boolean ValueArray using a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to set values in. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to set. |
| [in] | native_buffer A buffer containing the boolean values to set. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_SetRegion_Char()

```c
ani_status (*ValueArray_SetRegion_Char)(ani_env *env, ani_valuearray_char array, ani_size offset, ani_size length,const ani_char *native_buffer)
```

**Description**

Sets a region of character values in a ValueArray.<br> This function sets a portion of the specified character ValueArray using a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to set values in. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to set. |
| [in] | native_buffer A buffer containing the character values to set. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_SetRegion_Byte()

```c
ani_status (*ValueArray_SetRegion_Byte)(ani_env *env, ani_valuearray_byte array, ani_size offset, ani_size length,const ani_byte *native_buffer)
```

**Description**

Sets a region of byte values in a ValueArray.<br> This function sets a portion of the specified byte ValueArray using a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to set values in. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to set. |
| [in] | native_buffer A buffer containing the byte values to set. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_SetRegion_Short()

```c
ani_status (*ValueArray_SetRegion_Short)(ani_env *env, ani_valuearray_short array, ani_size offset, ani_size length,const ani_short *native_buffer)
```

**Description**

Sets a region of short values in a ValueArray.<br> This function sets a portion of the specified short ValueArray using a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to set values in. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to set. |
| [in] | native_buffer A buffer containing the short values to set. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_SetRegion_Int()

```c
ani_status (*ValueArray_SetRegion_Int)(ani_env *env, ani_valuearray_int array, ani_size offset, ani_size length,const ani_int *native_buffer)
```

**Description**

Sets a region of integer values in a ValueArray.<br> This function sets a portion of the specified integer ValueArray using a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to set values in. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to set. |
| [in] | native_buffer A buffer containing the integer values to set. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_SetRegion_Long()

```c
ani_status (*ValueArray_SetRegion_Long)(ani_env *env, ani_valuearray_long array, ani_size offset, ani_size length,const ani_long *native_buffer)
```

**Description**

Sets a region of long integer values in a ValueArray.<br> This function sets a portion of the specified long integer ValueArray using a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to set values in. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to set. |
| [in] | native_buffer A buffer containing the long integer values to set. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_SetRegion_Float()

```c
ani_status (*ValueArray_SetRegion_Float)(ani_env *env, ani_valuearray_float array, ani_size offset, ani_size length,const ani_float *native_buffer)
```

**Description**

Sets a region of float values in a ValueArray.<br> This function sets a portion of the specified float ValueArray using a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to set values in. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to set. |
| [in] | native_buffer A buffer containing the float values to set. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_SetRegion_Double()

```c
ani_status (*ValueArray_SetRegion_Double)(ani_env *env, ani_valuearray_double array, ani_size offset,ani_size length, const ani_double *native_buffer)
```

**Description**

Sets a region of double values in a ValueArray.<br> This function sets a portion of the specified double ValueArray using a native buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray to set values in. |
| [in] | offset The starting offset of the region. |
| [in] | length The number of elements to set. |
| [in] | native_buffer A buffer containing the double values to set. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FixedArray_New()

```c
ani_status (*FixedArray_New)(ani_env *env, ani_type type, ani_size length, ani_ref initial_element,ani_fixedarray *result)
```

**Description**

Creates a new FixedArray of references.<br> This function creates a new FixedArray of references, optionally initializing it with an initial_element ref.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | type The type of the elements of the FixedArray. |
| [in] | length The length of the FixedArray to be created. |
| [in] | initial_element An optional reference to initialize the FixedArray. Can be null. |
| [out] | result A pointer to store the created FixedArray of references. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FixedArray_Set()

```c
ani_status (*FixedArray_Set)(ani_env *env, ani_fixedarray array, ani_size index, ani_ref ref)
```

**Description**

Sets a reference at a specific index in a FixedArray.<br> This function sets the value of a reference at the specified index in the FixedArray.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The array of references to modify. |
| [in] | index The index at which to set the reference. |
| [in] | ref The reference to set at the specified index. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FixedArray_Get()

```c
ani_status (*FixedArray_Get)(ani_env *env, ani_fixedarray array, ani_size index, ani_ref *result)
```

**Description**

Retrieves a reference from a specific index in a FixedArray.<br> This function retrieves the value of a reference at the specified index in the FixedArray.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The FixedArray of references to query. |
| [in] | index The index from which to retrieve the reference. |
| [out] | result A pointer to store the retrieved reference. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Enum_GetEnumItemByName()

```c
ani_status (*Enum_GetEnumItemByName)(ani_env *env, ani_enum enm, const char *name, ani_enum_item *result)
```

**Description**

Retrieves an enum item by its name.<br> This function retrieves an enum item associated with the specified name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | enm The enum to search within. |
| [in] | name The name of the enum item to retrieve. |
| [out] | result A pointer to store the retrieved enum item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Enum_GetEnumItemByIndex()

```c
ani_status (*Enum_GetEnumItemByIndex)(ani_env *env, ani_enum enm, ani_size index, ani_enum_item *result)
```

**Description**

Retrieves an enum item by its index.<br> This function retrieves an enum item located at the specified index.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | enm The enum to search within. |
| [in] | index The index of the enum item to retrieve. |
| [out] | result A pointer to store the retrieved enum item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### EnumItem_GetEnum()

```c
ani_status (*EnumItem_GetEnum)(ani_env *env, ani_enum_item enum_item, ani_enum *result)
```

**Description**

Retrieves the enum associated with an enum item.<br> This function retrieves the enum to which the specified enum item belongs.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | enum_item The enum item whose associated enum is to be retrieved. |
| [out] | result A pointer to store the retrieved enum. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### EnumItem_GetValue_Int()

```c
ani_status (*EnumItem_GetValue_Int)(ani_env *env, ani_enum_item enum_item, ani_int *result)
```

**Description**

Retrieves the integer value of an enum item.<br> This function retrieves the integer representing the value of the specified enum item.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | enum_item The enum item whose underlying value is to be retrieved. |
| [out] | result A pointer to store the retrieved integer. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### EnumItem_GetValue_String()

```c
ani_status (*EnumItem_GetValue_String)(ani_env *env, ani_enum_item enum_item, ani_string *result)
```

**Description**

Retrieves the string value of an enum item.<br> This function retrieves the string representing the value of the specified enum item.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | enum_item The enum item whose underlying value is to be retrieved. |
| [out] | result A pointer to store the retrieved string. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### EnumItem_GetName()

```c
ani_status (*EnumItem_GetName)(ani_env *env, ani_enum_item enum_item, ani_string *result)
```

**Description**

Retrieves the name of an enum item.<br> This function retrieves the name associated with the specified enum item.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | enum_item The enum item whose name is to be retrieved. |
| [out] | result A pointer to store the retrieved name. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### EnumItem_GetIndex()

```c
ani_status (*EnumItem_GetIndex)(ani_env *env, ani_enum_item enum_item, ani_size *result)
```

**Description**

Retrieves the index of an enum item.<br> This function retrieves the index of the specified enum item within its enum.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | enum_item The enum item whose index is to be retrieved. |
| [out] | result A pointer to store the retrieved index. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### FunctionalObject_Call()

```c
ani_status (*FunctionalObject_Call)(ani_env *env, ani_fn_object fn, ani_size argc, ani_ref *argv, ani_ref *result)
```

**Description**

Invokes an object of function type.<br> This function invokes an object of function type with the specified arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function type object to invoke. |
| [in] | argc The number of arguments being passed on invocation. |
| [in] | argv A pointer to an array of references representing the arguments. Can be null if `argc` is 0. |
| [out] | result A pointer to store the result of the invocation. Must be non null. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Boolean()

```c
ani_status (*Variable_SetValue_Boolean)(ani_env *env, ani_variable variable, ani_boolean value)
```

**Description**

Sets a boolean value to a variable.<br> This function assigns a boolean value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The boolean value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Char()

```c
ani_status (*Variable_SetValue_Char)(ani_env *env, ani_variable variable, ani_char value)
```

**Description**

Sets a character value to a variable.<br> This function assigns a character value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The character value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Byte()

```c
ani_status (*Variable_SetValue_Byte)(ani_env *env, ani_variable variable, ani_byte value)
```

**Description**

Sets a byte value to a variable.<br> This function assigns a byte value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The byte value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Short()

```c
ani_status (*Variable_SetValue_Short)(ani_env *env, ani_variable variable, ani_short value)
```

**Description**

Sets a short value to a variable.<br> This function assigns a short integer value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The short integer value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Int()

```c
ani_status (*Variable_SetValue_Int)(ani_env *env, ani_variable variable, ani_int value)
```

**Description**

Sets an integer value to a variable.<br> This function assigns an integer value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The integer value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Long()

```c
ani_status (*Variable_SetValue_Long)(ani_env *env, ani_variable variable, ani_long value)
```

**Description**

Sets a long value to a variable.<br> This function assigns a long integer value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The long integer value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Float()

```c
ani_status (*Variable_SetValue_Float)(ani_env *env, ani_variable variable, ani_float value)
```

**Description**

Sets a float value to a variable.<br> This function assigns a float value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The float value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Double()

```c
ani_status (*Variable_SetValue_Double)(ani_env *env, ani_variable variable, ani_double value)
```

**Description**

Sets a double value to a variable.<br> This function assigns a double value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The double value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_SetValue_Ref()

```c
ani_status (*Variable_SetValue_Ref)(ani_env *env, ani_variable variable, ani_ref value)
```

**Description**

Sets a reference value to a variable.<br> This function assigns a reference value to the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to modify. |
| [in] | value The reference value to assign to the variable. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Boolean()

```c
ani_status (*Variable_GetValue_Boolean)(ani_env *env, ani_variable variable, ani_boolean *result)
```

**Description**

Retrieves a boolean value from a variable.<br> This function fetches a boolean value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Char()

```c
ani_status (*Variable_GetValue_Char)(ani_env *env, ani_variable variable, ani_char *result)
```

**Description**

Retrieves a character value from a variable.<br> This function fetches a character value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved character value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Byte()

```c
ani_status (*Variable_GetValue_Byte)(ani_env *env, ani_variable variable, ani_byte *result)
```

**Description**

Retrieves a byte value from a variable.<br> This function fetches a byte value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved byte value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Short()

```c
ani_status (*Variable_GetValue_Short)(ani_env *env, ani_variable variable, ani_short *result)
```

**Description**

Retrieves a short value from a variable.<br> This function fetches a short integer value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved short integer value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Int()

```c
ani_status (*Variable_GetValue_Int)(ani_env *env, ani_variable variable, ani_int *result)
```

**Description**

Retrieves an integer value from a variable.<br> This function fetches an integer value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved integer value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Long()

```c
ani_status (*Variable_GetValue_Long)(ani_env *env, ani_variable variable, ani_long *result)
```

**Description**

Retrieves a long value from a variable.<br> This function fetches a long integer value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved long integer value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Float()

```c
ani_status (*Variable_GetValue_Float)(ani_env *env, ani_variable variable, ani_float *result)
```

**Description**

Retrieves a float value from a variable.<br> This function fetches a float value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved float value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Double()

```c
ani_status (*Variable_GetValue_Double)(ani_env *env, ani_variable variable, ani_double *result)
```

**Description**

Retrieves a double value from a variable.<br> This function fetches a double value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved double value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Variable_GetValue_Ref()

```c
ani_status (*Variable_GetValue_Ref)(ani_env *env, ani_variable variable, ani_ref *result)
```

**Description**

Retrieves a reference value from a variable.<br> This function fetches a reference value from the specified variable.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | variable The variable to query. |
| [out] | result A pointer to store the retrieved reference value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Boolean()

```c
ani_status (*Function_Call_Boolean)(ani_env *env, ani_function fn, ani_boolean *result, ...)
```

**Description**

Calls a function and retrieves a boolean result.<br> This function calls the specified function with variadic arguments and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Boolean_A()

```c
ani_status (*Function_Call_Boolean_A)(ani_env *env, ani_function fn, ani_boolean *result, const ani_value *args)
```

**Description**

Calls a function and retrieves a boolean result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Boolean_V()

```c
ani_status (*Function_Call_Boolean_V)(ani_env *env, ani_function fn, ani_boolean *result, va_list args)
```

**Description**

Calls a function and retrieves a boolean result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Char()

```c
ani_status (*Function_Call_Char)(ani_env *env, ani_function fn, ani_char *result, ...)
```

**Description**

Calls a function and retrieves a character result.<br> This function calls the specified function with variadic arguments and retrieves a character result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the character result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Char_A()

```c
ani_status (*Function_Call_Char_A)(ani_env *env, ani_function fn, ani_char *result, const ani_value *args)
```

**Description**

Calls a function and retrieves a character result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a character result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the character result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Char_V()

```c
ani_status (*Function_Call_Char_V)(ani_env *env, ani_function fn, ani_char *result, va_list args)
```

**Description**

Calls a function and retrieves a character result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a character result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the character result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Byte()

```c
ani_status (*Function_Call_Byte)(ani_env *env, ani_function fn, ani_byte *result, ...)
```

**Description**

Calls a function and retrieves a byte result.<br> This function calls the specified function with variadic arguments and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the byte result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Byte_A()

```c
ani_status (*Function_Call_Byte_A)(ani_env *env, ani_function fn, ani_byte *result, const ani_value *args)
```

**Description**

Calls a function and retrieves a byte result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the byte result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Byte_V()

```c
ani_status (*Function_Call_Byte_V)(ani_env *env, ani_function fn, ani_byte *result, va_list args)
```

**Description**

Calls a function and retrieves a byte result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the byte result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Short()

```c
ani_status (*Function_Call_Short)(ani_env *env, ani_function fn, ani_short *result, ...)
```

**Description**

Calls a function and retrieves a short result.<br> This function calls the specified function with variadic arguments and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the short result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Short_A()

```c
ani_status (*Function_Call_Short_A)(ani_env *env, ani_function fn, ani_short *result, const ani_value *args)
```

**Description**

Calls a function and retrieves a short result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the short result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Short_V()

```c
ani_status (*Function_Call_Short_V)(ani_env *env, ani_function fn, ani_short *result, va_list args)
```

**Description**

Calls a function and retrieves a short result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the short result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Int()

```c
ani_status (*Function_Call_Int)(ani_env *env, ani_function fn, ani_int *result, ...)
```

**Description**

Calls a function and retrieves an integer result.<br> This function calls the specified function with variadic arguments and retrieves an integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the integer result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Int_A()

```c
ani_status (*Function_Call_Int_A)(ani_env *env, ani_function fn, ani_int *result, const ani_value *args)
```

**Description**

Calls a function and retrieves an integer result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves an integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the integer result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Int_V()

```c
ani_status (*Function_Call_Int_V)(ani_env *env, ani_function fn, ani_int *result, va_list args)
```

**Description**

Calls a function and retrieves an integer result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves an integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the integer result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Long()

```c
ani_status (*Function_Call_Long)(ani_env *env, ani_function fn, ani_long *result, ...)
```

**Description**

Calls a function and retrieves a long result.<br> This function calls the specified function with variadic arguments and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the long result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Long_A()

```c
ani_status (*Function_Call_Long_A)(ani_env *env, ani_function fn, ani_long *result, const ani_value *args)
```

**Description**

Calls a function and retrieves a long result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the long result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Long_V()

```c
ani_status (*Function_Call_Long_V)(ani_env *env, ani_function fn, ani_long *result, va_list args)
```

**Description**

Calls a function and retrieves a long result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the long result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Float()

```c
ani_status (*Function_Call_Float)(ani_env *env, ani_function fn, ani_float *result, ...)
```

**Description**

Calls a function and retrieves a float result.<br> This function calls the specified function with variadic arguments and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the float result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Float_A()

```c
ani_status (*Function_Call_Float_A)(ani_env *env, ani_function fn, ani_float *result, const ani_value *args)
```

**Description**

Calls a function and retrieves a float result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the float result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Float_V()

```c
ani_status (*Function_Call_Float_V)(ani_env *env, ani_function fn, ani_float *result, va_list args)
```

**Description**

Calls a function and retrieves a float result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the float result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Double()

```c
ani_status (*Function_Call_Double)(ani_env *env, ani_function fn, ani_double *result, ...)
```

**Description**

Calls a function and retrieves a double result.<br> This function calls the specified function with variadic arguments and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the double result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Double_A()

```c
ani_status (*Function_Call_Double_A)(ani_env *env, ani_function fn, ani_double *result, const ani_value *args)
```

**Description**

Calls a function and retrieves a double result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the double result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Double_V()

```c
ani_status (*Function_Call_Double_V)(ani_env *env, ani_function fn, ani_double *result, va_list args)
```

**Description**

Calls a function and retrieves a double result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the double result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Ref()

```c
ani_status (*Function_Call_Ref)(ani_env *env, ani_function fn, ani_ref *result, ...)
```

**Description**

Calls a function and retrieves a reference result.<br> This function calls the specified function with variadic arguments and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the reference result. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Ref_A()

```c
ani_status (*Function_Call_Ref_A)(ani_env *env, ani_function fn, ani_ref *result, const ani_value *args)
```

**Description**

Calls a function and retrieves a reference result (array-based).<br> This function calls the specified function with arguments provided in an array and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the reference result. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Ref_V()

```c
ani_status (*Function_Call_Ref_V)(ani_env *env, ani_function fn, ani_ref *result, va_list args)
```

**Description**

Calls a function and retrieves a reference result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [out] | result A pointer to store the reference result. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Void()

```c
ani_status (*Function_Call_Void)(ani_env *env, ani_function fn, ...)
```

**Description**

Calls a function without returning a result.<br> This function calls the specified function with variadic arguments and does not return a result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [in] | ... Variadic arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Void_A()

```c
ani_status (*Function_Call_Void_A)(ani_env *env, ani_function fn, const ani_value *args)
```

**Description**

Calls a function without returning a result (array-based).<br> This function calls the specified function with arguments provided in an array and does not return a result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [in] | args A pointer to an array of arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Function_Call_Void_V()

```c
ani_status (*Function_Call_Void_V)(ani_env *env, ani_function fn, va_list args)
```

**Description**

Calls a function without returning a result (variadic arguments).<br> This function calls the specified function with arguments provided in a `va_list` and does not return a result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | fn The function to call. |
| [in] | args A `va_list` containing the arguments to pass to the function. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindField()

```c
ani_status (*Class_FindField)(ani_env *env, ani_class cls, const char *name, ani_field *result)
```

**Description**

Finds a field from by its name.<br> This function locates a field based on its name and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [in] | name The name of the field to find. |
| [out] | result A pointer to the field to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindStaticField()

```c
ani_status (*Class_FindStaticField)(ani_env *env, ani_class cls, const char *name, ani_static_field *result)
```

**Description**

Finds a static field by its name.<br> This function locates a static field based on its name and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [in] | name The name of the static field to find. |
| [out] | result A pointer to the static field to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindMethod()

```c
ani_status (*Class_FindMethod)(ani_env *env, ani_class cls, const char *name, const char *signature,ani_method *result)
```

**Description**

Finds a method from by its name and signature.<br> This function locates a method based on its name and signature and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [in] | name The name of the method to find. |
| [in] | signature The signature of the method to find. |
| [out] | result A pointer to the method to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindStaticMethod()

```c
ani_status (*Class_FindStaticMethod)(ani_env *env, ani_class cls, const char *name, const char *signature,ani_static_method *result)
```

**Description**

Finds a static method from by its name and signature.<br> This function locates a static method based on its name and signature and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [in] | name The name of the static method to find. |
| [in] | signature The signature of the static method to find. |
| [out] | result A pointer to the static method to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindSetter()

```c
ani_status (*Class_FindSetter)(ani_env *env, ani_class cls, const char *name, ani_method *result)
```

**Description**

Finds a setter method from by its name.<br> This function locates a setter method based on its name and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [in] | name The name of the property whose setter is to be found. |
| [out] | result A pointer to the method to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindGetter()

```c
ani_status (*Class_FindGetter)(ani_env *env, ani_class cls, const char *name, ani_method *result)
```

**Description**

Finds a getter method from by its name.<br> This function locates a getter method based on its name and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [in] | name The name of the property whose getter is to be found. |
| [out] | result A pointer to the method to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindIndexableGetter()

```c
ani_status (*Class_FindIndexableGetter)(ani_env *env, ani_class cls, const char *signature, ani_method *result)
```

**Description**

Finds an indexable getter method from by its signature.<br> This function locates an indexable getter method based on its signature and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [in] | signature The signature of the indexable getter to find. |
| [out] | result A pointer to the method to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindIndexableSetter()

```c
ani_status (*Class_FindIndexableSetter)(ani_env *env, ani_class cls, const char *signature, ani_method *result)
```

**Description**

Finds an indexable setter method from by its signature.<br> This function locates an indexable setter method based on its signature and stores it in the result parameter.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [in] | signature The signature of the indexable setter to find. |
| [out] | result A pointer to the method to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_FindIterator()

```c
ani_status (*Class_FindIterator)(ani_env *env, ani_class cls, ani_method *result)
```

**Description**

Finds an iterator method.<br> This function locates an iterator method

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to query. |
| [out] | result A pointer to the method to be populated. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Boolean()

```c
ani_status (*Class_GetStaticField_Boolean)(ani_env *env, ani_class cls, ani_static_field field,ani_boolean *result)
```

**Description**

Retrieves a boolean value from a static field of a class.<br> This function retrieves the boolean value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Char()

```c
ani_status (*Class_GetStaticField_Char)(ani_env *env, ani_class cls, ani_static_field field, ani_char *result)
```

**Description**

Retrieves a character value from a static field of a class.<br> This function retrieves the character value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved character value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Byte()

```c
ani_status (*Class_GetStaticField_Byte)(ani_env *env, ani_class cls, ani_static_field field, ani_byte *result)
```

**Description**

Retrieves a byte value from a static field of a class.<br> This function retrieves the byte value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved byte value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Short()

```c
ani_status (*Class_GetStaticField_Short)(ani_env *env, ani_class cls, ani_static_field field, ani_short *result)
```

**Description**

Retrieves a short value from a static field of a class.<br> This function retrieves the short value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved short value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Int()

```c
ani_status (*Class_GetStaticField_Int)(ani_env *env, ani_class cls, ani_static_field field, ani_int *result)
```

**Description**

Retrieves an integer value from a static field of a class.<br> This function retrieves the integer value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved integer value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Long()

```c
ani_status (*Class_GetStaticField_Long)(ani_env *env, ani_class cls, ani_static_field field, ani_long *result)
```

**Description**

Retrieves a long value from a static field of a class.<br> This function retrieves the long value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved long value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Float()

```c
ani_status (*Class_GetStaticField_Float)(ani_env *env, ani_class cls, ani_static_field field, ani_float *result)
```

**Description**

Retrieves a float value from a static field of a class.<br> This function retrieves the float value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved float value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Double()

```c
ani_status (*Class_GetStaticField_Double)(ani_env *env, ani_class cls, ani_static_field field, ani_double *result)
```

**Description**

Retrieves a double value from a static field of a class.<br> This function retrieves the double value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved double value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticField_Ref()

```c
ani_status (*Class_GetStaticField_Ref)(ani_env *env, ani_class cls, ani_static_field field, ani_ref *result)
```

**Description**

Retrieves a reference value from a static field of a class.<br> This function retrieves the reference value of the specified static field from the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to retrieve. |
| [out] | result A pointer to store the retrieved reference value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Boolean()

```c
ani_status (*Class_SetStaticField_Boolean)(ani_env *env, ani_class cls, ani_static_field field, ani_boolean value)
```

**Description**

Sets a boolean value to a static field of a class.<br> This function assigns a boolean value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The boolean value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Char()

```c
ani_status (*Class_SetStaticField_Char)(ani_env *env, ani_class cls, ani_static_field field, ani_char value)
```

**Description**

Sets a character value to a static field of a class.<br> This function assigns a character value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The character value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Byte()

```c
ani_status (*Class_SetStaticField_Byte)(ani_env *env, ani_class cls, ani_static_field field, ani_byte value)
```

**Description**

Sets a byte value to a static field of a class.<br> This function assigns a byte value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The byte value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Short()

```c
ani_status (*Class_SetStaticField_Short)(ani_env *env, ani_class cls, ani_static_field field, ani_short value)
```

**Description**

Sets a short value to a static field of a class.<br> This function assigns a short value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The short value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Int()

```c
ani_status (*Class_SetStaticField_Int)(ani_env *env, ani_class cls, ani_static_field field, ani_int value)
```

**Description**

Sets an integer value to a static field of a class.<br> This function assigns an integer value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The integer value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Long()

```c
ani_status (*Class_SetStaticField_Long)(ani_env *env, ani_class cls, ani_static_field field, ani_long value)
```

**Description**

Sets a long value to a static field of a class.<br> This function assigns a long value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The long value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Float()

```c
ani_status (*Class_SetStaticField_Float)(ani_env *env, ani_class cls, ani_static_field field, ani_float value)
```

**Description**

Sets a float value to a static field of a class.<br> This function assigns a float value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The float value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Double()

```c
ani_status (*Class_SetStaticField_Double)(ani_env *env, ani_class cls, ani_static_field field, ani_double value)
```

**Description**

Sets a double value to a static field of a class.<br> This function assigns a double value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The double value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticField_Ref()

```c
ani_status (*Class_SetStaticField_Ref)(ani_env *env, ani_class cls, ani_static_field field, ani_ref value)
```

**Description**

Sets a reference value to a static field of a class.<br> This function assigns a reference value to the specified static field of the given class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | field The static field to modify. |
| [in] | value The reference value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Boolean()

```c
ani_status (*Class_GetStaticFieldByName_Boolean)(ani_env *env, ani_class cls, const char *name,ani_boolean *result)
```

**Description**

Retrieves a boolean value from a static field of a class by its name.<br> This function retrieves the boolean value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Char()

```c
ani_status (*Class_GetStaticFieldByName_Char)(ani_env *env, ani_class cls, const char *name, ani_char *result)
```

**Description**

Retrieves a character value from a static field of a class by its name.<br> This function retrieves the character value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved character value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Byte()

```c
ani_status (*Class_GetStaticFieldByName_Byte)(ani_env *env, ani_class cls, const char *name, ani_byte *result)
```

**Description**

Retrieves a byte value from a static field of a class by its name.<br> This function retrieves the byte value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved byte value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Short()

```c
ani_status (*Class_GetStaticFieldByName_Short)(ani_env *env, ani_class cls, const char *name, ani_short *result)
```

**Description**

Retrieves a short value from a static field of a class by its name.<br> This function retrieves the short value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved short value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Int()

```c
ani_status (*Class_GetStaticFieldByName_Int)(ani_env *env, ani_class cls, const char *name, ani_int *result)
```

**Description**

Retrieves an integer value from a static field of a class by its name.<br> This function retrieves the integer value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved integer value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Long()

```c
ani_status (*Class_GetStaticFieldByName_Long)(ani_env *env, ani_class cls, const char *name, ani_long *result)
```

**Description**

Retrieves a long value from a static field of a class by its name.<br> This function retrieves the long value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved long value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Float()

```c
ani_status (*Class_GetStaticFieldByName_Float)(ani_env *env, ani_class cls, const char *name, ani_float *result)
```

**Description**

Retrieves a float value from a static field of a class by its name.<br> This function retrieves the float value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved float value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Double()

```c
ani_status (*Class_GetStaticFieldByName_Double)(ani_env *env, ani_class cls, const char *name, ani_double *result)
```

**Description**

Retrieves a double value from a static field of a class by its name.<br> This function retrieves the double value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved double value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_GetStaticFieldByName_Ref()

```c
ani_status (*Class_GetStaticFieldByName_Ref)(ani_env *env, ani_class cls, const char *name, ani_ref *result)
```

**Description**

Retrieves a reference value from a static field of a class by its name.<br> This function retrieves the reference value of the specified static field from the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to retrieve. |
| [out] | result A pointer to store the retrieved reference value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Boolean()

```c
ani_status (*Class_SetStaticFieldByName_Boolean)(ani_env *env, ani_class cls, const char *name, ani_boolean value)
```

**Description**

Sets a boolean value to a static field of a class by its name.<br> This function assigns a boolean value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The boolean value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Char()

```c
ani_status (*Class_SetStaticFieldByName_Char)(ani_env *env, ani_class cls, const char *name, ani_char value)
```

**Description**

Sets a character value to a static field of a class by its name.<br> This function assigns a character value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The character value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Byte()

```c
ani_status (*Class_SetStaticFieldByName_Byte)(ani_env *env, ani_class cls, const char *name, ani_byte value)
```

**Description**

Sets a byte value to a static field of a class by its name.<br> This function assigns a byte value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The byte value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Short()

```c
ani_status (*Class_SetStaticFieldByName_Short)(ani_env *env, ani_class cls, const char *name, ani_short value)
```

**Description**

Sets a short value to a static field of a class by its name.<br> This function assigns a short value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The short value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Int()

```c
ani_status (*Class_SetStaticFieldByName_Int)(ani_env *env, ani_class cls, const char *name, ani_int value)
```

**Description**

Sets an integer value to a static field of a class by its name.<br> This function assigns an integer value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The integer value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Long()

```c
ani_status (*Class_SetStaticFieldByName_Long)(ani_env *env, ani_class cls, const char *name, ani_long value)
```

**Description**

Sets a long value to a static field of a class by its name.<br> This function assigns a long value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The long value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Float()

```c
ani_status (*Class_SetStaticFieldByName_Float)(ani_env *env, ani_class cls, const char *name, ani_float value)
```

**Description**

Sets a float value to a static field of a class by its name.<br> This function assigns a float value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The float value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Double()

```c
ani_status (*Class_SetStaticFieldByName_Double)(ani_env *env, ani_class cls, const char *name, ani_double value)
```

**Description**

Sets a double value to a static field of a class by its name.<br> This function assigns a double value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The double value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_SetStaticFieldByName_Ref()

```c
ani_status (*Class_SetStaticFieldByName_Ref)(ani_env *env, ani_class cls, const char *name, ani_ref value)
```

**Description**

Sets a reference value to a static field of a class by its name.<br> This function assigns a reference value to the specified static field of the given class by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static field. |
| [in] | name The name of the static field to modify. |
| [in] | value The reference value to assign. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Boolean()

```c
ani_status (*Class_CallStaticMethod_Boolean)(ani_env *env, ani_class cls, ani_static_method method,ani_boolean *result, ...)
```

**Description**

Calls a static method with a boolean return type.<br> This function calls the specified static method of a class and retrieves a boolean result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Boolean_A()

```c
ani_status (*Class_CallStaticMethod_Boolean_A)(ani_env *env, ani_class cls, ani_static_method method,ani_boolean *result, const ani_value *args)
```

**Description**

Calls a static method with a boolean return type (array-based).<br> This function calls the specified static method of a class and retrieves a boolean result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Boolean_V()

```c
ani_status (*Class_CallStaticMethod_Boolean_V)(ani_env *env, ani_class cls, ani_static_method method,ani_boolean *result, va_list args)
```

**Description**

Calls a static method with a boolean return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a boolean result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Char()

```c
ani_status (*Class_CallStaticMethod_Char)(ani_env *env, ani_class cls, ani_static_method method, ani_char *result,...)
```

**Description**

Calls a static method with a character return type.<br> This function calls the specified static method of a class and retrieves a character result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the character result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Char_A()

```c
ani_status (*Class_CallStaticMethod_Char_A)(ani_env *env, ani_class cls, ani_static_method method, ani_char *result,const ani_value *args)
```

**Description**

Calls a static method with a character return type (array-based).<br> This function calls the specified static method of a class and retrieves a character result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the character result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Char_V()

```c
ani_status (*Class_CallStaticMethod_Char_V)(ani_env *env, ani_class cls, ani_static_method method, ani_char *result,va_list args)
```

**Description**

Calls a static method with a character return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a character result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the character result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Byte()

```c
ani_status (*Class_CallStaticMethod_Byte)(ani_env *env, ani_class cls, ani_static_method method, ani_byte *result,...)
```

**Description**

Calls a static method with a byte return type.<br> This function calls the specified static method of a class and retrieves a byte result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the byte result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Byte_A()

```c
ani_status (*Class_CallStaticMethod_Byte_A)(ani_env *env, ani_class cls, ani_static_method method, ani_byte *result,const ani_value *args)
```

**Description**

Calls a static method with a byte return type (array-based).<br> This function calls the specified static method of a class and retrieves a byte result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the byte result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Byte_V()

```c
ani_status (*Class_CallStaticMethod_Byte_V)(ani_env *env, ani_class cls, ani_static_method method, ani_byte *result,va_list args)
```

**Description**

Calls a static method with a byte return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a byte result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the byte result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Short()

```c
ani_status (*Class_CallStaticMethod_Short)(ani_env *env, ani_class cls, ani_static_method method, ani_short *result,...)
```

**Description**

Calls a static method with a short return type.<br> This function calls the specified static method of a class and retrieves a short result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the short result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Short_A()

```c
ani_status (*Class_CallStaticMethod_Short_A)(ani_env *env, ani_class cls, ani_static_method method,ani_short *result, const ani_value *args)
```

**Description**

Calls a static method with a short return type (array-based).<br> This function calls the specified static method of a class and retrieves a short result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the short result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Short_V()

```c
ani_status (*Class_CallStaticMethod_Short_V)(ani_env *env, ani_class cls, ani_static_method method,ani_short *result, va_list args)
```

**Description**

Calls a static method with a short return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a short result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the short result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Int()

```c
ani_status (*Class_CallStaticMethod_Int)(ani_env *env, ani_class cls, ani_static_method method, ani_int *result,...)
```

**Description**

Calls a static method with an integer return type.<br> This function calls the specified static method of a class and retrieves an integer result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the integer result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Int_A()

```c
ani_status (*Class_CallStaticMethod_Int_A)(ani_env *env, ani_class cls, ani_static_method method, ani_int *result,const ani_value *args)
```

**Description**

Calls a static method with an integer return type (array-based).<br> This function calls the specified static method of a class and retrieves an integer result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the integer result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Int_V()

```c
ani_status (*Class_CallStaticMethod_Int_V)(ani_env *env, ani_class cls, ani_static_method method, ani_int *result,va_list args)
```

**Description**

Calls a static method with an integer return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves an integer result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the integer result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Long()

```c
ani_status (*Class_CallStaticMethod_Long)(ani_env *env, ani_class cls, ani_static_method method, ani_long *result,...)
```

**Description**

Calls a static method with a long return type.<br> This function calls the specified static method of a class and retrieves a long result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the long result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Long_A()

```c
ani_status (*Class_CallStaticMethod_Long_A)(ani_env *env, ani_class cls, ani_static_method method, ani_long *result,const ani_value *args)
```

**Description**

Calls a static method with a long return type (array-based).<br> This function calls the specified static method of a class and retrieves a long result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the long result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Long_V()

```c
ani_status (*Class_CallStaticMethod_Long_V)(ani_env *env, ani_class cls, ani_static_method method, ani_long *result,va_list args)
```

**Description**

Calls a static method with a long return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a long result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the long result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Float()

```c
ani_status (*Class_CallStaticMethod_Float)(ani_env *env, ani_class cls, ani_static_method method, ani_float *result,...)
```

**Description**

Calls a static method with a float return type.<br> This function calls the specified static method of a class and retrieves a float result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the float result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Float_A()

```c
ani_status (*Class_CallStaticMethod_Float_A)(ani_env *env, ani_class cls, ani_static_method method,ani_float *result, const ani_value *args)
```

**Description**

Calls a static method with a float return type (array-based).<br> This function calls the specified static method of a class and retrieves a float result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the float result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Float_V()

```c
ani_status (*Class_CallStaticMethod_Float_V)(ani_env *env, ani_class cls, ani_static_method method,ani_float *result, va_list args)
```

**Description**

Calls a static method with a float return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a float result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the float result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Double()

```c
ani_status (*Class_CallStaticMethod_Double)(ani_env *env, ani_class cls, ani_static_method method,ani_double *result, ...)
```

**Description**

Calls a static method with a double return type.<br> This function calls the specified static method of a class and retrieves a double result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the double result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Double_A()

```c
ani_status (*Class_CallStaticMethod_Double_A)(ani_env *env, ani_class cls, ani_static_method method,ani_double *result, const ani_value *args)
```

**Description**

Calls a static method with a double return type (array-based).<br> This function calls the specified static method of a class and retrieves a double result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the double result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Double_V()

```c
ani_status (*Class_CallStaticMethod_Double_V)(ani_env *env, ani_class cls, ani_static_method method,ani_double *result, va_list args)
```

**Description**

Calls a static method with a double return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a double result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the double result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Ref()

```c
ani_status (*Class_CallStaticMethod_Ref)(ani_env *env, ani_class cls, ani_static_method method, ani_ref *result,...)
```

**Description**

Calls a static method with a reference return type.<br> This function calls the specified static method of a class and retrieves a reference result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the reference result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Ref_A()

```c
ani_status (*Class_CallStaticMethod_Ref_A)(ani_env *env, ani_class cls, ani_static_method method, ani_ref *result,const ani_value *args)
```

**Description**

Calls a static method with a reference return type (array-based).<br> This function calls the specified static method of a class and retrieves a reference result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the reference result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Ref_V()

```c
ani_status (*Class_CallStaticMethod_Ref_V)(ani_env *env, ani_class cls, ani_static_method method, ani_ref *result,va_list args)
```

**Description**

Calls a static method with a reference return type (variadic arguments).<br> This function calls the specified static method of a class and retrieves a reference result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [out] | result A pointer to store the reference result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Void()

```c
ani_status (*Class_CallStaticMethod_Void)(ani_env *env, ani_class cls, ani_static_method method, ...)
```

**Description**

Calls a static method with no return value.<br> This function calls the specified static method of a class using variadic arguments. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Void_A()

```c
ani_status (*Class_CallStaticMethod_Void_A)(ani_env *env, ani_class cls, ani_static_method method,const ani_value *args)
```

**Description**

Calls a static method with no return value (array-based).<br> This function calls the specified static method of a class using arguments from an array. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethod_Void_V()

```c
ani_status (*Class_CallStaticMethod_Void_V)(ani_env *env, ani_class cls, ani_static_method method, va_list args)
```

**Description**

Calls a static method with no return value (variadic arguments).<br> This function calls the specified static method of a class using a `va_list`. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | method The static method to call. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Boolean()

```c
ani_status (*Class_CallStaticMethodByName_Boolean)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_boolean *result, ...)
```

**Description**

Calls a static method by name with a boolean return type.<br> This function calls the specified static method of a class by its name and retrieves a boolean result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Boolean_A()

```c
ani_status (*Class_CallStaticMethodByName_Boolean_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_boolean *result,const ani_value *args)
```

**Description**

Calls a static method by name with a boolean return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a boolean result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Boolean_V()

```c
ani_status (*Class_CallStaticMethodByName_Boolean_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_boolean *result, va_list args)
```

**Description**

Calls a static method by name with a boolean return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a boolean result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the boolean result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Char()

```c
ani_status (*Class_CallStaticMethodByName_Char)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_char *result, ...)
```

**Description**

Calls a static method by name with a char return type.<br> This function calls the specified static method of a class by its name and retrieves a char result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the char result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Char_A()

```c
ani_status (*Class_CallStaticMethodByName_Char_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_char *result, const ani_value *args)
```

**Description**

Calls a static method by name with a char return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a char result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the char result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Char_V()

```c
ani_status (*Class_CallStaticMethodByName_Char_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_char *result, va_list args)
```

**Description**

Calls a static method by name with a char return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a char result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the char result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Byte()

```c
ani_status (*Class_CallStaticMethodByName_Byte)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_byte *result, ...)
```

**Description**

Calls a static method by name with a byte return type.<br> This function calls the specified static method of a class by its name and retrieves a byte result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the byte result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Byte_A()

```c
ani_status (*Class_CallStaticMethodByName_Byte_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_byte *result, const ani_value *args)
```

**Description**

Calls a static method by name with a byte return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a byte result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the byte result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Byte_V()

```c
ani_status (*Class_CallStaticMethodByName_Byte_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_byte *result, va_list args)
```

**Description**

Calls a static method by name with a byte return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a byte result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the byte result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Short()

```c
ani_status (*Class_CallStaticMethodByName_Short)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_short *result, ...)
```

**Description**

Calls a static method by name with a short return type.<br> This function calls the specified static method of a class by its name and retrieves a short result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the short result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Short_A()

```c
ani_status (*Class_CallStaticMethodByName_Short_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_short *result, const ani_value *args)
```

**Description**

Calls a static method by name with a short return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a short result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the short result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Short_V()

```c
ani_status (*Class_CallStaticMethodByName_Short_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_short *result, va_list args)
```

**Description**

Calls a static method by name with a short return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a short result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the short result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Int()

```c
ani_status (*Class_CallStaticMethodByName_Int)(ani_env *env, ani_class cls, const char *name, const char *signature,ani_int *result, ...)
```

**Description**

Calls a static method by name with a integer return type.<br> This function calls the specified static method of a class by its name and retrieves a integer result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the integer result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Int_A()

```c
ani_status (*Class_CallStaticMethodByName_Int_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_int *result, const ani_value *args)
```

**Description**

Calls a static method by name with a integer return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a integer result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the integer result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Int_V()

```c
ani_status (*Class_CallStaticMethodByName_Int_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_int *result, va_list args)
```

**Description**

Calls a static method by name with a integer return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a integer result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the integer result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Long()

```c
ani_status (*Class_CallStaticMethodByName_Long)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_long *result, ...)
```

**Description**

Calls a static method by name with a long return type.<br> This function calls the specified static method of a class by its name and retrieves a long result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the long result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Long_A()

```c
ani_status (*Class_CallStaticMethodByName_Long_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_long *result, const ani_value *args)
```

**Description**

Calls a static method by name with a long return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a long result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the long result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Long_V()

```c
ani_status (*Class_CallStaticMethodByName_Long_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_long *result, va_list args)
```

**Description**

Calls a static method by name with a long return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a long result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the long result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Float()

```c
ani_status (*Class_CallStaticMethodByName_Float)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_float *result, ...)
```

**Description**

Calls a static method by name with a float return type.<br> This function calls the specified static method of a class by its name and retrieves a float result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the float result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Float_A()

```c
ani_status (*Class_CallStaticMethodByName_Float_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_float *result, const ani_value *args)
```

**Description**

Calls a static method by name with a float return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a float result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the float result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Float_V()

```c
ani_status (*Class_CallStaticMethodByName_Float_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_float *result, va_list args)
```

**Description**

Calls a static method by name with a float return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a float result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the float result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Double()

```c
ani_status (*Class_CallStaticMethodByName_Double)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_double *result, ...)
```

**Description**

Calls a static method by name with a double return type.<br> This function calls the specified static method of a class by its name and retrieves a double result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the double result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Double_A()

```c
ani_status (*Class_CallStaticMethodByName_Double_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_double *result,const ani_value *args)
```

**Description**

Calls a static method by name with a double return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a double result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the double result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Double_V()

```c
ani_status (*Class_CallStaticMethodByName_Double_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_double *result, va_list args)
```

**Description**

Calls a static method by name with a double return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a double result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the double result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Ref()

```c
ani_status (*Class_CallStaticMethodByName_Ref)(ani_env *env, ani_class cls, const char *name, const char *signature,ani_ref *result, ...)
```

**Description**

Calls a static method by name with a reference return type.<br> This function calls the specified static method of a class by its name and retrieves a reference result using variadic arguments.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the reference result. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Ref_A()

```c
ani_status (*Class_CallStaticMethodByName_Ref_A)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_ref *result, const ani_value *args)
```

**Description**

Calls a static method by name with a reference return type (array-based).<br> This function calls the specified static method of a class by its name and retrieves a reference result using arguments from an array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the reference result. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Ref_V()

```c
ani_status (*Class_CallStaticMethodByName_Ref_V)(ani_env *env, ani_class cls, const char *name,const char *signature, ani_ref *result, va_list args)
```

**Description**

Calls a static method by name with a reference return type (variadic arguments).<br> This function calls the specified static method of a class by its name and retrieves a reference result using a `va_list`.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [out] | result A pointer to store the reference result. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Void()

```c
ani_status (*Class_CallStaticMethodByName_Void)(ani_env *env, ani_class cls, const char *name,const char *signature, ...)
```

**Description**

Calls a static method by name with no return value.<br> This function calls the specified static method of a class by its name using variadic arguments. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Void_A()

```c
ani_status (*Class_CallStaticMethodByName_Void_A)(ani_env *env, ani_class cls, const char *name,const char *signature, const ani_value *args)
```

**Description**

Calls a static method by name with no return value (array-based).<br> This function calls the specified static method of a class by its name using arguments from an array. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Class_CallStaticMethodByName_Void_V()

```c
ani_status (*Class_CallStaticMethodByName_Void_V)(ani_env *env, ani_class cls, const char *name,const char *signature, va_list args)
```

**Description**

Calls a static method by name with no return value (variadic arguments).<br> This function calls the specified static method of a class by its name using a `va_list`. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class containing the static method. |
| [in] | name The name of the static method to call. |
| [in] | signature The signature of the static method to call. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Boolean()

```c
ani_status (*Object_GetField_Boolean)(ani_env *env, ani_object object, ani_field field, ani_boolean *result)
```

**Description**

Retrieves a boolean value from a field of an object.<br> This function retrieves the boolean value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the boolean value from. |
| [out] | result A pointer to store the retrieved boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Char()

```c
ani_status (*Object_GetField_Char)(ani_env *env, ani_object object, ani_field field, ani_char *result)
```

**Description**

Retrieves a char value from a field of an object.<br> This function retrieves the char value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the char value from. |
| [out] | result A pointer to store the retrieved char value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Byte()

```c
ani_status (*Object_GetField_Byte)(ani_env *env, ani_object object, ani_field field, ani_byte *result)
```

**Description**

Retrieves a byte value from a field of an object.<br> This function retrieves the byte value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the byte value from. |
| [out] | result A pointer to store the retrieved byte value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Short()

```c
ani_status (*Object_GetField_Short)(ani_env *env, ani_object object, ani_field field, ani_short *result)
```

**Description**

Retrieves a short value from a field of an object.<br> This function retrieves the short value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the short value from. |
| [out] | result A pointer to store the retrieved short value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Int()

```c
ani_status (*Object_GetField_Int)(ani_env *env, ani_object object, ani_field field, ani_int *result)
```

**Description**

Retrieves a integer value from a field of an object.<br> This function retrieves the integer value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the integer value from. |
| [out] | result A pointer to store the retrieved integer value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Long()

```c
ani_status (*Object_GetField_Long)(ani_env *env, ani_object object, ani_field field, ani_long *result)
```

**Description**

Retrieves a long value from a field of an object.<br> This function retrieves the long value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the long value from. |
| [out] | result A pointer to store the retrieved long value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Float()

```c
ani_status (*Object_GetField_Float)(ani_env *env, ani_object object, ani_field field, ani_float *result)
```

**Description**

Retrieves a float value from a field of an object.<br> This function retrieves the float value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the float value from. |
| [out] | result A pointer to store the retrieved float value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Double()

```c
ani_status (*Object_GetField_Double)(ani_env *env, ani_object object, ani_field field, ani_double *result)
```

**Description**

Retrieves a double value from a field of an object.<br> This function retrieves the double value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the double value from. |
| [out] | result A pointer to store the retrieved double value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetField_Ref()

```c
ani_status (*Object_GetField_Ref)(ani_env *env, ani_object object, ani_field field, ani_ref *result)
```

**Description**

Retrieves a reference value from a field of an object.<br> This function retrieves the reference value of the specified field from the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to retrieve the reference value from. |
| [out] | result A pointer to store the retrieved reference value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Boolean()

```c
ani_status (*Object_SetField_Boolean)(ani_env *env, ani_object object, ani_field field, ani_boolean value)
```

**Description**

Sets a boolean value to a field of an object.<br> This function assigns a boolean value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the boolean value to. |
| [in] | value The boolean value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Char()

```c
ani_status (*Object_SetField_Char)(ani_env *env, ani_object object, ani_field field, ani_char value)
```

**Description**

Sets a char value to a field of an object.<br> This function assigns a char value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the char value to. |
| [in] | value The char value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Byte()

```c
ani_status (*Object_SetField_Byte)(ani_env *env, ani_object object, ani_field field, ani_byte value)
```

**Description**

Sets a byte value to a field of an object.<br> This function assigns a byte value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the byte value to. |
| [in] | value The byte value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Short()

```c
ani_status (*Object_SetField_Short)(ani_env *env, ani_object object, ani_field field, ani_short value)
```

**Description**

Sets a short value to a field of an object.<br> This function assigns a short value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the short value to. |
| [in] | value The short value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Int()

```c
ani_status (*Object_SetField_Int)(ani_env *env, ani_object object, ani_field field, ani_int value)
```

**Description**

Sets a integer value to a field of an object.<br> This function assigns a integer value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the integer value to. |
| [in] | value The integer value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Long()

```c
ani_status (*Object_SetField_Long)(ani_env *env, ani_object object, ani_field field, ani_long value)
```

**Description**

Sets a long value to a field of an object.<br> This function assigns a long value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the long value to. |
| [in] | value The long value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Float()

```c
ani_status (*Object_SetField_Float)(ani_env *env, ani_object object, ani_field field, ani_float value)
```

**Description**

Sets a float value to a field of an object.<br> This function assigns a float value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the float value to. |
| [in] | value The float value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Double()

```c
ani_status (*Object_SetField_Double)(ani_env *env, ani_object object, ani_field field, ani_double value)
```

**Description**

Sets a double value to a field of an object.<br> This function assigns a double value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the double value to. |
| [in] | value The double value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetField_Ref()

```c
ani_status (*Object_SetField_Ref)(ani_env *env, ani_object object, ani_field field, ani_ref value)
```

**Description**

Sets a reference value to a field of an object.<br> This function assigns a reference value to the specified field of the given object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | field The field to set the reference value to. |
| [in] | value The reference value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Boolean()

```c
ani_status (*Object_GetFieldByName_Boolean)(ani_env *env, ani_object object, const char *name, ani_boolean *result)
```

**Description**

Retrieves a boolean value from a field of an object by its name.<br> This function retrieves the boolean value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the boolean value from. |
| [out] | result A pointer to store the retrieved boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Char()

```c
ani_status (*Object_GetFieldByName_Char)(ani_env *env, ani_object object, const char *name, ani_char *result)
```

**Description**

Retrieves a char value from a field of an object by its name.<br> This function retrieves the char value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the char value from. |
| [out] | result A pointer to store the retrieved char value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Byte()

```c
ani_status (*Object_GetFieldByName_Byte)(ani_env *env, ani_object object, const char *name, ani_byte *result)
```

**Description**

Retrieves a byte value from a field of an object by its name.<br> This function retrieves the byte value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the byte value from. |
| [out] | result A pointer to store the retrieved byte value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Short()

```c
ani_status (*Object_GetFieldByName_Short)(ani_env *env, ani_object object, const char *name, ani_short *result)
```

**Description**

Retrieves a short value from a field of an object by its name.<br> This function retrieves the short value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the short value from. |
| [out] | result A pointer to store the retrieved short value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Int()

```c
ani_status (*Object_GetFieldByName_Int)(ani_env *env, ani_object object, const char *name, ani_int *result)
```

**Description**

Retrieves a integer value from a field of an object by its name.<br> This function retrieves the integer value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the integer value from. |
| [out] | result A pointer to store the retrieved integer value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Long()

```c
ani_status (*Object_GetFieldByName_Long)(ani_env *env, ani_object object, const char *name, ani_long *result)
```

**Description**

Retrieves a long value from a field of an object by its name.<br> This function retrieves the long value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the long value from. |
| [out] | result A pointer to store the retrieved long value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Float()

```c
ani_status (*Object_GetFieldByName_Float)(ani_env *env, ani_object object, const char *name, ani_float *result)
```

**Description**

Retrieves a float value from a field of an object by its name.<br> This function retrieves the float value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the float value from. |
| [out] | result A pointer to store the retrieved float value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Double()

```c
ani_status (*Object_GetFieldByName_Double)(ani_env *env, ani_object object, const char *name, ani_double *result)
```

**Description**

Retrieves a double value from a field of an object by its name.<br> This function retrieves the double value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the double value from. |
| [out] | result A pointer to store the retrieved double value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetFieldByName_Ref()

```c
ani_status (*Object_GetFieldByName_Ref)(ani_env *env, ani_object object, const char *name, ani_ref *result)
```

**Description**

Retrieves a reference value from a field of an object by its name.<br> This function retrieves the reference value of the specified field from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to retrieve the reference value from. |
| [out] | result A pointer to store the retrieved reference value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Boolean()

```c
ani_status (*Object_SetFieldByName_Boolean)(ani_env *env, ani_object object, const char *name, ani_boolean value)
```

**Description**

Sets a boolean value to a field of an object by its name.<br> This function assigns a boolean value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the boolean value to. |
| [in] | value The boolean value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Char()

```c
ani_status (*Object_SetFieldByName_Char)(ani_env *env, ani_object object, const char *name, ani_char value)
```

**Description**

Sets a char value to a field of an object by its name.<br> This function assigns a char value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the char value to. |
| [in] | value The char value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Byte()

```c
ani_status (*Object_SetFieldByName_Byte)(ani_env *env, ani_object object, const char *name, ani_byte value)
```

**Description**

Sets a byte value to a field of an object by its name.<br> This function assigns a byte value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the byte value to. |
| [in] | value The byte value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Short()

```c
ani_status (*Object_SetFieldByName_Short)(ani_env *env, ani_object object, const char *name, ani_short value)
```

**Description**

Sets a short value to a field of an object by its name.<br> This function assigns a short value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the short value to. |
| [in] | value The short value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Int()

```c
ani_status (*Object_SetFieldByName_Int)(ani_env *env, ani_object object, const char *name, ani_int value)
```

**Description**

Sets a integer value to a field of an object by its name.<br> This function assigns a integer value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the integer value to. |
| [in] | value The integer value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Long()

```c
ani_status (*Object_SetFieldByName_Long)(ani_env *env, ani_object object, const char *name, ani_long value)
```

**Description**

Sets a long value to a field of an object by its name.<br> This function assigns a long value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the long value to. |
| [in] | value The long value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Float()

```c
ani_status (*Object_SetFieldByName_Float)(ani_env *env, ani_object object, const char *name, ani_float value)
```

**Description**

Sets a float value to a field of an object by its name.<br> This function assigns a float value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the float value to. |
| [in] | value The float value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Double()

```c
ani_status (*Object_SetFieldByName_Double)(ani_env *env, ani_object object, const char *name, ani_double value)
```

**Description**

Sets a double value to a field of an object by its name.<br> This function assigns a double value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the double value to. |
| [in] | value The double value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetFieldByName_Ref()

```c
ani_status (*Object_SetFieldByName_Ref)(ani_env *env, ani_object object, const char *name, ani_ref value)
```

**Description**

Sets a reference value to a field of an object by its name.<br> This function assigns a reference value to the specified field of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the field. |
| [in] | name The name of the field to set the reference value to. |
| [in] | value The reference value to assign to the field. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Boolean()

```c
ani_status (*Object_GetPropertyByName_Boolean)(ani_env *env, ani_object object, const char *name,ani_boolean *result)
```

**Description**

Retrieves a boolean value from a property of an object by its name.<br> This function retrieves the boolean value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the boolean value from. |
| [out] | result A pointer to store the retrieved boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Char()

```c
ani_status (*Object_GetPropertyByName_Char)(ani_env *env, ani_object object, const char *name, ani_char *result)
```

**Description**

Retrieves a char value from a property of an object by its name.<br> This function retrieves the char value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the char value from. |
| [out] | result A pointer to store the retrieved char value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Byte()

```c
ani_status (*Object_GetPropertyByName_Byte)(ani_env *env, ani_object object, const char *name, ani_byte *result)
```

**Description**

Retrieves a byte value from a property of an object by its name.<br> This function retrieves the byte value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the byte value from. |
| [out] | result A pointer to store the retrieved byte value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Short()

```c
ani_status (*Object_GetPropertyByName_Short)(ani_env *env, ani_object object, const char *name, ani_short *result)
```

**Description**

Retrieves a short value from a property of an object by its name.<br> This function retrieves the short value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the short value from. |
| [out] | result A pointer to store the retrieved short value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Int()

```c
ani_status (*Object_GetPropertyByName_Int)(ani_env *env, ani_object object, const char *name, ani_int *result)
```

**Description**

Retrieves a integer value from a property of an object by its name.<br> This function retrieves the integer value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the integer value from. |
| [out] | result A pointer to store the retrieved integer value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Long()

```c
ani_status (*Object_GetPropertyByName_Long)(ani_env *env, ani_object object, const char *name, ani_long *result)
```

**Description**

Retrieves a long value from a property of an object by its name.<br> This function retrieves the long value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the long value from. |
| [out] | result A pointer to store the retrieved long value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Float()

```c
ani_status (*Object_GetPropertyByName_Float)(ani_env *env, ani_object object, const char *name, ani_float *result)
```

**Description**

Retrieves a float value from a property of an object by its name.<br> This function retrieves the float value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the float value from. |
| [out] | result A pointer to store the retrieved float value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Double()

```c
ani_status (*Object_GetPropertyByName_Double)(ani_env *env, ani_object object, const char *name,ani_double *result)
```

**Description**

Retrieves a double value from a property of an object by its name.<br> This function retrieves the double value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the double value from. |
| [out] | result A pointer to store the retrieved double value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_GetPropertyByName_Ref()

```c
ani_status (*Object_GetPropertyByName_Ref)(ani_env *env, ani_object object, const char *name, ani_ref *result)
```

**Description**

Retrieves a reference value from a property of an object by its name.<br> This function retrieves the reference value of the specified property from the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to retrieve the reference value from. |
| [out] | result A pointer to store the retrieved reference value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Boolean()

```c
ani_status (*Object_SetPropertyByName_Boolean)(ani_env *env, ani_object object, const char *name,ani_boolean value)
```

**Description**

Sets a boolean value to a property of an object by its name.<br> This function assigns a boolean value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the boolean value to. |
| [in] | value The boolean value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Char()

```c
ani_status (*Object_SetPropertyByName_Char)(ani_env *env, ani_object object, const char *name, ani_char value)
```

**Description**

Sets a char value to a property of an object by its name.<br> This function assigns a char value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the char value to. |
| [in] | value The char value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Byte()

```c
ani_status (*Object_SetPropertyByName_Byte)(ani_env *env, ani_object object, const char *name, ani_byte value)
```

**Description**

Sets a byte value to a property of an object by its name.<br> This function assigns a byte value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the byte value to. |
| [in] | value The byte value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Short()

```c
ani_status (*Object_SetPropertyByName_Short)(ani_env *env, ani_object object, const char *name, ani_short value)
```

**Description**

Sets a short value to a property of an object by its name.<br> This function assigns a short value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the short value to. |
| [in] | value The short value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Int()

```c
ani_status (*Object_SetPropertyByName_Int)(ani_env *env, ani_object object, const char *name, ani_int value)
```

**Description**

Sets a integer value to a property of an object by its name.<br> This function assigns a integer value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the integer value to. |
| [in] | value The integer value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Long()

```c
ani_status (*Object_SetPropertyByName_Long)(ani_env *env, ani_object object, const char *name, ani_long value)
```

**Description**

Sets a long value to a property of an object by its name.<br> This function assigns a long value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the long value to. |
| [in] | value The long value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Float()

```c
ani_status (*Object_SetPropertyByName_Float)(ani_env *env, ani_object object, const char *name, ani_float value)
```

**Description**

Sets a float value to a property of an object by its name.<br> This function assigns a float value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the float value to. |
| [in] | value The float value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Double()

```c
ani_status (*Object_SetPropertyByName_Double)(ani_env *env, ani_object object, const char *name, ani_double value)
```

**Description**

Sets a double value to a property of an object by its name.<br> This function assigns a double value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the double value to. |
| [in] | value The double value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_SetPropertyByName_Ref()

```c
ani_status (*Object_SetPropertyByName_Ref)(ani_env *env, ani_object object, const char *name, ani_ref value)
```

**Description**

Sets a reference value to a property of an object by its name.<br> This function assigns a reference value to the specified property of the given object by its name.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object containing the property. |
| [in] | name The name of the property to set the reference value to. |
| [in] | value The reference value to assign to the property. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Boolean()

```c
ani_status (*Object_CallMethod_Boolean)(ani_env *env, ani_object object, ani_method method, ani_boolean *result,...)
```

**Description**

Calls a method on an object and retrieves a boolean return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the boolean return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Boolean_A()

```c
ani_status (*Object_CallMethod_Boolean_A)(ani_env *env, ani_object object, ani_method method, ani_boolean *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a boolean return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the boolean return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Boolean_V()

```c
ani_status (*Object_CallMethod_Boolean_V)(ani_env *env, ani_object object, ani_method method, ani_boolean *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a boolean return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the boolean return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Char()

```c
ani_status (*Object_CallMethod_Char)(ani_env *env, ani_object object, ani_method method, ani_char *result, ...)
```

**Description**

Calls a method on an object and retrieves a char return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a char result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the char return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Char_A()

```c
ani_status (*Object_CallMethod_Char_A)(ani_env *env, ani_object object, ani_method method, ani_char *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a char return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a char result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the char return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Char_V()

```c
ani_status (*Object_CallMethod_Char_V)(ani_env *env, ani_object object, ani_method method, ani_char *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a char return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a char result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the char return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Byte()

```c
ani_status (*Object_CallMethod_Byte)(ani_env *env, ani_object object, ani_method method, ani_byte *result, ...)
```

**Description**

Calls a method on an object and retrieves a byte return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the byte return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Byte_A()

```c
ani_status (*Object_CallMethod_Byte_A)(ani_env *env, ani_object object, ani_method method, ani_byte *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a byte return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the byte return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Byte_V()

```c
ani_status (*Object_CallMethod_Byte_V)(ani_env *env, ani_object object, ani_method method, ani_byte *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a byte return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the byte return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Short()

```c
ani_status (*Object_CallMethod_Short)(ani_env *env, ani_object object, ani_method method, ani_short *result, ...)
```

**Description**

Calls a method on an object and retrieves a short return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the short return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Short_A()

```c
ani_status (*Object_CallMethod_Short_A)(ani_env *env, ani_object object, ani_method method, ani_short *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a short return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the short return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Short_V()

```c
ani_status (*Object_CallMethod_Short_V)(ani_env *env, ani_object object, ani_method method, ani_short *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a short return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the short return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Int()

```c
ani_status (*Object_CallMethod_Int)(ani_env *env, ani_object object, ani_method method, ani_int *result, ...)
```

**Description**

Calls a method on an object and retrieves a integer return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the integer return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Int_A()

```c
ani_status (*Object_CallMethod_Int_A)(ani_env *env, ani_object object, ani_method method, ani_int *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a integer return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the integer return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Int_V()

```c
ani_status (*Object_CallMethod_Int_V)(ani_env *env, ani_object object, ani_method method, ani_int *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a integer return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the integer return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Long()

```c
ani_status (*Object_CallMethod_Long)(ani_env *env, ani_object object, ani_method method, ani_long *result, ...)
```

**Description**

Calls a method on an object and retrieves a long return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the long return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Long_A()

```c
ani_status (*Object_CallMethod_Long_A)(ani_env *env, ani_object object, ani_method method, ani_long *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a long return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the long return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Long_V()

```c
ani_status (*Object_CallMethod_Long_V)(ani_env *env, ani_object object, ani_method method, ani_long *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a long return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the long return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Float()

```c
ani_status (*Object_CallMethod_Float)(ani_env *env, ani_object object, ani_method method, ani_float *result, ...)
```

**Description**

Calls a method on an object and retrieves a float return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the float return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Float_A()

```c
ani_status (*Object_CallMethod_Float_A)(ani_env *env, ani_object object, ani_method method, ani_float *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a float return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the float return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Float_V()

```c
ani_status (*Object_CallMethod_Float_V)(ani_env *env, ani_object object, ani_method method, ani_float *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a float return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the float return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Double()

```c
ani_status (*Object_CallMethod_Double)(ani_env *env, ani_object object, ani_method method, ani_double *result, ...)
```

**Description**

Calls a method on an object and retrieves a double return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the double return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Double_A()

```c
ani_status (*Object_CallMethod_Double_A)(ani_env *env, ani_object object, ani_method method, ani_double *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a double return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the double return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Double_V()

```c
ani_status (*Object_CallMethod_Double_V)(ani_env *env, ani_object object, ani_method method, ani_double *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a double return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the double return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Ref()

```c
ani_status (*Object_CallMethod_Ref)(ani_env *env, ani_object object, ani_method method, ani_ref *result, ...)
```

**Description**

Calls a method on an object and retrieves a reference return value.<br> This function calls the specified method of an object using variadic arguments and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the reference return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Ref_A()

```c
ani_status (*Object_CallMethod_Ref_A)(ani_env *env, ani_object object, ani_method method, ani_ref *result,const ani_value *args)
```

**Description**

Calls a method on an object and retrieves a reference return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the reference return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Ref_V()

```c
ani_status (*Object_CallMethod_Ref_V)(ani_env *env, ani_object object, ani_method method, ani_ref *result,va_list args)
```

**Description**

Calls a method on an object and retrieves a reference return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list` and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [out] | result A pointer to store the reference return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Void()

```c
ani_status (*Object_CallMethod_Void)(ani_env *env, ani_object object, ani_method method, ...)
```

**Description**

Calls a method on an object with no return value.<br> This function calls the specified method of an object using variadic arguments. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Void_A()

```c
ani_status (*Object_CallMethod_Void_A)(ani_env *env, ani_object object, ani_method method, const ani_value *args)
```

**Description**

Calls a method on an object with no return value (array-based).<br> This function calls the specified method of an object using arguments provided in an array. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethod_Void_V()

```c
ani_status (*Object_CallMethod_Void_V)(ani_env *env, ani_object object, ani_method method, va_list args)
```

**Description**

Calls a method on an object with no return value (variadic arguments).<br> This function calls the specified method of an object using a `va_list`. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | method The method to call. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Boolean()

```c
ani_status (*Object_CallMethodByName_Boolean)(ani_env *env, ani_object object, const char *name,const char *signature, ani_boolean *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a boolean return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the boolean return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Boolean_A()

```c
ani_status (*Object_CallMethodByName_Boolean_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_boolean *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a boolean return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the boolean return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Boolean_V()

```c
ani_status (*Object_CallMethodByName_Boolean_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_boolean *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a boolean return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a boolean result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the boolean return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Char()

```c
ani_status (*Object_CallMethodByName_Char)(ani_env *env, ani_object object, const char *name, const char *signature,ani_char *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a char return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a char result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the char return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Char_A()

```c
ani_status (*Object_CallMethodByName_Char_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_char *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a char return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a char result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the char return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Char_V()

```c
ani_status (*Object_CallMethodByName_Char_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_char *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a char return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a char result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the char return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Byte()

```c
ani_status (*Object_CallMethodByName_Byte)(ani_env *env, ani_object object, const char *name, const char *signature,ani_byte *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a byte return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the byte return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Byte_A()

```c
ani_status (*Object_CallMethodByName_Byte_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_byte *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a byte return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the byte return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Byte_V()

```c
ani_status (*Object_CallMethodByName_Byte_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_byte *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a byte return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a byte result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the byte return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Short()

```c
ani_status (*Object_CallMethodByName_Short)(ani_env *env, ani_object object, const char *name,const char *signature, ani_short *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a short return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the short return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Short_A()

```c
ani_status (*Object_CallMethodByName_Short_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_short *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a short return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the short return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Short_V()

```c
ani_status (*Object_CallMethodByName_Short_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_short *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a short return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a short result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the short return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Int()

```c
ani_status (*Object_CallMethodByName_Int)(ani_env *env, ani_object object, const char *name, const char *signature,ani_int *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a integer return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the integer return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Int_A()

```c
ani_status (*Object_CallMethodByName_Int_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_int *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a integer return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the integer return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Int_V()

```c
ani_status (*Object_CallMethodByName_Int_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_int *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a integer return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a integer result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the integer return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Long()

```c
ani_status (*Object_CallMethodByName_Long)(ani_env *env, ani_object object, const char *name, const char *signature,ani_long *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a long return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the long return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Long_A()

```c
ani_status (*Object_CallMethodByName_Long_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_long *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a long return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the long return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Long_V()

```c
ani_status (*Object_CallMethodByName_Long_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_long *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a long return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a long result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the long return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Float()

```c
ani_status (*Object_CallMethodByName_Float)(ani_env *env, ani_object object, const char *name,const char *signature, ani_float *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a float return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the float return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Float_A()

```c
ani_status (*Object_CallMethodByName_Float_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_float *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a float return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the float return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Float_V()

```c
ani_status (*Object_CallMethodByName_Float_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_float *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a float return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a float result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the float return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Double()

```c
ani_status (*Object_CallMethodByName_Double)(ani_env *env, ani_object object, const char *name,const char *signature, ani_double *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a double return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the double return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Double_A()

```c
ani_status (*Object_CallMethodByName_Double_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_double *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a double return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the double return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Double_V()

```c
ani_status (*Object_CallMethodByName_Double_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_double *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a double return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a double result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the double return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Ref()

```c
ani_status (*Object_CallMethodByName_Ref)(ani_env *env, ani_object object, const char *name, const char *signature,ani_ref *result, ...)
```

**Description**

Calls a method by name on an object and retrieves a reference return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the reference return value. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Ref_A()

```c
ani_status (*Object_CallMethodByName_Ref_A)(ani_env *env, ani_object object, const char *name,const char *signature, ani_ref *result, const ani_value *args)
```

**Description**

Calls a method by name on an object and retrieves a reference return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the reference return value. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Ref_V()

```c
ani_status (*Object_CallMethodByName_Ref_V)(ani_env *env, ani_object object, const char *name,const char *signature, ani_ref *result, va_list args)
```

**Description**

Calls a method by name on an object and retrieves a reference return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list` and retrieves a reference result.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [out] | result A pointer to store the reference return value. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Void()

```c
ani_status (*Object_CallMethodByName_Void)(ani_env *env, ani_object object, const char *name, const char *signature,...)
```

**Description**

Calls a method by name on an object with no return value.<br> This function calls the specified method by its name and signature on an object using variadic arguments. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [in] | ... Variadic arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Void_A()

```c
ani_status (*Object_CallMethodByName_Void_A)(ani_env *env, ani_object object, const char *name,const char *signature, const ani_value *args)
```

**Description**

Calls a method by name on an object with no return value (array-based).<br> This function calls the specified method by its name and signature on an object using arguments provided in an array. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [in] | args An array of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Object_CallMethodByName_Void_V()

```c
ani_status (*Object_CallMethodByName_Void_V)(ani_env *env, ani_object object, const char *name,const char *signature, va_list args)
```

**Description**

Calls a method by name on an object with no return value (variadic arguments).<br> This function calls the specified method by its name and signature on an object using a `va_list`. The method does not return a value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | object The object on which the method is to be called. |
| [in] | name The name of the method to call. |
| [in] | signature The signature of the method to call. |
| [in] | args A `va_list` of arguments to pass to the method. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetNumberOfItems()

```c
ani_status (*TupleValue_GetNumberOfItems)(ani_env *env, ani_tuple_value tuple_value, ani_size *result)
```

**Description**

Retrieves the number of items in a tuple value.<br> This function retrieves the total number of items in the specified tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value whose number of items is to be retrieved. |
| [out] | result A pointer to store the number of items. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Boolean()

```c
ani_status (*TupleValue_GetItem_Boolean)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_boolean *result)
```

**Description**

Retrieves a boolean item from a tuple value.<br> This function retrieves the boolean value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the boolean value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Char()

```c
ani_status (*TupleValue_GetItem_Char)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_char *result)
```

**Description**

Retrieves a char item from a tuple value.<br> This function retrieves the char value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the char value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Byte()

```c
ani_status (*TupleValue_GetItem_Byte)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_byte *result)
```

**Description**

Retrieves a byte item from a tuple value.<br> This function retrieves the byte value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the byte value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Short()

```c
ani_status (*TupleValue_GetItem_Short)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_short *result)
```

**Description**

Retrieves a short item from a tuple value.<br> This function retrieves the short value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the short value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Int()

```c
ani_status (*TupleValue_GetItem_Int)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_int *result)
```

**Description**

Retrieves a integer item from a tuple value.<br> This function retrieves the integer value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the integer value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Long()

```c
ani_status (*TupleValue_GetItem_Long)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_long *result)
```

**Description**

Retrieves a long item from a tuple value.<br> This function retrieves the long value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the long value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Float()

```c
ani_status (*TupleValue_GetItem_Float)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_float *result)
```

**Description**

Retrieves a float item from a tuple value.<br> This function retrieves the float value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the float value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Double()

```c
ani_status (*TupleValue_GetItem_Double)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_double *result)
```

**Description**

Retrieves a double item from a tuple value.<br> This function retrieves the double value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the double value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_GetItem_Ref()

```c
ani_status (*TupleValue_GetItem_Ref)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_ref *result)
```

**Description**

Retrieves a reference item from a tuple value.<br> This function retrieves the reference value of the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [out] | result A pointer to store the reference value of the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Boolean()

```c
ani_status (*TupleValue_SetItem_Boolean)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_boolean value)
```

**Description**

Sets a boolean value to an item in a tuple value.<br> This function assigns a boolean value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The boolean value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Char()

```c
ani_status (*TupleValue_SetItem_Char)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_char value)
```

**Description**

Sets a char value to an item in a tuple value.<br> This function assigns a char value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The char value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Byte()

```c
ani_status (*TupleValue_SetItem_Byte)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_byte value)
```

**Description**

Sets a byte value to an item in a tuple value.<br> This function assigns a byte value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The byte value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Short()

```c
ani_status (*TupleValue_SetItem_Short)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_short value)
```

**Description**

Sets a short value to an item in a tuple value.<br> This function assigns a short value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The short value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Int()

```c
ani_status (*TupleValue_SetItem_Int)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_int value)
```

**Description**

Sets a integer value to an item in a tuple value.<br> This function assigns a integer value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The integer value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Long()

```c
ani_status (*TupleValue_SetItem_Long)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_long value)
```

**Description**

Sets a long value to an item in a tuple value.<br> This function assigns a long value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The long value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Float()

```c
ani_status (*TupleValue_SetItem_Float)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_float value)
```

**Description**

Sets a float value to an item in a tuple value.<br> This function assigns a float value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The float value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Double()

```c
ani_status (*TupleValue_SetItem_Double)(ani_env *env, ani_tuple_value tuple_value, ani_size index,ani_double value)
```

**Description**

Sets a double value to an item in a tuple value.<br> This function assigns a double value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The double value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### TupleValue_SetItem_Ref()

```c
ani_status (*TupleValue_SetItem_Ref)(ani_env *env, ani_tuple_value tuple_value, ani_size index, ani_ref value)
```

**Description**

Sets a reference value to an item in a tuple value.<br> This function assigns a reference value to the item at the specified index in the tuple value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | tuple_value The tuple value containing the item. |
| [in] | index The index of the item. |
| [in] | value The reference value to assign to the item. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### GlobalReference_Create()

```c
ani_status (*GlobalReference_Create)(ani_env *env, ani_ref ref, ani_ref *result)
```

**Description**

Creates a global reference.<br> This function creates a global reference from a local reference.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ref The local reference to convert to a global reference. |
| [out] | result A pointer to store the created global reference. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### GlobalReference_Delete()

```c
ani_status (*GlobalReference_Delete)(ani_env *env, ani_ref gref)
```

**Description**

Deletes a global reference.<br> This function deletes the specified global reference, releasing all associated resources.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | gref The global reference to delete. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### WeakReference_Create()

```c
ani_status (*WeakReference_Create)(ani_env *env, ani_ref ref, ani_wref *result)
```

**Description**

Creates a weak reference.<br> This function creates a weak reference from a local reference.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | ref The local reference to convert to a weak reference. |
| [out] | result A pointer to store the created weak reference. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### WeakReference_Delete()

```c
ani_status (*WeakReference_Delete)(ani_env *env, ani_wref wref)
```

**Description**

Deletes a weak reference.<br> This function deletes the specified weak reference, releasing all associated resources.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | wref The weak reference to delete. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### WeakReference_GetReference()

```c
ani_status (*WeakReference_GetReference)(ani_env *env, ani_wref wref, ani_boolean *was_released_result,ani_ref *ref_result)
```

**Description**

Retrieves the local reference associated with a weak reference.<br> This function retrieves the local reference that corresponds to the specified weak reference.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | wref The weak reference to query. |
| [out] | was_released_result A pointer to boolean flag which indicates that wref is GC collected. |
| [out] | ref_result A pointer to store the retrieved local reference. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### CreateArrayBuffer()

```c
ani_status (*CreateArrayBuffer)(ani_env *env, size_t length, void **data_result,ani_arraybuffer *arraybuffer_result)
```

**Description**

Creates a new array buffer.<br> This function creates a new array buffer with the specified length and returns a pointer to the allocated data.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | length The length of the array buffer in bytes. |
| [out] | data_result A pointer to store the allocated data of the array buffer. |
| [out] | arraybuffer_result A pointer to store the created array buffer object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ArrayBuffer_GetInfo()

```c
ani_status (*ArrayBuffer_GetInfo)(ani_env *env, ani_arraybuffer arraybuffer, void **data_result,size_t *length_result)
```

**Description**

Retrieves information about an array buffer.<br> This function retrieves the data pointer and length of the specified array buffer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | arraybuffer The array buffer to query. |
| [out] | data_result A pointer to store the data of the array buffer. |
| [out] | length_result A pointer to store the length of the array buffer in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Promise_New()

```c
ani_status (*Promise_New)(ani_env *env, ani_resolver *result_resolver, ani_object *result_promise)
```

**Description**

Creates a new Promise.<br> This function creates a new promise and a resolver to manage it.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [out] | result_resolver A pointer to store the created resolver. |
| [out] | result_promise A pointer to store the created promise. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### PromiseResolver_Resolve()

```c
ani_status (*PromiseResolver_Resolve)(ani_env *env, ani_resolver resolver, ani_ref resolution)
```

**Description**

Resolves a promise.<br> This function resolves a promise by way of the resolver with which it is associated and queues promise `then` callbacks.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | resolver A resolver whose associated promise to resolve. |
| [in] | resolution A reference with which to resolve the promise. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure.      The `resolver` is freed upon successful completion. |

### PromiseResolver_Reject()

```c
ani_status (*PromiseResolver_Reject)(ani_env *env, ani_resolver resolver, ani_error rejection)
void *reserved4void *reserved5void *reserved6void *reserved7void *reserved8void *reserved9void *reserved10void *reserved11void *reserved12void *reserved13
```

**Description**

Rejects a promise.<br> This function rejects a promise by way of the resolver with which it is associated and queues promise `catch` callbacks.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | resolver A resolver whose associated promise to resolve. |
| [in] | rejection An error with which to reject the promise. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure.      The `resolver` is freed upon successful completion. |

### Class_BindStaticNativeMethods()

```c
ani_status (*Class_BindStaticNativeMethods)(ani_env *env, ani_class cls, const ani_native_function *methods,ani_size nr_methods)
```

**Description**

Binds static native methods to a class.<br> This function binds an array of static native methods to the specified class.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | cls The class to which the native methods will be bound. |
| [in] | methods A pointer to an array of static native methods to bind. |
| [in] | nr_methods The number of static native methods in the array. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Box_Boolean()

```c
ani_status (*Primitive_Box_Boolean)(ani_env *env, ani_boolean value, ani_object *result)
```

**Description**

Box a boolean value into an object.<br> This function boxes a boolean value into an object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | value The boolean value to be boxed. |
| [out] | result A pointer to restore the resulting boxed object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Unbox_Boolean()

```c
ani_status (*Primitive_Unbox_Boolean)(ani_env *env, ani_object obj, ani_boolean *result)
```

**Description**

Unbox a boolean object into a boolean value.<br> This function unboxes a boolean object into a boolean value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | obj The obj to be unboxed. |
| [out] | result A pointer to restore the resulting unboxed boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Box_Byte()

```c
ani_status (*Primitive_Box_Byte)(ani_env *env, ani_byte value, ani_object *result)
```

**Description**

Box a byte value into an object.<br> This function boxes a byte value into an object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | value The byte value to be boxed. |
| [out] | result A pointer to restore the resulting boxed object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Unbox_Byte()

```c
ani_status (*Primitive_Unbox_Byte)(ani_env *env, ani_object obj, ani_byte *result)
```

**Description**

Unbox a byte object into a byte value.<br> This function unboxes a byte object into a byte value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | obj The obj to be unboxed. |
| [out] | result A pointer to restore the resulting unboxed byte value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Box_Char()

```c
ani_status (*Primitive_Box_Char)(ani_env *env, ani_char value, ani_object *result)
```

**Description**

Box a char value into an object.<br> This function boxes a char value into an object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | value The char value to be boxed. |
| [out] | result A pointer to restore the resulting boxed object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Unbox_Char()

```c
ani_status (*Primitive_Unbox_Char)(ani_env *env, ani_object obj, ani_char *result)
```

**Description**

Unbox a char object into a char value.<br> This function unboxes a char object into a char value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | obj The obj to be unboxed. |
| [out] | result A pointer to restore the resulting unboxed char value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Box_Short()

```c
ani_status (*Primitive_Box_Short)(ani_env *env, ani_short value, ani_object *result)
```

**Description**

Box a short value into an object.<br> This function boxes a short value into an object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | value The short value to be boxed. |
| [out] | result A pointer to restore the resulting boxed object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Unbox_Short()

```c
ani_status (*Primitive_Unbox_Short)(ani_env *env, ani_object obj, ani_short *result)
```

**Description**

Unbox a short object into a short value.<br> This function unboxes a short object into a short value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | obj The obj to be unboxed. |
| [out] | result A pointer to restore the resulting unboxed short value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Box_Int()

```c
ani_status (*Primitive_Box_Int)(ani_env *env, ani_int value, ani_object *result)
```

**Description**

Box a int value into an object.<br> This function boxes a int value into an object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | value The int value to be boxed. |
| [out] | result A pointer to restore the resulting boxed object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Unbox_Int()

```c
ani_status (*Primitive_Unbox_Int)(ani_env *env, ani_object obj, ani_int *result)
```

**Description**

Unbox a int object into a int value.<br> This function unboxes a int object into a int value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | obj The obj to be unboxed. |
| [out] | result A pointer to restore the resulting unboxed int value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Box_Long()

```c
ani_status (*Primitive_Box_Long)(ani_env *env, ani_long value, ani_object *result)
```

**Description**

Box a long value into an object.<br> This function boxes a long value into an object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | value The long value to be boxed. |
| [out] | result A pointer to restore the resulting boxed object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Unbox_Long()

```c
ani_status (*Primitive_Unbox_Long)(ani_env *env, ani_object obj, ani_long *result)
```

**Description**

Unbox a long object into a long value.<br> This function unboxes a long object into a long value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | obj The obj to be unboxed. |
| [out] | result A pointer to restore the resulting unboxed long value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Box_Float()

```c
ani_status (*Primitive_Box_Float)(ani_env *env, ani_float value, ani_object *result)
```

**Description**

Box a float value into an object.<br> This function boxes a float value into an object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | value The float value to be boxed. |
| [out] | result A pointer to restore the resulting boxed object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Unbox_Float()

```c
ani_status (*Primitive_Unbox_Float)(ani_env *env, ani_object obj, ani_float *result)
```

**Description**

Unbox a float object into a float value.<br> This function unboxes a float object into a float value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | obj The obj to be unboxed. |
| [out] | result A pointer to restore the resulting unboxed float value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Box_Double()

```c
ani_status (*Primitive_Box_Double)(ani_env *env, ani_double value, ani_object *result)
```

**Description**

Box a double value into an object.<br> This function boxes a double value into an object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | value The double value to be boxed. |
| [out] | result A pointer to restore the resulting boxed object. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### Primitive_Unbox_Double()

```c
ani_status (*Primitive_Unbox_Double)(ani_env *env, ani_object obj, ani_double *result)
```

**Description**

Unbox a double object into a double value.<br> This function unboxes a double object into a double value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | obj The obj to be unboxed. |
| [out] | result A pointer to restore the resulting unboxed double value. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |

### ValueArray_GetLength()

```c
ani_status (*ValueArray_GetLength)(ani_env *env, ani_valuearray array, ani_size *result)
```

**Description**

Retrieves the length of a ValueArray.<br> This function retrieves the length of the specified ValueArray.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [in] | env A pointer to the environment structure. |
| [in] | array The ValueArray whose length is to be retrieved. |
| [out] | result A pointer to store the length of the ValueArray. |

**Returns**:

| Type | Description |
| -- | -- |
| ani_status | Returns a status code of type `ani_status` indicating success or failure. |


