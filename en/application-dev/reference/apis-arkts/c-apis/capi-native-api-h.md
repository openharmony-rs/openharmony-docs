# native_api.h

## Overview

Defines native api of ArkTS native module.

**Library**: libace_napi.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Related module**: [ArkTS_Napi_NativeModule](capi-arkts-napi-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [napi_critical_scope\_\_*](capi-arkts-napi-nativemodule-napi-critical-scope--8h.md) | napi_critical_scope | Native critical scope provides a scope within that an ArkTS string buffer cache can be obtained. |
| [napi_strong_ref\_\_*](capi-arkts-napi-nativemodule-napi-strong-ref--8h.md) | napi_strong_ref | Native strong reference of an ArkTS object. |
| [napi_callsite_info\_\_*](capi-arkts-napi-nativemodule-napi-callsite-info--8h.md) | napi_callsite_info | Callsite info handle for caching inline cache (IC) information of property access. |
| [napi_sendable_ref\_\_*](capi-arkts-napi-nativemodule-napi-sendable-ref--8h.md) | napi_sendable_ref | Native strong sendable reference of an sendable ArkTS object. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void* (\*napi_native_binding_detach_callback)(napi_env env, void* native_object, void* hint)](#napi_native_binding_detach_callback) | napi_native_binding_detach_callback | Native detach callback of napi_coerce_to_native_binding_object that can be used to detach the ArkTS object and the native object. |
| [typedef napi_value (\*napi_native_binding_attach_callback)(napi_env env, void* native_object, void* hint)

NAPI_EXTERN napi_status napi_run_script_path(napi_env env, const char* path, napi_value* result)
NAPI_EXTERN napi_status napi_queue_async_work_with_qos(napi_env env, napi_async_work work, napi_qos_t qos)](#) | - | Native attach callback of napi_coerce_to_native_binding_object that can be used to bind the ArkTS object and the native object. |
| [typedef void (\*napi_finalize_callback)(void* finalize_data, void* finalize_hint)](#napi_finalize_callback) | napi_finalize_callback | Native finalize callback is utilized to recycle native object resource. |
| [NAPI_EXTERN napi_status napi_load_module(napi_env env, const char* path, napi_value* result)](#napi_load_module) | - | Loads an .abc file as a module. This API returns the namespace of the module. |
| [NAPI_EXTERN napi_status napi_set_instance_data(napi_env env, void* data, napi_finalize finalize_cb, void* finalize_hint)](#napi_set_instance_data) | - | Associates data with the currently running environment. |
| [NAPI_EXTERN napi_status napi_get_instance_data(napi_env env, void** data)](#napi_get_instance_data) | - | Retrieves the data that was previously associated with the currently running environment. |
| [NAPI_EXTERN napi_status napi_add_env_cleanup_hook(napi_env env, void (\*fun)(void* arg), void* arg)](#napi_add_env_cleanup_hook) | - | Registers a clean-up hook for releasing resources when the environment exits. |
| [NAPI_EXTERN napi_status napi_remove_env_cleanup_hook(napi_env env, void (\*fun)(void* arg), void* arg)](#napi_remove_env_cleanup_hook) | - | Unregisters the clean-up hook. |
| [NAPI_EXTERN napi_status napi_add_async_cleanup_hook(napi_env env, napi_async_cleanup_hook hook, void* arg, napi_async_cleanup_hook_handle* remove_handle)](#napi_add_async_cleanup_hook) | - | Registers an asynchronous clean-up hook for releasing resources when the environment exits. |
| [NAPI_EXTERN napi_status napi_remove_async_cleanup_hook(napi_async_cleanup_hook_handle remove_handle)](#napi_remove_async_cleanup_hook) | - | Unregisters the asynchronous clean-up hook. |
| [NAPI_EXTERN napi_status napi_async_init(napi_env env, napi_value async_resource, napi_value async_resource_name, napi_async_context* result)](#napi_async_init) | - | Creates an asynchronous context. The capabilities related to 'async_hook' are not supported currently. |
| [NAPI_EXTERN napi_status napi_async_destroy(napi_env env, napi_async_context async_context)](#napi_async_destroy) | - | Destroys the previously created asynchronous context. The capabilities related to 'async_hook' are not supported currently. |
| [NAPI_EXTERN napi_status napi_open_callback_scope(napi_env env, napi_value resource_object, napi_async_context context, napi_callback_scope* result)](#napi_open_callback_scope) | - | Opens a callback scope. The capabilities related to 'async_hook' are not supported currently. |
| [NAPI_EXTERN napi_status napi_close_callback_scope(napi_env env, napi_callback_scope scope)](#napi_close_callback_scope) | - | Closes the callback scope. The capabilities related to 'async_hook' are not supported currently. |
| [NAPI_EXTERN napi_status node_api_get_module_file_name(napi_env env, const char** result)](#node_api_get_module_file_name) | - | Obtains the absolute path of the location, from which the addon is loaded. |
| [NAPI_EXTERN napi_status napi_create_object_with_properties(napi_env env, napi_value* result, size_t property_count, const napi_property_descriptor* properties)](#napi_create_object_with_properties) | - | Create ArkTS Object with initial properties given by descriptors, note that property key must be String, and must can not convert to element_index, also all keys must not duplicate. |
| [NAPI_EXTERN napi_status napi_create_object_with_named_properties(napi_env env, napi_value* result, size_t property_count, const char** keys, const napi_value* values)](#napi_create_object_with_named_properties) | - | Create ArkTS Object with initial properties given by keys and values, note that property key must be String, and must can not convert to element_index, also all keys must not duplicate. |
| [NAPI_EXTERN napi_status napi_coerce_to_native_binding_object(napi_env env, napi_value js_object, napi_native_binding_detach_callback detach_cb, napi_native_binding_attach_callback attach_cb, void* native_object, void* hint)](#napi_coerce_to_native_binding_object) | - | This API sets native properties to a object and converts this ArkTS object to native binding object. |
| [NAPI_EXTERN napi_status napi_add_finalizer(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, void* finalize_hint, napi_ref* result)](#napi_add_finalizer) | - | Adds a 'napi_finalize' callback, which will be called when the ArkTS object is garbage-collected. |
| [NAPI_EXTERN napi_status napi_load_module_with_info(napi_env env, const char* path, const char* module_info, napi_value* result)](#napi_load_module_with_info) | - | The module is loaded through the NAPI. By default, the default object is exported from the module. |
| [NAPI_EXTERN napi_status napi_create_ark_runtime(napi_env* env)](#napi_create_ark_runtime) | - | Create the ark runtime. |
| [NAPI_EXTERN napi_status napi_destroy_ark_runtime(napi_env* env)](#napi_destroy_ark_runtime) | - | Destroy the ark runtime. |
| [NAPI_EXTERN napi_status napi_define_sendable_class(napi_env env, const char* utf8name, size_t length, napi_callback constructor, void* data, size_t property_count, const napi_property_descriptor* properties, napi_value parent, napi_value* result)](#napi_define_sendable_class) | - | Defines a sendable class. |
| [NAPI_EXTERN napi_status napi_is_sendable(napi_env env, napi_value value, bool* result)](#napi_is_sendable) | - | Queries a napi_value to check if it is sendable. |
| [NAPI_EXTERN napi_status napi_create_sendable_object_with_properties(napi_env env, size_t property_count, const napi_property_descriptor* properties, napi_value* result)](#napi_create_sendable_object_with_properties) | - | Defines a sendable object. |
| [NAPI_EXTERN napi_status napi_wrap_sendable(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, void* finalize_hint)](#napi_wrap_sendable) | - | Wraps a native instance in an ArkTS object. |
| [NAPI_EXTERN napi_status napi_wrap_sendable_with_size(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, void* finalize_hint, size_t native_binding_size)](#napi_wrap_sendable_with_size) | - | Wraps a native instance in an ArkTS object. |
| [NAPI_EXTERN napi_status napi_unwrap_sendable(napi_env env, napi_value js_object, void** result)](#napi_unwrap_sendable) | - | Retrieves a native instance that was previously wrapped in an ArkTS object. |
| [NAPI_EXTERN napi_status napi_remove_wrap_sendable(napi_env env, napi_value js_object, void** result)](#napi_remove_wrap_sendable) | - | Retrieves a native instance that was previously wrapped in an ArkTS object and removes the wrapping. |
| [NAPI_EXTERN napi_status napi_create_sendable_array(napi_env env, napi_value* result)](#napi_create_sendable_array) | - | Create a sendable array. |
| [NAPI_EXTERN napi_status napi_create_sendable_array_with_length(napi_env env, size_t length, napi_value* result)](#napi_create_sendable_array_with_length) | - | Create a sendable array with length. |
| [NAPI_EXTERN napi_status napi_create_sendable_arraybuffer(napi_env env, size_t byte_length, void** data, napi_value* result)](#napi_create_sendable_arraybuffer) | - | Create a sendable arraybuffer. |
| [NAPI_EXTERN napi_status napi_create_sendable_typedarray(napi_env env, napi_typedarray_type type, size_t length, napi_value arraybuffer, size_t byte_offset, napi_value* result)](#napi_create_sendable_typedarray) | - | Create a sendable typedarray. |
| [NAPI_EXTERN napi_status napi_run_event_loop(napi_env env, napi_event_mode mode)](#napi_run_event_loop) | - | Run the event loop by the given env and running mode in current thread.<br> Support to run the native event loop in an asynchronous native thread with the specified running mode. |
| [NAPI_EXTERN napi_status napi_stop_event_loop(napi_env env)](#napi_stop_event_loop) | - | Stop the event loop in current thread.<br> Support to stop the running event loop in current native thread. |
| [NAPI_EXTERN napi_status napi_serialize(napi_env env, napi_value object, napi_value transfer_list, napi_value clone_list, void** result)](#napi_serialize) | - | Serialize an ArkTS object. |
| [NAPI_EXTERN napi_status napi_deserialize(napi_env env, void* buffer, napi_value* object)](#napi_deserialize) | - | Restore serialization data to an ArkTS object. |
| [NAPI_EXTERN napi_status napi_delete_serialization_data(napi_env env, void* buffer)](#napi_delete_serialization_data) | - | Delete serialization data. |
| [NAPI_EXTERN napi_status napi_call_threadsafe_function_with_priority(napi_threadsafe_function func, void *data, napi_task_priority priority, bool isTail)](#napi_call_threadsafe_function_with_priority) | - | Dispatch a task with specified priority from a native thread to an ArkTS thread, the task will execute the given thread safe function. |
| [NAPI_EXTERN napi_status napi_fatal_exception(napi_env env, napi_value err)](#napi_fatal_exception) | - | Throws UncaughtException to ArkTS. |
| [NAPI_EXTERN napi_status napi_make_callback(napi_env env, napi_async_context async_context, napi_value recv, napi_value func, size_t argc, const napi_value* argv, napi_value* result)](#napi_make_callback) | - | Allows an ArkTS function to be called in the asynchronous context. The capabilities related to 'async_hook' are not supported currently. |
| [NAPI_EXTERN napi_status napi_create_buffer(napi_env env, size_t length, void** data, napi_value* result)](#napi_create_buffer) | - | Creates an ArkTS ArrayBuffer object of the specified size. |
| [NAPI_EXTERN napi_status napi_create_promise(napi_env env, napi_deferred* deferred, napi_value* promise)](#napi_create_promise) | - | Creates a deferred object and an ArkTS promise. |
| [NAPI_EXTERN napi_status napi_resolve_deferred(napi_env env, napi_deferred deferred, napi_value resolution)](#napi_resolve_deferred) | - | Resolves a promise by way of the deferred object associated. |
| [NAPI_EXTERN napi_status napi_reject_deferred(napi_env env, napi_deferred deferred, napi_value rejection)](#napi_reject_deferred) | - | Rejects a promise by way of the deferred object associated. |
| [NAPI_EXTERN napi_status napi_is_promise(napi_env env, napi_value value, bool* is_promise)](#napi_is_promise) | - | Checks whether the given 'napi_value' is a promise object. |
| [NAPI_EXTERN napi_status napi_get_uv_event_loop(napi_env env, struct uv_loop_s** loop)](#napi_get_uv_event_loop) | - | Obtains the current libuv loop instance. |
| [NAPI_EXTERN napi_status napi_create_threadsafe_function(napi_env env, napi_value func, napi_value async_resource, napi_value async_resource_name, size_t max_queue_size, size_t initial_thread_count, void* thread_finalize_data, napi_finalize thread_finalize_cb, void* context, napi_threadsafe_function_call_js call_js_cb, napi_threadsafe_function* result)](#napi_create_threadsafe_function) | - | Creates a thread-safe function. |
| [NAPI_EXTERN napi_status napi_get_threadsafe_function_context(napi_threadsafe_function func, void** result)](#napi_get_threadsafe_function_context) | - | Obtains the context of a thread-safe function. |
| [NAPI_EXTERN napi_status napi_call_threadsafe_function(napi_threadsafe_function func, void* data, napi_threadsafe_function_call_mode is_blocking)](#napi_call_threadsafe_function) | - | Calls a thread-safe function. |
| [NAPI_EXTERN napi_status napi_acquire_threadsafe_function(napi_threadsafe_function func)](#napi_acquire_threadsafe_function) | - | Acquires a thread-safe function. |
| [NAPI_EXTERN napi_status napi_release_threadsafe_function(napi_threadsafe_function func, napi_threadsafe_function_release_mode mode)](#napi_release_threadsafe_function) | - | Releases a thread-safe function. |
| [NAPI_EXTERN napi_status napi_unref_threadsafe_function(napi_env env, napi_threadsafe_function func)](#napi_unref_threadsafe_function) | - | Indicates that the event loop running on the main thread may exit before the thread-safe function is destroyed. |
| [NAPI_EXTERN napi_status napi_ref_threadsafe_function(napi_env env, napi_threadsafe_function func)](#napi_ref_threadsafe_function) | - | Indicates that the event loop running on the main thread should not exit until the thread-safe function is destroyed. |
| [NAPI_EXTERN napi_status napi_create_date(napi_env env, double time, napi_value* result)](#napi_create_date) | - | Creates an ArkTS 'Date' object from C double data |
| [NAPI_EXTERN napi_status napi_is_date(napi_env env, napi_value value, bool* is_date)](#napi_is_date) | - | Checks whether the given ArkTS value is a 'Date' object. You can use this API to check the type of the parameter passed from ArkTS. |
| [NAPI_EXTERN napi_status napi_get_date_value(napi_env env, napi_value value, double* result)](#napi_get_date_value) | - | Obtains the C equivalent of the given ArkTS 'Date' object. |
| [NAPI_EXTERN napi_status napi_create_bigint_int64(napi_env env, int64_t value, napi_value* result)](#napi_create_bigint_int64) | - | Creates an ArkTS BigInt from C int64 data. |
| [NAPI_EXTERN napi_status napi_create_bigint_uint64(napi_env env, uint64_t value, napi_value* result)](#napi_create_bigint_uint64) | - | Creates an ArkTS BigInt from C int64 data. |
| [NAPI_EXTERN napi_status napi_create_bigint_words(napi_env env, int sign_bit, size_t word_count, const uint64_t* words, napi_value* result)](#napi_create_bigint_words) | - | Creates a single ArkTS BigInt from a C uint64 array. |
| [NAPI_EXTERN napi_status napi_get_value_bigint_int64(napi_env env, napi_value value, int64_t* result, bool* lossless)](#napi_get_value_bigint_int64) | - | Obtains a signed 64-bit integer from an ArkTS BigInt object. |
| [NAPI_EXTERN napi_status napi_get_value_bigint_uint64(napi_env env, napi_value value, uint64_t* result, bool* lossless)](#napi_get_value_bigint_uint64) | - | Obtains an unsigned 64-bit integer from an ArkTS BigInt object. |
| [NAPI_EXTERN napi_status napi_get_value_bigint_words(napi_env env, napi_value value, int* sign_bit, size_t* word_count, uint64_t* words)](#napi_get_value_bigint_words) | - | Obtains the underlying 64-bit unsigned (uint64) byte data from an ArkTS BigInt object. |
| [NAPI_EXTERN napi_status napi_create_external_buffer(napi_env env, size_t length, void* data, napi_finalize finalize_cb, void* finalize_hint, napi_value* result)](#napi_create_external_buffer) | - | Creates an ArkTS ArrayBuffer object of the specified size and initializes it with the given data. |
| [NAPI_EXTERN napi_status napi_create_buffer_copy(napi_env env, size_t length, const void* data, void** result_data, napi_value* result)](#napi_create_buffer_copy) | - | Creates an ArkTS ArrayBuffer object of the specified size and initializes it with the given data. |
| [NAPI_EXTERN napi_status napi_is_buffer(napi_env env, napi_value value, bool* result)](#napi_is_buffer) | - | Checks whether the given ArkTS value is a 'ArrayBuffer' object. |
| [NAPI_EXTERN napi_status napi_get_buffer_info(napi_env env, napi_value value, void** data, size_t* length)](#napi_get_buffer_info) | - | Obtains the underlying data of 'ArrayBuffer' and its length. |
| [NAPI_EXTERN napi_status napi_object_freeze(napi_env env, napi_value object)](#napi_object_freeze) | - | Freezes an ArkTS object. Once an object is frozen, its properties are immutable. |
| [NAPI_EXTERN napi_status napi_object_seal(napi_env env, napi_value object)](#napi_object_seal) | - | Seals an ArkTS object. Once an object is sealed, its properties cannot be added or deleted, but property values can be modified. |
| [NAPI_EXTERN napi_status napi_detach_arraybuffer(napi_env env, napi_value arraybuffer)](#napi_detach_arraybuffer) | - | Detaches the underlying data from an 'ArrayBuffer' object. After the data is detached, you can operate the data in C/C++. |
| [NAPI_EXTERN napi_status napi_is_detached_arraybuffer(napi_env env, napi_value value, bool* result)](#napi_is_detached_arraybuffer) | - | Checks whether the given 'ArrayBuffer' has been detached. |
| [NAPI_EXTERN napi_status napi_get_all_property_names(napi_env env, napi_value object, napi_key_collection_mode key_mode, napi_key_filter key_filter, napi_key_conversion key_conversion, napi_value* result)](#napi_get_all_property_names) | - | Obtains the names of all properties of an ArkTS object. |
| [NAPI_EXTERN void napi_module_register(napi_module* mod)](#napi_module_register) | - | Registers a native module. |
| [NAPI_EXTERN napi_status napi_get_last_error_info(napi_env env, const napi_extended_error_info** result)](#napi_get_last_error_info) | - | Obtains the napi_extended_error_info struct, which contains the latest error information. |
| [NAPI_EXTERN napi_status napi_throw(napi_env env, napi_value error)](#napi_throw) | - | Throws an ArkTS error. |
| [NAPI_EXTERN napi_status napi_throw_error(napi_env env, const char* code, const char* msg)](#napi_throw_error) | - | Throws an ArkTS Error with text information. |
| [NAPI_EXTERN napi_status napi_throw_type_error(napi_env env, const char* code, const char* msg)](#napi_throw_type_error) | - | Throws an ArkTS TypeError with text information. |
| [NAPI_EXTERN napi_status napi_throw_range_error(napi_env env, const char* code, const char* msg)](#napi_throw_range_error) | - | Throws an ArkTS RangeError with text information. |
| [NAPI_EXTERN napi_status napi_is_error(napi_env env, napi_value value, bool* result)](#napi_is_error) | - | Checks whether a 'napi_value' is an error object. |
| [NAPI_EXTERN napi_status napi_create_error(napi_env env, napi_value code, napi_value msg, napi_value* result)](#napi_create_error) | - | Creates an ArkTS Error with text information. |
| [NAPI_EXTERN napi_status napi_create_type_error(napi_env env, napi_value code, napi_value msg, napi_value* result)](#napi_create_type_error) | - | Creates an ArkTS TypeError with text information. |
| [NAPI_EXTERN napi_status napi_create_range_error(napi_env env, napi_value code, napi_value msg, napi_value* result)](#napi_create_range_error) | - | Creates an ArkTS RangeError with text information. |
| [NAPI_EXTERN napi_status napi_is_exception_pending(napi_env env, bool* result)](#napi_is_exception_pending) | - | Checks whether an exception occurs. |
| [NAPI_EXTERN napi_status napi_get_and_clear_last_exception(napi_env env, napi_value* result)](#napi_get_and_clear_last_exception) | - | Obtains and clears the latest exception. |
| [NAPI_EXTERN NAPI_NO_RETURN void napi_fatal_error(const char* location, size_t location_len, const char* message, size_t message_len)](#napi_fatal_error) | - | Raises a fatal error to terminate the process immediately. |
| [NAPI_EXTERN napi_status napi_open_handle_scope(napi_env env, napi_handle_scope* result)](#napi_open_handle_scope) | - | Opens a scope. |
| [NAPI_EXTERN napi_status napi_close_handle_scope(napi_env env, napi_handle_scope scope)](#napi_close_handle_scope) | - | Closes the scope passed in. After the scope is closed, all references declared in it are closed. |
| [NAPI_EXTERN napi_status napi_open_escapable_handle_scope(napi_env env, napi_escapable_handle_scope* result)](#napi_open_escapable_handle_scope) | - | Opens an escapable handle scope from which the declared values can be returned to the outer scope. |
| [NAPI_EXTERN napi_status napi_close_escapable_handle_scope(napi_env env, napi_escapable_handle_scope scope)](#napi_close_escapable_handle_scope) | - | Closes the escapable handle scope passed in. |
| [NAPI_EXTERN napi_status napi_escape_handle(napi_env env, napi_escapable_handle_scope scope, napi_value escapee, napi_value* result)](#napi_escape_handle) | - | Promotes the handle to the input ArkTS object so that it is valid for the lifespan of its outer scope. |
| [NAPI_EXTERN napi_status napi_create_reference(napi_env env, napi_value value, uint32_t initial_refcount, napi_ref* result)](#napi_create_reference) | - | Creates a reference for an object to extend its lifespan. The caller needs to manage the reference lifespan. |
| [NAPI_EXTERN napi_status napi_delete_reference(napi_env env, napi_ref ref)](#napi_delete_reference) | - | Deletes the reference passed in. |
| [NAPI_EXTERN napi_status napi_reference_ref(napi_env env, napi_ref ref, uint32_t* result)](#napi_reference_ref) | - | Increments the reference count for the reference passed in and returns the count. |
| [NAPI_EXTERN napi_status napi_reference_unref(napi_env env, napi_ref ref, uint32_t* result)](#napi_reference_unref) | - | Decrements the reference count for the reference passed in and returns the count. |
| [NAPI_EXTERN napi_status napi_get_reference_value(napi_env env, napi_ref ref, napi_value* result)](#napi_get_reference_value) | - | Obtains the ArkTS Object associated with the reference. |
| [NAPI_EXTERN napi_status napi_has_own_property(napi_env env, napi_value object, napi_value key, bool* result)](#napi_has_own_property) | - | Check if the given ArkTS Object has the named own property or not. |
| [NAPI_EXTERN napi_status napi_define_class(napi_env env, const char* utf8name, size_t length, napi_callback constructor, void* data, size_t property_count, const napi_property_descriptor* properties, napi_value* result)](#napi_define_class) | - | Defines an ArkTS class, including constructor function and properties. |
| [NAPI_EXTERN napi_status napi_create_symbol(napi_env env, napi_value description, napi_value* result)](#napi_create_symbol) | - | Creates an ArkTS symbol. |
| [NAPI_EXTERN napi_status napi_create_function(napi_env env, const char* utf8name, size_t length, napi_callback cb, void* data, napi_value* result)](#napi_create_function) | - | Create an ArkTS function. This is the primary mechanism to call back into native code from ArkTS. |
| [NAPI_EXTERN napi_status napi_typeof(napi_env env, napi_value value, napi_valuetype* result)](#napi_typeof) | - | Similar to typeof operation, support external value, detects null as a separate type. |
| [NAPI_EXTERN napi_status napi_get_value_double(napi_env env, napi_value value, double* result)](#napi_get_value_double) | - | Obtains the double value corresponding to the given ArkTS value. |
| [NAPI_EXTERN napi_status napi_get_value_int32(napi_env env, napi_value value, int32_t* result)](#napi_get_value_int32) | - | Obtains the int32_t value corresponding to the given ArkTS value. |
| [NAPI_EXTERN napi_status napi_get_value_uint32(napi_env env, napi_value value, uint32_t* result)](#napi_get_value_uint32) | - | Obtains the uint32_t value corresponding to the given ArkTS value. |
| [NAPI_EXTERN napi_status napi_get_value_int64(napi_env env, napi_value value, int64_t* result)](#napi_get_value_int64) | - | Obtains the int64_t value corresponding to the given ArkTS value. |
| [NAPI_EXTERN napi_status napi_get_value_bool(napi_env env, napi_value value, bool* result)](#napi_get_value_bool) | - | Obtains the C Boolean equivalent of an ArkTS Boolean value. |
| [NAPI_EXTERN napi_status napi_get_value_string_latin1(napi_env env, napi_value value, char* buf, size_t bufsize, size_t* result)](#napi_get_value_string_latin1) | - | Obtains the ISO-8859-1-encoded string corresponding to the given ArkTS value. |
| [NAPI_EXTERN napi_status napi_get_value_string_utf8(napi_env env, napi_value value, char* buf, size_t bufsize, size_t* result)](#napi_get_value_string_utf8) | - | Obtains the UTF8-encoded string corresponding to the given ArkTS value. |
| [NAPI_EXTERN napi_status napi_get_undefined(napi_env env, napi_value* result)](#napi_get_undefined) | - | Obtains the ArkTS undefined value. |
| [NAPI_EXTERN napi_status napi_get_null(napi_env env, napi_value* result)](#napi_get_null) | - | Obtains the ArkTS null value. |
| [NAPI_EXTERN napi_status napi_get_global(napi_env env, napi_value* result)](#napi_get_global) | - | Obtains the ArkTS global object. |
| [NAPI_EXTERN napi_status napi_get_boolean(napi_env env, bool value, napi_value* result)

// Methods to create Primitive types/Objects](#napi_get_boolean) | - | Obtains the ArkTS singleton value corresponding to given C primitive boolean value. |
| [NAPI_EXTERN napi_status napi_create_object(napi_env env, napi_value* result)](#napi_create_object) | - | Creates a default ArkTS object. |
| [NAPI_EXTERN napi_status napi_create_array(napi_env env, napi_value* result)](#napi_create_array) | - | Creates an ArkTS array. |
| [NAPI_EXTERN napi_status napi_create_array_with_length(napi_env env, size_t length, napi_value* result)](#napi_create_array_with_length) | - | Creates an ArkTS array of the specified length. |
| [NAPI_EXTERN napi_status napi_create_double(napi_env env, double value, napi_value* result)](#napi_create_double) | - | Creates an ArkTS number from C double data. |
| [NAPI_EXTERN napi_status napi_create_int32(napi_env env, int32_t value, napi_value* result)](#napi_create_int32) | - | Creates an ArkTS number from C int32_t data. |
| [NAPI_EXTERN napi_status napi_create_uint32(napi_env env, uint32_t value, napi_value* result)](#napi_create_uint32) | - | Creates an ArkTS number from C uint32_t data. |
| [NAPI_EXTERN napi_status napi_create_int64(napi_env env, int64_t value, napi_value* result)](#napi_create_int64) | - | Creates an ArkTS number from C int64_t data. |
| [NAPI_EXTERN napi_status napi_create_string_latin1(napi_env env, const char* str, size_t length, napi_value* result)](#napi_create_string_latin1) | - | Creates an ArkTS string from an ISO-8859-1-encoded C string. |
| [NAPI_EXTERN napi_status napi_create_string_utf8(napi_env env, const char* str, size_t length, napi_value* result)](#napi_create_string_utf8) | - | Creates an ArkTS string from a UTF8-encoded C string. |
| [NAPI_EXTERN napi_status napi_is_arraybuffer(napi_env env, napi_value value, bool* result)](#napi_is_arraybuffer) | - | Checks if the ArkTS value is an ArkTS ArrayBuffer. |
| [NAPI_EXTERN napi_status napi_create_arraybuffer(napi_env env, size_t byte_length, void** data, napi_value* result)](#napi_create_arraybuffer) | - | Creates an ArkTS ArrayBuffer of the specified size. |
| [NAPI_EXTERN napi_status napi_create_external(napi_env env, void* data, napi_finalize finalize_cb, void* finalize_hint, napi_value* result)](#napi_create_external) | - | Allocates a JS value with external data. |
| [NAPI_EXTERN napi_status napi_create_external_arraybuffer(napi_env env, void* external_data, size_t byte_length, napi_finalize finalize_cb, void* finalize_hint, napi_value* result)](#napi_create_external_arraybuffer) | - | The underlying data that ArrayBuffer point to. |
| [NAPI_EXTERN napi_status napi_get_arraybuffer_info(napi_env env, napi_value arraybuffer, void** data, size_t* byte_length)](#napi_get_arraybuffer_info) | - | Obtains the underlying data buffer of ArrayBuffer and its length. |
| [NAPI_EXTERN napi_status napi_is_typedarray(napi_env env, napi_value value, bool* result)](#napi_is_typedarray) | - | Checks if the ArkTS value is an ArkTS TypedArray. |
| [NAPI_EXTERN napi_status napi_create_typedarray(napi_env env, napi_typedarray_type type, size_t length, napi_value arraybuffer, size_t byte_offset, napi_value* result)](#napi_create_typedarray) | - | Creates an ArkTS TypeArray from an existing ArrayBuffer. |
| [NAPI_EXTERN napi_status napi_get_typedarray_info(napi_env env, napi_value typedarray, napi_typedarray_type* type, size_t* length, void** data, napi_value* arraybuffer, size_t* byte_offset)](#napi_get_typedarray_info) | - | Obtains properties of a TypedArray. |
| [NAPI_EXTERN napi_status napi_create_dataview(napi_env env, size_t length, napi_value arraybuffer, size_t byte_offset, napi_value* result)](#napi_create_dataview) | - | Creates an ArkTS DataView from an existing ArrayBuffer. |
| [NAPI_EXTERN napi_status napi_is_dataview(napi_env env, napi_value value, bool* result)](#napi_is_dataview) | - | Checks if the ArkTS value is an ArkTS DataView. |
| [NAPI_EXTERN napi_status napi_get_dataview_info(napi_env env, napi_value dataview, size_t* bytelength, void** data, napi_value* arraybuffer, size_t* byte_offset)](#napi_get_dataview_info) | - | Obtains properties of a DataView. |
| [NAPI_EXTERN napi_status napi_get_array_length(napi_env env, napi_value value, uint32_t* result)](#napi_get_array_length) | - | Obtains the array length. |
| [NAPI_EXTERN napi_status napi_get_prototype(napi_env env, napi_value object, napi_value* result)](#napi_get_prototype) | - | Obtains the prototype of an ArkTS object. |
| [NAPI_EXTERN napi_status napi_get_value_external(napi_env env, napi_value value, void** result)](#napi_get_value_external) | - | Obtains the external data pointer previously passed through napi_create_external(). |
| [NAPI_EXTERN napi_status napi_coerce_to_bool(napi_env env, napi_value value, napi_value* result)](#napi_coerce_to_bool) | - | Coerce the given ArkTS value to an ArkTS boolean value. |
| [NAPI_EXTERN napi_status napi_coerce_to_number(napi_env env, napi_value value, napi_value* result)](#napi_coerce_to_number) | - | Coerce the given ArkTS value to an ArkTS number value. |
| [NAPI_EXTERN napi_status napi_coerce_to_object(napi_env env, napi_value value, napi_value* result)](#napi_coerce_to_object) | - | Coerce the given ArkTS value to an ArkTS object value. |
| [NAPI_EXTERN napi_status napi_coerce_to_string(napi_env env, napi_value value, napi_value* result)](#napi_coerce_to_string) | - | Coerce the given ArkTS value to an ArkTS string value. |
| [NAPI_EXTERN napi_status napi_instanceof(napi_env env, napi_value object, napi_value constructor, bool* result)](#napi_instanceof) | - | Invoke instanceof operation on the object. |
| [NAPI_EXTERN napi_status napi_is_array(napi_env env, napi_value value, bool* result)](#napi_is_array) | - | Checks if the ArkTS value is an ArkTS Array. |
| [NAPI_EXTERN napi_status napi_strict_equals(napi_env env, napi_value lhs, napi_value rhs, bool* result)](#napi_strict_equals) | - | Checks if the two ArkTS values are equal. |
| [NAPI_EXTERN napi_status napi_get_property_names(napi_env env, napi_value object, napi_value* result)](#napi_get_property_names) | - | Obtains the names of the enumerable properties of object as an Array of Strings. The keys that are symbols will not be included. |
| [NAPI_EXTERN napi_status napi_set_property(napi_env env, napi_value object, napi_value key, napi_value value)](#napi_set_property) | - | Set a property on the given ArkTS Object. |
| [NAPI_EXTERN napi_status napi_get_property(napi_env env, napi_value object, napi_value key, napi_value* result)](#napi_get_property) | - | Get the requests property of the given ArkTS Object. |
| [NAPI_EXTERN napi_status napi_has_property(napi_env env, napi_value object, napi_value key, bool* result)](#napi_has_property) | - | Check if the given ArkTS Object has the named property or not. |
| [NAPI_EXTERN napi_status napi_delete_property(napi_env env, napi_value object, napi_value key, bool* result)](#napi_delete_property) | - | Delete the named property of the given ArkTS Object. |
| [NAPI_EXTERN napi_status napi_set_named_property(napi_env env, napi_value object, const char* utf8name, napi_value value)](#napi_set_named_property) | - | Set a property on the given ArkTS Object. |
| [NAPI_EXTERN napi_status napi_get_named_property(napi_env env, napi_value object, const char* utf8name, napi_value* result)](#napi_get_named_property) | - | Get the requests property of the given ArkTS Object. |
| [NAPI_EXTERN napi_status napi_has_named_property(napi_env env, napi_value object, const char* utf8name, bool* result)](#napi_has_named_property) | - | Check if the given ArkTS Object has the named property or not. |
| [NAPI_EXTERN napi_status napi_set_element(napi_env env, napi_value object, uint32_t index, napi_value value)](#napi_set_element) | - | Set a element on the given ArkTS Array. |
| [NAPI_EXTERN napi_status napi_get_element(napi_env env, napi_value object, uint32_t index, napi_value* result)](#napi_get_element) | - | Get the requests element of the given ArkTS Array. |
| [NAPI_EXTERN napi_status napi_has_element(napi_env env, napi_value object, uint32_t index, bool* result)](#napi_has_element) | - | Check if the given ArkTS Array has an element at the requested index. |
| [NAPI_EXTERN napi_status napi_delete_element(napi_env env, napi_value object, uint32_t index, bool* result)](#napi_delete_element) | - | Delete the special index from the given ArkTS Array. |
| [NAPI_EXTERN napi_status napi_define_properties(napi_env env, napi_value object, size_t property_count, const napi_property_descriptor* properties)](#napi_define_properties) | - | Efficient define multiple properties on the given ArkTS Object by napi_property_descriptor. |
| [NAPI_EXTERN napi_status napi_call_function(napi_env env, napi_value recv, napi_value func, size_t argc, const napi_value* argv, napi_value* result)](#napi_call_function) | - | Invoke an ArkTS function. This is the primary mechanism to call back into JavaScript. |
| [NAPI_EXTERN napi_status napi_get_cb_info(napi_env env, napi_callback_info cbinfo, size_t* argc, napi_value* argv, napi_value* this_arg, void** data)](#napi_get_cb_info) | - | Obtains callback details about the call like arguments, this from given callback info. |
| [NAPI_EXTERN napi_status napi_get_new_target(napi_env env, napi_callback_info cbinfo, napi_value* result)](#napi_get_new_target) | - | Obtains callback details about the call like arguments, this from given callback info. |
| [NAPI_EXTERN napi_status napi_new_instance(napi_env env, napi_value constructor, size_t argc, const napi_value* argv, napi_value* result)](#napi_new_instance) | - | Instantiate a new ArkTS value using a given napi_value that represents the constructor for the object. |
| [NAPI_EXTERN napi_status napi_wrap(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, void* finalize_hint, napi_ref* result)](#napi_wrap) | - | Wraps a native instance in a ArkTS object. The native instance can be retrieved later using napi_unwrap. |
| [NAPI_EXTERN napi_status napi_unwrap(napi_env env, napi_value js_object, void** result)](#napi_unwrap) | - | Retrieves a native instance that was previously wrapped in an ArkTS object using napi_wrap. |
| [NAPI_EXTERN napi_status napi_remove_wrap(napi_env env, napi_value js_object, void** result)](#napi_remove_wrap) | - | Retrieves a native instance that was previously wrapped in the ArkTS object js_object using napi_wrap and removes the wrapping. |
| [NAPI_EXTERN napi_status napi_create_async_work(napi_env env, napi_value async_resource, napi_value async_resource_name, napi_async_execute_callback execute, napi_async_complete_callback complete, void* data, napi_async_work* result)](#napi_create_async_work) | - | Allocate a work object that is used to execute logic asynchronously. |
| [NAPI_EXTERN napi_status napi_delete_async_work(napi_env env, napi_async_work work)](#napi_delete_async_work) | - | Free a previously allocated work object. |
| [NAPI_EXTERN napi_status napi_queue_async_work(napi_env env, napi_async_work work)](#napi_queue_async_work) | - | Requests that the previously allocated work be scheduled for execution. Once it returns successfully, this API must not be called again with the same napi_async_work item or the result will be undefined. |
| [NAPI_EXTERN napi_status napi_cancel_async_work(napi_env env, napi_async_work work)](#napi_cancel_async_work) | - | Cancels queued work if it has not yet been started. If it has already started executing, it cannot be cancelled. If successful, the complete callback will be invoked with a status value of napi_cancelled. The work should not be deleted before the complete callback invocation, even if it has been successfully cancelled. |
| [NAPI_EXTERN napi_status napi_wrap_enhance(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, bool async_finalizer, void* finalize_hint, size_t native_binding_size, napi_ref* result)](#napi_wrap_enhance) | - | Wraps a native instance in an ArkTS object. |
| [NAPI_EXTERN napi_status napi_create_ark_context(napi_env env, napi_env *newEnv)](#napi_create_ark_context) | - | To create a new virtual machine context. |
| [NAPI_EXTERN napi_status napi_switch_ark_context(napi_env env)](#napi_switch_ark_context) | - | To switch a virtual machine context which is expected to be used later. |
| [NAPI_EXTERN napi_status napi_destroy_ark_context(napi_env env)](#napi_destroy_ark_context) | - | To destroy a virtual machine context which will not be used again. |
| [NAPI_EXTERN napi_status napi_open_critical_scope(napi_env env, napi_critical_scope* scope)](#napi_open_critical_scope) | - | To open a critical scope. |
| [NAPI_EXTERN napi_status napi_close_critical_scope(napi_env env, napi_critical_scope scope)](#napi_close_critical_scope) | - | To close a critical scope. |
| [NAPI_EXTERN napi_status napi_get_buffer_string_utf16_in_critical_scope(napi_env env, napi_value value, const char16_t** buffer, size_t* length)](#napi_get_buffer_string_utf16_in_critical_scope) | - | To obtain a ArkTS string buffer cache within the critical scope. |
| [NAPI_EXTERN napi_status napi_create_strong_reference(napi_env env, napi_value value, napi_strong_ref* result)](#napi_create_strong_reference) | - | Creates a strong reference for an ArkTS object to extend its lifespan. The caller needs to manage the reference lifespan. |
| [NAPI_EXTERN napi_status napi_delete_strong_reference(napi_env env, napi_strong_ref ref)](#napi_delete_strong_reference) | - | Deletes the strong reference passed in. |
| [NAPI_EXTERN napi_status napi_get_strong_reference_value(napi_env env, napi_strong_ref ref, napi_value* result)](#napi_get_strong_reference_value) | - | Obtains the ArkTS Object associated with the strong reference. |
| [NAPI_EXTERN napi_status napi_create_external_string_utf16(napi_env env, const char16_t* str, size_t length, napi_finalize_callback finalize_callback, void* finalize_hint, napi_value* result)](#napi_create_external_string_utf16) | - | Creates an ArkTS string from a UTF16-encoded C string. |
| [NAPI_EXTERN napi_status napi_create_external_string_ascii(napi_env env, const char* str, size_t length, napi_finalize_callback finalize_callback, void* finalize_hint, napi_value* result)](#napi_create_external_string_ascii) | - | Creates an ArkTS string from a ASCII-encoded C string. |
| [NAPI_EXTERN napi_status napi_create_strong_sendable_reference(napi_env env, napi_value value, napi_sendable_ref* result)](#napi_create_strong_sendable_reference) | - | Creates a strong sendable reference for an ArkTS object to extend its lifespan. The caller needs to manage the sendable reference lifespan. |
| [NAPI_EXTERN napi_status napi_delete_strong_sendable_reference(napi_env env, napi_sendable_ref ref)](#napi_delete_strong_sendable_reference) | - | Deletes the strong sendable reference passed in. |
| [NAPI_EXTERN napi_status napi_get_strong_sendable_reference_value(napi_env env, napi_sendable_ref ref, napi_value* result)](#napi_get_strong_sendable_reference_value) | - | Obtains the ArkTS Object associated with the strong reference. |
| [NAPI_EXTERN napi_status napi_throw_business_error(napi_env env, int32_t errorCode, const char* msg)](#napi_throw_business_error) | - | Throws an ArkTS Error with text information. |
| [NAPI_EXTERN napi_status napi_create_callsite_info(napi_env env, napi_callsite_info* result)](#napi_create_callsite_info) | - | Creates a callsite info handle for caching inline cache (IC) information of property access. Each different callsite should create an independent handle. The same handle can be reused across multiple calls but must not be used across threads. When no longer needed, napi_delete_callsite_info must be called to release the handle. |
| [NAPI_EXTERN napi_status napi_delete_callsite_info(napi_env env, napi_callsite_info info)](#napi_delete_callsite_info) | - | Deletes a callsite info handle and releases associated cache resources. |
| [NAPI_EXTERN napi_status napi_get_property_with_callsite_info(napi_env env, napi_value object, napi_value key, napi_callsite_info info, napi_value* result, bool* hit)](#napi_get_property_with_callsite_info) | - | Uses callsite info to quickly get an object property value. When the IC hits (the object has the same hidden class), it skips the regular hash table lookup and prototype chain traversal. The info parameter can be NULL, in which case the behavior is equivalent to napi_get_property. |
| [NAPI_EXTERN napi_status napi_set_property_with_callsite_info(napi_env env, napi_value object, napi_value key, napi_value value, napi_callsite_info info, bool* hit)](#napi_set_property_with_callsite_info) | - | Uses callsite info to quickly set an object property value. When the IC hits (the object has the same hidden class), it skips the regular property setting process. The info parameter can be NULL, in which case the behavior is equivalent to napi_set_property. |
| [NAPI_EXTERN napi_status napi_get_global_handle_count(napi_env env, size_t* count)](#napi_get_global_handle_count) | - | To obtain the count of global object in current ArkTS runtime thread. |

### Variable

| Name | Description |
| -- | -- |
| void* (*napi_native_binding_detach_callback)(napi_env env, void* native_object, void* hint) | Native detach callback of napi_coerce_to_native_binding_object that can be used to detach the ArkTS object and the native object.<br>**Since**: 11 |
| napi_value (*napi_native_binding_attach_callback)(napi_env env, void* native_object, void* hint) | Native attach callback of napi_coerce_to_native_binding_object that can be used to bind the ArkTS object and the native object.<br>**Since**: 11 |
| void (*napi_finalize_callback)(void* finalize_data, void* finalize_hint) | Native finalize callback is utilized to recycle native object resource.<br>**Since**: 22 |

## Function description

### napi_native_binding_detach_callback()

```c
typedef void* (*napi_native_binding_detach_callback)(napi_env env, void* native_object, void* hint)
```

**Description**

Native detach callback of napi_coerce_to_native_binding_object that can be used to detach the ArkTS object and the native object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

### ()

```c
typedef napi_value (*napi_native_binding_attach_callback)(napi_env env, void* native_object, void* hint)

NAPI_EXTERN napi_status napi_run_script_path(napi_env env, const char* path, napi_value* result)
NAPI_EXTERN napi_status napi_queue_async_work_with_qos(napi_env env, napi_async_work work, napi_qos_t qos)
```

**Description**

Native attach callback of napi_coerce_to_native_binding_object that can be used to bind the ArkTS object and the native object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

### napi_finalize_callback()

```c
typedef void (*napi_finalize_callback)(void* finalize_data, void* finalize_hint)
```

**Description**

Native finalize callback is utilized to recycle native object resource.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 22

### napi_load_module()

```c
NAPI_EXTERN napi_status napi_load_module(napi_env env, const char* path, napi_value* result)
```

**Description**

Loads an .abc file as a module. This API returns the namespace of the module.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* path | Path of the .abc file or name of the module to load. |
| napi_value* result | Result of the module object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_set_instance_data()

```c
NAPI_EXTERN napi_status napi_set_instance_data(napi_env env, void* data, napi_finalize finalize_cb, void* finalize_hint)
```

**Description**

Associates data with the currently running environment.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| void* data | Data item to bind with the 'env'. |
| napi_finalize finalize_cb | Optional native callback that will be triggered when 'env' is destroyed or this interface repeatedly calls. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize callback. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_get_instance_data()

```c
NAPI_EXTERN napi_status napi_get_instance_data(napi_env env, void** data)
```

**Description**

Retrieves the data that was previously associated with the currently running environment.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| void** data | Data item is bound with the 'env'. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_add_env_cleanup_hook()

```c
NAPI_EXTERN napi_status napi_add_env_cleanup_hook(napi_env env, void (*fun)(void* arg), void* arg)
```

**Description**

Registers a clean-up hook for releasing resources when the environment exits.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| api_env env | Current running virtual machine context. |
| void (\*fun)(void\* arg) | Function pointer which will be triggered when environment is destroy. |
| void (\*fun)(void\* arg) | The argument is passed to the function pointer 'fun'. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_remove_env_cleanup_hook()

```c
NAPI_EXTERN napi_status napi_remove_env_cleanup_hook(napi_env env, void (*fun)(void* arg), void* arg)
```

**Description**

Unregisters the clean-up hook.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| api_env env | Current running virtual machine context. |
| void (\*fun)(void\* arg) | Function pointer which will be triggered when environment is destroy. |
| void (\*fun)(void\* arg) | The argument is passed to the function pointer 'fun'. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_add_async_cleanup_hook()

```c
NAPI_EXTERN napi_status napi_add_async_cleanup_hook(napi_env env, napi_async_cleanup_hook hook, void* arg, napi_async_cleanup_hook_handle* remove_handle)
```

**Description**

Registers an asynchronous clean-up hook for releasing resources when the environment exits.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_async_cleanup_hook hook | The function pointer to call at environment teardown. |
| void* arg | The pointer to pass to `hook` when it gets called. |
| napi_async_cleanup_hook_handle* remove_handle | Optional handle that refers to the asynchronous cleanup. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_remove_async_cleanup_hook()

```c
NAPI_EXTERN napi_status napi_remove_async_cleanup_hook(napi_async_cleanup_hook_handle remove_handle)
```

**Description**

Unregisters the asynchronous clean-up hook.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_async_cleanup_hook_handle remove_handle | Optional handle that refers to the asynchronous cleanup. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_async_init()

```c
NAPI_EXTERN napi_status napi_async_init(napi_env env, napi_value async_resource, napi_value async_resource_name, napi_async_context* result)
```

**Description**

Creates an asynchronous context. The capabilities related to 'async_hook' are not supported currently.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value async_resource | Object associated with the async work that will be passed to possible 'async_hook'. |
| napi_value async_resource_name | Identifier for the kind of resource that is being provided for diagnostic information exposed by the async_hooks API. |
| napi_async_context* result | The initialized async context. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_async_destroy()

```c
NAPI_EXTERN napi_status napi_async_destroy(napi_env env, napi_async_context async_context)
```

**Description**

Destroys the previously created asynchronous context. The capabilities related to 'async_hook' are not supported currently.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_async_context async_context | The async context to be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_open_callback_scope()

```c
NAPI_EXTERN napi_status napi_open_callback_scope(napi_env env, napi_value resource_object, napi_async_context context, napi_callback_scope* result)
```

**Description**

Opens a callback scope. The capabilities related to 'async_hook' are not supported currently.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value resource_object | The resource object to be passed to possible 'async_hook'. |
| napi_async_context context | The context environment for the async operation. |
| napi_callback_scope* result | The generated callback scope. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_close_callback_scope()

```c
NAPI_EXTERN napi_status napi_close_callback_scope(napi_env env, napi_callback_scope scope)
```

**Description**

Closes the callback scope. The capabilities related to 'async_hook' are not supported currently.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_callback_scope scope | The callback scope to be closed. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### node_api_get_module_file_name()

```c
NAPI_EXTERN napi_status node_api_get_module_file_name(napi_env env, const char** result)
```

**Description**

Obtains the absolute path of the location, from which the addon is loaded.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char** result | The absolute path of the location of the loaded addon. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_create_object_with_properties()

```c
NAPI_EXTERN napi_status napi_create_object_with_properties(napi_env env, napi_value* result, size_t property_count, const napi_property_descriptor* properties)
```

**Description**

Create ArkTS Object with initial properties given by descriptors, note that property key must be String, and must can not convert to element_index, also all keys must not duplicate.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value* result | The created ArkTS object. |
| size_t property_count | Number of the property descriptors. |
| const napi_property_descriptor* properties | Array of property descriptors which are expected to be applied to the ArkTS object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_create_object_with_named_properties()

```c
NAPI_EXTERN napi_status napi_create_object_with_named_properties(napi_env env, napi_value* result, size_t property_count, const char** keys, const napi_value* values)
```

**Description**

Create ArkTS Object with initial properties given by keys and values, note that property key must be String, and must can not convert to element_index, also all keys must not duplicate.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value* result | The absolute path of the location of the loaded addon. |
| size_t property_count | Number of the propertied which needs to be applied on the ArkTS object. |
| const char** keys | Array of the keys of the properties. |
| const napi_value* values | Array of the values of the properties. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_coerce_to_native_binding_object()

```c
NAPI_EXTERN napi_status napi_coerce_to_native_binding_object(napi_env env, napi_value js_object, napi_native_binding_detach_callback detach_cb, napi_native_binding_attach_callback attach_cb, void* native_object, void* hint)
```

**Description**

This API sets native properties to a object and converts this ArkTS object to native binding object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value js_object | The ArkTS value to coerce. |
| [napi_native_binding_detach_callback](capi-native-api-h.md#napi_native_binding_detach_callback) detach_cb | Native callback that can be used to detach the ArkTS object and the native object. |
| napi_native_binding_attach_callback attach_cb | Native callback that can be used to bind the ArkTS object and the native object. |
| void* native_object | User-provided native instance to pass to thr detach callback and attach callback. |
| void* hint | Optional hint to pass to the detach callback and attach callback. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_add_finalizer()

```c
NAPI_EXTERN napi_status napi_add_finalizer(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, void* finalize_hint, napi_ref* result)
```

**Description**

Adds a 'napi_finalize' callback, which will be called when the ArkTS object is garbage-collected.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value js_object | The ArkTS object value. |
| void* native_object | Native object to bind with the ArkTS object. |
| napi_finalize finalize_cb | Native callback that can be used to free the native object when the ArkTS object is garbage-collected. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize callback. |
| napi_ref* result | Optional reference of the ArkTS object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_load_module_with_info()

```c
NAPI_EXTERN napi_status napi_load_module_with_info(napi_env env, const char* path, const char* module_info, napi_value* result)
```

**Description**

The module is loaded through the NAPI. By default, the default object is exported from the module.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* path | Path name of the module to be loaded, like @ohos.hilog. |
| const char* module_info | Path names of bundle and module, like com.example.application/entry. |
| napi_value* result | Result of loading a module, which is an exported object of the module. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_create_ark_runtime()

```c
NAPI_EXTERN napi_status napi_create_ark_runtime(napi_env* env)
```

**Description**

Create the ark runtime.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env* env | Indicates the ark runtime environment. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_destroy_ark_runtime()

```c
NAPI_EXTERN napi_status napi_destroy_ark_runtime(napi_env* env)
```

**Description**

Destroy the ark runtime.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env* env | Indicates the ark runtime environment. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_define_sendable_class()

```c
NAPI_EXTERN napi_status napi_define_sendable_class(napi_env env, const char* utf8name, size_t length, napi_callback constructor, void* data, size_t property_count, const napi_property_descriptor* properties, napi_value parent, napi_value* result)
```

**Description**

Defines a sendable class.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| const char* utf8name | Name of the ArkTS constructor function. |
| size_t length | The length of the utf8name in bytes, or NAPI_AUTO_LENGTH if it is null-terminated. |
| napi_callback constructor | Callback function that handles constructing instances of the class. |
| void* data | Optional data to be passed to the constructor callback as the data property of the callback info. |
| size_t property_count | Number of items in the properties array argument. |
| const napi_property_descriptor* properties | Array of property descriptors describing static and instance data properties, accessors, and methods on the class. See napi_property_descriptor. |
| napi_value parent | A napi_value representing the Superclass. |
| napi_value* result | A napi_value representing the constructor function for the class. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_is_sendable()

```c
NAPI_EXTERN napi_status napi_is_sendable(napi_env env, napi_value value, bool* result)
```

**Description**

Queries a napi_value to check if it is sendable.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| napi_value value | The napi_value to be checked. |
| bool* result | Boolean value that is set to true if napi_value is sendable, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_create_sendable_object_with_properties()

```c
NAPI_EXTERN napi_status napi_create_sendable_object_with_properties(napi_env env, size_t property_count, const napi_property_descriptor* properties, napi_value* result)
```

**Description**

Defines a sendable object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| size_t property_count | The count of object properties. |
| const napi_property_descriptor* properties | Object properties. |
| napi_value* result | The created sendable object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_wrap_sendable()

```c
NAPI_EXTERN napi_status napi_wrap_sendable(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, void* finalize_hint)
```

**Description**

Wraps a native instance in an ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| napi_value js_object | The ArkTS object that will be the wrapper for the native object. |
| void* native_object | The native instance that will be wrapped in the ArkTS object. |
| napi_finalize finalize_cb | Optional native callback that can be used to free the native instance when the ArkTS object has been garbage-collected. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize callback. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_wrap_sendable_with_size()

```c
NAPI_EXTERN napi_status napi_wrap_sendable_with_size(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, void* finalize_hint, size_t native_binding_size)
```

**Description**

Wraps a native instance in an ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| napi_value js_object | The ArkTS object that will be the wrapper for the native object. |
| void* native_object | The native instance that will be wrapped in the ArkTS object. |
| napi_finalize finalize_cb | Optional native callback that can be used to free the native instance when the ArkTS object has been garbage-collected. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize callback. |
| size_t native_binding_size | The size of native binding. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_unwrap_sendable()

```c
NAPI_EXTERN napi_status napi_unwrap_sendable(napi_env env, napi_value js_object, void** result)
```

**Description**

Retrieves a native instance that was previously wrapped in an ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| napi_value js_object | The object associated with the native instance. |
| void** result | Pointer to the wrapped native instance. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_remove_wrap_sendable()

```c
NAPI_EXTERN napi_status napi_remove_wrap_sendable(napi_env env, napi_value js_object, void** result)
```

**Description**

Retrieves a native instance that was previously wrapped in an ArkTS object and removes the wrapping.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| napi_value js_object | The object associated with the native instance. |
| void** result | Pointer to the wrapped native instance. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_create_sendable_array()

```c
NAPI_EXTERN napi_status napi_create_sendable_array(napi_env env, napi_value* result)
```

**Description**

Create a sendable array.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| napi_value* result | A napi_value representing a sendable array. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_create_sendable_array_with_length()

```c
NAPI_EXTERN napi_status napi_create_sendable_array_with_length(napi_env env, size_t length, napi_value* result)
```

**Description**

Create a sendable array with length.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| size_t length | The initial length of the sendable array. |
| napi_value* result | A napi_value representing a sendable array. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_create_sendable_arraybuffer()

```c
NAPI_EXTERN napi_status napi_create_sendable_arraybuffer(napi_env env, size_t byte_length, void** data, napi_value* result)
```

**Description**

Create a sendable arraybuffer.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| size_t byte_length | The length in bytes of the sendable arraybuffer to create. |
| void** data | Pointer to the underlying byte buffer of the sendable arraybuffer. |
| napi_value* result | A napi_value representing a sendable arraybuffer. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_create_sendable_typedarray()

```c
NAPI_EXTERN napi_status napi_create_sendable_typedarray(napi_env env, napi_typedarray_type type, size_t length, napi_value arraybuffer, size_t byte_offset, napi_value* result)
```

**Description**

Create a sendable typedarray.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| napi_typedarray_type type | Scalar datatype of the elements within the sendable typedarray. |
| size_t length | Number of elements in the typedarray. |
| napi_value arraybuffer | Sendable arraybuffer underlying the sendable typedarray. |
| size_t byte_offset | The byte offset within the sendable arraybuffer from which to start projecting the sendable typedarray. |
| napi_value* result | A napi_value representing a sendable typedarray. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_run_event_loop()

```c
NAPI_EXTERN napi_status napi_run_event_loop(napi_env env, napi_event_mode mode)
```

**Description**

Run the event loop by the given env and running mode in current thread.<br> Support to run the native event loop in an asynchronous native thread with the specified running mode.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_event_mode mode | Indicates the running mode of the native event loop. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_stop_event_loop()

```c
NAPI_EXTERN napi_status napi_stop_event_loop(napi_env env)
```

**Description**

Stop the event loop in current thread.<br> Support to stop the running event loop in current native thread.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_serialize()

```c
NAPI_EXTERN napi_status napi_serialize(napi_env env, napi_value object, napi_value transfer_list, napi_value clone_list, void** result)
```

**Description**

Serialize an ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object to serialize. |
| napi_value transfer_list | List of data to transfer in transfer mode. |
| napi_value clone_list | List of Sendable data to transfer in clone mode. |
| void** result | Serialization result of the ArkTS object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_deserialize()

```c
NAPI_EXTERN napi_status napi_deserialize(napi_env env, void* buffer, napi_value* object)
```

**Description**

Restore serialization data to an ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| void* buffer | Data to deserialize. |
| napi_value* object | ArkTS object obtained by deserialization. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_delete_serialization_data()

```c
NAPI_EXTERN napi_status napi_delete_serialization_data(napi_env env, void* buffer)
```

**Description**

Delete serialization data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| void* buffer | Data to delete. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status. |

### napi_call_threadsafe_function_with_priority()

```c
NAPI_EXTERN napi_status napi_call_threadsafe_function_with_priority(napi_threadsafe_function func, void *data, napi_task_priority priority, bool isTail)
```

**Description**

Dispatch a task with specified priority from a native thread to an ArkTS thread, the task will execute the given thread safe function.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_threadsafe_function func | Indicates the thread safe function. |
| void *data | Indicates the data anticipated to be transferred to the ArkTS thread. |
| napi_task_priority priority | Indicates the priority of the task dispatched. |
| bool isTail | Indicates the way of the task dispatched into the native event queue. When "isTail" is true, the task will be dispatched to the tail of the native event queue. Conversely, when "isTail" is false, the tasks will be dispatched to the head of the native event queue. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Return the function execution status. |

### napi_fatal_exception()

```c
NAPI_EXTERN napi_status napi_fatal_exception(napi_env env, napi_value err)
```

**Description**

Throws UncaughtException to ArkTS.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value err | Error object which is passed to 'UncaughtException'. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) err is nullptr;\n<br>                                  If the param err is not an ArkTS Error value.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before execution.\n |

### napi_make_callback()

```c
NAPI_EXTERN napi_status napi_make_callback(napi_env env, napi_async_context async_context, napi_value recv, napi_value func, size_t argc, const napi_value* argv, napi_value* result)
```

**Description**

Allows an ArkTS function to be called in the asynchronous context. The capabilities related to 'async_hook' are not supported currently.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_async_context async_context | The context environment for the async operation. |
| napi_value recv | The 'this' pointer of the function. |
| napi_value func | ArkTS function to be called. |
| size_t argc | Size of the argument array which is passed to 'func'. |
| const napi_value* argv | Argument array. |
| napi_value* result | Result returned by the ArkTS function. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, func and(or) recv is nullptr;\n<br>                                  If the param argc is greater than 0 but argv is nullptr.\n<br>        {@link napi_object_expected } If the param recv is not an ArkTS Object.\n<br>        {@link napi_function_expected } If the param func is not an ArkTS Function.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_create_buffer()

```c
NAPI_EXTERN napi_status napi_create_buffer(napi_env env, size_t length, void** data, napi_value* result)
```

**Description**

Creates an ArkTS ArrayBuffer object of the specified size.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| size_t length | Bytes size of the underlying arraybuffer. |
| void** data | Raw pointer to the underlying arraybuffer. |
| napi_value* result | Created ArkTS ArrayBuffer object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, data or result is nullptr, or length is larger than 2097152,                                    or length is less than zero.\n |

### napi_create_promise()

```c
NAPI_EXTERN napi_status napi_create_promise(napi_env env, napi_deferred* deferred, napi_value* promise)
```

**Description**

Creates a deferred object and an ArkTS promise.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_deferred* deferred | The created deferred object which will be passed to 'napi_resolve_deferred()' or 'napi_reject_deferred()' to resolve or reject the promise. |
| napi_value* promise | The ArkTS promise which is associated with the deferred object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, deferred or resolution is nullptr.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n<br>        {@link napi_generic_failure } If create promise failed.\n |

### napi_resolve_deferred()

```c
NAPI_EXTERN napi_status napi_resolve_deferred(napi_env env, napi_deferred deferred, napi_value resolution)
```

**Description**

Resolves a promise by way of the deferred object associated.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_deferred deferred | The deferred object which is utilized to resolve the promise. |
| napi_value resolution | The resolution value used to resolve the promise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, deferred or resolution is nullptr.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n |

### napi_reject_deferred()

```c
NAPI_EXTERN napi_status napi_reject_deferred(napi_env env, napi_deferred deferred, napi_value rejection)
```

**Description**

Rejects a promise by way of the deferred object associated.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_deferred deferred | The deferred object which is utilized to reject the promise. |
| napi_value rejection | The rejection value used to reject the promise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, deferred or rejection is nullptr.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n |

### napi_is_promise()

```c
NAPI_EXTERN napi_status napi_is_promise(napi_env env, napi_value value, bool* is_promise)
```

**Description**

Checks whether the given 'napi_value' is a promise object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The 'napi_value' to be checked. |
| bool* is_promise | Boolean value that is set to true if the 'value' is a promise object, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or is_promise is nullptr.\n |

### napi_get_uv_event_loop()

```c
NAPI_EXTERN napi_status napi_get_uv_event_loop(napi_env env, struct uv_loop_s** loop)
```

**Description**

Obtains the current libuv loop instance.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| struct uv_loop_s** loop | Libuv event loop. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or loop is nullptr.\n<br>        {@link napi_generic_failure } If env is invalid.\n |

### napi_create_threadsafe_function()

```c
NAPI_EXTERN napi_status napi_create_threadsafe_function(napi_env env, napi_value func, napi_value async_resource, napi_value async_resource_name, size_t max_queue_size, size_t initial_thread_count, void* thread_finalize_data, napi_finalize thread_finalize_cb, void* context, napi_threadsafe_function_call_js call_js_cb, napi_threadsafe_function* result)
```

**Description**

Creates a thread-safe function.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value func | ArkTS function to be called. |
| napi_value async_resource | An optional Object associated with the async work that will be passed to possible 'async_hooks'. |
| napi_value async_resource_name | An ArkTS string to provide an identifier for the kind of resource that is being provided for diagnostic information exposed by the `async_hooks` interface. |
| size_t max_queue_size | Maximum size of the event queue in the thread-safe function. |
| size_t initial_thread_count | Initial thread count of the thread-safe function. |
| void* thread_finalize_data | Data passed to the finalize callback. |
| napi_finalize thread_finalize_cb | Finalize callback function which will be triggered when the thread-safe function is released. |
| void* context | Optional data is passed to 'call_js_cb'. |
| napi_threadsafe_function_call_js call_js_cb | Callback function which will be triggered after 'napi_call_threadsafe_function()' is called. |
| napi_threadsafe_function* result | The created thread-safe function. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, async_resource_name or result is nullptr; max_queue_size is less than 0;\n<br>                                  initial_thread_count is greater than 128 or less than 0; func and call_js_cb are\n<br>                                  nullptr at same time.\n<br>        {@link napi_generic_failure } If create thread-safe function failed.\n |

### napi_get_threadsafe_function_context()

```c
NAPI_EXTERN napi_status napi_get_threadsafe_function_context(napi_threadsafe_function func, void** result)
```

**Description**

Obtains the context of a thread-safe function.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_threadsafe_function func | The created thread-safe function. |
| void** result | Pointer pointer to the context of the thread-safe function. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If func or result is nullptr.\n |

### napi_call_threadsafe_function()

```c
NAPI_EXTERN napi_status napi_call_threadsafe_function(napi_threadsafe_function func, void* data, napi_threadsafe_function_call_mode is_blocking)
```

**Description**

Calls a thread-safe function.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_threadsafe_function func | The created thread-safe function. |
| void* data | Data passed to the callback function 'call_js_cb' which is registered by calling 'napi_create_threadsafe_function()'. |
| napi_threadsafe_function_call_mode is_blocking | If true, this function blocks until the event queue is not full. If false, return directly. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If func is nullptr.\n<br>        {@link napi_queue_full } If event queue is full.\n<br>        {@link napi_closing } If the thread-safe function is closing.\n<br>        {@link napi_generic_failure } If call thread-safe function failed.\n |

### napi_acquire_threadsafe_function()

```c
NAPI_EXTERN napi_status napi_acquire_threadsafe_function(napi_threadsafe_function func)
```

**Description**

Acquires a thread-safe function.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_threadsafe_function func | The created thread-safe function. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If func is nullptr.\n<br>        {@link napi_generic_failure } If acquire thread-safe function failed.\n |

### napi_release_threadsafe_function()

```c
NAPI_EXTERN napi_status napi_release_threadsafe_function(napi_threadsafe_function func, napi_threadsafe_function_release_mode mode)
```

**Description**

Releases a thread-safe function.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_threadsafe_function func | The created thread-safe function. |
| napi_threadsafe_function_release_mode mode | Value of mode can be either 'napi_tsfn_release' to indicate that no more calls should be made to the thread-safe function from current thread or 'napi_tsfn_abort' to indicate that the queue of the thread-safe function will be closed and 'napi_closing' will be return when calling 'napi_call_threadsafe_function()' under the circumstance. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If func is nullptr.\n<br>        {@link napi_generic_failure } If release thread-safe function failed.\n |

### napi_unref_threadsafe_function()

```c
NAPI_EXTERN napi_status napi_unref_threadsafe_function(napi_env env, napi_threadsafe_function func)
```

**Description**

Indicates that the event loop running on the main thread may exit before the thread-safe function is destroyed.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_threadsafe_function func | The created thread-safe function. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or func is nullptr.\n<br>        {@link napi_generic_failure } If unref thread-safe function failed.\n |

### napi_ref_threadsafe_function()

```c
NAPI_EXTERN napi_status napi_ref_threadsafe_function(napi_env env, napi_threadsafe_function func)
```

**Description**

Indicates that the event loop running on the main thread should not exit until the thread-safe function is destroyed.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_threadsafe_function func | The created thread-safe function. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or func is nullptr.\n<br>        {@link napi_generic_failure } If ref thread-safe function failed.\n |

### napi_create_date()

```c
NAPI_EXTERN napi_status napi_create_date(napi_env env, double time, napi_value* result)
```

**Description**

Creates an ArkTS 'Date' object from C double data

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| double time | ArkTS time value in milliseconds format since 01 January, 1970 UTC. |
| napi_value* result | Created ArkTS data object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n |

### napi_is_date()

```c
NAPI_EXTERN napi_status napi_is_date(napi_env env, napi_value value, bool* is_date)
```

**Description**

Checks whether the given ArkTS value is a 'Date' object. You can use this API to check the type of the parameter passed from ArkTS.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS data object. |
| bool* is_date | Boolean value that is set to true if the 'value' is a 'Date' object, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or is_date is nullptr.\n |

### napi_get_date_value()

```c
NAPI_EXTERN napi_status napi_get_date_value(napi_env env, napi_value value, double* result)
```

**Description**

Obtains the C equivalent of the given ArkTS 'Date' object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS data object. |
| double* result | C time value in milliseconds format since 01 January, 1970 UTC. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or result is nullptr.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n<br>        {@link napi_date_expected } If the 'value' is not a 'Date' object.\n |

### napi_create_bigint_int64()

```c
NAPI_EXTERN napi_status napi_create_bigint_int64(napi_env env, int64_t value, napi_value* result)
```

**Description**

Creates an ArkTS BigInt from C int64 data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| int64_t value | C int64 data. |
| napi_value* result | Created ArkTS BigInt object from C int64 data. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n |

### napi_create_bigint_uint64()

```c
NAPI_EXTERN napi_status napi_create_bigint_uint64(napi_env env, uint64_t value, napi_value* result)
```

**Description**

Creates an ArkTS BigInt from C int64 data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| uint64_t value | C int64 data. |
| napi_value* result | Created ArkTS BigInt object from C int64 data. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n |

### napi_create_bigint_words()

```c
NAPI_EXTERN napi_status napi_create_bigint_words(napi_env env, int sign_bit, size_t word_count, const uint64_t* words, napi_value* result)
```

**Description**

Creates a single ArkTS BigInt from a C uint64 array.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| int sign_bit | Sign bit of the BigInt. If sign_bit is 0, the BigInt is positive, otherwise it is negative. |
| size_t word_count | The size of the words array. |
| const uint64_t* words | C uint64 array in little-endian 64-bit format. |
| napi_value* result | Created ArkTS BigInt object from C int64 array. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, words or result is nullptr or word_count is larger than 2147483647.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n |

### napi_get_value_bigint_int64()

```c
NAPI_EXTERN napi_status napi_get_value_bigint_int64(napi_env env, napi_value value, int64_t* result, bool* lossless)
```

**Description**

Obtains a signed 64-bit integer from an ArkTS BigInt object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS BigInt object. |
| int64_t* result | Pointer points to the location where store the C signed 64-bit integer value. |
| bool* lossless | Indicates whether the conversion is lossless. If lossless is true, the conversion is lossless, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value, result or lossless is nullptr or word_count is larger than\n<br>                                  2147483647.\n<br>        {@link napi_bigint_expected } If the 'value' is not an ArkTS bigint object.\n |

### napi_get_value_bigint_uint64()

```c
NAPI_EXTERN napi_status napi_get_value_bigint_uint64(napi_env env, napi_value value, uint64_t* result, bool* lossless)
```

**Description**

Obtains an unsigned 64-bit integer from an ArkTS BigInt object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS BigInt object. |
| uint64_t* result | Pointer points to the location where store the C unsigned 64-bit integer value. |
| bool* lossless | Indicates whether the conversion is lossless. If lossless is true, the conversion is lossless, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value, result or lossless is nullptr or word_count is larger than\n<br>                                  2147483647.\n<br>        {@link napi_bigint_expected } If the 'value' is not an ArkTS bigint object.\n |

### napi_get_value_bigint_words()

```c
NAPI_EXTERN napi_status napi_get_value_bigint_words(napi_env env, napi_value value, int* sign_bit, size_t* word_count, uint64_t* words)
```

**Description**

Obtains the underlying 64-bit unsigned (uint64) byte data from an ArkTS BigInt object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS BigInt object. |
| int* sign_bit | Sign bit of the BigInt. If sign_bit is 0, the BigInt is positive, otherwise it is negative. |
| size_t* word_count | The size of the words array. |
| uint64_t* words | C uint64 array in little-endian 64-bit format. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or word_count is nullptr or word_count is larger than 2147483647.\n<br>        {@link napi_bigint_expected } If the 'value' is not an ArkTS bigint object.\n |

### napi_create_external_buffer()

```c
NAPI_EXTERN napi_status napi_create_external_buffer(napi_env env, size_t length, void* data, napi_finalize finalize_cb, void* finalize_hint, napi_value* result)
```

**Description**

Creates an ArkTS ArrayBuffer object of the specified size and initializes it with the given data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context.n |
| size_t length | Bytes size of the given data. |
| void* data | Given data. |
| napi_finalize finalize_cb | Optional native callback that can be used to free the given data when the ArkTS ArrayBuffer object has been garbage-collected. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize callback. |
| napi_value* result | Created ArkTS ArrayBuffer object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, data or result is nullptr, or length is larger than 2097152,<br>                                  or length is less than or equal to zero.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n |

### napi_create_buffer_copy()

```c
NAPI_EXTERN napi_status napi_create_buffer_copy(napi_env env, size_t length, const void* data, void** result_data, napi_value* result)
```

**Description**

Creates an ArkTS ArrayBuffer object of the specified size and initializes it with the given data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| size_t length | Bytes size of the given data. |
| const void* data | Given data. |
| void** result_data | Raw pointer to the underlying arraybuffer. |
| napi_value* result | Created ArkTS ArrayBuffer object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, data or result is nullptr, or length is larger than 2097152,                                    or length is less than or equal to zero.\n |

### napi_is_buffer()

```c
NAPI_EXTERN napi_status napi_is_buffer(napi_env env, napi_value value, bool* result)
```

**Description**

Checks whether the given ArkTS value is a 'ArrayBuffer' object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS ArrayBuffer object. |
| bool* result | Boolean value that is set to true if the 'value' is a 'ArrayBuffer' object, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or result is nullptr.\n |

### napi_get_buffer_info()

```c
NAPI_EXTERN napi_status napi_get_buffer_info(napi_env env, napi_value value, void** data, size_t* length)
```

**Description**

Obtains the underlying data of 'ArrayBuffer' and its length.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS ArrayBuffer object. |
| void** data | Raw pointer to the underlying arraybuffer. |
| size_t* length | Bytes size of the underlying arraybuffer. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or result is nullptr.\n<br>        {@link napi_arraybuffer_expected } If the 'value' is not an ArkTS array buffer object.\n |

### napi_object_freeze()

```c
NAPI_EXTERN napi_status napi_object_freeze(napi_env env, napi_value object)
```

**Description**

Freezes an ArkTS object. Once an object is frozen, its properties are immutable.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The given ArkTS object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or object is nullptr.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n |

### napi_object_seal()

```c
NAPI_EXTERN napi_status napi_object_seal(napi_env env, napi_value object)
```

**Description**

Seals an ArkTS object. Once an object is sealed, its properties cannot be added or deleted, but property values can be modified.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The given ArkTS object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or object is nullptr.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n |

### napi_detach_arraybuffer()

```c
NAPI_EXTERN napi_status napi_detach_arraybuffer(napi_env env, napi_value arraybuffer)
```

**Description**

Detaches the underlying data from an 'ArrayBuffer' object. After the data is detached, you can operate the data in C/C++.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value arraybuffer | ArkTS ArrayBuffer object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or arraybuffer is nullptr, if 'arraybuffer' is not an ArrayBuffer object.\n<br>        {@link napi_object_expected } If the 'arraybuffer' is not an ArkTS object.\n |

### napi_is_detached_arraybuffer()

```c
NAPI_EXTERN napi_status napi_is_detached_arraybuffer(napi_env env, napi_value value, bool* result)
```

**Description**

Checks whether the given 'ArrayBuffer' has been detached.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS ArrayBuffer object. |
| bool* result | Boolean value that is set to true if the 'value' has been detached, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or result is nullptr.\n |

### napi_get_all_property_names()

```c
NAPI_EXTERN napi_status napi_get_all_property_names(napi_env env, napi_value object, napi_key_collection_mode key_mode, napi_key_filter key_filter, napi_key_conversion key_conversion, napi_value* result)
```

**Description**

Obtains the names of all properties of an ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | ArkTS object. |
| napi_key_collection_mode key_mode | Key collection mode. If key_mode is napi_key_include_prototypes, the result includes properties on prototypes. If key_mode is napi_key_own_only, the result includes only properties directly on own object. |
| napi_key_filter key_filter | Which properties to be collected. |
| napi_key_conversion key_conversion | Key conversion mode. If key_conversion is napi_key_keep_numbers, the numbered property keys will keep number type. If key_conversion is napi_key_numbers_to_strings, the numbered property keys will be convert to string type. |
| napi_value* result | An array of ArkTS object that represent the property names of the object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, object or result is nullptr;\n<br>                                  key_mode is not enumeration value of napi_key_collection_mode;\n<br>                                  key_conversion is not enumeration value of napi_key_conversion.\n<br>        {@link napi_pending_exception } If an ArkTS exception existed when the function was called.\n<br>        {@link napi_object_expected } If object is not object type and function type.\n |

### napi_module_register()

```c
NAPI_EXTERN void napi_module_register(napi_module* mod)
```

**Description**

Registers a native module.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_module* mod | Native module of type 'napi_module' to be registered. |

### napi_get_last_error_info()

```c
NAPI_EXTERN napi_status napi_get_last_error_info(napi_env env, const napi_extended_error_info** result)
```

**Description**

Obtains the napi_extended_error_info struct, which contains the latest error information.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const napi_extended_error_info** result | The error info about the error. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n |

### napi_throw()

```c
NAPI_EXTERN napi_status napi_throw(napi_env env, napi_value error)
```

**Description**

Throws an ArkTS error.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value error | The ArkTS error to be thrown. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or error is nullptr, or error is not an error object.\n |

### napi_throw_error()

```c
NAPI_EXTERN napi_status napi_throw_error(napi_env env, const char* code, const char* msg)
```

**Description**

Throws an ArkTS Error with text information.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* code | Optional error code to set on the error. |
| const char* msg | C string representing the text to be associated with the error. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or msg is nullptr.\n |

### napi_throw_type_error()

```c
NAPI_EXTERN napi_status napi_throw_type_error(napi_env env, const char* code, const char* msg)
```

**Description**

Throws an ArkTS TypeError with text information.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* code | Optional error code to set on the error. |
| const char* msg | C string representing the text to be associated with the error. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or msg is nullptr.\n |

### napi_throw_range_error()

```c
NAPI_EXTERN napi_status napi_throw_range_error(napi_env env, const char* code, const char* msg)
```

**Description**

Throws an ArkTS RangeError with text information.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* code | Optional error code to set on the error. |
| const char* msg | C string representing the text to be associated with the error. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or msg is nullptr.\n |

### napi_is_error()

```c
NAPI_EXTERN napi_status napi_is_error(napi_env env, napi_value value, bool* result)
```

**Description**

Checks whether a 'napi_value' is an error object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The value to check |
| bool* result | Boolean value that is set to true if the value represents an error object, false otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or result is nullptr.\n |

### napi_create_error()

```c
NAPI_EXTERN napi_status napi_create_error(napi_env env, napi_value code, napi_value msg, napi_value* result)
```

**Description**

Creates an ArkTS Error with text information.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value code | Optional error code to set on the error. |
| napi_value msg | napi_value representing the EcmaScript string to be associated with the error. |
| napi_value* result | napi_value representing the error created. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, msg or result is nullptr, code is not string and number type or msg is\n                                    not a string type.\n |

### napi_create_type_error()

```c
NAPI_EXTERN napi_status napi_create_type_error(napi_env env, napi_value code, napi_value msg, napi_value* result)
```

**Description**

Creates an ArkTS TypeError with text information.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value code | Optional error code to set on the error. |
| napi_value msg | napi_value representing the EcmaScript string to be associated with the error. |
| napi_value* result | napi_value representing the error created. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, msg or result is nullptr, code is not string and number type or msg is\n                                    not a string type.\n |

### napi_create_range_error()

```c
NAPI_EXTERN napi_status napi_create_range_error(napi_env env, napi_value code, napi_value msg, napi_value* result)
```

**Description**

Creates an ArkTS RangeError with text information.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value code | Optional error code to set on the error. |
| napi_value msg | napi_value representing the EcmaScript string to be associated with the error. |
| napi_value* result | napi_value representing the error created. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, msg or result is nullptr, code is not string and number type or msg is\n                                    not a string type.\n |

### napi_is_exception_pending()

```c
NAPI_EXTERN napi_status napi_is_exception_pending(napi_env env, bool* result)
```

**Description**

Checks whether an exception occurs.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| bool* result | Boolean value that is true if there is a pending exception. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n |

### napi_get_and_clear_last_exception()

```c
NAPI_EXTERN napi_status napi_get_and_clear_last_exception(napi_env env, napi_value* result)
```

**Description**

Obtains and clears the latest exception.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value* result | The exception if there is a pending exception; otherwise return a null value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n |

### napi_fatal_error()

```c
NAPI_EXTERN NAPI_NO_RETURN void napi_fatal_error(const char* location, size_t location_len, const char* message, size_t message_len)
```

**Description**

Raises a fatal error to terminate the process immediately.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* location | Optional location for the error occurrence. |
| size_t location_len | The byte length of the location, or NAPI_AUTO_LENGTH if it is terminated by a null character. |
| const char* message | The message associated with the error. |
| size_t message_len | The byte length of the message, or NAPI_AUTO_LENGTH if it is terminated by a null character. |

### napi_open_handle_scope()

```c
NAPI_EXTERN napi_status napi_open_handle_scope(napi_env env, napi_handle_scope* result)
```

**Description**

Opens a scope.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_handle_scope* result | napi_value representing the new scope. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n |

### napi_close_handle_scope()

```c
NAPI_EXTERN napi_status napi_close_handle_scope(napi_env env, napi_handle_scope scope)
```

**Description**

Closes the scope passed in. After the scope is closed, all references declared in it are closed.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_handle_scope scope | The scope to close. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or scope is nullptr.\n<br>        {@link napi_handle_scope_mismatch } If there is no scope still existed.\n |

### napi_open_escapable_handle_scope()

```c
NAPI_EXTERN napi_status napi_open_escapable_handle_scope(napi_env env, napi_escapable_handle_scope* result)
```

**Description**

Opens an escapable handle scope from which the declared values can be returned to the outer scope.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_escapable_handle_scope* result | The new scope. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n |

### napi_close_escapable_handle_scope()

```c
NAPI_EXTERN napi_status napi_close_escapable_handle_scope(napi_env env, napi_escapable_handle_scope scope)
```

**Description**

Closes the escapable handle scope passed in.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_escapable_handle_scope scope | The scope to close. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or scope is nullptr.\n<br>        {@link napi_handle_scope_mismatch } If there is no scope still existed.\n |

### napi_escape_handle()

```c
NAPI_EXTERN napi_status napi_escape_handle(napi_env env, napi_escapable_handle_scope scope, napi_value escapee, napi_value* result)
```

**Description**

Promotes the handle to the input ArkTS object so that it is valid for the lifespan of its outer scope.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_escapable_handle_scope scope | Current scope. |
| napi_value escapee | The ArkTS object to be escaped. |
| napi_value* result | The handle to the escaped object in the outer scope. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, scope, escapee or result is nullptr.\n |

### napi_create_reference()

```c
NAPI_EXTERN napi_status napi_create_reference(napi_env env, napi_value value, uint32_t initial_refcount, napi_ref* result)
```

**Description**

Creates a reference for an object to extend its lifespan. The caller needs to manage the reference lifespan.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The napi_value that is being referenced. |
| uint32_t initial_refcount | The initial count for the new reference. |
| napi_ref* result | napi_ref pointing to the new reference. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or result is nullptr.\n |

### napi_delete_reference()

```c
NAPI_EXTERN napi_status napi_delete_reference(napi_env env, napi_ref ref)
```

**Description**

Deletes the reference passed in.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_ref ref | The napi_ref to be deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or ref is nullptr.\n |

### napi_reference_ref()

```c
NAPI_EXTERN napi_status napi_reference_ref(napi_env env, napi_ref ref, uint32_t* result)
```

**Description**

Increments the reference count for the reference passed in and returns the count.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_ref ref | The napi_ref whose reference count will be incremented. |
| uint32_t* result | The new reference count. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or ref is nullptr.\n |

### napi_reference_unref()

```c
NAPI_EXTERN napi_status napi_reference_unref(napi_env env, napi_ref ref, uint32_t* result)
```

**Description**

Decrements the reference count for the reference passed in and returns the count.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_ref ref | The napi_ref whose reference count will be decremented. |
| uint32_t* result | The new reference count. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or ref is nullptr.\n |

### napi_get_reference_value()

```c
NAPI_EXTERN napi_status napi_get_reference_value(napi_env env, napi_ref ref, napi_value* result)
```

**Description**

Obtains the ArkTS Object associated with the reference.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_ref ref | The napi_ref of the value being requested. |
| napi_value* result | The napi_value referenced by the napi_ref. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, ref or result is nullptr.\n |

### napi_has_own_property()

```c
NAPI_EXTERN napi_status napi_has_own_property(napi_env env, napi_value object, napi_value key, bool* result)
```

**Description**

Check if the given ArkTS Object has the named own property or not.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object. |
| napi_value key | The name of the property to check. |
| bool* result | Whether the own property exists on the object or not. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object, key and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurs in execution.\n |

### napi_define_class()

```c
NAPI_EXTERN napi_status napi_define_class(napi_env env, const char* utf8name, size_t length, napi_callback constructor, void* data, size_t property_count, const napi_property_descriptor* properties, napi_value* result)
```

**Description**

Defines an ArkTS class, including constructor function and properties.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* utf8name | Name of the ArkTS constructor function. |
| size_t length | The length of the utf8name in bytes, or NAPI_AUTO_LENGTH if it is null-terminated. |
| napi_callback constructor | Callback function that handles constructing instances of the class. |
| void* data | Optional data to be passed to the constructor callback as the data property of the callback info. |
| size_t property_count | Number of items in the properties array argument. |
| const napi_property_descriptor* properties | Array of property descriptors. |
| napi_value* result | A napi_value representing the constructor function for the class. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n execution.\n<br>        {@link napi_invalid_arg } If the param env, utf8name and(or) result is nullptr. If napi_property_descriptor<br>                                  is nullptr but property_count greater than 0.\n<br>        {@link napi_function_expected } If the param func is not an ArkTS Function.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurs in execution.\n |

### napi_create_symbol()

```c
NAPI_EXTERN napi_status napi_create_symbol(napi_env env, napi_value description, napi_value* result)
```

**Description**

Creates an ArkTS symbol.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value description | Optional napi_value representing an ArkTS string to describe the symbol. |
| napi_value* result | A napi_value representing an ArkTS symbol. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr;\n                                    If the param description is not nullptr and is not an ArkTS String.\n |

### napi_create_function()

```c
NAPI_EXTERN napi_status napi_create_function(napi_env env, const char* utf8name, size_t length, napi_callback cb, void* data, napi_value* result)
```

**Description**

Create an ArkTS function. This is the primary mechanism to call back into native code from ArkTS.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* utf8name | The visible within ArkTS as the new function's name property. |
| size_t length | The length oh the utf8name, or NAPI_AUTO_LENGTH if it is null-terminated. |
| napi_callback cb | The native function which should be called when this function object is called. |
| void* data | User-provided data context. This will be passed back into the function when invoked. |
| napi_value* result | The newly created ArkTS function. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, cb and(or) result is nullptr.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_typeof()

```c
NAPI_EXTERN napi_status napi_typeof(napi_env env, napi_value value, napi_valuetype* result)
```

**Description**

Similar to typeof operation, support external value, detects null as a separate type.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value whose type expects to query. |
| napi_valuetype* result | The type of ArkTS value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_get_value_double()

```c
NAPI_EXTERN napi_status napi_get_value_double(napi_env env, napi_value value, double* result)
```

**Description**

Obtains the double value corresponding to the given ArkTS value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS number. |
| double* result | The C primitive equivalent of ArkTS value as double. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n<br>        {@link napi_number_expected } If a non-number ArkTS value passed in it.\n |

### napi_get_value_int32()

```c
NAPI_EXTERN napi_status napi_get_value_int32(napi_env env, napi_value value, int32_t* result)
```

**Description**

Obtains the int32_t value corresponding to the given ArkTS value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS number. |
| int32_t* result | The C primitive equivalent of ArkTS value as int32_t. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n<br>        {@link napi_number_expected } If a non-number ArkTS value passed in it.\n |

### napi_get_value_uint32()

```c
NAPI_EXTERN napi_status napi_get_value_uint32(napi_env env, napi_value value, uint32_t* result)
```

**Description**

Obtains the uint32_t value corresponding to the given ArkTS value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS number. |
| uint32_t* result | The C primitive equivalent of ArkTS value as uint32_t. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n<br>        {@link napi_number_expected } If a non-number ArkTS value passed in it.\n |

### napi_get_value_int64()

```c
NAPI_EXTERN napi_status napi_get_value_int64(napi_env env, napi_value value, int64_t* result)
```

**Description**

Obtains the int64_t value corresponding to the given ArkTS value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS number. |
| int64_t* result | The C primitive equivalent of ArkTS value as int64_t. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n<br>        {@link napi_number_expected } If a non-number ArkTS value passed in it.\n |

### napi_get_value_bool()

```c
NAPI_EXTERN napi_status napi_get_value_bool(napi_env env, napi_value value, bool* result)
```

**Description**

Obtains the C Boolean equivalent of an ArkTS Boolean value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | A napi_value representing ArkTS Boolean. |
| bool* result | The C boolean equivalent of the ArkTS Boolean. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n<br>        {@link napi_boolean_expected } If a non-boolean ArkTS value passed in it.\n |

### napi_get_value_string_latin1()

```c
NAPI_EXTERN napi_status napi_get_value_string_latin1(napi_env env, napi_value value, char* buf, size_t bufsize, size_t* result)
```

**Description**

Obtains the ISO-8859-1-encoded string corresponding to the given ArkTS value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS string. |
| char* buf | Destination buffer that will be filled with the provided ISO-8859-1-encoded string. |
| size_t bufsize | The size of the buffer 'buf'. |
| size_t* result | The length of the string in ISO-8859-1-encoded format. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) value is nullptr;\n<br>                                  If the param buf and result both are nullptr.\n<br>        {@link napi_string_expected } If a non-string ArkTS value passed in it.\n |

### napi_get_value_string_utf8()

```c
NAPI_EXTERN napi_status napi_get_value_string_utf8(napi_env env, napi_value value, char* buf, size_t bufsize, size_t* result)
```

**Description**

Obtains the UTF8-encoded string corresponding to the given ArkTS value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | ArkTS string. |
| char* buf | Destination buffer that will be filled with the provided UTF8-encoded string. |
| size_t bufsize | The size of the buffer 'buf'. |
| size_t* result | The length of the string in UTF8-encoded format. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) value is nullptr;\n<br>                                  If the param buf and result both are nullptr.\n<br>        {@link napi_string_expected } If a non-string ArkTS value passed in it.\n |

### napi_get_undefined()

```c
NAPI_EXTERN napi_status napi_get_undefined(napi_env env, napi_value* result)
```

**Description**

Obtains the ArkTS undefined value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value* result | The ArkTS undefined value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the parameter env and(or) result is nullptr.\n |

### napi_get_null()

```c
NAPI_EXTERN napi_status napi_get_null(napi_env env, napi_value* result)
```

**Description**

Obtains the ArkTS null value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value* result | The ArkTS null value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_get_global()

```c
NAPI_EXTERN napi_status napi_get_global(napi_env env, napi_value* result)
```

**Description**

Obtains the ArkTS global object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value* result | The ArkTS global Object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_get_boolean()

```c
NAPI_EXTERN napi_status napi_get_boolean(napi_env env, bool value, napi_value* result)

// Methods to create Primitive types/Objects
```

**Description**

Obtains the ArkTS singleton value corresponding to given C primitive boolean value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| bool value | C primitive boolean value. |
| result | The ArkTS singleton value equivalent of C primitive boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_create_object()

```c
NAPI_EXTERN napi_status napi_create_object(napi_env env, napi_value* result)
```

**Description**

Creates a default ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value* result | napi_value representing an ArkTS object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_create_array()

```c
NAPI_EXTERN napi_status napi_create_array(napi_env env, napi_value* result)
```

**Description**

Creates an ArkTS array.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value* result | napi_value representing an ArkTS Array. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_create_array_with_length()

```c
NAPI_EXTERN napi_status napi_create_array_with_length(napi_env env, size_t length, napi_value* result)
```

**Description**

Creates an ArkTS array of the specified length.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| size_t length | The length of the Array. |
| napi_value* result | napi_value representing an ArkTS Array. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_create_double()

```c
NAPI_EXTERN napi_status napi_create_double(napi_env env, double value, napi_value* result)
```

**Description**

Creates an ArkTS number from C double data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| double value | The double value to be represented in ArkTS. |
| napi_value* result | A napi_value representing an ArkTS number. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_create_int32()

```c
NAPI_EXTERN napi_status napi_create_int32(napi_env env, int32_t value, napi_value* result)
```

**Description**

Creates an ArkTS number from C int32_t data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| int32_t value | The int32 value to be represented in ArkTS. |
| napi_value* result | A napi_value representing an ArkTS number. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_create_uint32()

```c
NAPI_EXTERN napi_status napi_create_uint32(napi_env env, uint32_t value, napi_value* result)
```

**Description**

Creates an ArkTS number from C uint32_t data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| uint32_t value | The uint32 value to be represented in ArkTS. |
| napi_value* result | A napi_value representing an ArkTS number. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_create_int64()

```c
NAPI_EXTERN napi_status napi_create_int64(napi_env env, int64_t value, napi_value* result)
```

**Description**

Creates an ArkTS number from C int64_t data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| int64_t value | The int64 value to be represented in ArkTS. |
| napi_value* result | A napi_value representing an ArkTS number. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) result is nullptr.\n |

### napi_create_string_latin1()

```c
NAPI_EXTERN napi_status napi_create_string_latin1(napi_env env, const char* str, size_t length, napi_value* result)
```

**Description**

Creates an ArkTS string from an ISO-8859-1-encoded C string.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* str | C string encoded in ISO-8859-1-encoded format. |
| size_t length | The length of the C string 'str'. |
| napi_value* result | Result of the ArkTS string from the ISO-8859-1-encoded C string. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, str and(or) result is nullptr.\n |

### napi_create_string_utf8()

```c
NAPI_EXTERN napi_status napi_create_string_utf8(napi_env env, const char* str, size_t length, napi_value* result)
```

**Description**

Creates an ArkTS string from a UTF8-encoded C string.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* str | C string encoded in UTF8 format. |
| size_t length | The length of the C string 'str'. |
| napi_value* result | Result of the ArkTS string from the UTF8-encoded C string. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, str and(or) result is nullptr.\n |

### napi_is_arraybuffer()

```c
NAPI_EXTERN napi_status napi_is_arraybuffer(napi_env env, napi_value value, bool* result)
```

**Description**

Checks if the ArkTS value is an ArkTS ArrayBuffer.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value to check. |
| bool* result | Whether the given ArkTS value is an ArkTS ArrayBuffer. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_create_arraybuffer()

```c
NAPI_EXTERN napi_status napi_create_arraybuffer(napi_env env, size_t byte_length, void** data, napi_value* result)
```

**Description**

Creates an ArkTS ArrayBuffer of the specified size.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| size_t byte_length | The length in bytes of the array buffer. |
| void** data | The byte buffer of the ArrayBuffer. |
| napi_value* result | A napi_value representing an ArkTS ArrayBuffer. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, data and(or) result is nullptr.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_create_external()

```c
NAPI_EXTERN napi_status napi_create_external(napi_env env, void* data, napi_finalize finalize_cb, void* finalize_hint, napi_value* result)
```

**Description**

Allocates a JS value with external data.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| void* data | Allocates a JS value that references external data. |
| napi_finalize finalize_cb | Optional callback to call when the external value is being collected. |
| void* finalize_hint | Optional hint that can be passed to the finalize callback function during the garbage collection process. |
| napi_value* result | A napi_value representing an external value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env or result is nullptr.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_create_external_arraybuffer()

```c
NAPI_EXTERN napi_status napi_create_external_arraybuffer(napi_env env, void* external_data, size_t byte_length, napi_finalize finalize_cb, void* finalize_hint, napi_value* result)
```

**Description**

The underlying data that ArrayBuffer point to.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| void* external_data | Allocates an ArkTS value that references external data. |
| size_t byte_length | The length in bytes of the underlying buffer. |
| napi_finalize finalize_cb | Optional callback to call when the ArrayBuffer is being collected. |
| void* finalize_hint | Optional hint that can be passed to the finalize callback function during the garbage collection process. |
| napi_value* result | A napi_value representing an ArkTS ArrayBuffer. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, external_data, finalize_cb and(or) result is nullptr.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_get_arraybuffer_info()

```c
NAPI_EXTERN napi_status napi_get_arraybuffer_info(napi_env env, napi_value arraybuffer, void** data, size_t* byte_length)
```

**Description**

Obtains the underlying data buffer of ArrayBuffer and its length.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value arraybuffer | The napi_value representing the ArrayBuffer being queried. |
| void** data | The underlying data buffer of the ArrayBuffer. |
| size_t* byte_length | Length in bytes of the underlying data buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, arraybuffer and(or) byte_length is nullptr.\n<br>        {@link napi_arraybuffer_expected } If the param is neither ArkTS TypedArray nor SendableArrayBuffer.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_is_typedarray()

```c
NAPI_EXTERN napi_status napi_is_typedarray(napi_env env, napi_value value, bool* result)
```

**Description**

Checks if the ArkTS value is an ArkTS TypedArray.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value to check. |
| bool* result | Whether the given ArkTS value is an ArkTS TypedArray. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_create_typedarray()

```c
NAPI_EXTERN napi_status napi_create_typedarray(napi_env env, napi_typedarray_type type, size_t length, napi_value arraybuffer, size_t byte_offset, napi_value* result)
```

**Description**

Creates an ArkTS TypeArray from an existing ArrayBuffer.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_typedarray_type type | The element datatype of the TypedArray. |
| size_t length | Number of elements in the TypedArray. |
| napi_value arraybuffer | The underlying ArrayBuffer that supports the TypedArray. |
| size_t byte_offset | The byte offset within the ArrayBuffer from which to start projecting the TypedArray. |
| napi_value* result | A napi_value representing an ArkTS TypedArray. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, arraybuffer and(or) result is nullptr;\n<br>                                  If param type is not a valid napi_typedarray_type.\n<br>        {@link napi_arraybuffer_expected } If a non-arraybuffer ArkTS value passed in it.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_get_typedarray_info()

```c
NAPI_EXTERN napi_status napi_get_typedarray_info(napi_env env, napi_value typedarray, napi_typedarray_type* type, size_t* length, void** data, napi_value* arraybuffer, size_t* byte_offset)
```

**Description**

Obtains properties of a TypedArray.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value typedarray | The napi_value for the TypedArray whose properties are being checked. |
| napi_typedarray_type* type | The datatype of elements in the TypedArray. |
| size_t* length | The number of elements in the TypedArray. |
| void** data | The data buffer underlying the TypedArray adjusted by the byte_offset. |
| napi_value* arraybuffer | The ArrayBuffer underlying the TypedArray. |
| size_t* byte_offset | The byte offset within the underlying arraybuffer |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) typedarray is nullptr;\n                                     If the param typedarray is neither ArkTS TypedArray nor SendableTypedArray.\n |

### napi_create_dataview()

```c
NAPI_EXTERN napi_status napi_create_dataview(napi_env env, size_t length, napi_value arraybuffer, size_t byte_offset, napi_value* result)
```

**Description**

Creates an ArkTS DataView from an existing ArrayBuffer.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| size_t length | Number of elements in the DataView. |
| napi_value arraybuffer | The underlying ArrayBuffer that supports the DataView. |
| size_t byte_offset | The byte offset within the ArrayBuffer from which to start projecting the DataView. |
| napi_value* result | A napi_value representing an ArkTS DataView. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, arraybuffer and(or) result is nullptr.\n<br>        {@link napi_arraybuffer_expected } If a non-arraybuffer ArkTS value passed in it.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n                                          If the sum of byte_length and length is greater than the byte length of\n                                          the arraybuffer.\n |

### napi_is_dataview()

```c
NAPI_EXTERN napi_status napi_is_dataview(napi_env env, napi_value value, bool* result)
```

**Description**

Checks if the ArkTS value is an ArkTS DataView.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value to check. |
| bool* result | Whether the given ArkTS value is an ArkTS DataView. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_get_dataview_info()

```c
NAPI_EXTERN napi_status napi_get_dataview_info(napi_env env, napi_value dataview, size_t* bytelength, void** data, napi_value* arraybuffer, size_t* byte_offset)
```

**Description**

Obtains properties of a DataView.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value dataview | The napi_value for the DataView whose properties are being checked. |
| size_t* bytelength | The number of elements in the DataView. |
| void** data | The data buffer underlying the DataView. |
| napi_value* arraybuffer | The ArrayBuffer underlying the DataView. |
| size_t* byte_offset | The byte offset within the underlying arraybuffer |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) dataview is nullptr;\n                                    If non-dataview ArkTS value passed in.\n |

### napi_get_array_length()

```c
NAPI_EXTERN napi_status napi_get_array_length(napi_env env, napi_value value, uint32_t* result)
```

**Description**

Obtains the array length.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The napi_value representing the ArkTS Array being queried. |
| uint32_t* result | The length of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr;\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_get_prototype()

```c
NAPI_EXTERN napi_status napi_get_prototype(napi_env env, napi_value object, napi_value* result)
```

**Description**

Obtains the prototype of an ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The napi_value representing an ArkTS Object whose prototype to return. |
| napi_value* result | A napi_value representing prototype of the object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object or result is nullptr;\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_get_value_external()

```c
NAPI_EXTERN napi_status napi_get_value_external(napi_env env, napi_value value, void** result)
```

**Description**

Obtains the external data pointer previously passed through napi_create_external().

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | JavaScript external value. |
| void** result | The data wrapped by the JavaScript external value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value or result is nullptr;\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_coerce_to_bool()

```c
NAPI_EXTERN napi_status napi_coerce_to_bool(napi_env env, napi_value value, napi_value* result)
```

**Description**

Coerce the given ArkTS value to an ArkTS boolean value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value to coerce. |
| napi_value* result | The coerced ArkTS boolean value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_coerce_to_number()

```c
NAPI_EXTERN napi_status napi_coerce_to_number(napi_env env, napi_value value, napi_value* result)
```

**Description**

Coerce the given ArkTS value to an ArkTS number value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value to coerce. |
| napi_value* result | The coerced ArkTS number value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_coerce_to_object()

```c
NAPI_EXTERN napi_status napi_coerce_to_object(napi_env env, napi_value value, napi_value* result)
```

**Description**

Coerce the given ArkTS value to an ArkTS object value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value to coerce. |
| napi_value* result | The coerced ArkTS object value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_coerce_to_string()

```c
NAPI_EXTERN napi_status napi_coerce_to_string(napi_env env, napi_value value, napi_value* result)
```

**Description**

Coerce the given ArkTS value to an ArkTS string value.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value to coerce. |
| napi_value* result | The coerced ArkTS string value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_instanceof()

```c
NAPI_EXTERN napi_status napi_instanceof(napi_env env, napi_value object, napi_value constructor, bool* result)
```

**Description**

Invoke instanceof operation on the object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object to check. |
| napi_value constructor | The ArkTS constructor function to check against. |
| bool* result | Set to true if the given ArkTS object instanceof constructor. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object, constructor and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS object value.\n<br>        {@link napi_function_expected } If the param constructor is not an ArkTS function value.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_is_array()

```c
NAPI_EXTERN napi_status napi_is_array(napi_env env, napi_value value, bool* result)
```

**Description**

Checks if the ArkTS value is an ArkTS Array.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The ArkTS value to check. |
| bool* result | Whether the given ArkTS value is an ArkTS Array. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_strict_equals()

```c
NAPI_EXTERN napi_status napi_strict_equals(napi_env env, napi_value lhs, napi_value rhs, bool* result)
```

**Description**

Checks if the two ArkTS values are equal.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value lhs | The ArkTS value to check. |
| napi_value rhs | The ArkTS value to check against. |
| bool* result | Whether the two given ArkTS values are equal. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n |

### napi_get_property_names()

```c
NAPI_EXTERN napi_status napi_get_property_names(napi_env env, napi_value object, napi_value* result)
```

**Description**

Obtains the names of the enumerable properties of object as an Array of Strings. The keys that are symbols will not be included.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object from which the property is retrieved. |
| napi_value* result | An ArkTS Array that contains the attribute names of the object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n |

### napi_set_property()

```c
NAPI_EXTERN napi_status napi_set_property(napi_env env, napi_value object, napi_value key, napi_value value)
```

**Description**

Set a property on the given ArkTS Object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object. |
| napi_value key | The name of the property to set. |
| napi_value value | The property value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object, key and(or) value is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_get_property()

```c
NAPI_EXTERN napi_status napi_get_property(napi_env env, napi_value object, napi_value key, napi_value* result)
```

**Description**

Get the requests property of the given ArkTS Object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object. |
| napi_value key | The name of the property to get. |
| napi_value* result | The value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object, key and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_has_property()

```c
NAPI_EXTERN napi_status napi_has_property(napi_env env, napi_value object, napi_value key, bool* result)
```

**Description**

Check if the given ArkTS Object has the named property or not.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object. |
| napi_value key | The name of the property to check. |
| bool* result | Whether the property exists on the object or not. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object, key and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_delete_property()

```c
NAPI_EXTERN napi_status napi_delete_property(napi_env env, napi_value object, napi_value key, bool* result)
```

**Description**

Delete the named property of the given ArkTS Object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object. |
| napi_value key | The name of the property to delete. |
| bool* result | Whether the execution is succeed or not. Can optionally be ignored by passing nullptr. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object and(or) key is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_set_named_property()

```c
NAPI_EXTERN napi_status napi_set_named_property(napi_env env, napi_value object, const char* utf8name, napi_value value)
```

**Description**

Set a property on the given ArkTS Object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object. |
| const char* utf8name | The name of the property to set. |
| napi_value value | The property value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object, utf8name and(or) value is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_get_named_property()

```c
NAPI_EXTERN napi_status napi_get_named_property(napi_env env, napi_value object, const char* utf8name, napi_value* result)
```

**Description**

Get the requests property of the given ArkTS Object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object. |
| const char* utf8name | The name of the property to get. |
| napi_value* result | The value of the property. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object, utf8name and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_has_named_property()

```c
NAPI_EXTERN napi_status napi_has_named_property(napi_env env, napi_value object, const char* utf8name, bool* result)
```

**Description**

Check if the given ArkTS Object has the named property or not.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS object. |
| const char* utf8name | The name of the property to check. |
| bool* result | Whether the property exists on the object or not. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object, utf8name and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_set_element()

```c
NAPI_EXTERN napi_status napi_set_element(napi_env env, napi_value object, uint32_t index, napi_value value)
```

**Description**

Set a element on the given ArkTS Array.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS Array. |
| uint32_t index | The index of the element to set. |
| napi_value value | The element value. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object and(or) value is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_get_element()

```c
NAPI_EXTERN napi_status napi_get_element(napi_env env, napi_value object, uint32_t index, napi_value* result)
```

**Description**

Get the requests element of the given ArkTS Array.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS Array. |
| uint32_t index | The index of the element to get. |
| napi_value* result | The value of the element. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_has_element()

```c
NAPI_EXTERN napi_status napi_has_element(napi_env env, napi_value object, uint32_t index, bool* result)
```

**Description**

Check if the given ArkTS Array has an element at the requested index.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS Array. |
| uint32_t index | The name of the property to check. |
| bool* result | Whether the property exists on the Array or not. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_delete_element()

```c
NAPI_EXTERN napi_status napi_delete_element(napi_env env, napi_value object, uint32_t index, bool* result)
```

**Description**

Delete the special index from the given ArkTS Array.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS Array. |
| uint32_t index | The index of the element to delete. |
| bool* result | Whether the execution is succeed or not. Can optionally  be ignored by passing nullptr. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object and(or) key is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_define_properties()

```c
NAPI_EXTERN napi_status napi_define_properties(napi_env env, napi_value object, size_t property_count, const napi_property_descriptor* properties)
```

**Description**

Efficient define multiple properties on the given ArkTS Object by napi_property_descriptor.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The ArkTS Object. |
| size_t property_count | The count of elements in the properties array. |
| const napi_property_descriptor* properties | The properties array. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, object and(or) properties is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_call_function()

```c
NAPI_EXTERN napi_status napi_call_function(napi_env env, napi_value recv, napi_value func, size_t argc, const napi_value* argv, napi_value* result)
```

**Description**

Invoke an ArkTS function. This is the primary mechanism to call back into JavaScript.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value recv | The this value passed to the called function |
| napi_value func | The ArkTS function to be invoked. |
| size_t argc | The count of elements in the argv array. |
| const napi_value* argv | ArkTS values passed in as arguments to the function. |
| napi_value* result | Whether the provided 'type_tag' is matched with the tag on the ArkTS object 'value'. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) func is nullptr. If argv is nullptr but argc greater\n<br>                                  than 0.\n<br>        {@link napi_function_expected } If the param func is not an ArkTS Function.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_get_cb_info()

```c
NAPI_EXTERN napi_status napi_get_cb_info(napi_env env, napi_callback_info cbinfo, size_t* argc, napi_value* argv, napi_value* this_arg, void** data)
```

**Description**

Obtains callback details about the call like arguments, this from given callback info.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_callback_info cbinfo | The callback info. |
| size_t* argc | Size of the argv array. |
| napi_value* argv | The Array which arguments will be copied to. If there are more arguments than the provided count, only the requested number of arguments are copied. If there are fewer arguments provided, the rest argv is filled with undefined. Can optionally be ignored by passing nullptr. |
| napi_value* this_arg | Receives the ArkTS this argument for the call. Can optionally be ignored by passing nullptr. |
| void** data | Receives the data pointer for the callback. Can optionally be ignored by passing nullptr. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) cbinfo is nullptr.\n |

### napi_get_new_target()

```c
NAPI_EXTERN napi_status napi_get_new_target(napi_env env, napi_callback_info cbinfo, napi_value* result)
```

**Description**

Obtains callback details about the call like arguments, this from given callback info.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_callback_info cbinfo | The callback info. |
| napi_value* result | The new.target of the constructor call. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, cbinfo and(or) result is nullptr.\n |

### napi_new_instance()

```c
NAPI_EXTERN napi_status napi_new_instance(napi_env env, napi_value constructor, size_t argc, const napi_value* argv, napi_value* result)
```

**Description**

Instantiate a new ArkTS value using a given napi_value that represents the constructor for the object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value constructor | The ArkTS function to be invoked as a constructor. |
| size_t argc | The count of elements in the argv array. |
| const napi_value* argv | Array of ArkTS values representing the arguments to the constructor. If argc is 0 this parameter may be omitted by passing in nullptr. |
| napi_value* result | The ArkTS object returned, which in this case is the constructed object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) func is nullptr. If argv is nullptr but argc greater\n<br>                                  than 0.\n<br>        {@link napi_function_expected } If the param func is not an ArkTS Function.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_wrap()

```c
NAPI_EXTERN napi_status napi_wrap(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, void* finalize_hint, napi_ref* result)
```

**Description**

Wraps a native instance in a ArkTS object. The native instance can be retrieved later using napi_unwrap.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value js_object | The ArkTS object that will be the wrapper for the native object. |
| void* native_object | The native instance that will be wrapped in the ArkTS object. |
| napi_finalize finalize_cb | Native callback that can be used to free the native instance when the JavaScript object has been garbage-collected. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize callback. |
| napi_ref* result | Optional reference to the wrapped object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, js_object, native_object and(or) finalize_cb is nullptr.\n<br>        {@link napi_object_expected } If the param js_object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_unwrap()

```c
NAPI_EXTERN napi_status napi_unwrap(napi_env env, napi_value js_object, void** result)
```

**Description**

Retrieves a native instance that was previously wrapped in an ArkTS object using napi_wrap.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value js_object | The ArkTS object. |
| void** result | Pointer to the wrapped native instance. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, js_object and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param js_object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_remove_wrap()

```c
NAPI_EXTERN napi_status napi_remove_wrap(napi_env env, napi_value js_object, void** result)
```

**Description**

Retrieves a native instance that was previously wrapped in the ArkTS object js_object using napi_wrap and removes the wrapping.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value js_object | The ArkTS object. |
| void** result | Pointer to the wrapped native instance. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, js_object and(or) result is nullptr.\n<br>        {@link napi_object_expected } If the param js_object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_create_async_work()

```c
NAPI_EXTERN napi_status napi_create_async_work(napi_env env, napi_value async_resource, napi_value async_resource_name, napi_async_execute_callback execute, napi_async_complete_callback complete, void* data, napi_async_work* result)
```

**Description**

Allocate a work object that is used to execute logic asynchronously.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value async_resource | Not supported, can be ignored by passing nullptr. |
| napi_value async_resource_name |  Identifier for the kind of resource that is being provided for diagnostic information exposed by the HiTrace. |
| napi_async_execute_callback execute | The native function which should be called to execute the logic asynchronously. The given function is called from a worker pool thread and can execute in parallel with the main event loop thread. |
| napi_async_complete_callback complete | The native function which will be called when the asynchronous logic is completed or is cancelled. The given function is called from the main event loop thread. |
| void* data | User-provided data context. This will be passed back into the execute and complete functions. |
| napi_async_work* result | The handle to the newly created async work. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, async_resource_name, execute, complete and(or) result is\n                                    nullptr.\n |

### napi_delete_async_work()

```c
NAPI_EXTERN napi_status napi_delete_async_work(napi_env env, napi_async_work work)
```

**Description**

Free a previously allocated work object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_async_work work | The handle returned by the call to napi_create_async_work. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) work is nullptr.\n |

### napi_queue_async_work()

```c
NAPI_EXTERN napi_status napi_queue_async_work(napi_env env, napi_async_work work)
```

**Description**

Requests that the previously allocated work be scheduled for execution. Once it returns successfully, this API must not be called again with the same napi_async_work item or the result will be undefined.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_async_work work | The handle returned by the call to napi_create_async_work. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) work is nullptr.\n |

### napi_cancel_async_work()

```c
NAPI_EXTERN napi_status napi_cancel_async_work(napi_env env, napi_async_work work)
```

**Description**

Cancels queued work if it has not yet been started. If it has already started executing, it cannot be cancelled. If successful, the complete callback will be invoked with a status value of napi_cancelled. The work should not be deleted before the complete callback invocation, even if it has been successfully cancelled.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_async_work work | The handle returned by the call to napi_create_async_work. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env and(or) work is nullptr.\n |

### napi_wrap_enhance()

```c
NAPI_EXTERN napi_status napi_wrap_enhance(napi_env env, napi_value js_object, void* native_object, napi_finalize finalize_cb, bool async_finalizer, void* finalize_hint, size_t native_binding_size, napi_ref* result)
```

**Description**

Wraps a native instance in an ArkTS object.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | The environment that the API is invoked under. |
| napi_value js_object | The ArkTS object that will be the wrapper for the native object. |
| void* native_object | The native instance that will be wrapped in the ArkTS object. |
| napi_finalize finalize_cb | Optional native callback that can be used to free the native instance when the ArkTS object has been garbage-collected. |
| bool async_finalizer | A boolean value to determine that finalize_cb execute async or not. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize callback. |
| size_t native_binding_size | The size of native binding. |
| napi_ref* result | Optional reference to the wrapped object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, js_object or native_object is nullptr.\n<br>        {@link napi_object_expected } If the param js_object is not an ArkTS Object or Function.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before(in) execution.\n |

### napi_create_ark_context()

```c
NAPI_EXTERN napi_status napi_create_ark_context(napi_env env, napi_env *newEnv)
```

**Description**

To create a new virtual machine context.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_env *newEnv | New generated virtual machine context which is expected to be used later. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env is nullptr.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurs in execution.\n |

### napi_switch_ark_context()

```c
NAPI_EXTERN napi_status napi_switch_ark_context(napi_env env)
```

**Description**

To switch a virtual machine context which is expected to be used later.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Designated Virtual machine context which is expected to be used as the current virtual machine context. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env is nullptr.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurs in execution.\n |

### napi_destroy_ark_context()

```c
NAPI_EXTERN napi_status napi_destroy_ark_context(napi_env env)
```

**Description**

To destroy a virtual machine context which will not be used again.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Virtual machine context expected to be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env is nullptr.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurs in execution.\n |

### napi_open_critical_scope()

```c
NAPI_EXTERN napi_status napi_open_critical_scope(napi_env env, napi_critical_scope* scope)
```

**Description**

To open a critical scope.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| [napi_critical_scope](capi-arkts-napi-nativemodule-napi-critical-scope--8h.md)* scope | A critical scope of type of napi_critical_scope is generated. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param scope is nullptr.\n |

### napi_close_critical_scope()

```c
NAPI_EXTERN napi_status napi_close_critical_scope(napi_env env, napi_critical_scope scope)
```

**Description**

To close a critical scope.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| [napi_critical_scope](capi-arkts-napi-nativemodule-napi-critical-scope--8h.md) scope | A critical scope to be closed. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param scope is nullptr.\n |

### napi_get_buffer_string_utf16_in_critical_scope()

```c
NAPI_EXTERN napi_status napi_get_buffer_string_utf16_in_critical_scope(napi_env env, napi_value value, const char16_t** buffer, size_t* length)
```

**Description**

To obtain a ArkTS string buffer cache within the critical scope.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | An ArkTS string object which need be encoded with UTF16 format. |
| const char16_t** buffer | String buffer cache of the ArkTS string object value. |
| size_t* length | Length size of the string buffer cache which needs to be obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, value, buffer and length is nullptr.\n |

### napi_create_strong_reference()

```c
NAPI_EXTERN napi_status napi_create_strong_reference(napi_env env, napi_value value, napi_strong_ref* result)
```

**Description**

Creates a strong reference for an ArkTS object to extend its lifespan. The caller needs to manage the reference lifespan.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The napi_value that is being referenced. |
| [napi_strong_ref](capi-arkts-napi-nativemodule-napi-strong-ref--8h.md)* result | napi_strong_ref pointing to the new strong reference. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or result is nullptr.\n |

### napi_delete_strong_reference()

```c
NAPI_EXTERN napi_status napi_delete_strong_reference(napi_env env, napi_strong_ref ref)
```

**Description**

Deletes the strong reference passed in.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| [napi_strong_ref](capi-arkts-napi-nativemodule-napi-strong-ref--8h.md) ref | The napi_strong_ref to be deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or ref is nullptr.\n |

### napi_get_strong_reference_value()

```c
NAPI_EXTERN napi_status napi_get_strong_reference_value(napi_env env, napi_strong_ref ref, napi_value* result)
```

**Description**

Obtains the ArkTS Object associated with the strong reference.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| [napi_strong_ref](capi-arkts-napi-nativemodule-napi-strong-ref--8h.md) ref | The napi_strong_ref of the value being requested. |
| napi_value* result | The napi_value referenced by the napi_strong_ref. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, ref or result is nullptr.\n |

### napi_create_external_string_utf16()

```c
NAPI_EXTERN napi_status napi_create_external_string_utf16(napi_env env, const char16_t* str, size_t length, napi_finalize_callback finalize_callback, void* finalize_hint, napi_value* result)
```

**Description**

Creates an ArkTS string from a UTF16-encoded C string.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char16_t* str | C string encoded in UTF16 format. |
| size_t length | The length of the C string 'str'. |
| [napi_finalize_callback](capi-native-api-h.md#napi_finalize_callback) finalize_callback | Native finalize callback used to recycle native resource. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize_callback. |
| napi_value* result | Result of the ArkTS string from the UTF16-encoded C string. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, str and(or) result is nullptr;\n                                    If the param length is not equal with NAPI_AUTO_LENGTH and\n                                    length is larger than INT_MAX;\n |

### napi_create_external_string_ascii()

```c
NAPI_EXTERN napi_status napi_create_external_string_ascii(napi_env env, const char* str, size_t length, napi_finalize_callback finalize_callback, void* finalize_hint, napi_value* result)
```

**Description**

Creates an ArkTS string from a ASCII-encoded C string.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| const char* str | C string encoded in ASCII format. |
| size_t length | The length of the C string 'str'. |
| [napi_finalize_callback](capi-native-api-h.md#napi_finalize_callback) finalize_callback | Native finalize callback used to recycle native resource. |
| void* finalize_hint | Optional contextual hint that is passed to the finalize_callback. |
| napi_value* result | Result of the ArkTS string from the ASCII-encoded C string. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If the param env, str and(or) result is nullptr;\n                                    If the param length is not equal with NAPI_AUTO_LENGTH and\n                                    length is larger than INT_MAX;\n |

### napi_create_strong_sendable_reference()

```c
NAPI_EXTERN napi_status napi_create_strong_sendable_reference(napi_env env, napi_value value, napi_sendable_ref* result)
```

**Description**

Creates a strong sendable reference for an ArkTS object to extend its lifespan. The caller needs to manage the sendable reference lifespan.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value value | The sendable ArkTS object that is being referenced. |
| [napi_sendable_ref](capi-arkts-napi-nativemodule-napi-sendable-ref--8h.md)* result | The napi_sendable_ref pointing to the new strong sendable reference. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, value or result is nullptr.\n |

### napi_delete_strong_sendable_reference()

```c
NAPI_EXTERN napi_status napi_delete_strong_sendable_reference(napi_env env, napi_sendable_ref ref)
```

**Description**

Deletes the strong sendable reference passed in.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| [napi_sendable_ref](capi-arkts-napi-nativemodule-napi-sendable-ref--8h.md) ref | The sendable reference to be deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or ref is nullptr.\n |

### napi_get_strong_sendable_reference_value()

```c
NAPI_EXTERN napi_status napi_get_strong_sendable_reference_value(napi_env env, napi_sendable_ref ref, napi_value* result)
```

**Description**

Obtains the ArkTS Object associated with the strong reference.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| [napi_sendable_ref](capi-arkts-napi-nativemodule-napi-sendable-ref--8h.md) ref | The sendable reference of the sendable object value being requested. |
| napi_value* result | The sendable ArkTS object referenced by the sendable reference. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, ref or result is nullptr.\n |

### napi_throw_business_error()

```c
NAPI_EXTERN napi_status napi_throw_business_error(napi_env env, int32_t errorCode, const char* msg)
```

**Description**

Throws an ArkTS Error with text information.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| int32_t errorCode | Error code to be set on the error object. |
| const char* msg | C string representing the text to be associated with the error object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or msg is nullptr.\n<br>        {@link napi_pending_exception } There is an uncaught exception occurred before execution.\n |

### napi_create_callsite_info()

```c
NAPI_EXTERN napi_status napi_create_callsite_info(napi_env env, napi_callsite_info* result)
```

**Description**

Creates a callsite info handle for caching inline cache (IC) information of property access. Each different callsite should create an independent handle. The same handle can be reused across multiple calls but must not be used across threads. When no longer needed, napi_delete_callsite_info must be called to release the handle.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| [napi_callsite_info](capi-arkts-napi-nativemodule-napi-callsite-info--8h.md)* result | Pointer to napi_callsite_info to receive the created callsite info handle. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env or result is nullptr.\n<br>        {@link napi_pending_exception } If a pending exception existed before the call.\n<br>        {@link napi_generic_failure } If the callsite info creation failed.\n |

### napi_delete_callsite_info()

```c
NAPI_EXTERN napi_status napi_delete_callsite_info(napi_env env, napi_callsite_info info)
```

**Description**

Deletes a callsite info handle and releases associated cache resources.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| [napi_callsite_info](capi-arkts-napi-nativemodule-napi-callsite-info--8h.md) info | The callsite info handle to be deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env is nullptr.\n |

### napi_get_property_with_callsite_info()

```c
NAPI_EXTERN napi_status napi_get_property_with_callsite_info(napi_env env, napi_value object, napi_value key, napi_callsite_info info, napi_value* result, bool* hit)
```

**Description**

Uses callsite info to quickly get an object property value. When the IC hits (the object has the same hidden class), it skips the regular hash table lookup and prototype chain traversal. The info parameter can be NULL, in which case the behavior is equivalent to napi_get_property.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The object to get the property from. |
| napi_value key | The key name of the property to get. |
| [napi_callsite_info](capi-arkts-napi-nativemodule-napi-callsite-info--8h.md) info | Callsite info handle for IC caching. Can be NULL. |
| napi_value* result | Pointer to napi_value to receive the property value. |
| bool* hit | Receives whether the IC cache was hit (true) or missed (false). |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, object, key or result is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_set_property_with_callsite_info()

```c
NAPI_EXTERN napi_status napi_set_property_with_callsite_info(napi_env env, napi_value object, napi_value key, napi_value value, napi_callsite_info info, bool* hit)
```

**Description**

Uses callsite info to quickly set an object property value. When the IC hits (the object has the same hidden class), it skips the regular property setting process. The info parameter can be NULL, in which case the behavior is equivalent to napi_set_property.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| napi_value object | The object to set the property on. |
| napi_value key | The key name of the property to set. |
| napi_value value | The property value to set. |
| [napi_callsite_info](capi-arkts-napi-nativemodule-napi-callsite-info--8h.md) info | Callsite info handle for IC caching. Can be NULL. |
| bool* hit | Receives whether the IC cache was hit (true) or missed (false). |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          {@link napi_ok } If the function executed successfully.\n<br>        {@link napi_invalid_arg } If env, object, key or value is nullptr.\n<br>        {@link napi_object_expected } If the param object is not an ArkTS Object.\n<br>        {@link napi_pending_exception } If have uncaught exception, or exception occurred in execution.\n |

### napi_get_global_handle_count()

```c
NAPI_EXTERN napi_status napi_get_global_handle_count(napi_env env, size_t* count)
```

**Description**

To obtain the count of global object in current ArkTS runtime thread.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| napi_env env | Current running virtual machine context. |
| size_t* count | The count number of global object. |

**Returns**:

| Type | Description |
| -- | -- |
| NAPI_EXTERN napi_status | Returns the function execution status.          <ul><li>{@link napi_ok } If the function executed successfully.</li><br>        <li>{@link napi_invalid_arg } If env or count is nullptr.</li><br>        <li>{@link napi_pending_exception } There is an uncaught exception occurred before execution.</li></ul> |


