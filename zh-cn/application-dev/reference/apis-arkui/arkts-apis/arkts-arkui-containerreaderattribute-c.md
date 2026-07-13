# ContainerReaderAttribute

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** ContainerReaderAttribute extends [CommonMethod<ContainerReaderAttribute>](CommonMethod<ContainerReaderAttribute>)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## breakpointConfig

```TypeScript
breakpointConfig(value?: BreakpointOptions): ContainerReaderAttribute
```

设置断点配置选项，定义触发不同布局行为的尺寸阈值。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BreakpointOptions | 否 | 断点配置选项，包含宽度和高度的断点阈值数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ContainerReaderAttribute | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

