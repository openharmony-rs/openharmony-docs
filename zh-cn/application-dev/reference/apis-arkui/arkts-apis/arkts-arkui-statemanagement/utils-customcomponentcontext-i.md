# CustomComponentContext

自定义组件的上下文信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface CustomComponentContext--><!--Device-unnamed-export declare interface CustomComponentContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getReusePool

```TypeScript
getReusePool(): IReusePool | undefined
```

从当前自定义组件获取全局重用池。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentContext-getReusePool(): IReusePool | undefined--><!--Device-CustomComponentContext-getReusePool(): IReusePool | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the recyclepool instance. |

## registerActiveAndInactiveCallback

```TypeScript
registerActiveAndInactiveCallback(active?: ActiveAndInactiveCallbackType,
    inactive?: ActiveAndInactiveCallbackType): void
```

注册激活和非激活回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentContext-registerActiveAndInactiveCallback(active?: ActiveAndInactiveCallbackType,    inactive?: ActiveAndInactiveCallbackType): void--><!--Device-CustomComponentContext-registerActiveAndInactiveCallback(active?: ActiveAndInactiveCallbackType,    inactive?: ActiveAndInactiveCallbackType): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| active | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 激活函数回调默认值： 默认值：undefined。 |
| inactive | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | in激活函数回调默认值： 默认值：undefined。 |

