# ArkUI_GridItemRect

```c
typedef struct ArkUI_GridItemRect {...} ArkUI_GridItemRect
```

## 概述

Defines the return value structure for the <b>onGetRectByIndex</b> callback in <b>Grid</b> layout options.

**起始版本：** 22

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t rowStart | Starting row position of the <b>GridItem</b> component. |
| uint32_t columnStart | Starting column position of the <b>GridItem</b> component. |
| uint32_t rowSpan | Number of rows occupied by the <b>GridItem</b> component. |
| uint32_t columnSpan | Number of columns occupied by the <b>GridItem</b> component. |


