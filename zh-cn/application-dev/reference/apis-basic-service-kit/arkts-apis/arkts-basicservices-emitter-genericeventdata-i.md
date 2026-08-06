# GenericEventData

发送事件时传递的泛型数据。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-emitter-export interface GenericEventData<T>--><!--Device-emitter-export interface GenericEventData<T>-End-->

**系统能力：** SystemCapability.Notification.Emitter

## data

```TypeScript
data?: T
```

发送事件时传递的数据。T：泛型类型，由开发者根据业务需要自定义具体的数据类型。

**类型：** T

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GenericEventData-data?: T--><!--Device-GenericEventData-data?: T-End-->

**系统能力：** SystemCapability.Notification.Emitter

