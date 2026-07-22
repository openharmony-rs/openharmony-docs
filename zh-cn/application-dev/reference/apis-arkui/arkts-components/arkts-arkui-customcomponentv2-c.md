# CustomComponentV2

自定义组件V2

**继承/实现关系：** CustomComponentV2 extends [BaseCustomComponent](arkts-arkui-basecustomcomponent-c.md)

**起始版本：** 18

<!--Device-unnamed-declare class CustomComponentV2 extends BaseCustomComponent--><!--Device-unnamed-declare class CustomComponentV2 extends BaseCustomComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToReuse

```TypeScript
aboutToReuse?(): void
```

aboutToReuse Method for @ComponentV2, it is executed when fetching instance of custom component from RecyclePool.It is different from the @Reusable in CustomComponent, there is no param parameter in this callback.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponentV2-aboutToReuse?(): void--><!--Device-CustomComponentV2-aboutToReuse?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

