# @ohos.resourceManager

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为-1。

**废弃版本：** -1

<!--Device-unnamed-declare namespace resourceManager--><!--Device-unnamed-declare namespace resourceManager-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getResourceManager](arkts-localization-resourcemanager-getresourcemanager-f.md#getResourceManager) | 获取当前应用的资源管理对象。使用callback异步回调。 |
| [getResourceManager](arkts-localization-resourcemanager-getresourcemanager-f.md#getResourceManager) | 获取指定应用的资源管理对象。使用callback异步回调。 |
| [getResourceManager](arkts-localization-resourcemanager-getresourcemanager-f.md#getResourceManager) | 获取当前应用的资源管理对象。使用Promise异步回调。 |
| [getResourceManager](arkts-localization-resourcemanager-getresourcemanager-f.md#getResourceManager) | 获取指定应用的资源管理对象。使用Promise异步回调。 |
| [getSysResourceManager](arkts-localization-resourcemanager-getsysresourcemanager-f.md#getSysResourceManager) | 获取系统资源管理对象，用于访问系统预置的资源。 |
| [getSystemResourceManager](arkts-localization-resourcemanager-getsystemresourcemanager-f.md#getSystemResourceManager) | 获取系统资源管理对象，用于访问系统预置的资源。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Configuration](arkts-localization-resourcemanager-configuration-c.md) | 表示当前设备的状态。 |
| [DeviceCapability](arkts-localization-resourcemanager-devicecapability-c.md) | 表示设备支持的能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md) | 异步回调接口 |
| [ResourceManager](arkts-localization-resourcemanager-resourcemanager-i.md) | 提供访问应用资源和系统资源的能力，可访问的资源范围为当前Context对应的HAP/HSP模块中的资源以及所有的系统资源。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ColorMode](arkts-localization-resourcemanager-colormode-e.md) | 用于表示当前设备颜色模式。 |
| [DeviceType](arkts-localization-resourcemanager-devicetype-e.md) | 用于表示当前设备类型。 &lt;!--RP1--&gt; &lt;!--RP1End--&gt; |
| [Direction](arkts-localization-resourcemanager-direction-e.md) | 用于表示设备屏幕方向。 |
| [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md) | 用于表示当前设备屏幕密度。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RawFileDescriptor](arkts-localization-resourcemanager-rawfiledescriptor-t.md) | 表示rawfile文件所在HAP的文件描述符信息。 |
| [Resource](arkts-localization-resourcemanager-resource-t.md) | 表示资源相关信息，包括应用包名、应用模块名、资源ID、资源类型和格式化参数等。 |

