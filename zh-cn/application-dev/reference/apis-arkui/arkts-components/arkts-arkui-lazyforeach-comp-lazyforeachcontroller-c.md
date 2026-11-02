# LazyForEachController

```TypeScript
declare class LazyForEachController
```

LazyForEach组件的控制器。通过[LazyForEachOptions](arkts-arkui-lazyforeach-comp-lazyforeachoptions-i.md)中的controller字段将控制器绑定到LazyForEach组件上，需要清理缓存时调用[clearCache](#clearcache)清理LazyForEach组件预加载的子组件。

**起始版本：** 26.1.0

<!--Device-unnamed-declare class LazyForEachController--><!--Device-unnamed-declare class LazyForEachController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearCache

```TypeScript
clearCache(): void
```

清理该控制器绑定的LazyForEach组件预加载的子组件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-LazyForEachController-clearCache(): void--><!--Device-LazyForEachController-clearCache(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

构造函数，用于创建一个<em>LazyForEachController</em>对象。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-LazyForEachController-constructor()--><!--Device-LazyForEachController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
