# IDisplayComposer

## 概述

显示合成接口声明。

主要提供注册热插拔事件回调、获取显示设备能力集等功能，在v1_2.IDisplayComposer基础上新增注册更改VBlankIdle事件回调、清除缓冲区、硬光标特性等功能，具体方法使用详见函数说明。

**起始版本：**  6.0

**相关模块：**  [Display](_composer_display_v13.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [RegHwcEventCallback](#reghwceventcallback) ([in] [IHwcEventCallback](_composer_interface_i_hwc_event_callback_v13.md) cb) | 注册环境变化时要调用的回调接口。 |
| [GetSupportLayerType](#getsupportlayertype) ([in] unsigned int devId, [out] struct [LayerType](_composer_display_v13.md#layertype)[] types) | 返回支持的图层类型列表。 |
| [SetTunnelLayerId](#settunnellayerid) ([in] unsigned int devId, [in] unsigned int layerId, [in] unsigned long tunnelId) | 设置隧道层的TunnelId。 |
| [SetTunnelLayerProperty](#settunnellayerproperty) ([in] unsigned int devId, [in] unsigned int layerId, [in] unsigned int property) | 设置隧道层的隧道属性。 |
| [SetTunnelLayerPosition](#settunnellayerposition) ([in] unsigned int devId, [in] unsigned long tunnelId, [in] int x, [in] int y) | 设置隧道层的位置参数。 |
| [SetTunnelLayerBuffer](#settunnellayerbuffer) ([in] unsigned int devId, [in] unsigned long tunnelId, [in] NativeBuffer inHandle, [in] HdifdParcelable acquireFence) | 设置隧道层的层缓冲区地址。 |
| [CommitTunnelLayer](#committunnellayer) ([in] unsigned int devId, [in] unsigned long tunnelId, [out] HdifdParcelable releaseFence) | 从属隧道提交隧道层。 |

## 成员函数说明

### CommitTunnelLayer()

```idl
IDisplayComposer::CommitTunnelLayer([in] unsigned int devId, [in] unsigned long tunnelId, [out] HdifdParcelable releaseFence)
```

**描述**

从属隧道提交隧道层。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| tunnelId | 隧道层ID。 |
| releaseFence | 释放缓冲栅栏。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### GetSupportLayerType()

```idl
IDisplayComposer::GetSupportLayerType([in] unsigned int devId, [out] struct LayerType[] types)
```

**描述**

返回支持的图层类型列表。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| types | 支持的图层类型。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### RegHwcEventCallback()

```idl
IDisplayComposer::RegHwcEventCallback([in] IHwcEventCallback cb)
```

**描述**

注册环境变化时要调用的回调接口。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| cb | 用于通知图形服务发生环境更改事件的实例。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### SetTunnelLayerBuffer()

```idl
IDisplayComposer::SetTunnelLayerBuffer([in] unsigned int devId, [in] unsigned long tunnelId, [in] NativeBuffer inHandle, [in] HdifdParcelable acquireFence)
```

**描述**

设置隧道层的层缓冲区地址。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| tunnelId | 隧道层ID。 |
| inHandle | 缓冲区。 |
| acquireFence | 缓冲围栏。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### SetTunnelLayerId()

```idl
IDisplayComposer::SetTunnelLayerId([in] unsigned int devId, [in] unsigned int layerId, [in] unsigned long tunnelId)
```

**描述**

设置隧道层的TunnelId。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| layerId | Indicates 操作的图层的ID。 |
| tunnelId | Indicates 隧道层ID。 |

**返回：**

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### SetTunnelLayerPosition()

```idl
IDisplayComposer::SetTunnelLayerPosition([in] unsigned int devId, [in] unsigned long tunnelId, [in] int x, [in] int y)
```

**描述**

设置隧道层的位置参数。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| tunnelId | 隧道层ID。 |
| x | Indicates x坐标。 |
| y | Indicates y坐标。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### SetTunnelLayerProperty()

```idl
IDisplayComposer::SetTunnelLayerProperty([in] unsigned int devId, [in] unsigned int layerId, [in] unsigned int property)
```

**描述**

设置隧道层的隧道属性。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| layerId | 操作的图层的ID。 |
| property | 隧道层属性。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。
