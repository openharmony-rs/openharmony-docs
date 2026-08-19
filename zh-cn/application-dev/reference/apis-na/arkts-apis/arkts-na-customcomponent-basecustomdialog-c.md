# BaseCustomDialog

Definition of base custom dialog class.

**继承/实现关系：** BaseCustomDialog extends [ExtendableComponent](arkts-na-extendablecomponent-extendablecomponent-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class BaseCustomDialog--><!--Device-unnamed-export declare abstract class BaseCustomDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## _invokeImpl

```TypeScript
@Builder
  static _invokeImpl<S extends BaseCustomDialog<S, S_Options>, S_Options>(
        factory: () => S,
        initializers?: () => S_Options,
        content?: CustomBuilder
    ): void
```

创建自定义对话框的实现

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseCustomDialog-@Builder  static _invokeImpl<S extends BaseCustomDialog<S, S_Options>, S_Options>(        factory: () => S,        initializers?: () => S_Options,        content?: CustomBuilder    ): void--><!--Device-BaseCustomDialog-@Builder  static _invokeImpl<S extends BaseCustomDialog<S, S_Options>, S_Options>(        factory: () => S,        initializers?: () => S_Options,        content?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | () =&gt; S | 是 | 用于创建自定义对话框实例的工厂 |
| initializers | () =&gt; S_Options | 否 | 自定义对话框中所有字段的初始数据 |
| content | CustomBuilder | 否 | 自定义对话框的尾随闭包 |

## constructor

```TypeScript
constructor(useSharedStorage?: boolean, storage?: LocalStorage)
```

Constructor to use to create a custom dialog instance.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseCustomDialog-constructor(useSharedStorage?: boolean, storage?: LocalStorage)--><!--Device-BaseCustomDialog-constructor(useSharedStorage?: boolean, storage?: LocalStorage)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| useSharedStorage | boolean | 否 | determine whether to use the LocalStorage instance object returned by UIContext.getSharedLocalStorage() interface. |
| storage | LocalStorage | 否 | localStorage instance. |

