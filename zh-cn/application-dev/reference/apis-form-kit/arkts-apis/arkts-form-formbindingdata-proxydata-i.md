# ProxyData

卡片代理刷新订阅数据信息。

**起始版本：** 23

<!--Device-formBindingData-interface ProxyData--><!--Device-formBindingData-interface ProxyData-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formBindingData } from '@kit.FormKit';
```

## key

```TypeScript
key: string
```

卡片代理刷新的订阅标识，与数据发布者保持一致。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyData-key: string--><!--Device-ProxyData-key: string-End-->

**系统能力：** SystemCapability.Ability.Form

## subscriberId

```TypeScript
subscriberId?: string
```

卡片代理刷新的订阅条件，用于指定订阅的消息过滤条件。设置后会根据subscriberId匹配相应的代理刷新消息，默认值为当前卡片的formId。当需要指定特定的订阅条件时传入此参数，不传入时默认值为当前卡片的formId。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ProxyData-subscriberId?: string--><!--Device-ProxyData-subscriberId?: string-End-->

**系统能力：** SystemCapability.Ability.Form

