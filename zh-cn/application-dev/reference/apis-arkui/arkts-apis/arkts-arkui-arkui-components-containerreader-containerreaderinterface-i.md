# ContainerReaderInterface

定义ContainerReader组件。用于在动态场景下基于尺寸断点读取和分析容器布局信息。提供容器尺寸分析和断点检测能力。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ContainerReaderInterface--><!--Device-unnamed-export interface ContainerReaderInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { BreakpointOptions, ContainerReader, ContainerReaderAttribute } from '@kit.ArkUI';
```

<a id="constructor"></a>
## constructor

```TypeScript
(value: ContainerReaderInfo): ContainerReaderAttribute
```

创建容器断点组件并配置容器读取参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-ContainerReaderInterface-(value: ContainerReaderInfo): ContainerReaderAttribute--><!--Device-ContainerReaderInterface-(value: ContainerReaderInfo): ContainerReaderAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ContainerReaderInfo](arkts-arkui-arkui-components-containerreader-containerreaderinfo-i.md) | 是 | 容器读取配置选项，包含尺寸数据和断点配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContainerReaderAttribute](arkts-arkui-arkui-components-containerreader-containerreaderattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

