# 常量

## WithEnv

```TypeScript
export declare const WithEnv: WithEnvInterface
```

WithEnv组件用于为子组件树设置局部环境变量作用域。开发者可以通过该组件为后代组件提供自定义环境变量，或设置系统环境变量。

> **说明：**

> - 此接口仅可在Stage模型下使用。  
>  
> - 可通过[customEnv](arkts-arkui-arkui-withenv-withenvattribute-c.md#customenv-1)设置自定义环境变量。  
>  
> - 支持通过[env](arkts-arkui-arkui-withenv-withenvattribute-c.md#env-1)设置的系统环境变量键，系统环境变量键存于[WritableEnvKey](../arkts-components/arkts-arkui-writableenvkey-c.md)。  
>  
> - WithEnv嵌套时，同名环境变量按最近作用域生效。

### 子组件

支持单个子组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const WithEnv: WithEnvInterface--><!--Device-unnamed-export declare const WithEnv: WithEnvInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WithEnvInstance

```TypeScript
export declare const WithEnvInstance: WithEnvAttribute
```

定义WithEnv逻辑组件实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare const WithEnvInstance: WithEnvAttribute--><!--Device-unnamed-export declare const WithEnvInstance: WithEnvAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

