# 数据防泄漏服务(C/C++)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @lucky-jinduo-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 数据防泄漏服务简介
数据防泄漏（DLP）是系统提供的系统级的数据防泄漏解决方案。通过调用Data Protection Kit的接口，提供跨设备的文件的权限管理、加盟存储、授权访问等能力。

- 权限管理：查询当前DLP沙箱的权限信息，包括DLP文件授权类型和详细操作权限
- 文件信息获取：获取DLP文件的基本信息，如原始文件名
- 沙箱环境检测：查询当前应用是否运行在DLP沙箱环境
- 配置管理：设置、获取和清理沙箱应用配置信息

在使用数据防泄漏服务前，开发者应了解以下基本概念：
- DLP文件:  经过数据防泄漏保护的文件，具有访问权限控制和安全特性。
- DLP沙箱:  为应用提供的隔离运行环境，用于安全地处理DLP文件，防止数据泄露。
- DLP文件授权类型:  定义应用对DLP文件的访问权限级别，如只读、读写等。

数据防泄漏服务通过系统级权限控制和沙箱隔离机制，确保DLP文件在跨设备传输和使用过程中的安全性。应用通过Data Protection Kit提供的C/C++接口与系统DLP服务交互，系统自动处理权限验证和访问控制。
### 规格限制
- 配置信息大小不超过1KB
- 文件名长度不超过256字符
## 数据防泄漏服务开发指导
### 接口说明
数据防泄漏服务关键接口如下表所示。具体API说明详见API参考。
| 名称 | 描述 |
| -------- | -------- |
| DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess *dlpFileAccess, uint32_t *flags)| 查询当前DLP沙箱的权限信息。 |
|DLP_ErrCode OH_DLP_GetOriginalFileName(const char *fileName, char **originalFileName)  | 获取指定DLP文件名的原始文件名。 |
|DLP_ErrCode OH_DLP_IsInSandbox(bool *isInSandbox)  |查询当前应用是否运行在DLP沙箱环境。  |
| DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char *configInfo) | 设置沙箱应用配置信息。 |
| DLP_ErrCode OH_DLP_GetSandboxAppConfig(char **configInfo) |获取沙箱应用配置信息。  |
|DLP_ErrCode OH_DLP_CleanSandboxAppConfig()  |清理沙箱应用配置信息。  |


###  开发步骤

1. 在CMakeLists.txt中导入数据防泄漏的共享库，并链接该库。
``` TypeScript
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

2. 导入数据防泄漏服务的头文件和NAPI相关头文件
``` TypeScript
#include "napi/native_api.h"
#include <cstdint>
#include <cstdlib>
#include "DataProtectionKit/dlp_permission_api.h"
```

3. 查询当前DLP沙箱的权限信息。
``` TypeScript
static napi_value GetDlpPermissionInfo(napi_env env, napi_callback_info info)
{
    DLP_FileAccess dlpFileAccess = NO_PERMISSION; //表示DLP文件授权类型
    uint32_t flags = 0; //表示DLP文件的详细操作权限
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

4. 获取指定DLP文件名的原始文件名。
``` TypeScript
static napi_value GetOriginalFileName(napi_env env, napi_callback_info info)
{
    const char *fileName = "test.txt.dlp"; //表示dlp文件名，用以获取原始文件名
    char *originalFileName = nullptr; //表示原始文件名
    DLP_ErrCode ret = OH_DLP_GetOriginalFileName(fileName, &originalFileName);
    if (ret == DLP_ErrCode::ERR_OH_SUCCESS) {
        napi_value result = nullptr;
        napi_create_string_utf8(env, originalFileName, NAPI_AUTO_LENGTH, &result);
        return result;
    }
    napi_value result = nullptr;
    napi_create_int32(env, ret, &result);
    free(originalFileName); //处理完后手动释放originalFileName
    return result;
}
``` 

5. 查询当前应用是否运行在DLP沙箱环境。
``` TypeScript
static napi_value IsInSandbox(napi_env env, napi_callback_info info)
{
    bool isInSandbox = false; //true 表示当前应用在沙箱中，false 表示应用不在沙箱
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

6. 设置沙箱应用配置信息。
``` TypeScript
static napi_value SetSandboxAppConfig(napi_env env, napi_callback_info info)
{
    const char *configInfo = "configInfo"; //沙箱应用配置信息，用户可将配置信息json化后传入
    DLP_ErrCode ret = OH_DLP_SetSandboxAppConfig(configInfo);
    
    napi_value result = nullptr;
    napi_create_int32(env, ret, &result);
    return result;
}
``` 

7. 获取沙箱应用配置信息。
``` TypeScript
static napi_value GetSandboxAppConfig(napi_env env, napi_callback_info info)
{
    char *configInfo = nullptr; //输出json化后的沙箱应用配置信息
    DLP_ErrCode ret = OH_DLP_GetSandboxAppConfig(&configInfo);
    if (ret == DLP_ErrCode::ERR_OH_SUCCESS) {
        napi_value result = nullptr;
        napi_create_string_utf8(env, configInfo, NAPI_AUTO_LENGTH, &result);
        return result;
    }
    napi_value result = nullptr;
    napi_create_int32(env, ret, &result);
    free(configInfo); //处理完后手动释放configInfo
    return result;
}
``` 

8. 清理沙箱应用配置信息。
``` TypeScript
static napi_value CleanSandboxAppConfig(napi_env env, napi_callback_info info)
{
    DLP_ErrCode ret = OH_DLP_CleanSandboxAppConfig();
    
    napi_value result = nullptr;
    napi_create_int32(env, ret, &result);
    return result;
}
``` 

9. C接口到Arkts接口的映射
``` TypeScript
EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        {"GetDlpPermissionInfo", nullptr, GetDlpPermissionInfo, nullptr,
         nullptr, nullptr, napi_default, nullptr},
        {"GetOriginalFileName", nullptr, GetOriginalFileName, nullptr,
         nullptr, nullptr, napi_default, nullptr},
        {"IsInSandbox", nullptr, IsInSandbox, nullptr,
         nullptr, nullptr, napi_default, nullptr},
        {"SetSandboxAppConfig", nullptr, SetSandboxAppConfig, nullptr,
         nullptr, nullptr, napi_default, nullptr},
        {"GetSandboxAppConfig", nullptr, GetSandboxAppConfig, nullptr,
         nullptr, nullptr, napi_default, nullptr},
        {"CleanSandboxAppConfig", nullptr, CleanSandboxAppConfig, nullptr,
         nullptr, nullptr, napi_default, nullptr}
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END

static napi_module demoModule = {
    .nm_version = 1,
    .nm_flags = 0,
    .nm_filename = nullptr,
    .nm_register_func = Init,
    .nm_modname = "entry",
    .nm_priv = ((void*)0),
    .reserved = { 0 },
};

extern "C" __attribute__((constructor)) void RegisterEntryModule(void)
{
    napi_module_register(&demoModule);
}
``` 
9. Arkts接口导出
``` TypeScript
export const GetDlpPermissionInfo: () => number;
export const GetOriginalFileName: () => number;
export const IsInSandbox: () => boolean;
export const SetSandboxAppConfig: () => number;
export const GetSandboxAppConfig: () => number;
export const CleanSandboxAppConfig: () => number;
```