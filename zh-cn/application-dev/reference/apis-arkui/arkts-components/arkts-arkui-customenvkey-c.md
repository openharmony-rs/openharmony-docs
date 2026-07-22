# CustomEnvKey

定义自定义环境Key。

**起始版本：** 26.0.0

<!--Device-unnamed-declare class CustomEnvKey<S>--><!--Device-unnamed-declare class CustomEnvKey<S>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
protected constructor()
```

构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomEnvKey-protected constructor()--><!--Device-CustomEnvKey-protected constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## create

```TypeScript
static create<T>(): CustomEnvKey<T>
```

创建自定义环境密钥

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomEnvKey-static create<T>(): CustomEnvKey<T>--><!--Device-CustomEnvKey-static create<T>(): CustomEnvKey<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CustomEnvKey](arkts-arkui-customenvkey-c.md)&lt;T&gt; | 自定义EnvKey |

## type

```TypeScript
private type?: S
```

自定义env key对应的类型。

**类型：** S

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomEnvKey-private type?: S--><!--Device-CustomEnvKey-private type?: S-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

