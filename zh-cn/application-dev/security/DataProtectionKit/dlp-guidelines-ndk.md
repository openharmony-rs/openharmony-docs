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
    <!-- @[dlp_C_makeLists](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` c++
   ```

2. 导入数据防泄漏服务的头文件和NAPI相关头文件。
    <!-- @[dlp_C_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` c++
   ```

3. 查询当前DLP沙箱的权限信息。
    <!-- @[dlp_C_GetDlpPermissionInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` c++
   ```

4. 获取指定DLP文件名的原始文件名。
    <!-- @[dlp_C_GetOriginalFileName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` c++
   ``` 

5. 查询当前应用是否运行在DLP沙箱环境。
    <!-- @[dlp_C_IsInSandbox](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` c++
   ``` 

6. 设置沙箱应用配置信息。
    <!-- @[dlp_C_SetSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` c++
   ``` 

7. 获取沙箱应用配置信息。
    <!-- @[dlp_C_GetSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` c++
   ``` 

8. 清理沙箱应用配置信息。
    <!-- @[dlp_C_CleanSandboxAppConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/SystemFeature/Security/DlpCApiTest/entry/src/main/cpp/napi_init.cpp) -->
   ``` c++
   ``` 