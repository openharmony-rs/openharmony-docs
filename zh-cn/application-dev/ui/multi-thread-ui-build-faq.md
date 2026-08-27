# UI并行化常见问题
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 如何获取和使用支持多线程调用的NDK接口

从API version 22开始，ArkUI_NativeAPIVariantKind中新增ARKUI_MULTI_THREAD_NATIVE_NODE枚举。

调用OH_ArkUI_GetModuleInterface接口，入参传入ARKUI_MULTI_THREAD_NATIVE_NODE，可以获取多线程NDK接口集合，完整示例请参考多线程NDK接口使用方式。

## 调用多线程NDK接口返回ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD错误码

**问题现象**

调用多线程NDK接口返回ARKUI_ERROR_CODE_NODE_ON_INVALID_THREAD错误码。

**解决措施**

首先参考多线程NDK接口集合规格，查看调用的接口是否支持多线程调用，之后按照如下步骤排查。

1. 如果接口只支持在UI线程调用，需要调整函数调用时机，在UI线程调用接口。
2. 如果接口支持多线程调用，报错原因是接口操作的节点处于Attached状态。
   - 确认节点是由多线程createNode接口创建的。
   - 参考多线程NDK接口调用规范，将组件所在组件树中所有不可转换的Attached组件移除。

## 如何保证多线程操作ArkUI组件时线程安全

在使用多线程NDK接口时，多个线程同时操作同一个组件或组件树，无法保证线程安全，需要开发者通过合理的架构设计避免出现上述情况。

可以参考多线程NDK接口调用规范，按照文档中的约束使用多线程NDK接口来保证线程安全。