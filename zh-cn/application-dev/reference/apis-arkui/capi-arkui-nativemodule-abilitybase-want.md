# AbilityBase_Want
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct AbilityBase_Want AbilityBase_Want
```

## 概述

声明元能力Want结构。Want用于封装启动Ability所需的信息，包括目标Bundle名称、Ability名称、操作类型及传递参数等，支持跨Ability通信、应用拉起、服务调用等场景。

**起始版本：** 20

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

