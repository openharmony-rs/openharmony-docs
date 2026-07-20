# MonitorDecorator

```TypeScript
declare type MonitorDecorator = (value: string | MonitorDecoratorOptions, ...args: string[]) => MethodDecorator
```

Defines Monitor Decorator type

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type MonitorDecorator = (value: string | MonitorDecoratorOptions, ...args: string[]) => MethodDecorator--><!--Device-unnamed-declare type MonitorDecorator = (value: string | MonitorDecoratorOptions, ...args: string[]) => MethodDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| MonitorDecoratorOptions | 是 | 由用户或配置选项输入的监视路径。  |
| args | string[] | 是 | 用户输入的监控路径  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MethodDecorator | 监视器装饰器  |

