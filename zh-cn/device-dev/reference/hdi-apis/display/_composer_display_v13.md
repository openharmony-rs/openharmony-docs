# Display (V1_3)

## 概述

显示模块驱动接口定义。

提供给上层图形服务使用的驱动接口，包括图层管理、设备控制、显示内存管理等相关接口。

**起始版本：**  6.0

## 汇总

### 文件

| 名称 | 描述 |
| -------- | -------- |
| [DisplayComposerType.idl](_composer_display_composer_type_8idl_v13.md) | 显示合成类型定义，定义显示图层合成操作相关接口所使用的数据类型。 |
| [IDisplayComposer.idl](_composer_i_display_composer_8idl_v13.md) | 显示合成接口声明。 |
| [IHwcEventCallback.idl](_composer_i_hwc_event_callback_8idl_v13.md) | 帧同步事件回调接口声明。 |

### 结构体

| 名称 | 描述 |
| -------- | -------- |
| interface&nbsp;&nbsp;[IDisplayComposer](_composer_interface_i_display_composer_v13.md) | 显示合成接口声明。 |
| interface&nbsp;&nbsp;[IHwcEventCallback](_composer_interface_i_hwc_event_callback_v13.md) | 环境变化事件回调接口。 |

### 枚举

| 名称 | 描述 |
| -------- | -------- |
| [TunnelLayerProperty](#tunnellayerproperty) {<br/>TUNNEL_PROP_INVALID = 0, TUNNEL_PROP_POSTION = (1 &lt;&lt; 0), TUNNEL_PROP_BUFFER_ADDR = (1 &lt;&lt; 1), TUNNEL_PROP_CLIENT_COMMIT = (1 &lt;&lt; 2),<br/>TUNNEL_PROP_DEVICE_COMMIT = (1 &lt;&lt; 3), TUNNEL_PROP_SECURE_DEVICE_COMMIT = (1 &lt;&lt; 4)<br/>} | 隧道层的属性ID枚举。 |
| [LayerType](#layertype) : ohos.hdi.display.composer.v1_0.LayerType { LAYER_TYPE_TUNNEL } | 隧道层类型。 |

## 枚举类型说明

### LayerType

```idl
enum LayerType : ohos.hdi.display.composer.v1_0.LayerType
```

**描述**

隧道层类型。

**起始版本：**  6.0

| 枚举值 | 描述 |
| -------- | -------- |
| LAYER_TYPE_TUNNEL | 隧道层。 |

### TunnelLayerProperty

```idl
enum TunnelLayerProperty
```

**描述**

隧道层的属性ID枚举。

**起始版本：**  6.0

| 枚举值 | 描述 |
| -------- | -------- |
| TUNNEL_PROP_INVALID | 无效的隧道层属性。 |
| TUNNEL_PROP_POSTION | 通过隧道更新图层位置。 |
| TUNNEL_PROP_BUFFER_ADDR | 通过隧道更新图层缓冲区地址。 |
| TUNNEL_PROP_CLIENT_COMMIT | 客户端更新隧道层。 |
| TUNNEL_PROP_DEVICE_COMMIT | 设备更新隧道层。 |
| TUNNEL_PROP_SECURE_DEVICE_COMMIT | 通过安全设备更新隧道层。 |