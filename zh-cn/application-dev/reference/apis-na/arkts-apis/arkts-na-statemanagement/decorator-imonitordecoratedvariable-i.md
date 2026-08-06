# IMonitorDecoratedVariable

Defines @Monitor decorated variable interface.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IMonitorDecoratedVariable--><!--Device-unnamed-export declare interface IMonitorDecoratedVariable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetOnReuse

```TypeScript
resetOnReuse(): void
```

ComponentV2被重用时重置Monitor。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMonitorDecoratedVariable-resetOnReuse(): void--><!--Device-IMonitorDecoratedVariable-resetOnReuse(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
readonly path: string[]
```

获取所有被监听的状态变量的路径。

**类型：** string[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMonitorDecoratedVariable-readonly path: string[]--><!--Device-IMonitorDecoratedVariable-readonly path: string[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

