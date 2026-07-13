# Env

## Env

```TypeScript
declare function Env<T>(key: SystemEnvKey<T> | SystemProperties): PropertyDecorator
```

定义Env PropertyDecorator。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | SystemEnvKey&lt;T&gt; \| SystemProperties | 是 | 用户输入的键值。【自22至26】 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PropertyDecorator | 环境装饰器 |

