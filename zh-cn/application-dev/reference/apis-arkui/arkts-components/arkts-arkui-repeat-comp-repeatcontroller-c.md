# RepeatController

```TypeScript
declare class RepeatController
```

Repeat组件的控制器。通过[RepeatOptions](arkts-arkui-repeat-comp-repeatoptions-i.md)中的controller字段将控制器绑定到Repeat组件上，需要清理缓存时调用[clearCache](#clearcache)清理Repeat组件复用池中的节点。

**起始版本：** 26.1.0

<!--Device-unnamed-declare class RepeatController--><!--Device-unnamed-declare class RepeatController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearCache

```TypeScript
clearCache(): void
```

清理该控制器绑定的Repeat组件复用池中的节点。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RepeatController-clearCache(): void--><!--Device-RepeatController-clearCache(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

构造函数，用于创建一个<em>RepeatController</em>对象。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RepeatController-constructor()--><!--Device-RepeatController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
