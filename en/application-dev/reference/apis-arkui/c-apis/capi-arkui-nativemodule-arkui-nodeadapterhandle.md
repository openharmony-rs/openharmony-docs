# ArkUI_NodeAdapterHandle

```c
typedef struct ArkUI_NodeAdapterHandle ArkUI_NodeAdapterHandle
```

## Overview

Defines the pointer to a component adapter object, which is used for lazy loading of elements in scrollable components. This is applicable to scenarios where a large amount of scrollable content needs to be loaded on demand. It prevents all elements from being created at once, reducing memory usage and improving scrolling performance.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

