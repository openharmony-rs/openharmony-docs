# ArkUI_AccessibilityProviderCallbacksWithInstance

## 概述

适配多实例场景第三方操作provider回调函数结构定义，需要第三方平台实现的相关函数，通过OH_ArkUI_AccessibilityProviderRegisterCallbackWithInstance注册到系统侧。

**起始版本：** 15

**相关模块：** [ArkUI_Accessibility](capi-arkui-accessibility.md)

**所在头文件：** [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*findAccessibilityNodeInfosById)(const char* instanceId, int64_t elementId,ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbyid) | 由接入方平台实现的回调函数，注册给系统侧调用。基于指定的节点，查询所需的节点信息。支持多实例场景。 |
| [int32_t (\*findAccessibilityNodeInfosByText)(const char* instanceId, int64_t elementId, const char* text,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)](#findaccessibilitynodeinfosbytext) | 由接入方平台实现的回调函数，注册给系统侧调用。基于指定的节点，查询满足指定组件文本内容的节点信息。支持多实例场景。 |
| [int32_t (\*findFocusedAccessibilityNode)(const char* instanceId, int64_t elementId,ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findfocusedaccessibilitynode) | 由接入方平台实现的回调函数，注册给系统侧调用。从指定节点查找已经聚焦的节点。支持多实例场景。 |
| [int32_t (\*findNextFocusAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)](#findnextfocusaccessibilitynode) | 由接入方平台实现的回调函数，注册给系统侧调用。从指定节点查询指定方向的节点。支持多实例场景。 |
| [int32_t (\*executeAccessibilityAction)(const char* instanceId, int64_t elementId,ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)](#executeaccessibilityaction) | 由接入方平台实现的回调函数，注册给系统侧调用。对指定节点执行指定的操作。支持多实例场景。 |
| [int32_t (\*clearFocusedFocusAccessibilityNode)(const char* instanceId)](#clearfocusedfocusaccessibilitynode) | 由接入方平台实现的回调函数，注册给系统侧调用。 清除当前获焦的节点。支持多实例场景。 |
| [int32_t (\*getAccessibilityNodeCursorPosition)(const char* instanceId, int64_t elementId,int32_t requestId, int32_t* index)](#getaccessibilitynodecursorposition) | 由接入方平台实现的回调函数，注册给系统侧调用。获取当前组件中（文本组件）光标位置。支持多实例场景。 |

## 成员函数说明

### findAccessibilityNodeInfosById()

```
int32_t (*findAccessibilityNodeInfosById)(const char* instanceId, int64_t elementId,ArkUI_AccessibilitySearchMode mode, int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**描述：**

由接入方平台实现的回调函数，注册给系统侧调用。基于指定的节点，查询所需的节点信息。支持多实例场景。

**起始版本：** 15

**参数：**

| 参数项                                                                            | 描述 |
|--------------------------------------------------------------------------------| -- |
| const char* instanceId                                                         | 第三方框架的实例编码。 |
| int64_t elementId                                                              | 无障碍元素的唯一编号。 |
| [ArkUI_AccessibilitySearchMode](capi-native-interface-accessibility-h.md) mode | 无障碍服务的搜索模式。 |
| int32_t requestId                                                              | 请求id，用于关联请求过程，方便问题定位。建议日志打印时附带输出该信息，方便定位。 |
| [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList                            | 本次查询到的所有无障碍元素列表。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 成功返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。<br>            参数错误返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。 |

### findAccessibilityNodeInfosByText()

```
int32_t (*findAccessibilityNodeInfosByText)(const char* instanceId, int64_t elementId, const char* text,int32_t requestId, ArkUI_AccessibilityElementInfoList* elementList)
```

**描述：**

由接入方平台实现的回调函数，注册给系统侧调用。基于指定的节点，查询满足指定组件文本内容的节点信息。支持多实例场景。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* instanceId | 第三方框架的实例编码。 |
|  int64_t elementId | 无障碍元素的唯一编号。 |
|  const char* text | 组件需要匹配的文本内容。 |
| int32_t requestId | 请求id，用于关联请求过程，方便问题定位。建议日志打印时附带输出该信息，方便定位。 |
|  [ArkUI_AccessibilityElementInfoList](capi-arkui-accessibility-arkui-accessibilityelementinfolist.md)* elementList | 本次查询到的所有无障碍元素列表。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 成功返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。<br>            参数错误返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。 |

### findFocusedAccessibilityNode()

```
int32_t (*findFocusedAccessibilityNode)(const char* instanceId, int64_t elementId,ArkUI_AccessibilityFocusType focusType, int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**描述：**

由接入方平台实现的回调函数，注册给系统侧调用。从指定节点查找已经聚焦的节点。支持多实例场景。

**起始版本：** 15

**参数：**

| 参数项                                                                                | 描述 |
|------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                             | 第三方框架的实例编码。 |
| int64_t elementId                                                                  | 无障碍元素的唯一编号。 |
| [ArkUI_AccessibilityFocusType](capi-native-interface-accessibility-h.md) focusType | 焦点类型。 |
| int32_t requestId                                                                  | 请求id，用于关联请求过程，方便问题定位。建议日志打印时附带输出该信息，方便定位。 |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo                                    | 本次查询到的无障碍元素。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 成功返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。<br>            参数错误返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。 |

### findNextFocusAccessibilityNode()

```
int32_t (*findNextFocusAccessibilityNode)(const char* instanceId, int64_t elementId, ArkUI_AccessibilityFocusMoveDirection direction,int32_t requestId, ArkUI_AccessibilityElementInfo* elementInfo)
```

**描述：**

由接入方平台实现的回调函数，注册给系统侧调用。从指定节点查询指定方向的节点。支持多实例场景。

**起始版本：** 15

**参数：**

| 参数项                                                                                                                               | 描述 |
|-----------------------------------------------------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                                                                            | 第三方框架的实例编码。 |
| int64_t elementId                                                                                                                 | 无障碍元素的唯一编号。 |
| [ArkUI_AccessibilityFocusMoveDirection](capi-native-interface-accessibility-h.md#arkui_accessibilityfocusmovedirection) direction | 搜索方向。 |
| int32_t requestId                                                                                                                 | 请求id，用于关联请求过程，方便问题定位。建议日志打印时附带输出该信息，方便定位。 |
| [ArkUI_AccessibilityElementInfo](capi-arkui-accessibility-arkui-accessibilityelementinfo.md)* elementInfo                         | 本次查询到的无障碍元素。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 成功返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。<br>参数错误返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。 |

### executeAccessibilityAction()

```
int32_t (*executeAccessibilityAction)(const char* instanceId, int64_t elementId,ArkUI_Accessibility_ActionType action, ArkUI_AccessibilityActionArguments *actionArguments, int32_t requestId)
```

**描述：**

由接入方平台实现的回调函数，注册给系统侧调用。对指定节点执行指定的操作。支持多实例场景。

**起始版本：** 15

**参数：**

| 参数项                                                                                                              | 描述 |
|------------------------------------------------------------------------------------------------------------------| -- |
| const char* instanceId                                                                                           | 第三方框架的实例编码。 |
| int64_t elementId                                                                                                | 无障碍元素的唯一编号。 |
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) action | 需要执行的操作，比如聚焦、点击和长按等。 |
| [ArkUI_AccessibilityActionArguments](capi-arkui-accessibility-arkui-accessibilityactionarguments.md) *actionArguments                                                          | 控制操作的参数。 |
| int32_t requestId                                                                                                | 请求id，用于关联请求过程，方便问题定位。建议日志打印时附带输出该信息，方便定位。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 成功返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。<br>参数错误返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。 |

### clearFocusedFocusAccessibilityNode()

```
int32_t (*clearFocusedFocusAccessibilityNode)(const char* instanceId)
```

**描述：**

由接入方平台实现的回调函数，注册给系统侧调用。 清除当前获焦的节点。支持多实例场景。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* instanceId | 第三方框架的实例编码。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 成功返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。<br>参数错误返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。 |

### getAccessibilityNodeCursorPosition()

```
int32_t (*getAccessibilityNodeCursorPosition)(const char* instanceId, int64_t elementId,int32_t requestId, int32_t* index)
```

**描述：**

由接入方平台实现的回调函数，注册给系统侧调用。获取当前组件中（文本组件）光标位置。支持多实例场景。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* instanceId | 第三方框架的实例编码。 |
|  int64_t elementId | 无障碍元素的唯一编号。 |
| int32_t requestId | 请求id，用于关联请求过程，方便问题定位。建议日志打印时附带输出该信息，方便定位。 |
|  int32_t* index | 光标的位置结果。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 成功返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_SUCCESSFUL](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。<br>参数错误返回[ARKUI_ACCESSIBILITY_NATIVE_RESULT_BAD_PARAMETER](capi-native-interface-accessibility-h.md#arkui_acessbilityerrorcode)。 |


