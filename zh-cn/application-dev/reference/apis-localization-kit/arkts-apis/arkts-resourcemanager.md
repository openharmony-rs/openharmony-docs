# @ohos.resourceManager

本模块提供资源获取能力。根据当前的[Configuration](arkts-localization-configuration-c.md)配置，获取最匹配的应用资源或系统资源。
具体匹配规则参考[资源匹配](../../../../quick-start/resource-categories-and-access.md#资源匹配)。
Configuration配置包括语言、区域、横竖屏、颜色模式、Mcc（移动国家码）和Mnc（移动网络码）、Device capability（设备类型）、Density（分辨率）。

**起始版本：** 6

**系统能力：** SystemCapability.Global.ResourceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getResourceManager](arkts-localization-getresourcemanager-f.md#getresourcemanager-1) | 获取当前应用的资源管理对象，使用callback异步回调。 |
| [getResourceManager](arkts-localization-getresourcemanager-f.md#getresourcemanager-2) | 获取指定应用的资源管理对象，使用callback异步回调。 |
| [getResourceManager](arkts-localization-getresourcemanager-f.md#getresourcemanager-3) | 获取当前应用的资源管理对象，使用Promise异步回调。 |
| [getResourceManager](arkts-localization-getresourcemanager-f.md#getresourcemanager-4) | 获取指定应用的资源管理对象，使用Promise异步回调。 |
| [getSysResourceManager](arkts-localization-getsysresourcemanager-f.md#getsysresourcemanager-1) | 获取系统资源管理对象。 |
| [getSystemResourceManager](arkts-localization-getsystemresourcemanager-f.md#getsystemresourcemanager-1) | 获取系统资源管理ResourceManager对象。&gt; **说明**&gt;&gt; 当前接口获取到的系统资源管理ResourceManager对象中的Configuration为默认值。默认值如下：&gt; {"locale": "", "direction": -1, "deviceType": -1, "screenDensity": 0, "colorMode": 1, "mcc": 0, "mnc": 0}。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Configuration](arkts-localization-configuration-c.md) | 表示当前设备的状态。 |
| [DeviceCapability](arkts-localization-devicecapability-c.md) | 表示设备支持的能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AsyncCallback](arkts-localization-asynccallback-i.md) | The ResourceManager callback. |
| [ResourceManager](arkts-localization-resourcemanager-i.md) | 提供访问应用资源和系统资源的能力。@link @ohos.app.ability.application:application.createModuleContext(context: Context, moduleName: string)}创建对应module的context**&gt; ，再调用参数为resName或resId的接口。更多请参考[资源访问](../../../../quick-start/resource-categories-and-access.md#资源访问)。&gt;&gt; - 在API version 22及之前版本，中间码HAR、字节码HAR通过资源ID相关接口访问资源时，因ID无效会抛出异常；从API version 23开始，中间码HAR、字节码HAR通过资源ID相关接口可以正常访问资源，&gt; 更多请参考[资源访问](../../../../quick-start/resource-categories-and-access.md#资源访问)。&gt;&gt; - 示例代码中test文件的具体内容请参考[附录](../../../../reference/apis-localization-kit/js-apis-resource-manager.md#附录)。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ColorMode](arkts-localization-colormode-e.md) | 用于表示当前设备颜色模式。 |
| [DeviceType](arkts-localization-devicetype-e.md) | 用于表示当前设备类型。 |
| [Direction](arkts-localization-direction-e.md) | 用于表示设备屏幕方向。 |
| [ScreenDensity](arkts-localization-screendensity-e.md) | 用于表示当前设备屏幕密度。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RawFileDescriptor](arkts-localization-rawfiledescriptor-t.md) | 表示rawfile文件所在HAP的文件描述符（fd）。 |
| [Resource](arkts-localization-resource-t.md) | 表示资源信息，包含资源ID值、应用包名、模块名称等信息，一般可使用$r方式获取。 |

