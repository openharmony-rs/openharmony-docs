# Rawfile开发指导

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## 场景介绍

开发者可以通过本指导了解在OpenHarmony应用中，如何使用Native Rawfile接口操作Rawfile目录和文件。功能包括文件列表遍历、文件打开、搜索、读取和关闭Rawfile。  
64后缀相关接口属于新增接口，新接口支持打开更大的rawfile文件(超过2G建议使用)，具体请参考：[Rawfile接口介绍](../reference/apis-localization-kit/capi-rawfile.md)。64相关的开发步骤和非64一致，将非64接口替换为64接口即可，例如：OH_ResourceManager_OpenRawFile替换为OH_ResourceManager_OpenRawFile64。

## 接口说明

| 接口名                                                       | 描述                                     |
| :----------------------------------------------------------- | :--------------------------------------- |
| NativeResourceManager *OH_ResourceManager_InitNativeResourceManager(napi_env env, napi_value jsResMgr) | 初始化native resource manager。          |
| RawDir *OH_ResourceManager_OpenRawDir(const NativeResourceManager *mgr, const char *dirName) | 打开指定rawfile目录。                    |
| int OH_ResourceManager_GetRawFileCount(RawDir *rawDir)       | 获取指定rawfile目录下的rawfile文件数量。 |
| const char *OH_ResourceManager_GetRawFileName(RawDir *rawDir, int index) | 获取rawfile名字。                        |
| RawFile *OH_ResourceManager_OpenRawFile(const NativeResourceManager *mgr, const char *fileName) | 打开指定rawfile文件。                    |
| long OH_ResourceManager_GetRawFileSize(RawFile *rawFile)     | 获取rawfile文件大小。                    |
| int OH_ResourceManager_ReadRawFile(const RawFile *rawFile, void *buf, size_t length) | 读取rawfile文件内容。                    |
| void OH_ResourceManager_CloseRawFile(RawFile *rawFile)       | 释放rawfile文件相关资源。                |
| void OH_ResourceManager_CloseRawDir(RawDir *rawDir)          | 释放rawfile目录相关资源。                |
| bool OH_ResourceManager_GetRawFileDescriptor(const RawFile *rawFile, RawFileDescriptor &descriptor) | 获取rawfile的fd。                        |
| void OH_ResourceManager_ReleaseNativeResourceManager(NativeResourceManager *resMgr) | 释放native resource manager相关资源。    |
| bool OH_ResourceManager_IsRawDir(const NativeResourceManager *mgr, const char *path) | 判断路径是否是rawfile下的目录。    |

详细的接口说明请参考[rawfile](../reference/apis-localization-kit/capi-rawfile.md)。

## 开发步骤

   以ArkTS侧获取rawfile文件列表、获取rawfile文件内容、获取rawfile描述符（fd, offset, length）、判断是否是rawfile下的目录四种调用方式为例。

**1. 创建工程**

![创建C++应用](figures/rawfile1.png)

**2. 添加依赖**

创建完成后，DevEco Studio会在工程生成cpp目录，目录下有libentry/index.d.ts、hello.cpp、CMakeLists.txt等文件。

1. 打开src/main/cpp/CMakeLists.txt，在target_link_libraries依赖中添加rawfile依赖librawfile.z.so以及日志依赖libhilog_ndk.z.so。

    ```c++
    target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so librawfile.z.so)
    ```

2. 打开src/main/cpp/types/libentry/index.d.ts文件，在此文件中声明ArkTS侧接口getFileList、getRawFileContent、getRawFileDescriptor、isRawDir。

    <!-- @[declare_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/types/libentry/Index.d.ts) -->

**3. 修改源文件**

1. 打开src/main/cpp/hello.cpp文件，在Init方法中添加ArkTS接口与C++接口的映射。ArkTS侧接口getFileList、getRawFileContent、getRawFileDescriptor、isRawDir，映射C++接口分别为GetFileList、GetRawFileContent、GetRawFileDescriptor、IsRawDir。

    <!-- @[module_registration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/hello.cpp) -->

2. 在src/main/cpp/目录下创建hello.h文件，在hello.h文件中增加对应的四个方法，如下所示：

    <!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/hello.h) -->

3. 在hello.cpp文件中实现上述四个方法。通过env和info获取Js的资源管理对象，并转换为Native的资源管理对象，即可调用Native资源管理对象的接口，示例代码如下：
    
    导入头文件
    <!-- @[includes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/hello.cpp) -->

    声明hilog日志打印的DOMAIN和TAG常量
    <!-- @[constants](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/hello.cpp) -->

    示例：
    <!-- @[example_get_file_list](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/hello.cpp) -->


    <!-- @[example_get_rawfile_content](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/hello.cpp) -->


    <!-- @[example_get_rawfile_descriptor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/hello.cpp) -->


    <!-- @[example_is_raw_dir](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/cpp/hello.cpp) -->

**4. ArkTS侧调用**

1. 打开src\main\ets\pages\index.ets, 导入"libentry.so"。

2. 资源获取包括获取本应用包资源、应用内跨包资源、跨应用包资源。<br>通过context.resourceManager获取本应用包resourceManager对象。<br>通过context.createModuleContext().resourceManager获取应用内跨包resourceManager对象。<!--Del--><br>通过context.createModuleContext(bundleName: 'bundleName name', moduleName: 'module name').resourceManager获取跨应用包resourceManager对象，该方法仅支持系统应用使用。<!--DelEnd--><br>Context的更多使用信息请参考[应用上下文Context](../application-models/application-context-stage.md)。
    
3. 调用src/main/cpp/types/libentry/index.d.ts中声明的接口，如getFileList，传入js的资源管理对象以及rawfile文件夹的相对路径。

   获取本应用包资源resourceManager对象的示例如下：

	<!-- @[native_rawfile_guide_sample](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ResourceManagement/RawFile/entry/src/main/ets/pages/Index.ets) -->

## 相关实例

针对资源管理Rawfile开发，有以下相关实例可供参考：

- [获取Rawfile资源（API9）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Native/NdkRawfile)
