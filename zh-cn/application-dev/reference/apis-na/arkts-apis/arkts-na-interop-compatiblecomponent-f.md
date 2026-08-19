# compatibleComponent

## compatibleComponent

```TypeScript
@Builder
export declare function compatibleComponent(
    init: CompatibleInitCallback,
    update: CompatibleUpdateCallback,
    component?: ExtendableComponent
): void
```

在ArkTS-Sta中引用ArkTS-Dyn自定义组件的占位组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function compatibleComponent(    init: CompatibleInitCallback,    update: CompatibleUpdateCallback,    component?: ExtendableComponent): void--><!--Device-unnamed-@Builderexport declare function compatibleComponent(    init: CompatibleInitCallback,    update: CompatibleUpdateCallback,    component?: ExtendableComponent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| init | [CompatibleInitCallback](arkts-na-compatibleinitcallback-t.md) | 是 | 初始化占位组件的回调函数。 |
| update | [CompatibleUpdateCallback](arkts-na-compatibleupdatecallback-t.md) | 是 | 更新占位组件的回调函数。 |
| component | [ExtendableComponent](arkts-na-extendablecomponent-extendablecomponent-c.md) | 否 | 当前ArkTS-Sta自定义组件。 |

