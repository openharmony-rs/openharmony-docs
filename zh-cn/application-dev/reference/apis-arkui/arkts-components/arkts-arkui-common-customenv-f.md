# CustomEnv

## CustomEnv

```TypeScript
declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator
```

定义自定义环境PropertyDecorator。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator--><!--Device-unnamed-declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [CustomEnvKey](arkts-arkui-common-customenvkey-c.md)<T> | 是 | 自定义环境密钥 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PropertyDecorator | CustomEnv装饰器 |

