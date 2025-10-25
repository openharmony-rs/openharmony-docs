# 标准化数据类型 (C/C++)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->


## 场景介绍

统一数据管理框架（UDMF）提供数据跨应用、跨设备交互标准，定义数据交互过程中的数据语言，提升数据交互效率。它提供安全、标准化的数据流通路径，支持不同级别的数据访问权限和生命周期管理策略，实现高效的数据共享。


## 基本概念

- **标准化数据类型**：Uniform Type Descriptor，简称UTD。主要针对同一种数据类型，提供统一定义，即标准数据类型描述符，定义了包括标识数据类型的ID、类型归属关系等相关信息，用于解决OpenHarmony系统中的类型模糊问题。一般用于过滤或者识别某一种数据类型的场景，比如文件预览、文件分享等。


## 接口说明

详细的接口说明请参考[UTD接口文档](../reference/apis-arkdata/capi-utd-h.md)。

| 接口名称                                                     | 描述                                                        |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| OH_Utd* OH_Utd_Create(const char* typeId)                    | 创建一个指向统一数据类型描述符OH_Utd的指针。                |
| void OH_Utd_Destroy(OH_Utd* pThis)                           | 销毁指向统一数据类型描述符OH_Utd的指针。                    |
| const char** OH_Utd_GetTypesByFilenameExtension(const char* extension, unsigned int* count) | 通过文件后缀名获取标准化数据类型ID。                        |
| const char** OH_Utd_GetTypesByMimeType(const char* mimeType, unsigned int* count) | 通过MIME类型获取标准化数据类型ID。                          |
| bool OH_Utd_Equals(OH_Utd* utd1, OH_Utd* utd2)               | 判断两种标准化数据类型是否相等。                            |
| void OH_Utd_DestroyStringList(const char** list, unsigned int count) | 销毁字符串列表数据。                                        |
| bool OH_Utd_BelongsTo (const char *srcTypeId, const char *destTypeId) | 判断两个标准化数据描述类型是否存在归属关系。                  |
| bool OH_Utd_IsLower (const char* srcTypeId, const char* destTypeId ) | 判断原标准化数据类型是否是目标标准化数据类型的低层级类型。 例如TYPE_SCRIPT为SOURCE_CODE的低层级类型，TYPE_SCRIPT和SOURCE_CODE为PLAIN_TEXT的低层级类型。       |
| bool OH_Utd_IsHigher (const char* srcTypeId, const char* destTypeId ) | 判断原标准化数据类型是否是目标标准化数据类型的高层级类型。 例如SOURCE_CODE为TYPE_SCRIPT的高层级类型，PLAIN_TEXT为SOURCE_CODE和TYPE_SCRIPT的高层级类型。       |


## 添加动态链接库

CMakeLists.txt中添加以下库。

```txt
libudmf.so, libhilog_ndk.z.so
```

## 引用头文件

<!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/UniformDataTypeDescriptors_C/entry/src/main/cpp/napi_init.cpp) -->

## 通过不同方式获取不同类型数据并且比较它们之间的关系

下面以获取纯文本数据的查询场景为例，说明如何使用UTD。
1. 通过后缀名“.txt”获取UTD的typeId。
2. 通过MIME类型“text/plain”获取UTD的typeId。
3. 使用以上两个步骤获取到的typeId创建UTD实例对象。
4. 比较UTD实例对象是否相等。
5. 比较两种方式获取到的typeId是否存在归属关系。
6. 比较两种方式获取到的typeIds1[0]是否是typeIds2[0]的低层级类型。
7. 比较两种方式获取到的typeIds1[0]是否是typeIds2[0]的高层级类型。
8. 使用结束后，删除上述步骤中产生的指针。

<!-- @[uniform_data_type_descriptors_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/UniformDataTypeDescriptors_C/entry/src/main/cpp/napi_init.cpp) -->