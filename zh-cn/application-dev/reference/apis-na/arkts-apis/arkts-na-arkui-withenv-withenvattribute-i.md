# WithEnvAttribute

定义WithEnv组件的属性功能。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface WithEnvAttribute--><!--Device-unnamed-export declare interface WithEnvAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## applyAttributesFinish

```TypeScript
applyAttributesFinish(): void
```

通知WithEnv属性设置完成。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WithEnvAttribute-applyAttributesFinish(): void--><!--Device-WithEnvAttribute-applyAttributesFinish(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## customEnv

```TypeScript
customEnv<T>(key: CustomEnvKey<T>,  value: T): this
```

设置作用域内可被后代自定义组件读取的自定义环境变量。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WithEnvAttribute-customEnv<T>(key: CustomEnvKey<T>,  value: T): this--><!--Device-WithEnvAttribute-customEnv<T>(key: CustomEnvKey<T>,  value: T): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [CustomEnvKey](arkts-na-decorator-customenvkey-c.md)&lt;T&gt; | 是 | 自定义环境变量的键。 |
| value | T | 是 | 自定义环境变量的值。value的类型T对应CustomEnvKey&lt;T&gt;的类型T。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | WithEnvAttribute对象。 |

## env

```TypeScript
env<T>(key: WritableSystemEnvKey<T>, value: T): this
```

设置作用域内的系统环境变量。当前正式支持的系统环境变量键为WritableEnvKey.FONT_SCALE、WritableEnvKey.DIRECTION。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WithEnvAttribute-env<T>(key: WritableSystemEnvKey<T>, value: T): this--><!--Device-WithEnvAttribute-env<T>(key: WritableSystemEnvKey<T>, value: T): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [WritableSystemEnvKey](arkts-na-decorator-writablesystemenvkey-c.md)&lt;T&gt; | 是 | 系统环境变量键。当前正式支持WritableEnvKey.FONT_SCALE和WritableEnvKey.DIRECTION。 |
| value | T | 是 | 系统环境变量值。value的类型T对应WritableSystemEnvKey&lt;T&gt;中的类型T。当key为WritableEnvKey.FONT_SCALE时，value类型为number；当key为WritableEnvKey.DIRECTION时，value类型为Direction。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | WithEnvAttribute对象。 |

## setWithEnvOptions

```TypeScript
setWithEnvOptions(): this
```

设置WithEnv选项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WithEnvAttribute-setWithEnvOptions(): this--><!--Device-WithEnvAttribute-setWithEnvOptions(): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | WithEnvAttribute实例。 |

