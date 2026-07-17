# EnvDecorator

```TypeScript
declare type EnvDecorator = (value: SystemProperties) => PropertyDecorator
```

定义Env装饰器类型

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type EnvDecorator = (value: SystemProperties) => PropertyDecorator--><!--Device-unnamed-declare type EnvDecorator = (value: SystemProperties) => PropertyDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | SystemProperties | 是 | 用户输入的环境变量key值 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PropertyDecorator | Env装饰器 |

