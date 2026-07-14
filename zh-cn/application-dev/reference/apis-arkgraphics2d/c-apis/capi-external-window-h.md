# external_window.h

## 概述

定义获取和使用NativeWindow的相关函数。

**库：** libnative_window.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**相关模块：** [NativeWindow](capi-nativewindow.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Region](capi-nativewindow-region.md) | Region | 表示本地窗口OHNativeWindow需要更新内容的矩形区域（脏区）。 |
| [OHHDRMetaData](capi-nativewindow-ohhdrmetadata.md) | OHHDRMetaData | Defines the HDR metadata.(API10废弃) |
| [OHExtDataHandle](capi-nativewindow-ohextdatahandle.md) | OHExtDataHandle | Defines the ExtData Handle(API10废弃) |
| [OHIPCParcel](capi-nativewindow-ohipcparcel.md) | OHIPCParcel | 提供OHIPCParcel结构体声明，用于进程间通信。 |
| [NativeWindow](capi-nativewindow-nativewindow.md) | - | 提供对OHNativeWindow的访问功能。 |
| [NativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) | - | 提供对OHNativeWindowBuffer的访问功能。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [NativeWindowOperation](#nativewindowoperation) | NativeWindowOperation | OH_NativeWindow_NativeWindowHandleOpt函数中的操作码。 |
| [OHScalingMode](#ohscalingmode) | OHScalingMode | Indicates Scaling Mode.(API10废弃) |
| [OHScalingModeV2](#ohscalingmodev2) | OHScalingModeV2 | Indicates Scaling Mode. |
| [OHHDRMetadataKey](#ohhdrmetadatakey) | OHHDRMetadataKey | Enumerates the HDR metadata keys.(API10废弃) |
| [OHSurfaceSource](#ohsurfacesource) | OHSurfaceSource | Indicates the source type of surface. |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OHNativeWindow* OH_NativeWindow_CreateNativeWindow(void* pSurface)](#oh_nativewindow_createnativewindow) | 创建OHNativeWindow实例，每次调用都会产生一个新的OHNativeWindow实例。<br> 说明：此接口不可用，可通过OH_NativeImage_AcquireNativeWindow创建，或通过XComponent创建。<br>(API12废弃) |
| [void OH_NativeWindow_DestroyNativeWindow(OHNativeWindow* window)](#oh_nativewindow_destroynativewindow) | 将OHNativeWindow对象的引用计数减1，当引用计数为0的时候，该OHNativeWindow对象会被析构掉。<br> 本接口为非线程安全类型接口。<br> |
| [OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromSurfaceBuffer(void* pSurfaceBuffer)](#oh_nativewindow_createnativewindowbufferfromsurfacebuffer) | 创建OHNativeWindowBuffer实例，每次调用都会产生一个新的OHNativeWindowBuffer实例。<br> 说明：此接口不可用，使用OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer替代。<br>(API12废弃) |
| [OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer(OH_NativeBuffer* nativeBuffer)](#oh_nativewindow_createnativewindowbufferfromnativebuffer) | 创建OHNativeWindowBuffer实例，每次调用都会产生一个新的OHNativeWindowBuffer实例。<br> 本接口需要与OH_NativeWindow_DestroyNativeWindowBuffer接口配合使用，否则会存在内存泄露。<br> 本接口为非线程安全类型接口。<br> |
| [void OH_NativeWindow_DestroyNativeWindowBuffer(OHNativeWindowBuffer* buffer)](#oh_nativewindow_destroynativewindowbuffer) | 将OHNativeWindowBuffer对象的引用计数减1，当引用计数为0的时候，该OHNativeWindowBuffer对象会被析构掉。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_NativeWindowRequestBuffer(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd)](#oh_nativewindow_nativewindowrequestbuffer) | 通过OHNativeWindow对象申请一块OHNativeWindowBuffer，用以内容生产。<br> 在调用本接口前，需要通过SET_BUFFER_GEOMETRY对OHNativeWindow设置宽高。<br> 本接口需要与OH_NativeWindow_NativeWindowFlushBuffer接口配合使用，否则内存会耗尽。<br> 当fenceFd使用完，用户需要将其close。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_NativeWindowFlushBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer, int fenceFd, Region region)](#oh_nativewindow_nativewindowflushbuffer) | 通过OHNativeWindow将生产好内容的OHNativeWindowBuffer放回到Buffer队列中，用以内容消费。<br> 系统会将fenceFd关闭，无需用户close。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_GetLastFlushedBuffer(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd, float matrix[16])](#oh_nativewindow_getlastflushedbuffer) | 从OHNativeWindow获取上次送回到buffer队列中的OHNativeWindowBuffer。<br>(API12废弃) |
| [int32_t OH_NativeWindow_NativeWindowAbortBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)](#oh_nativewindow_nativewindowabortbuffer) | 通过OHNativeWindow将之前申请出来的OHNativeWindowBuffer返还到Buffer队列中，供下次再申请。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_NativeWindowHandleOpt(OHNativeWindow *window, int code, ...)](#oh_nativewindow_nativewindowhandleopt) | 设置/获取OHNativeWindow的属性，包括设置/获取宽高、内容格式等。<br> 本接口为非线程安全类型接口。<br> |
| [BufferHandle *OH_NativeWindow_GetBufferHandleFromNative(OHNativeWindowBuffer *buffer)](#oh_nativewindow_getbufferhandlefromnative) | 通过OHNativeWindowBuffer获取该buffer的BufferHandle指针。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_NativeObjectReference(void *obj)](#oh_nativewindow_nativeobjectreference) | 增加一个NativeObject的引用计数。<br> 本接口需要与OH_NativeWindow_NativeObjectUnreference接口配合使用，否则会存在内存泄露。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_NativeObjectUnreference(void *obj)](#oh_nativewindow_nativeobjectunreference) | 减少一个NativeObject的引用计数，当引用计数减少为0时，该NativeObject将被析构掉。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_GetNativeObjectMagic(void *obj)](#oh_nativewindow_getnativeobjectmagic) | 获取NativeObject的MagicId。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_NativeWindowSetScalingMode(OHNativeWindow *window, uint32_t sequence, OHScalingMode scalingMode)](#oh_nativewindow_nativewindowsetscalingmode) | 设置OHNativeWindow的ScalingMode。<br>(API10废弃) |
| [int32_t OH_NativeWindow_NativeWindowSetMetaData(OHNativeWindow *window, uint32_t sequence, int32_t size, const OHHDRMetaData *metaData)](#oh_nativewindow_nativewindowsetmetadata) | 设置OHNativeWindow的元数据。<br>(API10废弃) |
| [int32_t OH_NativeWindow_NativeWindowSetMetaDataSet(OHNativeWindow *window, uint32_t sequence, OHHDRMetadataKey key, int32_t size, const uint8_t *metaData)](#oh_nativewindow_nativewindowsetmetadataset) | 设置OHNativeWindow的元数据集。<br>(API10废弃) |
| [int32_t OH_NativeWindow_NativeWindowSetTunnelHandle(OHNativeWindow *window, const OHExtDataHandle *handle)](#oh_nativewindow_nativewindowsettunnelhandle) | 设置OHNativeWindow的TunnelHandle。<br>(API10废弃) |
| [int32_t OH_NativeWindow_NativeWindowAttachBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)](#oh_nativewindow_nativewindowattachbuffer) | 将OHNativeWindowBuffer添加进OHNativeWindow中。<br> 本接口需要与OH_NativeWindow_NativeWindowDetachBuffer接口配合使用，否则会存在内存管理混乱问题。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_NativeWindowDetachBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)](#oh_nativewindow_nativewindowdetachbuffer) | 将OHNativeWindowBuffer从OHNativeWindow中分离。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_GetSurfaceId(OHNativeWindow *window, uint64_t *surfaceId)](#oh_nativewindow_getsurfaceid) | 通过OHNativeWindow获取对应的surfaceId。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_CreateNativeWindowFromSurfaceId(uint64_t surfaceId, OHNativeWindow **window)](#oh_nativewindow_createnativewindowfromsurfaceid) | 通过surfaceId创建对应的OHNativeWindow。<br> 本接口需要与OH_NativeWindow_DestroyNativeWindow接口配合使用，否则会存在内存泄露。<br> 如果存在并发释放OHNativeWindow的情况，需要通过OH_NativeWindow_NativeObjectReference和<br> OH_NativeWindow_NativeObjectUnreference对OHNativeWindow进行引用计数加一和减一。<br> 通过surfaceId获取的surface需要是在本进程中创建的，不能跨进程获取surface。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_NativeWindowSetScalingModeV2(OHNativeWindow *window, OHScalingModeV2 scalingMode)](#oh_nativewindow_nativewindowsetscalingmodev2) | 设置OHNativeWindow的渲染缩放模式。<br> 本接口为非线程安全类型接口。<br> |
| [void OH_NativeWindow_SetBufferHold(OHNativeWindow *window)](#oh_nativewindow_setbufferhold) | 启用单帧缓存机制，通过提前缓存一帧buffer并延迟显示，用于平滑帧率波动。<br> 启用后，系统会预留一帧buffer作为缓冲，该帧会延迟一个显示周期才上屏。当后续渲染出现超长帧或帧间不均匀时，可使用该缓存帧填补空白，减少画面卡顿。<br> 建议在预知即将出现渲染高峰前提前调用，以建立缓冲保护；缓存仅生效一次，被消费后自动失效，如需持续保护需重新调用本接口。<br> 适用于游戏、动画、复杂UI渲染等对帧率稳定性要求较高的场景，但会引入一帧显示延迟（比如，在60hz的刷新率下，会延迟16.6ms上屏显示），不建议在高交互实时场景中使用。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_WriteToParcel(OHNativeWindow *window, OHIPCParcel *parcel)](#oh_nativewindow_writetoparcel) | 将窗口对象写入IPC序列化对象中。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_ReadFromParcel(OHIPCParcel *parcel, OHNativeWindow **window)](#oh_nativewindow_readfromparcel) | 从IPC序列化对象中读取窗口对象。<br> 本接口将会创建一个OHNativeWindow，当窗口对象使用完，开发者需要与OH_NativeWindow_DestroyNativeWindow接口配合使用，否则会存在内存泄漏。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_GetLastFlushedBufferV2(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd, float matrix[16])](#oh_nativewindow_getlastflushedbufferv2) | 从OHNativeWindow获取上次送回到buffer队列中的OHNativeWindowBuffer，与OH_NativeWindow_GetLastFlushedBuffer的差异在于matrix不同。<br> 本接口需要与OH_NativeWindow_NativeObjectUnreference接口配合使用，否则会存在内存泄露。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_SetColorSpace(OHNativeWindow *window, OH_NativeBuffer_ColorSpace colorSpace)](#oh_nativewindow_setcolorspace) | 为OHNativeWindow设置颜色空间属性。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_GetColorSpace(OHNativeWindow *window, OH_NativeBuffer_ColorSpace *colorSpace)](#oh_nativewindow_getcolorspace) | 获取OHNativeWindow颜色空间属性。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_SetMetadataValue(OHNativeWindow *window, OH_NativeBuffer_MetadataKey metadataKey, int32_t size, uint8_t *metadata)](#oh_nativewindow_setmetadatavalue) | 为OHNativeWindow设置元数据属性值。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_GetMetadataValue(OHNativeWindow *window, OH_NativeBuffer_MetadataKey metadataKey, int32_t *size, uint8_t **metadata)](#oh_nativewindow_getmetadatavalue) | 获取OHNativeWindow元数据属性值。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_CleanCache(OHNativeWindow *window)](#oh_nativewindow_cleancache) | 清理OHNativeWindow中的OHNativeWindowBuffer缓存。<br> 使用该接口清理缓存前，需确保已通过OH_NativeWindow_NativeWindowRequestBuffer接口成功申请OHNativeWindowBuffer。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_PreAllocBuffers(OHNativeWindow *window, uint32_t allocBufferCnt)](#oh_nativewindow_preallocbuffers) | 通过OHNativeWindow对象提前申请多块OHNativeWindowBuffer，用以内容生产。<br> 在调用本接口前，需要通过OH_NativeWindow_NativeWindowHandleOpt对OHNativeWindow设置宽高。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_LockBuffer(OHNativeWindow* window, Region region, OHNativeWindowBuffer** buffer)](#oh_nativewindow_lockbuffer) | 通过OHNativeWindow对象申请一块OHNativeWindowBuffer，用以内容生产，并对该OHNativeWindowBuffer加锁。<br> 本接口需要和OH_NativeWindow_UnlockAndFlushBuffer接口配合使用。<br> 本接口对OHNativeWindowBuffer加锁后，需要调OH_NativeWindow_UnlockAndFlushBuffer接口解锁后才能重新对OHNativeWindowBuffer加锁。<br> 若用本接口重复对OHNativeWindowBuffer加锁，会返回操作非法错误码。<br> 本接口支持通过CPU上的内存读写直接渲染图像。<br> 本接口为非线程安全类型接口。<br> |
| [int32_t OH_NativeWindow_UnlockAndFlushBuffer(OHNativeWindow* window)](#oh_nativewindow_unlockandflushbuffer) | 通过OHNativeWindow将生产好内容的OHNativeWindowBuffer放回到Buffer队列中，用以内容消费，并对OHNativeWindowBuffer解锁。<br> 本接口需要和OH_NativeWindow_LockBuffer接口配合使用。<br> 若用本接口重复对OHNativeWindowBuffer解锁，会返回操作非法错误码。<br> 本接口为非线程安全类型接口。<br> |

## 枚举类型说明

### NativeWindowOperation

```c
enum NativeWindowOperation
```

**描述**

OH_NativeWindow_NativeWindowHandleOpt函数中的操作码。

**起始版本：** 8

| 枚举项 | 描述 |
| -- | -- |
| SET_BUFFER_GEOMETRY | 设置本地窗口缓冲区几何图形，函数中的可变参数是[输入] int32_t width, [输入] int32_t height |
| GET_BUFFER_GEOMETRY | 获取本地窗口缓冲区几何图形，函数中的可变参数是[输出] int32_t *height, [输出] int32_t *width |
| GET_FORMAT | 获取本地窗口缓冲区格式，函数中的可变参数是[输出] int32_t *format，取值具体可见OH_NativeBuffer_Format枚举值。 |
| SET_FORMAT | 设置本地窗口缓冲区格式，函数中的可变参数是[输入] int32_t format，取值具体可见OH_NativeBuffer_Format枚举值。 |
| GET_USAGE | get native window buffer usage,variable parameter in function is[out] uint64_t *usage, the enumeration value refers to {@link OH_NativeBuffer_Usage}. |
| SET_USAGE | 设置本地窗口缓冲区读写方式，函数中的可变参数是[输入] uint64_t usage，取值具体可见OH_NativeBuffer_Usage枚举值。 |
| SET_STRIDE |  |
| GET_STRIDE |  |
| SET_SWAP_INTERVAL | 设置本地窗口缓冲区交换间隔，函数中的可变参数是[输入] int32_t interval。 |
| GET_SWAP_INTERVAL | 获取本地窗口缓冲区交换间隔，函数中的可变参数是[输出] int32_t *interval。 |
| SET_TIMEOUT | 设置请求本地窗口请求缓冲区的超时等待时间，未手动设置时默认值为3000毫秒，函数中的可变参数是[输入] int32_t timeout, 单位为毫秒。 |
| GET_TIMEOUT | 获取请求本地窗口请求缓冲区的超时等待时间，未手动设置时默认值为3000毫秒，函数中的可变参数是[输出] int32_t *timeout, 单位为毫秒。 |
| SET_COLOR_GAMUT | 设置本地窗口缓冲区色彩空间，函数中的可变参数是[输入] int32_t colorGamut，取值具体可见OH_NativeBuffer_ColorGamut枚举值。 |
| GET_COLOR_GAMUT | 获取本地窗口缓冲区色彩空间，函数中的可变参数是[输出] int32_t *colorGamut，取值具体可见OH_NativeBuffer_ColorGamut枚举值。 |
| SET_TRANSFORM | 设置本地窗口缓冲区变换，函数中的可变参数是[输入] int32_t transform，取值具体可见OH_NativeBuffer_TransformType枚举值。 |
| GET_TRANSFORM | 获取本地窗口缓冲区变换，函数中的可变参数是[输出] int32_t *transform，取值具体可见OH_NativeBuffer_TransformType枚举值。 |
| SET_UI_TIMESTAMP | 设置本地窗口缓冲区UI时间戳，函数中的可变参数是[输入] uint64_t uiTimestamp。 |
| GET_BUFFERQUEUE_SIZE |  |
| SET_SOURCE_TYPE |  |
| GET_SOURCE_TYPE |  |
| SET_APP_FRAMEWORK_TYPE |  |
| GET_APP_FRAMEWORK_TYPE |  |
| SET_HDR_WHITE_POINT_BRIGHTNESS |  |
| SET_SDR_WHITE_POINT_BRIGHTNESS |  |
| SET_DESIRED_PRESENT_TIMESTAMP = 24 |  |

### OHScalingMode

```c
enum OHScalingMode
```

**描述**

Indicates Scaling Mode.

**起始版本：** 9

**废弃版本：** 10

**替代接口：** OHScalingModeV2

| 枚举项 | 描述 |
| -- | -- |
| OH_SCALING_MODE_FREEZE = 0 | the window content is not updated until a buffer ofthe window size is received |
| OH_SCALING_MODE_SCALE_TO_WINDOW | the buffer is scaled in two dimensions to match the window size |
| OH_SCALING_MODE_SCALE_CROP | the buffer is uniformly scaled so that the smaller size ofthe buffer matches the window size |
| OH_SCALING_MODE_NO_SCALE_CROP | the window is clipped to the size of the buffer's clipping rectanglepixels outside the clipping rectangle are considered fully transparent. |

### OHScalingModeV2

```c
enum OHScalingModeV2
```

**描述**

Indicates Scaling Mode.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_SCALING_MODE_FREEZE_V2 = 0 | the window content is not updated until a buffer ofthe window size is received |
| OH_SCALING_MODE_SCALE_TO_WINDOW_V2 | the buffer is scaled in two dimensions to match the window size |
| OH_SCALING_MODE_SCALE_CROP_V2 | the buffer is uniformly scaled so that the smaller size ofthe buffer matches the window size |
| OH_SCALING_MODE_NO_SCALE_CROP_V2 | the window is clipped to the size of the buffer's clipping rectanglepixels outside the clipping rectangle are considered fully transparent. |
| OH_SCALING_MODE_SCALE_FIT_V2 | Adapt to the buffer and scale proportionally to the buffer size. Prioritize displaying all buffer content.If the size is not the same as the window size, fill the unfilled area of the window with a background color. |

### OHHDRMetadataKey

```c
enum OHHDRMetadataKey
```

**描述**

Enumerates the HDR metadata keys.

**起始版本：** 9

**废弃版本：** 10

| 枚举项 | 描述 |
| -- | -- |

### OHSurfaceSource

```c
enum OHSurfaceSource
```

**描述**

Indicates the source type of surface.

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_SURFACE_SOURCE_DEFAULT = 0 | the default source type of surface. |
| OH_SURFACE_SOURCE_UI | the surface is created by ui. |
| OH_SURFACE_SOURCE_GAME | the surface is created by game. |
| OH_SURFACE_SOURCE_CAMERA | the surface is created by camera. |
| OH_SURFACE_SOURCE_VIDEO | the surface is created by video. |


## 函数说明

### OH_NativeWindow_CreateNativeWindow()

```c
OHNativeWindow* OH_NativeWindow_CreateNativeWindow(void* pSurface)
```

**描述**

创建OHNativeWindow实例，每次调用都会产生一个新的OHNativeWindow实例。<br> 说明：此接口不可用，可通过OH_NativeImage_AcquireNativeWindow创建，或通过XComponent创建。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**废弃版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void* pSurface | 一个指向生产者ProduceSurface的指针，类型为sptr<OHOS::Surface>。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OHNativeWindow*](capi-nativewindow-nativewindow.md) | 返回一个指针，指向OHNativeWindow的结构体实例。 |

### OH_NativeWindow_DestroyNativeWindow()

```c
void OH_NativeWindow_DestroyNativeWindow(OHNativeWindow* window)
```

**描述**

将OHNativeWindow对象的引用计数减1，当引用计数为0的时候，该OHNativeWindow对象会被析构掉。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md)* window | 一个OHNativeWindow的结构体实例的指针。 |

### OH_NativeWindow_CreateNativeWindowBufferFromSurfaceBuffer()

```c
OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromSurfaceBuffer(void* pSurfaceBuffer)
```

**描述**

创建OHNativeWindowBuffer实例，每次调用都会产生一个新的OHNativeWindowBuffer实例。<br> 说明：此接口不可用，使用OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer替代。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**废弃版本：** 12

**替代接口：** OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void* pSurfaceBuffer | 一个指向生产者buffer的指针，类型为sptr<OHOS::SurfaceBuffer>。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OHNativeWindowBuffer*](capi-nativewindow-nativewindowbuffer.md) | 返回一个指针，指向OHNativeWindowBuffer的结构体实例。 |

### OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer()

```c
OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer(OH_NativeBuffer* nativeBuffer)
```

**描述**

创建OHNativeWindowBuffer实例，每次调用都会产生一个新的OHNativeWindowBuffer实例。<br> 本接口需要与OH_NativeWindow_DestroyNativeWindowBuffer接口配合使用，否则会存在内存泄露。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_NativeBuffer* nativeBuffer | 一个指向OH_NativeBuffer的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OHNativeWindowBuffer*](capi-nativewindow-nativewindowbuffer.md) | 返回一个指针，指向OHNativeWindowBuffer的结构体实例。 |

### OH_NativeWindow_DestroyNativeWindowBuffer()

```c
void OH_NativeWindow_DestroyNativeWindowBuffer(OHNativeWindowBuffer* buffer)
```

**描述**

将OHNativeWindowBuffer对象的引用计数减1，当引用计数为0的时候，该OHNativeWindowBuffer对象会被析构掉。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md)* buffer | 一个OHNativeWindowBuffer的结构体实例的指针。 |

### OH_NativeWindow_NativeWindowRequestBuffer()

```c
int32_t OH_NativeWindow_NativeWindowRequestBuffer(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd)
```

**描述**

通过OHNativeWindow对象申请一块OHNativeWindowBuffer，用以内容生产。<br> 在调用本接口前，需要通过SET_BUFFER_GEOMETRY对OHNativeWindow设置宽高。<br> 本接口需要与OH_NativeWindow_NativeWindowFlushBuffer接口配合使用，否则内存会耗尽。<br> 当fenceFd使用完，用户需要将其close。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) **buffer | 一个指向OHNativeWindowBuffer指针的指针（二级指针）。<br> 通过OH_NativeWindow_GetBufferHandleFromNative可获取BufferHandle结构体，访问缓冲区内存。 |
| int *fenceFd | 一个文件描述符句柄，用于GPU/CPU同步：不同取值及含义如下：<br>- 返回≥0：缓冲区正被GPU使用，需要等待文件描述符fenceFd就绪。<br>- 返回-1：缓冲区可直接使用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowFlushBuffer()

```c
int32_t OH_NativeWindow_NativeWindowFlushBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer, int fenceFd, Region region)
```

**描述**

通过OHNativeWindow将生产好内容的OHNativeWindowBuffer放回到Buffer队列中，用以内容消费。<br> 系统会将fenceFd关闭，无需用户close。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | 一个OHNativeWindowBuffer的结构体实例的指针。 |
| int fenceFd | 一个文件描述符句柄，用以同步时序。不同取值及含义如下：<br>- -1：CPU渲染完成，无需同步时序。<br>- ≥0：从GPU同步对象转换<br> （如EGL的eglDupNativeFenceFDANDROID），对端需要通过此fenceFd同步时序。 |
| [Region](capi-nativewindow-region.md) region | 一个Region结构体，表示一块脏区域，该区域有内容更新。<br>Region.rectNumber限制最大数量为1000，<br> 当rectNumber≤0或者rectNumber>1000时，使用整个buffer作为脏区。<br>Region.rect以buffer左下角为坐标原点。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_GetLastFlushedBuffer()

```c
int32_t OH_NativeWindow_GetLastFlushedBuffer(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd, float matrix[16])
```

**描述**

从OHNativeWindow获取上次送回到buffer队列中的OHNativeWindowBuffer。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 11

**废弃版本：** 12

**替代接口：** OH_NativeWindow_GetLastFlushedBufferV2

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) **buffer | 一个OHNativeWindowBuffer结构体指针的指针。 |
| int *fenceFd | 一个文件描述符的指针。 |
| matrix | 表示检索到的4*4变换矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowAbortBuffer()

```c
int32_t OH_NativeWindow_NativeWindowAbortBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)
```

**描述**

通过OHNativeWindow将之前申请出来的OHNativeWindowBuffer返还到Buffer队列中，供下次再申请。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | 一个OHNativeWindowBuffer的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowHandleOpt()

```c
int32_t OH_NativeWindow_NativeWindowHandleOpt(OHNativeWindow *window, int code, ...)
```

**描述**

设置/获取OHNativeWindow的属性，包括设置/获取宽高、内容格式等。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| int code | 表示操作码，详见NativeWindowOperation。 |
| [](capi-nativewindow-nativewindow.md).[](capi-nativewindow-nativewindow.md).[](capi-nativewindow-nativewindow.md).[](capi-nativewindow-nativewindow.md) | 可变参数，必须与操作码对应的数据类型保持一致，且入参数量严格按照操作码提示传入，否则会存在未定义行为。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_GetBufferHandleFromNative()

```c
BufferHandle *OH_NativeWindow_GetBufferHandleFromNative(OHNativeWindowBuffer *buffer)
```

**描述**

通过OHNativeWindowBuffer获取该buffer的BufferHandle指针。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | 一个OHNativeWindowBuffer的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [BufferHandle *](capi-nativewindow-bufferhandle.md) | 返回一个指针，指向BufferHandle的结构体实例。 |

### OH_NativeWindow_NativeObjectReference()

```c
int32_t OH_NativeWindow_NativeObjectReference(void *obj)
```

**描述**

增加一个NativeObject的引用计数。<br> 本接口需要与OH_NativeWindow_NativeObjectUnreference接口配合使用，否则会存在内存泄露。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void *obj | 一个OHNativeWindow或者OHNativeWindowBuffer的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeObjectUnreference()

```c
int32_t OH_NativeWindow_NativeObjectUnreference(void *obj)
```

**描述**

减少一个NativeObject的引用计数，当引用计数减少为0时，该NativeObject将被析构掉。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void *obj | 一个OHNativeWindow或者OHNativeWindowBuffer的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_GetNativeObjectMagic()

```c
int32_t OH_NativeWindow_GetNativeObjectMagic(void *obj)
```

**描述**

获取NativeObject的MagicId。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void *obj | 一个OHNativeWindow或者OHNativeWindowBuffer的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为魔鬼数字，每个NativeObject唯一。 |

### OH_NativeWindow_NativeWindowSetScalingMode()

```c
int32_t OH_NativeWindow_NativeWindowSetScalingMode(OHNativeWindow *window, uint32_t sequence, OHScalingMode scalingMode)
```

**描述**

设置OHNativeWindow的ScalingMode。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 9

**废弃版本：** 10

**替代接口：** OH_NativeWindow_NativeWindowSetScalingModeV2

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| uint32_t sequence | 生产缓冲区的序列。 |
| [OHScalingMode](capi-external-window-h.md#ohscalingmode) scalingMode | 枚举值OHScalingMode。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowSetMetaData()

```c
int32_t OH_NativeWindow_NativeWindowSetMetaData(OHNativeWindow *window, uint32_t sequence, int32_t size, const OHHDRMetaData *metaData)
```

**描述**

设置OHNativeWindow的元数据。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 9

**废弃版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| uint32_t sequence | 生产缓冲区的序列。 |
| int32_t size | OHHDRMetaData数组的大小，最大支持为3000，超出会返回NATIVE_ERROR_INVALID_ARGUMENTS。 |
| [const OHHDRMetaData](capi-nativewindow-ohhdrmetadata.md) *metaData | 指向OHHDRMetaData数组的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowSetMetaDataSet()

```c
int32_t OH_NativeWindow_NativeWindowSetMetaDataSet(OHNativeWindow *window, uint32_t sequence, OHHDRMetadataKey key, int32_t size, const uint8_t *metaData)
```

**描述**

设置OHNativeWindow的元数据集。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 9

**废弃版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| uint32_t sequence | 生产缓冲区的序列。 |
| [OHHDRMetadataKey](capi-external-window-h.md#ohhdrmetadatakey) key | 枚举值OHHDRMetadataKey。 |
| int32_t size | uint8_t向量的大小，最大支持为3000，超出会返回NATIVE_ERROR_INVALID_ARGUMENTS。 |
| const uint8_t *metaData | 指向uint8_t向量的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowSetTunnelHandle()

```c
int32_t OH_NativeWindow_NativeWindowSetTunnelHandle(OHNativeWindow *window, const OHExtDataHandle *handle)
```

**描述**

设置OHNativeWindow的TunnelHandle。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 9

**废弃版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [const OHExtDataHandle](capi-nativewindow-ohextdatahandle.md) *handle | 指向OHExtDataHandle的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowAttachBuffer()

```c
int32_t OH_NativeWindow_NativeWindowAttachBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)
```

**描述**

将OHNativeWindowBuffer添加进OHNativeWindow中。<br> 本接口需要与OH_NativeWindow_NativeWindowDetachBuffer接口配合使用，否则会存在内存管理混乱问题。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | 一个OHNativeWindowBuffer的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowDetachBuffer()

```c
int32_t OH_NativeWindow_NativeWindowDetachBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)
```

**描述**

将OHNativeWindowBuffer从OHNativeWindow中分离。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | 一个OHNativeWindowBuffer的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_GetSurfaceId()

```c
int32_t OH_NativeWindow_GetSurfaceId(OHNativeWindow *window, uint64_t *surfaceId)
```

**描述**

通过OHNativeWindow获取对应的surfaceId。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| uint64_t *surfaceId | 一个surface对应ID的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_CreateNativeWindowFromSurfaceId()

```c
int32_t OH_NativeWindow_CreateNativeWindowFromSurfaceId(uint64_t surfaceId, OHNativeWindow **window)
```

**描述**

通过surfaceId创建对应的OHNativeWindow。<br> 本接口需要与OH_NativeWindow_DestroyNativeWindow接口配合使用，否则会存在内存泄露。<br> 如果存在并发释放OHNativeWindow的情况，需要通过OH_NativeWindow_NativeObjectReference和<br> OH_NativeWindow_NativeObjectUnreference对OHNativeWindow进行引用计数加一和减一。<br> 通过surfaceId获取的surface需要是在本进程中创建的，不能跨进程获取surface。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t surfaceId | 一个surface对应的ID。 |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) **window | 一个OHNativeWindow的结构体实例的二级指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_NativeWindowSetScalingModeV2()

```c
int32_t OH_NativeWindow_NativeWindowSetScalingModeV2(OHNativeWindow *window, OHScalingModeV2 scalingMode)
```

**描述**

设置OHNativeWindow的渲染缩放模式。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [OHScalingModeV2](capi-external-window-h.md#ohscalingmodev2) scalingMode | 一个OHScalingModeV2类型的枚举值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_SetBufferHold()

```c
void OH_NativeWindow_SetBufferHold(OHNativeWindow *window)
```

**描述**

启用单帧缓存机制，通过提前缓存一帧buffer并延迟显示，用于平滑帧率波动。<br> 启用后，系统会预留一帧buffer作为缓冲，该帧会延迟一个显示周期才上屏。当后续渲染出现超长帧或帧间不均匀时，可使用该缓存帧填补空白，减少画面卡顿。<br> 建议在预知即将出现渲染高峰前提前调用，以建立缓冲保护；缓存仅生效一次，被消费后自动失效，如需持续保护需重新调用本接口。<br> 适用于游戏、动画、复杂UI渲染等对帧率稳定性要求较高的场景，但会引入一帧显示延迟（比如，在60hz的刷新率下，会延迟16.6ms上屏显示），不建议在高交互实时场景中使用。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |

### OH_NativeWindow_WriteToParcel()

```c
int32_t OH_NativeWindow_WriteToParcel(OHNativeWindow *window, OHIPCParcel *parcel)
```

**描述**

将窗口对象写入IPC序列化对象中。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个指向OHNativeWindow的结构体实例的指针。 |
| [OHIPCParcel](capi-nativewindow-ohipcparcel.md) *parcel | 一个指向OHIPCParcel的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - parcel为空或window为空。 |

### OH_NativeWindow_ReadFromParcel()

```c
int32_t OH_NativeWindow_ReadFromParcel(OHIPCParcel *parcel, OHNativeWindow **window)
```

**描述**

从IPC序列化对象中读取窗口对象。<br> 本接口将会创建一个OHNativeWindow，当窗口对象使用完，开发者需要与OH_NativeWindow_DestroyNativeWindow接口配合使用，否则会存在内存泄漏。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHIPCParcel](capi-nativewindow-ohipcparcel.md) *parcel | 一个指向OHIPCParcel的结构体实例的指针。 |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) **window | 一个指向OHNativeWindow的结构体实例的二级指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - parcel为空或parcel不包含window。 |

### OH_NativeWindow_GetLastFlushedBufferV2()

```c
int32_t OH_NativeWindow_GetLastFlushedBufferV2(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd, float matrix[16])
```

**描述**

从OHNativeWindow获取上次送回到buffer队列中的OHNativeWindowBuffer，与OH_NativeWindow_GetLastFlushedBuffer的差异在于matrix不同。<br> 本接口需要与OH_NativeWindow_NativeObjectUnreference接口配合使用，否则会存在内存泄露。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个OHNativeWindow的结构体实例的指针。 |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) **buffer | 一个OHNativeWindowBuffer结构体指针的指针。 |
| int *fenceFd | 一个文件描述符的指针。 |
| matrix | 表示检索到的4*4变换矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - window为空或buffer为空或fenceFd为空。<br>     NATIVE_ERROR_BUFFER_STATE_INVALID 41207000 - buffer状态错误。 |

### OH_NativeWindow_SetColorSpace()

```c
int32_t OH_NativeWindow_SetColorSpace(OHNativeWindow *window, OH_NativeBuffer_ColorSpace colorSpace)
```

**描述**

为OHNativeWindow设置颜色空间属性。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个指向OHNativeWindow的结构体实例的指针。 |
| [OH_NativeBuffer_ColorSpace](capi-buffer-common-h.md#oh_nativebuffer_colorspace) colorSpace | 为OHNativeWindow设置的颜色空间，其值从OH_NativeBuffer_ColorSpace获取。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - window为空。<br>     NATIVE_ERROR_BUFFER_STATE_INVALID 41207000 - colorSpace状态错误。 |

### OH_NativeWindow_GetColorSpace()

```c
int32_t OH_NativeWindow_GetColorSpace(OHNativeWindow *window, OH_NativeBuffer_ColorSpace *colorSpace)
```

**描述**

获取OHNativeWindow颜色空间属性。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个指向OHNativeWindow的结构体实例的指针。 |
| [OH_NativeBuffer_ColorSpace](capi-buffer-common-h.md#oh_nativebuffer_colorspace) *colorSpace | OHNativeWindow的颜色空间，值从OH_NativeBuffer_ColorSpace获取。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - window为空。<br>     NATIVE_ERROR_BUFFER_STATE_INVALID 41207000 - colorSpace状态错误。 |

### OH_NativeWindow_SetMetadataValue()

```c
int32_t OH_NativeWindow_SetMetadataValue(OHNativeWindow *window, OH_NativeBuffer_MetadataKey metadataKey, int32_t size, uint8_t *metadata)
```

**描述**

为OHNativeWindow设置元数据属性值。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个指向OHNativeWindow的结构体实例的指针。 |
| [OH_NativeBuffer_MetadataKey](capi-buffer-common-h.md#oh_nativebuffer_metadatakey) metadataKey | Window的元数据类型，其值从OH_NativeBuffer_MetadataKey获取。 |
| int32_t size | uint8_t向量的大小，其取值范围见OH_NativeBuffer_MetadataKey。 |
| uint8_t *metadata | 指向uint8_t向量的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - window或metadata为空。<br>     NATIVE_ERROR_BUFFER_STATE_INVALID 41207000 - metadata状态错误。<br>     NATIVE_ERROR_UNSUPPORTED 50102000 - 不支持的metadata key。 |

### OH_NativeWindow_GetMetadataValue()

```c
int32_t OH_NativeWindow_GetMetadataValue(OHNativeWindow *window, OH_NativeBuffer_MetadataKey metadataKey, int32_t *size, uint8_t **metadata)
```

**描述**

获取OHNativeWindow元数据属性值。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个指向OHNativeWindow的结构体实例的指针。 |
| [OH_NativeBuffer_MetadataKey](capi-buffer-common-h.md#oh_nativebuffer_metadatakey) metadataKey | Window的元数据类型，其值从OH_NativeBuffer_MetadataKey获取。 |
| int32_t *size | uint8_t向量的大小，其取值范围见OH_NativeBuffer_MetadataKey。 |
| uint8_t **metadata | 指向uint8_t向量的二级指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - window、metadata或size为空。<br>     NATIVE_ERROR_BUFFER_STATE_INVALID 41207000 - metadata状态错误。<br>     NATIVE_ERROR_UNSUPPORTED 50102000 - 不支持的metadata key。 |

### OH_NativeWindow_CleanCache()

```c
int32_t OH_NativeWindow_CleanCache(OHNativeWindow *window)
```

**描述**

清理OHNativeWindow中的OHNativeWindowBuffer缓存。<br> 使用该接口清理缓存前，需确保已通过OH_NativeWindow_NativeWindowRequestBuffer接口成功申请OHNativeWindowBuffer。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个指向OHNativeWindow的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - window为空。<br>     NATIVE_ERROR_CONSUMER_DISCONNECTED 41211000 - consumer断开连接。<br>     NATIVE_ERROR_BINDER_ERROR 50401000 - ipc发送失败。 |

### OH_NativeWindow_PreAllocBuffers()

```c
int32_t OH_NativeWindow_PreAllocBuffers(OHNativeWindow *window, uint32_t allocBufferCnt)
```

**描述**

通过OHNativeWindow对象提前申请多块OHNativeWindowBuffer，用以内容生产。<br> 在调用本接口前，需要通过OH_NativeWindow_NativeWindowHandleOpt对OHNativeWindow设置宽高。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | 一个指向OHNativeWindow的结构体实例的指针。 |
| uint32_t allocBufferCnt | 提前申请buffer的数量。当allocBufferCnt大于bufferQueueSize时，只能提前申请bufferQueueSize数量的buffer。<br> bufferQueueSize可以通过OH_NativeWindow_NativeWindowHandleOpt获取。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 返回值为0表示执行成功，其他返回值可参考OHNativeErrorCode。 |

### OH_NativeWindow_LockBuffer()

```c
int32_t OH_NativeWindow_LockBuffer(OHNativeWindow* window, Region region, OHNativeWindowBuffer** buffer)
```

**描述**

通过OHNativeWindow对象申请一块OHNativeWindowBuffer，用以内容生产，并对该OHNativeWindowBuffer加锁。<br> 本接口需要和OH_NativeWindow_UnlockAndFlushBuffer接口配合使用。<br> 本接口对OHNativeWindowBuffer加锁后，需要调OH_NativeWindow_UnlockAndFlushBuffer接口解锁后才能重新对OHNativeWindowBuffer加锁。<br> 若用本接口重复对OHNativeWindowBuffer加锁，会返回操作非法错误码。<br> 本接口支持通过CPU上的内存读写直接渲染图像。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md)* window | 一个指向OHNativeWindow的结构体实例的指针。 |
| [Region](capi-nativewindow-region.md) region | 一个Region结构体，表示一块脏区域，该区域有内容更新。<br>Region.rectNumber限制最大数量为1000，<br> 当rectNumber≤0或者rectNumber>1000时，使用整个buffer作为脏区。<br>Region.rect以buffer左下角为坐标原点。 |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md)** buffer | 一个指向OHNativeWindowBuffer的二级指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - window或buffer为空。<br>     NATIVE_ERROR_UNKNOWN 50002000 - window的surface成员为空。 |

### OH_NativeWindow_UnlockAndFlushBuffer()

```c
int32_t OH_NativeWindow_UnlockAndFlushBuffer(OHNativeWindow* window)
```

**描述**

通过OHNativeWindow将生产好内容的OHNativeWindowBuffer放回到Buffer队列中，用以内容消费，并对OHNativeWindowBuffer解锁。<br> 本接口需要和OH_NativeWindow_LockBuffer接口配合使用。<br> 若用本接口重复对OHNativeWindowBuffer解锁，会返回操作非法错误码。<br> 本接口为非线程安全类型接口。<br>

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md)* window | 一个指向OHNativeWindow的结构体实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | NATIVE_ERROR_OK 0 - 成功。<br>     NATIVE_ERROR_INVALID_ARGUMENTS 40001000 - window为空。<br>     NATIVE_ERROR_UNKNOWN 50002000 - window的surface成员为空。 |


