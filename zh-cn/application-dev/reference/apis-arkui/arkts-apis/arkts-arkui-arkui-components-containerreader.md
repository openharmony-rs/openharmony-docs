# @ohos.arkui.components.ContainerReader

## 导入模块

```TypeScript
import { ContainerReader, ContainerReaderAttribute, BreakpointOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ContainerReaderAttribute](arkts-arkui-arkui-components-containerreader-containerreaderattribute-c.md) | 除支持[通用属性](../arkts-components/arkts-arkui-commonmethod-c.md)外，还支持以下属性： |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BreakpointOptions](arkts-arkui-arkui-components-containerreader-breakpointoptions-i.md) | 定义断点配置选项，用于指定容器尺寸分析的阈值参数。 |
| [ContainerReaderInfo](arkts-arkui-arkui-components-containerreader-containerreaderinfo-i.md) | 定义ContainerReader组件的配置选项，用于指定容器尺寸读取和断点值获取的参数，不能通过此参数改变组件尺寸和断点值。 |
| [ContainerReaderInterface](arkts-arkui-arkui-components-containerreader-containerreaderinterface-i.md) | 定义ContainerReader组件。用于在动态场景下基于尺寸断点读取和分析容器布局信息。提供容器尺寸分析和断点检测能力。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ContainerReader](arkts-arkui-arkui-components-containerreader-con.md) | ContainerReader是容器断点组件，用于在动态场景下根据容器尺寸获取断点信息并进行响应式布局。该组件通过[双向绑定](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)实时返回容器的尺寸和断点，使开发者能够基于容器大小进行差异化的组件创建和布局。 |
| [ContainerReaderInstance](arkts-arkui-arkui-components-containerreader-con.md#containerreaderinstance) | 定义ContainerReader组件实例。提供对ContainerReader组件方法的访问，用于容器尺寸分析和断点检测。 |

## 示例

```TypeScript
### 示例1 （根据ContainerReader宽度断点切换布局方向）

该示例展示了[ContainerReader](#containerreader-1)组件，如何通过双向绑定获取容器尺寸和断点信息，并根据宽度断点切换布局方向。

从API版本26.0.0开始，新增ContainerReader。


```

```TypeScript
### 示例2 （自定义断点配置）

该示例展示了如何通过[breakpointConfig](arkts-arkui-arkui-components-containerreader-containerreaderattribute-c.md#breakpointconfig)自定义断点阈值，定义不同的宽窄布局尺寸要求，实现更精细化的布局控制。

从API版本26.0.0开始，新增ContainerReader与breakpointConfig。

通过单击按钮改变父容器的宽度，返回不同的宽度断点值，从而调整布局方向。


```

```TypeScript
### 示例3 （利用宽度断点动态调整列数）

该示例展示了如何根据ContainerReader得到的宽度断点动态调整列数，实现多设备自适应布局。根据宽度断点不同设置不同的列数。

从API版本26.0.0开始，新增ContainerReader。
```
