# CustomComponent

定义自定义组件类

**继承/实现关系：** CustomComponent extends [BaseCustomComponent<T_Options>](BaseCustomComponent<T_Options>)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class CustomComponent<T extends CustomComponent<T, T_Options>, T_Options> extends BaseCustomComponent<T_Options>--><!--Device-unnamed-export declare abstract class CustomComponent<T extends CustomComponent<T, T_Options>, T_Options> extends BaseCustomComponent<T_Options>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## _invokeImpl

```TypeScript
static _invokeImpl<S extends CustomComponent<S, S_Options>, S_Options>(factory: () => S,
        initializers?: () => S_Options,
        reuseId?: string,
        content?: CustomBuilder
    ): void
```

Implementation for creating a custom component

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponent-static _invokeImpl<S extends CustomComponent<S, S_Options>, S_Options>(factory: () => S,        initializers?: () => S_Options,        reuseId?: string,        content?: CustomBuilder    ): void--><!--Device-CustomComponent-static _invokeImpl<S extends CustomComponent<S, S_Options>, S_Options>(factory: () => S,        initializers?: () => S_Options,        reuseId?: string,        content?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | ((instance: S) =&gt; void) \| undefined | 是 | styles of custom component |
| factory | () =&gt; S | 是 | factory to create instance of custom component |
| initializers | () =&gt; S\_Options | 否 | initial data for all the fields in custom component |
| reuseId | string | 否 | reuse id for reusable. Only valid if custom component decorated with @Reusable |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | tail closure for custom component |

## aboutToReuse

```TypeScript
aboutToReuse(params: ReuseObject): void
```

aboutToReuse Method

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponent-aboutToReuse(params: ReuseObject): void--><!--Device-CustomComponent-aboutToReuse(params: ReuseObject): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Custom component init params. |

## constructor

```TypeScript
constructor(useSharedStorage?: boolean, storage?: LocalStorage)
```

Constructor to use to create a customComponent instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponent-constructor(useSharedStorage?: boolean, storage?: LocalStorage)--><!--Device-CustomComponent-constructor(useSharedStorage?: boolean, storage?: LocalStorage)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| useSharedStorage | boolean | 否 | determine whether to use the LocalStorage instance object returned by UIContext.getSharedLocalStorage() interface. |
| storage | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | localStorage instance. |

