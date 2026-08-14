# native_display_soloist.h

## 概述

定义获取和使用NativeDisplaySoloist的相关函数。

**库：** libnative_display_soloist.so

**系统能力：** SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**起始版本：** 12

**相关模块：** [NativeDisplaySoloist](capi-nativedisplaysoloist.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [DisplaySoloist_ExpectedRateRange](capi-nativedisplaysoloist-displaysoloist-expectedraterange.md) | DisplaySoloist_ExpectedRateRange | 期望帧率范围结构体，用于设置DisplaySoloist（可变帧率独立线程绘制）的期望帧率范围。设置的期望帧率范围将作为系统调度的参考，系统会尽量在此范围内调整绘制帧率。 |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) | OH_DisplaySoloist | OH_DisplaySoloist结构体声明，此结构体用于需要在独立线程中实现帧率控制的Native侧业务。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_DisplaySoloist_FrameCallback)(long long timestamp, long long targetTimestamp, void* data)](#oh_displaysoloist_framecallback) | OH_DisplaySoloist_FrameCallback | OH_DisplaySoloist回调函数类型。在每次VSync信号到来时被系统调用，用于执行每帧的自定义业务。 |
| [OH_DisplaySoloist* OH_DisplaySoloist_Create(bool useExclusiveThread)](#oh_displaysoloist_create) | - | 创建一个OH_DisplaySoloist实例，每次调用都会产生一个新的实例。useExclusiveThread参数决定线程模式：独占线程模式下，该实例拥有独立的线程，性能更高但资源消耗更大；共享线程模式下，多个实例共享线程，资源消耗较小但可能存在调度延迟。 |
| [int32_t OH_DisplaySoloist_Destroy(OH_DisplaySoloist* displaySoloist)](#oh_displaysoloist_destroy) | - | 销毁OH_DisplaySoloist实例并回收对象占用的内存。销毁前应先调用OH_DisplaySoloist_Stop停止回调。销毁后不应再访问该实例或依赖其回调。 |
| [int32_t OH_DisplaySoloist_Start(OH_DisplaySoloist* displaySoloist, OH_DisplaySoloist_FrameCallback callback, void* data)](#oh_displaysoloist_start) | - | 开始请求VSync信号，并且每次VSync信号到来时调用回调函数。如果通过OH_DisplaySoloist_SetExpectedFrameRateRange设置了期望帧率范围，则开始生效该期望帧率范围。 |
| [int32_t OH_DisplaySoloist_Stop(OH_DisplaySoloist* displaySoloist)](#oh_displaysoloist_stop) | - | 用于停止请求VSync信号，并停止调用回调函数callback；同时会使通过OH_DisplaySoloist_SetExpectedFrameRateRange设置的期望帧率范围失效。停止后可再次调用OH_DisplaySoloist_Start重新启动。与OH_DisplaySoloist_Start成对使用，且必须在OH_DisplaySoloist_Start之后调用。 |
| [int32_t OH_DisplaySoloist_SetExpectedFrameRateRange(OH_DisplaySoloist* displaySoloist, DisplaySoloist_ExpectedRateRange* range)](#oh_displaysoloist_setexpectedframeraterange) | - | 设置VSync期望帧率范围，设置的期望帧率范围将作为系统调度的参考，系统会尽量在此范围内调整绘制帧率。未调用该方法或传入DisplaySoloist_ExpectedRateRange(0, 0, 0)时，将跟随应用当前运行的帧率。建议在调用OH_DisplaySoloist_Start前设置，以便立即生效；调用OH_DisplaySoloist_Start之后设置也可以生效但可能存在延迟。 |

## 函数说明

### OH_DisplaySoloist_FrameCallback()

```c
typedef void (*OH_DisplaySoloist_FrameCallback)(long long timestamp, long long targetTimestamp, void* data)
```

**描述**

OH_DisplaySoloist回调函数类型。在每次VSync信号到来时被系统调用，用于执行每帧的自定义业务。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (long long timestamp | 当前帧VSync时间戳（单位：纳秒）。 |
| long long targetTimestamp | 预期的下一帧VSync时间戳（单位：纳秒）。 |
| void\* data | 用户自定义数据的指针。 |

### OH_DisplaySoloist_Create()

```c
OH_DisplaySoloist* OH_DisplaySoloist_Create(bool useExclusiveThread)
```

**描述**

创建一个OH_DisplaySoloist实例，每次调用都会产生一个新的实例。useExclusiveThread参数决定线程模式：独占线程模式下，该实例拥有独立的线程，性能更高但资源消耗更大；共享线程模式下，多个实例共享线程，资源消耗较小但可能存在调度延迟。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| bool useExclusiveThread | 表示此OH_DisplaySoloist实例是否独占线程。true表示独占线程，false表示共享线程（与其他实例共享线程）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_DisplaySoloist*](capi-nativedisplaysoloist-oh-displaysoloist.md) | 返回一个指向OH_DisplaySoloist实例的指针，如果返回空表示执行失败，可能的原因是内存不足。 |

### OH_DisplaySoloist_Destroy()

```c
int32_t OH_DisplaySoloist_Destroy(OH_DisplaySoloist* displaySoloist)
```

**描述**

销毁OH_DisplaySoloist实例并回收对象占用的内存。销毁前应先调用OH_DisplaySoloist_Stop停止回调。销毁后不应再访问该实例或依赖其回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | 一个指向OH_DisplaySoloist实例的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功；-1表示执行失败，可能原因是传入错误的displaySoloist。 |

### OH_DisplaySoloist_Start()

```c
int32_t OH_DisplaySoloist_Start(OH_DisplaySoloist* displaySoloist, OH_DisplaySoloist_FrameCallback callback, void* data)
```

**描述**

开始请求VSync信号，并且每次VSync信号到来时调用回调函数。如果通过OH_DisplaySoloist_SetExpectedFrameRateRange设置了期望帧率范围，则开始生效该期望帧率范围。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | 一个指向OH_DisplaySoloist实例的指针，不能为空。 |
| [OH_DisplaySoloist_FrameCallback](capi-native-display-soloist-h.md#oh_displaysoloist_framecallback) callback | 表示下一次VSync信号到来时执行的回调函数。 |
| void* data | 用户自定义数据的指针，用于传递自定义数据给回调函数。需要在回调函数中访问自定义数据时传入，可以为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功；-1表示执行失败，可能原因是传入错误的displaySoloist或callback。 |

### OH_DisplaySoloist_Stop()

```c
int32_t OH_DisplaySoloist_Stop(OH_DisplaySoloist* displaySoloist)
```

**描述**

用于停止请求VSync信号，并停止调用回调函数callback；同时会使通过OH_DisplaySoloist_SetExpectedFrameRateRange设置的期望帧率范围失效。停止后可再次调用OH_DisplaySoloist_Start重新启动。与OH_DisplaySoloist_Start成对使用，且必须在OH_DisplaySoloist_Start之后调用。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | 一个指向OH_DisplaySoloist实例的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功；-1表示执行失败，可能原因是传入错误的displaySoloist。 |

### OH_DisplaySoloist_SetExpectedFrameRateRange()

```c
int32_t OH_DisplaySoloist_SetExpectedFrameRateRange(OH_DisplaySoloist* displaySoloist, DisplaySoloist_ExpectedRateRange* range)
```

**描述**

设置VSync期望帧率范围，设置的期望帧率范围将作为系统调度的参考，系统会尽量在此范围内调整绘制帧率。未调用该方法或传入DisplaySoloist_ExpectedRateRange(0, 0, 0)时，将跟随应用当前运行的帧率。建议在调用OH_DisplaySoloist_Start前设置，以便立即生效；调用OH_DisplaySoloist_Start之后设置也可以生效但可能存在延迟。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | 一个指向OH_DisplaySoloist实例的指针，不能为空。 |
| [DisplaySoloist_ExpectedRateRange](capi-nativedisplaysoloist-displaysoloist-expectedraterange.md)* range | 一个指向期望帧率范围DisplaySoloist_ExpectedRateRange实例的指针，不能为空。包含expected、min、max三个字段，单位为帧/秒（fps），字段需为非负整数，取值范围为[0, 设备最大帧率]，且满足min <= expected <= max。超出有效范围时参数校验失败。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功；-1表示执行失败，可能的失败原因：1. 必填参数未指定；2. 参数类型错误；3. 参数校验失败或DisplaySoloist_ExpectedRateRange无效。 |


