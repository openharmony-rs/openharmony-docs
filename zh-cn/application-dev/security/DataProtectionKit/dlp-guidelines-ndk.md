# 数据防泄漏服务开发指导(C/C++)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

数据防泄漏（Data Loss Prevention，DLP）是系统提供的系统级的数据防泄漏解决方案，提供跨设备的文件的权限管理、加密存储、授权访问等能力。

- 权限管理：查询当前DLP沙箱的权限信息。
- 文件信息获取：获取DLP文件的基本信息，如原始文件名。
- 沙箱环境检测：查询当前应用是否运行在DLP沙箱环境。
- 配置管理：设置、获取和清理沙箱应用配置信息。
      
## 接口说明
数据防泄漏服务关键接口如下表所示。具体API说明详见[API参考](../../reference/apis-data-protection-kit/capi-dlp-permission-api-h.md)
| 名称 | 描述 |
| -------- | -------- |
| DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess \*dlpFileAccess, uint32_t \*flags)| 查询当前DLP沙箱的权限信息。 |
|DLP_ErrCode OH_DLP_GetOriginalFileName(const char \*fileName, char \*\*originalFileName)  | 获取指定DLP文件名的原始文件名。 |
|DLP_ErrCode OH_DLP_IsInSandbox(bool \*isInSandbox)  |查询当前应用是否运行在DLP沙箱环境。  |
| DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char \*configInfo) | 设置沙箱应用配置信息。 |
| DLP_ErrCode OH_DLP_GetSandboxAppConfig(char \*\*configInfo) |获取沙箱应用配置信息。  |
|DLP_ErrCode OH_DLP_CleanSandboxAppConfig()  |清理沙箱应用配置信息。  |


## 开发步骤

1. 在CMakeLists.txt中导入数据防泄漏的共享库，并链接该库。
    <!-- @[dlp_C_makeLists](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/CMakeLists.txt) -->
    
    ``` Text
    # the minimum version of CMake.
    cmake_minimum_required(VERSION 3.5.0)
    project(DlpApiTest)
    
    set(NATIVERENDER_ROOT_PATH &#36;{CMAKE_CURRENT_SOURCE_DIR})
    
    if(DEFINED PACKAGE_FIND_FILE)
        include(&#36;{PACKAGE_FIND_FILE})
    endif()
    
    include_directories(&#36;{NATIVERENDER_ROOT_PATH}
                        &#36;{NATIVERENDER_ROOT_PATH}/include)
    
    add_library(entry SHARED napi_init.cpp)
    target_link_libraries(entry PUBLIC libace_napi.z.so libohdlp_permission.so)
    ```

4. 获取指定DLP文件名的原始文件名。
    <!-- @[dlp_C_GetOriginalFileName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value GetOriginalFileName(napi_env env, napi_callback_info info)
    <!-- @[dlp_C_IsInSandbox](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value IsInSandbox(napi_env env, napi_callback_info info)
    <!-- @[dlp_C_SetSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value SetSandboxAppConfig(napi_env env, napi_callback_info info)
    {
        const char *configInfo = "configInfo"; //沙箱应用配置信息，用户可将配置信息json化后传入
        DLP_ErrCode ret = OH_DLP_SetSandboxAppConfig(configInfo);
        
        napi_value result = nullptr;
        napi_create_int32(env, ret, &result);
        return result;
    }
    ```
            return result;
        }
        napi_value result = nullptr;
        napi_create_int32(env, ret, &result);
        return result;
    }
    ```
            napi_create_string_utf8(env, originalFileName, NAPI_AUTO_LENGTH, &result);
            return result;
        }
        napi_value result = nullptr;
        napi_create_int32(env, ret, &result);
        free(originalFileName); //处理完后手动释放originalFileName
        return result;
    }
    ```
   
6. 设置沙箱应用配置信息。
    <!-- @[dlp_C_SetSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` 

7. 获取沙箱应用配置信息。
    <!-- @[dlp_C_GetSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` 

8. 清理沙箱应用配置信息。
    <!-- @[dlp_C_CleanSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` 