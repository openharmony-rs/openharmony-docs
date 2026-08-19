# BaseCustomComponent

基础自定义组件的定义，它是所有自定义组件的基类。

**继承/实现关系：** BaseCustomComponent extends [ExtendableComponent](arkts-na-extendablecomponent-extendablecomponent-c.md) implements CommonAttribute

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class BaseCustomComponent--><!--Device-unnamed-export declare abstract class BaseCustomComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToRecycle

```TypeScript
aboutToRecycle(): void
```

组件复用在放入复用驰时，会触发回调

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseCustomComponent-aboutToRecycle(): void--><!--Device-BaseCustomComponent-aboutToRecycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

