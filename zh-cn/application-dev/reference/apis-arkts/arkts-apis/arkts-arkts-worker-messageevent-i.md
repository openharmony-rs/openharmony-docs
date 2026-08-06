# MessageEvent

消息类，持有Worker线程间传递的数据，MessageEvent类继承Event。

**继承/实现关系：** MessageEvent extends [Event](arkts-arkts-worker-event-i.md)

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-export interface MessageEvent<T> extends Event--><!--Device-unnamed-export interface MessageEvent<T> extends Event-End-->

**系统能力：** SystemCapability.Utils.Lang

## data

```TypeScript
readonly data: T
```

异常发生时传递的数据。

**类型：** T

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MessageEvent-readonly data: T--><!--Device-MessageEvent-readonly data: T-End-->

**系统能力：** SystemCapability.Utils.Lang

