# @ohos.arkui.components.ContainerReader

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ContainerReaderAttribute](arkts-arkui-containerreaderattribute-c.md) | 除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性： |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BreakpointOptions](arkts-arkui-breakpointoptions-i.md) | 定义断点配置选项，用于指定容器尺寸分析的阈值参数。 |
| [ContainerReaderInfo](arkts-arkui-containerreaderinfo-i.md) | 定义ContainerReader组件的配置选项，用于指定容器尺寸读取和断点值获取的参数，不能通过此参数改变组件尺寸和断点值。 |
| [ContainerReaderInterface](arkts-arkui-containerreaderinterface-i.md) | 定义ContainerReader组件。用于在动态场景下基于尺寸断点读取和分析容器布局信息。提供容器尺寸分析和断点检测能力。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ContainerReader](arkts-arkui-arkui-components-containerreader-con.md#containerreader) | ContainerReader是容器断点组件，用于在动态场景下根据容器尺寸获取断点信息并进行响应式布局。该组件通过[双向绑定](../../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)实时返回容器的尺寸和断点，使开发者能够基于容器大小进行差异化的组件创建和布局。 |
| [ContainerReaderInstance](arkts-arkui-arkui-components-containerreader-con.md#containerreaderinstance) | 定义ContainerReader组件实例。提供对ContainerReader组件方法的访问，用于容器尺寸分析和断点检测。 |

