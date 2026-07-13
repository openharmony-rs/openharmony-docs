# native_vsync.h

## 概述

定义获取和使用NativeVsync的相关函数。

**库：** libnative_vsync.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 9

**相关模块：** [NativeVsync](capi-nativevsync.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_NativeVSync_ExpectedRateRange](capi-nativevsync-oh-nativevsync-expectedraterange.md) | OH_NativeVSync_ExpectedRateRange | 期望帧率范围结构体。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_NativeVSync* OH_NativeVSync_Create(const char* name, unsigned int length)](#oh_nativevsync_create) | 创建一个OH_NativeVSync实例，每次调用都会产生一个新的实例。<br> 本接口需要与OH_NativeVSync_Destroy接口配合使用，否则会存在内存泄露。 |
| [void OH_NativeVSync_Destroy(OH_NativeVSync* nativeVsync)](#oh_nativevsync_destroy) | 销毁OH_NativeVSync实例。<br> 销毁后的OH_NativeVSync指针不能再继续使用，否则会有野指针问题，尤其需要注意多线程并发时对于OH_NativeVSync指针的管理。 |
| [OH_NativeVSync* OH_NativeVSync_Create_ForAssociatedWindow(uint64_t windowID, const char* name, unsigned int length)](#oh_nativevsync_create_forassociatedwindow) | 创建一个和窗口绑定的OH_NativeVSync实例，每次调用都会产生一个新的实例。<br> 使用本接口创建出来的OH_NativeVSync实例的实际vsync周期与系统vsync周期不完全一致，系统会根据窗口的状态对实际vsync周期进行调整。 |
| [int OH_NativeVSync_RequestFrame(OH_NativeVSync* nativeVsync, OH_NativeVSync_FrameCallback callback, void* data)](#oh_nativevsync_requestframe) | 请求下一次vsync信号，当信号到来时，调用回调函数callback。<br> 如果在同一帧内中多次调用此接口，则只会触发最后一个回调。 |
| [int OH_NativeVSync_RequestFrameWithMultiCallback(OH_NativeVSync* nativeVsync, OH_NativeVSync_FrameCallback callback, void* data)](#oh_nativevsync_requestframewithmulticallback) | 请求下一次vsync信号，当信号到来时，调用回调函数callback。<br> 如果在同一帧内中多次调用此接口，每一次传入的callback都会被执行。 |
| [int OH_NativeVSync_GetPeriod(OH_NativeVSync* nativeVsync, long long* period)](#oh_nativevsync_getperiod) | 获取vsync周期。<br> vsync周期是在每次使用OH_NativeVSync_RequestFrame接口请求vsync信号后收到OH_NativeVSync_FrameCallback回调的时候才会更新。<br> 首次使用该接口获取vsync周期之前，需要先使用OH_NativeVSync_RequestFrame接口请求vsync信号，<br> 在收到OH_NativeVSync_FrameCallback回调之后，才可以通过该接口获取到vsync周期。 |
| [int OH_NativeVSync_DVSyncSwitch(OH_NativeVSync* nativeVsync, bool enable)](#oh_nativevsync_dvsyncswitch) | 启用DVSync以提高自绘制动画场景的流畅性。<br> DVSync是Decoupled VSync的缩写，它是一种与硬件VSync解耦的帧时序管理策略。<br> DVSync通过提前发送带有未来时间戳的VSync信号驱动后续动画帧的提前绘制，这些帧会被帧缓冲队列缓存；DVSync通过缓存的帧减少未来可能发生的丢帧，进而提高动画场景的流畅性。<br> 因为DVSync需要占用空闲的自绘制帧缓冲用于缓存提前绘制的动画帧，用户需要确保至少有一个空闲的帧缓冲区，否则不建议启用此功能。<br> 启用DVSync后，用户需要正确响应提前发送的VSync信号，并在前一个VSync对应的动画帧完成后再请求下一个VSync，且自绘制帧需要携带与VSync一致的时间戳。<br> 在动画结束之后，用户需要关闭DVSync。<br> 在不支持DVSync的平台或者如果有另一个应用程序已经启用了DVSync，则当前的启用操作将不会生效，应用程序仍将收到正常的VSync信号。 |
| [int OH_NativeVSync_SetExpectedFrameRateRange(OH_NativeVSync* nativeVsync, OH_NativeVSync_ExpectedRateRange* range)](#oh_nativevsync_setexpectedframeraterange) | 设置VSync期望帧率及其范围。实际帧率可能因系统功耗、性能和硬件规格等限制而与设置的期望值不一致。 |

## 函数说明

### OH_NativeVSync_Create()

```c
OH_NativeVSync* OH_NativeVSync_Create(const char* name, unsigned int length)
```

**描述**

创建一个OH_NativeVSync实例，每次调用都会产生一个新的实例。<br> 本接口需要与OH_NativeVSync_Destroy接口配合使用，否则会存在内存泄露。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 9

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* name | 表示一个名字，与创建的OH_NativeVSync实例关联。 |
| unsigned int length | name的长度（字符数）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_NativeVSync* | 返回一个指向OH_NativeVSync实例的指针。 |

### OH_NativeVSync_Destroy()

```c
void OH_NativeVSync_Destroy(OH_NativeVSync* nativeVsync)
```

**描述**

销毁OH_NativeVSync实例。<br> 销毁后的OH_NativeVSync指针不能再继续使用，否则会有野指针问题，尤其需要注意多线程并发时对于OH_NativeVSync指针的管理。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 9

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_NativeVSync* nativeVsync | 一个指向OH_NativeVSync实例的指针。 |

### OH_NativeVSync_Create_ForAssociatedWindow()

```c
OH_NativeVSync* OH_NativeVSync_Create_ForAssociatedWindow(uint64_t windowID, const char* name, unsigned int length)
```

**描述**

创建一个和窗口绑定的OH_NativeVSync实例，每次调用都会产生一个新的实例。<br> 使用本接口创建出来的OH_NativeVSync实例的实际vsync周期与系统vsync周期不完全一致，系统会根据窗口的状态对实际vsync周期进行调整。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t windowID | 表示窗口ID，窗口子进程索引标识符。 |
| const char* name | 表示一个名称，与创建的OH_NativeVSync实例关联。 |
| unsigned int length | name的长度（字符数）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_NativeVSync* | 返回一个指向OH_NativeVSync实例的指针。 |

### OH_NativeVSync_RequestFrame()

```c
int OH_NativeVSync_RequestFrame(OH_NativeVSync* nativeVsync, OH_NativeVSync_FrameCallback callback, void* data)
```

**描述**

请求下一次vsync信号，当信号到来时，调用回调函数callback。<br> 如果在同一帧内中多次调用此接口，则只会触发最后一个回调。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 9

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_NativeVSync* nativeVsync | 一个指向OH_NativeVSync实例的指针。 |
| OH_NativeVSync_FrameCallback callback | 一个OH_NativeVSync_FrameCallback类型的函数指针，当下一次vsync信号到来时会被调用。 |
| void* data | 一个指向用户自定义数据结构的指针，类型是void。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - 参数nativeVsync或callback为空。<br>     NATIVE_ERROR_BINDER_ERROR 50401000 - ipc发送失败。 |

### OH_NativeVSync_RequestFrameWithMultiCallback()

```c
int OH_NativeVSync_RequestFrameWithMultiCallback(OH_NativeVSync* nativeVsync, OH_NativeVSync_FrameCallback callback, void* data)
```

**描述**

请求下一次vsync信号，当信号到来时，调用回调函数callback。<br> 如果在同一帧内中多次调用此接口，每一次传入的callback都会被执行。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_NativeVSync* nativeVsync | 一个指向OH_NativeVSync实例的指针。 |
| OH_NativeVSync_FrameCallback callback | 一个OH_NativeVSync_FrameCallback类型的函数指针，当下一次vsync信号到来时会被调用。 |
| void* data | 一个指向用户自定义数据结构的指针，类型是void。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - 参数nativeVsync或callback为空。<br>     NATIVE_ERROR_BINDER_ERROR 50401000 - ipc发送失败。 |

### OH_NativeVSync_GetPeriod()

```c
int OH_NativeVSync_GetPeriod(OH_NativeVSync* nativeVsync, long long* period)
```

**描述**

获取vsync周期。<br> vsync周期是在每次使用OH_NativeVSync_RequestFrame接口请求vsync信号后收到OH_NativeVSync_FrameCallback回调的时候才会更新。<br> 首次使用该接口获取vsync周期之前，需要先使用OH_NativeVSync_RequestFrame接口请求vsync信号，<br> 在收到OH_NativeVSync_FrameCallback回调之后，才可以通过该接口获取到vsync周期。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_NativeVSync* nativeVsync | 一个指向OH_NativeVSync实例的指针。 |
| long long* period | 表示vsync周期，作为出参使用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeVSync_DVSyncSwitch()

```c
int OH_NativeVSync_DVSyncSwitch(OH_NativeVSync* nativeVsync, bool enable)
```

**描述**

启用DVSync以提高自绘制动画场景的流畅性。<br> DVSync是Decoupled VSync的缩写，它是一种与硬件VSync解耦的帧时序管理策略。<br> DVSync通过提前发送带有未来时间戳的VSync信号驱动后续动画帧的提前绘制，这些帧会被帧缓冲队列缓存；DVSync通过缓存的帧减少未来可能发生的丢帧，进而提高动画场景的流畅性。<br> 因为DVSync需要占用空闲的自绘制帧缓冲用于缓存提前绘制的动画帧，用户需要确保至少有一个空闲的帧缓冲区，否则不建议启用此功能。<br> 启用DVSync后，用户需要正确响应提前发送的VSync信号，并在前一个VSync对应的动画帧完成后再请求下一个VSync，且自绘制帧需要携带与VSync一致的时间戳。<br> 在动画结束之后，用户需要关闭DVSync。<br> 在不支持DVSync的平台或者如果有另一个应用程序已经启用了DVSync，则当前的启用操作将不会生效，应用程序仍将收到正常的VSync信号。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_NativeVSync* nativeVsync | 一个指向OH_NativeVSync实例的指针。 |
| bool enable | 表示打开或者关闭DVSync，true表示打开，false表示关闭。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - 参数nativeVsync为空。<br>     NATIVE_ERROR_BINDER_ERROR 50401000 - ipc发送失败。 |

### OH_NativeVSync_SetExpectedFrameRateRange()

```c
int OH_NativeVSync_SetExpectedFrameRateRange(OH_NativeVSync* nativeVsync, OH_NativeVSync_ExpectedRateRange* range)
```

**描述**

设置VSync期望帧率及其范围。实际帧率可能因系统功耗、性能和硬件规格等限制而与设置的期望值不一致。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeVsync

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_NativeVSync* nativeVsync | 指向OH_NativeVSync实例的指针。 |
| [OH_NativeVSync_ExpectedRateRange](capi-nativevsync-oh-nativevsync-expectedraterange.md)* range | 指向OH_NativeVSync_ExpectedRateRange实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - 参数nativeVsync为空，或者range为空或无效。 |


