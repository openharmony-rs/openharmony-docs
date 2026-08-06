# compatibleComponent

## compatibleComponent

```TypeScript
export declare function compatibleComponent(
    init: CompatibleInitCallback,
    update: CompatibleUpdateCallback,
    component?: ExtendableComponent
): void
```

在ArkTS-Sta中引用ArkTS-Dyn自定义组件的占位组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function compatibleComponent(    init: CompatibleInitCallback,    update: CompatibleUpdateCallback,    component?: ExtendableComponent): void--><!--Device-unnamed-export declare function compatibleComponent(    init: CompatibleInitCallback,    update: CompatibleUpdateCallback,    component?: ExtendableComponent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| init | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 初始化占位组件的回调函数。 |
| update | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 更新占位组件的回调函数。 |
| component | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 当前ArkTS-Sta自定义组件。 |

