# ISubscribedWatches

Define ISubscribedWatches interface.

**继承/实现关系：** ISubscribedWatches extends [IWatchSubscriberRegister](decorator-iwatchsubscriberregister-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ISubscribedWatches extends IWatchSubscriberRegister--><!--Device-unnamed-export declare interface ISubscribedWatches extends IWatchSubscriberRegister-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## executeOnSubscribingWatches

```TypeScript
executeOnSubscribingWatches(propertyName: string): void
```

Execute the watch function callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ISubscribedWatches-executeOnSubscribingWatches(propertyName: string): void--><!--Device-ISubscribedWatches-executeOnSubscribingWatches(propertyName: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyName | string | 是 | property name |

