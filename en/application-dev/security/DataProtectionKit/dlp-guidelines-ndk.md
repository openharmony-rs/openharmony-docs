# DLP Service Development (C/C++)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

Data loss prevention (DLP) is a system solution provided to prevent data disclosure. This module provides APIs for cross-device file access management, encrypted storage, and access authorization.

- Permission management: obtains the permission information of this DLP sandbox.
- File information obtaining: obtains basic information about a DLP file, such as the original file name.
- Sandbox environment detection: checks whether this application is running in a DLP sandbox environment.
- Configuration management: sets, obtains, and clears sandbox application configuration.
      
## API Description
The following table lists the key APIs of the DLP service. For details about the APIs, see the [API Reference](../../reference/apis-data-protection-kit/capi-dlp-permission-api-h.md)
| Name| Description|
| -------- | -------- |
| DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess \*dlpFileAccess, uint32_t \*flags)| Obtains the permission information of this DLP sandbox.|
|DLP_ErrCode OH_DLP_GetOriginalFileName(const char \*fileName, char \*\*originalFileName)  | Obtains the original file name of a DLP file.|
|DLP_ErrCode OH_DLP_IsInSandbox(bool \*isInSandbox)  |Checks whether this application is running in a DLP sandbox environment. |
| DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char \*configInfo) | Sets sandbox application configuration.|
| DLP_ErrCode OH_DLP_GetSandboxAppConfig(char \*\*configInfo) |Obtains the sandbox application configuration. |
|DLP_ErrCode OH_DLP_CleanSandboxAppConfig()  |Cleans the sandbox application configuration. |


## Development Procedure

1. Import the shared library of the data leakage prevention function to the **CMakeLists.txt** file and link the library.
   ``` c++
   cmake_minimum_required(VERSION 3.5.0)
   project(DlpApiTest)

   set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

   if(DEFINED PACKAGE_FIND_FILE)
       include(${PACKAGE_FIND_FILE})
   endif()

   include_directories(${NATIVERENDER_ROOT_PATH}
                       ${NATIVERENDER_ROOT_PATH}/include)

   add_library(entry SHARED napi_init.cpp)
   target_link_libraries(entry PUBLIC libace_napi.z.so libohdlp_permission.so)
   ```

2. Import the header file of the data loss prevention service and the header file related to NAPI.
   ``` c++
   #include "napi/native_api.h"
   #include <cstdint>
   #include <cstdlib>
   #include "DataProtectionKit/dlp_permission_api.h"
   ```

3. Obtain the permission information of this DLP sandbox.
   ``` c++
   static napi_value GetDlpPermissionInfo(napi_env env, napi_callback_info info)
   {
       DLP_FileAccess dlpFileAccess = NO_PERMISSION;
       uint32_t flags = 0;
       DLP_ErrCode ret = OH_DLP_GetDlpPermissionInfo(&dlpFileAccess, &flags);
       if (ret == DLP_ErrCode::ERR_OH_SUCCESS) {
           napi_value result[2] = {nullptr};
           napi_create_int32(env, dlpFileAccess, &result[0]);
           napi_create_int32(env, flags, &result[1]);
           return result[1];
       }
       napi_value result = nullptr;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ```

4. Obtain the original name of a DLP file.
   ``` c++
   static napi_value GetOriginalFileName(napi_env env, napi_callback_info info)
   {
       const char *fileName = "test.txt.dlp";
       char *originalFileName = nullptr;
       DLP_ErrCode ret = OH_DLP_GetOriginalFileName(fileName, &originalFileName);
       if (ret == DLP_ErrCode::ERR_OH_SUCCESS) {
           napi_value result = nullptr;
           napi_create_string_utf8(env, originalFileName, NAPI_AUTO_LENGTH, &result);
           return result;
       }
       napi_value result = nullptr;
       napi_create_int32(env, ret, &result);
       free(originalFileName);
       return result;
   }
   ``` 

5. Check whether this application is running in a DLP sandbox environment.
   ``` c++
   static napi_value IsInSandbox(napi_env env, napi_callback_info info)
   {
       bool isInSandbox = false;
       DLP_ErrCode ret = OH_DLP_IsInSandbox(&isInSandbox);
       if (ret == DLP_ErrCode::ERR_OH_SUCCESS) {
           napi_value result = nullptr;
           napi_get_boolean(env, isInSandbox, &result);
           return result;
       }
       napi_value result = nullptr;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ``` 

6. Set sandbox application configuration.
   ``` c++
   static napi_value SetSandboxAppConfig(napi_env env, napi_callback_info info)
   {
       const char *configInfo = "configInfo";
       DLP_ErrCode ret = OH_DLP_SetSandboxAppConfig(configInfo);
    
       napi_value result = nullptr;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ``` 

7. Obtain the sandbox application configuration.
   ``` c++
   static napi_value GetSandboxAppConfig(napi_env env, napi_callback_info info)
   {
       char *configInfo = nullptr;
       DLP_ErrCode ret = OH_DLP_GetSandboxAppConfig(&configInfo);
       if (ret == DLP_ErrCode::ERR_OH_SUCCESS) {
           napi_value result = nullptr;
           napi_create_string_utf8(env, configInfo, NAPI_AUTO_LENGTH, &result);
           return result;
       }
       napi_value result = nullptr;
       napi_create_int32(env, ret, &result);
       free(configInfo);
       return result;
   }
   ``` 

8. Clean the sandbox application configuration.
   ``` c++
   static napi_value CleanSandboxAppConfig(napi_env env, napi_callback_info info)
   {
       DLP_ErrCode ret = OH_DLP_CleanSandboxAppConfig();
    
       napi_value result = nullptr;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ``` 
