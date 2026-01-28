# Display (V1_4)

## 概述

显示模块驱动接口定义。

提供给上层图形服务使用的驱动接口，包括图层管理、设备控制、显示内存管理等相关接口。

**起始版本：**  6.1

## 汇总

### 文件

| 名称 | 描述 |
| -------- | -------- |
| [DisplayComposerType.idl](_composer_display_composer_type_8idl_v14.md) | 显示合成类型定义，定义显示图层合成操作相关接口所使用的数据类型。 |
| [IDisplayComposer.idl](_composer_i_display_composer_8idl_v14.md) | 显示合成接口声明。 |

### 结构体

| 名称 | 描述 |
| -------- | -------- |
| interface&nbsp;&nbsp;[IDisplayComposer](_composer_interface_i_display_composer_v14.md) | 显示合成接口声明。 |

### 枚举

| 名称 | 描述 |
| -------- | -------- |
| [PanelPowerStatus](#panelpowerstatus) { PANEL_POWER_STATUS_ON = 0, PANEL_POWER_STATUS_OFF = 1, PANEL_POWER_STATUS_BUTT } | 面板的电源状态。 |
| [DisplayPropertyID](#displaypropertyid) : ohos.hdi.display.composer.v1_2.DisplayPropertyID { DISPLAY_PROPERTY_ID_SUPPORT_PARALLEL = 4, DISPLAY_PROPERTY_ID_MULTI_DISPLAY_COORDINATION = 5 } | 显示VDI的属性ID。 |
| [DisplayConnectionType](#displayconnectiontype) { DISPLAY_CONNECTION_TYPE_INTERNAL = 0, DISPLAY_CONNECTION_TYPE_EXTERNAL = 1 } | 显示连接类型。 |

## 枚举类型说明

### DisplayConnectionType

```idl
enum DisplayConnectionType
```

**描述**

显示连接类型。

**起始版本：**  6.1

| 枚举值 | 描述 |
| -------- | -------- |
| DISPLAY_CONNECTION_TYPE_INTERNAL | 内装式 |
| DISPLAY_CONNECTION_TYPE_EXTERNAL | 外置式 |


### DisplayPropertyID

```idl
enum DisplayPropertyID : ohos.hdi.display.composer.v1_2.DisplayPropertyID
```

**描述**

显示VDI的属性ID。

**起始版本：**  6.1

| 枚举值 | 描述 |
| -------- | -------- |
| DISPLAY_PROPERTY_ID_SUPPORT_PARALLEL | 如果硬件支持并行呈现 |
| DISPLAY_PROPERTY_ID_MULTI_DISPLAY_COORDINATION | 所有显示设备是否同时开启。 |


### PanelPowerStatus

```idl
enum PanelPowerStatus
```

**描述**

面板的电源状态。

**起始版本：**  6.1

| 枚举值 | 描述 |
| -------- | -------- |
| PANEL_POWER_STATUS_ON | 面板电源状态为开启 |
| PANEL_POWER_STATUS_OFF | 面板电源状态为关闭 |
| PANEL_POWER_STATUS_BUTT | 面板电源状态按钮 |