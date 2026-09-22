# ArkUI_ImmersiveMaterial*

```c
typedef struct ArkUI_ImmersiveMaterial* ArkUI_ImmersiveMaterialHandle
```

## 概述

定义指向沉浸式材质对象的指针，沉浸式材质用于实现沉浸式视觉效果对象。<br>可以通过{@link OH_ArkUI_NativeModule_ImmersiveMaterial_Create}创建沉浸式材质对象，<br>创建后必须在使用完毕时调用{@link OH_ArkUI_NativeModule_ImmersiveMaterial_Destroy}销毁沉浸式材质对象以释放资源，避免内存泄漏。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_material.h](capi-native-material-h.md)

