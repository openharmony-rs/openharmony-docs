# ArkUI_StringAsyncEvent

```c
typedef struct ArkUI_StringAsyncEvent {...} ArkUI_StringAsyncEvent
```

## 概述

定义组件回调事件使用字符串参数的类型，用于在组件异步事件回调中传递字符串数据，适用于组件回调事件需要携带文本信息的场景。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-others-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* pStr | 组件回调事件中传递的字符串数据。 |


