# WithEnvAttribute

定义WithEnv组件的属性功能。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class WithEnvAttribute--><!--Device-unnamed-export declare class WithEnvAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { WithEnvAttribute, WithEnv } from '@kit.ArkUI';
```

## customEnv

```TypeScript
customEnv<T>(key: CustomEnvKey<T>,  value: T): WithEnvAttribute
```

设置作用域内可被后代自定义组件读取的自定义环境变量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WithEnvAttribute-customEnv<T>(key: CustomEnvKey<T>,  value: T): WithEnvAttribute--><!--Device-WithEnvAttribute-customEnv<T>(key: CustomEnvKey<T>,  value: T): WithEnvAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [CustomEnvKey](../arkts-components/arkts-arkui-common-customenvkey-c.md)<T> | 是 | 自定义环境变量的键。 |
| value | T | 是 | 自定义环境变量的值。value的类型T对应CustomEnvKey&lt;T&gt;的类型T。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WithEnvAttribute](arkts-arkui-arkui-withenv-withenvattribute-c.md) | WithEnvAttribute对象。 |

## env

```TypeScript
env<T>(key: WritableSystemEnvKey<T>, value: T): WithEnvAttribute
```

设置作用域内的系统环境变量。当前正式支持的系统环境变量键为WritableEnvKey.FONT_SCALE、WritableEnvKey.DIRECTION。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WithEnvAttribute-env<T>(key: WritableSystemEnvKey<T>, value: T): WithEnvAttribute--><!--Device-WithEnvAttribute-env<T>(key: WritableSystemEnvKey<T>, value: T): WithEnvAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [WritableSystemEnvKey](../arkts-components/arkts-arkui-common-writablesystemenvkey-c.md)<T> | 是 | 系统环境变量键。当前正式支持WritableEnvKey.FONT_SCALE和WritableEnvKey.DIRECTION。 |
| value | T | 是 | 系统环境变量值。value的类型T对应WritableSystemEnvKey&lt;T&gt;中的类型T。当key为WritableEnvKey.FONT_SCALE时，value类型为number；当key为WritableEnvKey.DIRECTION时，value类型为Direction。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WithEnvAttribute](arkts-arkui-arkui-withenv-withenvattribute-c.md) | WithEnvAttribute对象。 |

