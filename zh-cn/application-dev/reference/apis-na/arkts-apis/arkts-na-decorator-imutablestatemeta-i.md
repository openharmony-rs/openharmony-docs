# IMutableStateMeta

Define mutable state meta interface.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface IMutableStateMeta--><!--Device-unnamed-export declare interface IMutableStateMeta-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addRef

```TypeScript
addRef(): void
```

Collect the dependancy for UI component with state variable

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMutableStateMeta-addRef(): void--><!--Device-IMutableStateMeta-addRef(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fireChange

```TypeScript
fireChange(): void
```

Notify UI component to update when state variable is changed

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMutableStateMeta-fireChange(): void--><!--Device-IMutableStateMeta-fireChange(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

