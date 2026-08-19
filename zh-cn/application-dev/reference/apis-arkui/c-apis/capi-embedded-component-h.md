# embedded_component.h

## 概述

EmbeddedComponent组件相关的结构体和方法定义。

**引用文件：** <arkui/embedded_component.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** [embedded_component_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/UIExtensionAndAccessibility)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md) | AbilityBase_Want | 声明元能力want结构。 |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md) | ArkUI_EmbeddedComponentOption | 为EmbeddedComponent定义参数EmbeddedComponentOption。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()](#oh_arkui_embeddedcomponentoption_create) | 创建EmbeddedComponent组件选项的对象。 |
| [void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)](#oh_arkui_embeddedcomponentoption_dispose) | 删除EmbeddedComponent组件选项的对象。 |
| [void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, const char* name, const char* message))](#oh_arkui_embeddedcomponentoption_setonerror) | 设置EmbeddedComponent组件的onError回调。EmbeddedComponent组件在运行过程中发生异常时触发本回调。 |
| [void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (\*callback)(int32_t code, AbilityBase_Want* want))](#oh_arkui_embeddedcomponentoption_setonterminated) | 设置EmbeddedComponent组件的onTerminated回调。EmbeddedComponent组件正常退出时触发本回调。 |

## 函数说明

### OH_ArkUI_EmbeddedComponentOption_Create()

```c
ArkUI_EmbeddedComponentOption* OH_ArkUI_EmbeddedComponentOption_Create()
```

**描述**

创建EmbeddedComponent组件选项的对象。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_EmbeddedComponentOption*](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md) | 返回指向EmbeddedComponent组件选项的对象的指针。 |

### OH_ArkUI_EmbeddedComponentOption_Dispose()

```c
void OH_ArkUI_EmbeddedComponentOption_Dispose(ArkUI_EmbeddedComponentOption* option)
```

**描述**

删除EmbeddedComponent组件选项的对象。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)* option | 要销毁的EmbeddedComponent组件选项的对象的指针。 |

### OH_ArkUI_EmbeddedComponentOption_SetOnError()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnError(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, const char* name, const char* message))
```

**描述**

设置EmbeddedComponent组件的onError回调。EmbeddedComponent组件在运行过程中发生异常时触发本回调。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_EmbeddedComponentOption\* option | EmbeddedComponent组件选项的对象的指针。 |
| void (\*callback)(int32_t code | 开发者自定义回调函数。        - code：接口调用失败返回的错误码信息。错误码的详细介绍请参考[UIExtension错误码](errorcode-uiextension.md)。        - name：接口调用失败返回的名称信息。        - message：接口调用失败返回的详细信息。 |

### OH_ArkUI_EmbeddedComponentOption_SetOnTerminated()

```c
void OH_ArkUI_EmbeddedComponentOption_SetOnTerminated(ArkUI_EmbeddedComponentOption* option, void (*callback)(int32_t code, AbilityBase_Want* want))
```

**描述**

设置EmbeddedComponent组件的onTerminated回调。EmbeddedComponent组件正常退出时触发本回调。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| rkUI_EmbeddedComponentOption\* option | EmbeddedComponent组件选项的对象的指针。 |
| void (\*callback)(int32_t code | 开发者自定义回调函数。         - code：被拉起EmbeddedUIExtensionAbility退出时返回的结果码。         若EmbeddedUIExtensionAbility通过调用terminateSelfWithResult退出，结果码为EmbeddedUIExtensionAbility设置的值。         若EmbeddedUIExtensionAbility通过调用terminateSelf退出，结果码为默认值"0"。         - want：被拉起EmbeddedUIExtensionAbility退出时返回的数据。 |


