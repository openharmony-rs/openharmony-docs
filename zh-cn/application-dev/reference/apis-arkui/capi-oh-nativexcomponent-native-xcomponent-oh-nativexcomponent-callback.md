# OH_NativeXComponent_Callback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_NativeXComponent_Callback {...} OH_NativeXComponent_Callback
```

## 概述

注册Surface生命周期和触摸事件回调。

**起始版本：** 8

**相关模块：** [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**所在头文件：** [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [void (\*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)](#onsurfacecreated) | 创建Surface时调用。 |
| [void (\*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)](#onsurfacechanged) | 当Surface改变时调用。 |
| [void (\*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)](#onsurfacedestroyed) | 当Surface被销毁时调用。 |
| [void (\*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)](#dispatchtouchevent) | 当触摸事件被触发时调用。 |

## 成员函数说明

### OnSurfaceCreated()

```c
void (*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)
```

**描述：**


创建Surface时调用。

**起始版本：** 8

**参数：**

| 参数项                                | 描述 |
|------------------------------------| -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | 表示指向[OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)实例的指针。 |
| void* window                       | 表示NativeWindow句柄。<br/>通过XComponent生命周期获取的NativeWindow本身由系统侧持有了一次引用计数，并会在OnSurfaceDestroyed回调触发之后将引用计数减一，引用计数归零后NativeWindow将被释放。 |

### OnSurfaceChanged()

```c
void (*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)
```

**描述：**


当Surface改变时调用。

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | 表示指向[OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)实例的指针。 |
|  void* window | 表示NativeWindow句柄。 |

### OnSurfaceDestroyed()

```c
void (*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)
```

**描述：**


当Surface被销毁时调用。

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | 表示指向[OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)实例的指针。 |
|  void* window | 表示NativeWindow句柄。 |

### DispatchTouchEvent()

```c
void (*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)
```

**描述：**


当触摸事件被触发时调用。

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | 表示指向[OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)实例的指针。 |
|  void* window | 表示NativeWindow句柄。 |


