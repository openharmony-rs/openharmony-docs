# CustomEnv

## CustomEnv

```TypeScript
declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator
```

用于获取自定义环境变量。 开发者指南见：[\@CustomEnv开发者指南](../../../ui/arkts-custom-env-property.md)。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator--><!--Device-unnamed-declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [CustomEnvKey](arkts-arkui-customenvkey-c.md)&lt;T&gt; | 是 | 自定义环境变量Key，用于标识要获取的自定义环境变量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PropertyDecorator | 属性装饰器，开发者无需关注该返回值。 |

