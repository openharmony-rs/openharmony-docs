# CustomComponentV2

V2自定义组件类的定义。

**继承/实现关系：** CustomComponentV2 extends BaseCustomComponent<T_Options>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class CustomComponentV2--><!--Device-unnamed-export declare abstract class CustomComponentV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## _invokeImpl

```TypeScript
@Builder
  static _invokeImpl<S extends CustomComponentV2<S, S_Options>, S_Options>(
        @Builder styles: ((instance: S) => void) | undefined,
        factory: () => S,
        initializers?: () => S_Options,
        reuseId?: () => string,
        content?: CustomBuilder
    ): void
```

Implementation for creating a v2 custom component

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentV2-@Builder  static _invokeImpl<S extends CustomComponentV2<S, S_Options>, S_Options>(        @Builder styles: ((instance: S) => void) | undefined,        factory: () => S,        initializers?: () => S_Options,        reuseId?: () => string,        content?: CustomBuilder    ): void--><!--Device-CustomComponentV2-@Builder  static _invokeImpl<S extends CustomComponentV2<S, S_Options>, S_Options>(        @Builder styles: ((instance: S) => void) | undefined,        factory: () => S,        initializers?: () => S_Options,        reuseId?: () => string,        content?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | ((instance: S) =&gt; void) \| undefined | 是 | styles of custom component |
| factory | () =&gt; S | 是 | factory to create instance of custom component |
| initializers | () =&gt; S_Options | 否 | initial data for all the fields in custom component |
| reuseId | () =&gt; string | 否 | reuse id for reusable. Only valid if custom component decorated with @ReusableV2 |
| content | CustomBuilder | 否 | tail closure for custom component |

## _invokeImpl

```TypeScript
@Builder
  static _invokeImpl<S extends CustomComponentV2<S, S_Options>, S_Options>(
        @Builder styles: ((instance: S) => void) | undefined,
        factory: () => S,
        initializers?: () => S_Options,
        reuseId?: () => string,
        content?: CustomBuilder,
        options?: CustomComponentInvokeOptions
    ): void
```

Implementation for creating a v2 custom component

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentV2-@Builder  static _invokeImpl<S extends CustomComponentV2<S, S_Options>, S_Options>(        @Builder styles: ((instance: S) => void) | undefined,        factory: () => S,        initializers?: () => S_Options,        reuseId?: () => string,        content?: CustomBuilder,        options?: CustomComponentInvokeOptions    ): void--><!--Device-CustomComponentV2-@Builder  static _invokeImpl<S extends CustomComponentV2<S, S_Options>, S_Options>(        @Builder styles: ((instance: S) => void) | undefined,        factory: () => S,        initializers?: () => S_Options,        reuseId?: () => string,        content?: CustomBuilder,        options?: CustomComponentInvokeOptions    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | ((instance: S) =&gt; void) \| undefined | 是 | styles of custom component |
| factory | () =&gt; S | 是 | factory to create instance of custom component |
| initializers | () =&gt; S_Options | 否 | initial data for all the fields in custom component |
| reuseId | () =&gt; string | 否 | reuse id for reusable. Only valid if custom component decorated with @ReusableV2 |
| content | CustomBuilder | 否 | tail closure for custom component |
| options | [CustomComponentInvokeOptions](arkts-na-customcomponent-customcomponentinvokeoptions-i.md) | 否 | additional invoke options |

## aboutToReuse

```TypeScript
aboutToReuse(): void
```

组件复用时，触发回调

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentV2-aboutToReuse(): void--><!--Device-CustomComponentV2-aboutToReuse(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetStateVarsOnReuse

```TypeScript
resetStateVarsOnReuse(params?: T_Options): void
```

重置状态变量

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentV2-resetStateVarsOnReuse(params?: T_Options): void--><!--Device-CustomComponentV2-resetStateVarsOnReuse(params?: T_Options): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | T_Options | 否 | 自定义组件成员变量的数据 |

