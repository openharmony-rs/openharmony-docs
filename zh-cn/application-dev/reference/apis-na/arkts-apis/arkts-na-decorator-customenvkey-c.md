# CustomEnvKey

自定义环境变量的Key的类型。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class CustomEnvKey--><!--Device-unnamed-export declare class CustomEnvKey-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
protected constructor()
```

用于创建该类的实例对象。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomEnvKey-protected constructor()--><!--Device-CustomEnvKey-protected constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## create

```TypeScript
static create<T>(): CustomEnvKey<T>
```

创建一个自定义环境变量Key，作为@CustomEnv装饰器的参数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomEnvKey-static create<T>(): CustomEnvKey<T>--><!--Device-CustomEnvKey-static create<T>(): CustomEnvKey<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CustomEnvKey](arkts-na-decorator-customenvkey-c.md)&lt;T&gt; | CustomEnvKey |

