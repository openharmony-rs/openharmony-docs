# CommonConfiguration

开发者需要自定义class实现ContentModifier接口。

**起始版本：** 12

<!--Device-unnamed-declare interface CommonConfiguration<T>--><!--Device-unnamed-declare interface CommonConfiguration<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier: ContentModifier<T>
```

用于将用户需要的组件信息发送到自定义内容区。

**类型：** ContentModifier&lt;T&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonConfiguration-contentModifier: ContentModifier<T>--><!--Device-CommonConfiguration-contentModifier: ContentModifier<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled: boolean
```

如果该值为true，则contentModifier可用，并且可以响应triggerChange等操作，如果设置为false，则不会响应triggerChange等操作。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CommonConfiguration-enabled: boolean--><!--Device-CommonConfiguration-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

