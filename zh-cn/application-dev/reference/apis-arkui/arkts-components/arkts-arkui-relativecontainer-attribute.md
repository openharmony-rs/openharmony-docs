# RelativeContainer属性/事件

除支持通用属性外，还支持如下属性：支持通用事件。

**继承/实现关系：** RelativeContainerAttribute extends CommonMethod<RelativeContainerAttribute>

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## barrier

```TypeScript
barrier(value: Array<BarrierStyle>)
```

设置RelativeContainer容器内的[屏障](../../../ui/arkts-layout-development-relative-layout.md#多个组件的屏障)，子组件可以以屏障为锚点进行对齐定位。数组中 每个元素代表一条屏障。典型使用场景：避免子组件重叠、基于组件边缘创建虚拟边界、实现组件间自动间隔。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[BarrierStyle](arkts-arkui-barrierstyle-i.md)&gt; | 是 | RelativeContainer容器内的屏障，用于定义屏障的id、方向和依赖组件，子组件可以以屏障为锚点进行对齐定位。 |

## barrier

```TypeScript
barrier(barrierStyle: Array<LocalizedBarrierStyle>)
```

设置RelativeContainer容器内的屏障，子组件可以以屏障为锚点进行对齐定位，支持定义镜像模式的屏障线。数组中每个元素代表一条屏障。典型使用场景：RTL语言布局适配、镜像界面设计、根据阅读方向自动调整屏障位置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| barrierStyle | Array&lt;[LocalizedBarrierStyle](arkts-arkui-localizedbarrierstyle-i.md)&gt; | 是 | RelativeContainer容器内的屏障，支持定义镜像模式的屏障线。 |

## guideLine

```TypeScript
guideLine(value: Array<GuideLineStyle>)
```

设置RelativeContainer容器内的[辅助线](../../../ui/arkts-layout-development-relative-layout.md#使用辅助线辅助定位子组件)，数组中每个元素代表一条辅助线。 典型使用场景：子组件基于虚拟参考线对齐、创建可灵活调整的参考线定位、多个子组件基于同一基准线布局。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[GuideLineStyle](arkts-arkui-guidelinestyle-i.md)&gt; | 是 | RelativeContainer容器内的辅助线，定义guideLine的id、方向和位置，用于辅助定位子组件。 |
