# IWatchSubscriberRegister

Define IWatchSubscriberRegister interface.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IWatchSubscriberRegister--><!--Device-unnamed-export declare interface IWatchSubscriberRegister-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addWatchSubscriber

```TypeScript
addWatchSubscriber(watchId: WatchIdType): void
```

Registers the watch function callback.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IWatchSubscriberRegister-addWatchSubscriber(watchId: WatchIdType): void--><!--Device-IWatchSubscriberRegister-addWatchSubscriber(watchId: WatchIdType): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watchId | [WatchIdType](arkts-na-watchidtype-t.md) | 是 | the watch function id |

## removeWatchSubscriber

```TypeScript
removeWatchSubscriber(watchId: WatchIdType): boolean
```

UnRegister the watch function callback.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IWatchSubscriberRegister-removeWatchSubscriber(watchId: WatchIdType): boolean--><!--Device-IWatchSubscriberRegister-removeWatchSubscriber(watchId: WatchIdType): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watchId | [WatchIdType](arkts-na-watchidtype-t.md) | 是 | the watch function id |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean |  |

