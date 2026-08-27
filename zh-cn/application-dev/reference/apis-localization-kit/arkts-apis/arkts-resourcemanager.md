# @ohos.resourceManager(资源管理)

本模块提供应用资源和系统资源的访问能力，允许应用根据当前的[Configuration](arkts-localization-resourcemanager-configuration-c.md)配置，获取最匹配的应用资源或系统资源，支持国际化资源匹配和多设备适配。具 体匹配规则参考[资源匹配](../../../quick-start/resource-categories-and-access.md#资源匹配)。Configuration配置包括语言-文字-国家地区、横竖屏、颜色模式、Mcc（移动国家码）和Mnc（移动网络码）、设备类型、屏幕密度。  
**使用场景**：  
- 应用国际化：根据用户语言和地区自动获取匹配的字符串资源。  
- 多设备适配：根据设备类型、屏幕密度获取合适的媒体资源。  
- 动态资源配置：根据设备状态（横竖屏、颜色模式等）获取对应配置的资源。  
**使用说明**：  
- FA模型需要先导入模块，再调用[getResourceManager](arkts-localization-resourcemanager-getresourcemanager-f.md)接口获取资源管理对象。  
- 从API version 9开始，Stage模型无需导入模块，支持通过Context获取资源管理resourceManager对象。Context的更多介绍请参考  
[应用上下文Context](../../../application-models/application-context-stage.md)。  
 ```ts
 import { UIAbility } from '@kit.AbilityKit';
 import { window } from '@kit.ArkUI';

 export default class EntryAbility extends UIAbility {
 onWindowStageCreate(windowStage: window.WindowStage) {
 let context = this.context;
 let resourceManager = context.resourceManager;
 }
 }
 ```

**起始版本：** 6

**系统能力：** SystemCapability.Global.ResourceManager

## 导入模块

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getResourceManager(资源管理)](arkts-localization-resourcemanager-getresourcemanager-f.md) | 获取当前应用的资源管理对象。使用callback异步回调。 |
| [getResourceManager(资源管理)](arkts-localization-resourcemanager-getresourcemanager-f.md) | 获取指定应用的资源管理对象。使用callback异步回调。 |
| [getResourceManager(资源管理)](arkts-localization-resourcemanager-getresourcemanager-f.md) | 获取当前应用的资源管理对象。使用Promise异步回调。 |
| [getResourceManager(资源管理)](arkts-localization-resourcemanager-getresourcemanager-f.md) | 获取指定应用的资源管理对象。使用Promise异步回调。 |
| [getSysResourceManager(资源管理)](arkts-localization-resourcemanager-getsysresourcemanager-f.md) | 获取系统资源管理对象，用于访问系统预置的资源。 |
| [getSystemResourceManager(资源管理)](arkts-localization-resourcemanager-getsystemresourcemanager-f.md) | 获取系统资源管理对象，用于访问系统预置的资源。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Configuration(资源管理)](arkts-localization-resourcemanager-configuration-c.md) | 表示当前设备的状态。 |
| [DeviceCapability(资源管理)](arkts-localization-resourcemanager-devicecapability-c.md) | 表示设备支持的能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AsyncCallback(资源管理)](arkts-localization-resourcemanager-asynccallback-i.md) | 异步回调接口 |
| [ResourceManager(资源管理)](arkts-localization-resourcemanager-resourcemanager-i.md) | 提供访问应用资源和系统资源的能力，可访问的资源范围为当前Context对应的HAP/HSP模块中的资源以及所有的系统资源。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ColorMode(资源管理)](arkts-localization-resourcemanager-colormode-e.md) | 用于表示当前设备颜色模式。 |
| [DeviceType(资源管理)](arkts-localization-resourcemanager-devicetype-e.md) | 用于表示当前设备类型。<!--RP1--><!--RP1End--> |
| [Direction(资源管理)](arkts-localization-resourcemanager-direction-e.md) | 用于表示设备屏幕方向。 |
| [ScreenDensity(资源管理)](arkts-localization-resourcemanager-screendensity-e.md) | 用于表示当前设备屏幕密度。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [RawFileDescriptor(资源管理)](arkts-localization-resourcemanager-rawfiledescriptor-t.md) | 表示rawfile文件所在HAP的文件描述符信息。 |
| [Resource(资源管理)](arkts-localization-resourcemanager-resource-t.md) | 表示资源相关信息，包括应用包名、应用模块名、资源ID、资源类型和格式化参数等。 |
