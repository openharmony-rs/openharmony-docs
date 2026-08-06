# CommonConfiguration

Defines the common configuration.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface CommonConfiguration<T>--><!--Device-unnamed-export declare interface CommonConfiguration<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier: ContentModifier<T>
```

Obtains the contentModifier instance object

**类型：** ContentModifier&lt;T&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonConfiguration-contentModifier: ContentModifier<T>--><!--Device-CommonConfiguration-contentModifier: ContentModifier<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled: boolean
```

If the value is true, the contentModifier is available and can respond to operations such as triggerChange. If it is set to false, triggerChange operations are not responded.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonConfiguration-enabled: boolean--><!--Device-CommonConfiguration-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

