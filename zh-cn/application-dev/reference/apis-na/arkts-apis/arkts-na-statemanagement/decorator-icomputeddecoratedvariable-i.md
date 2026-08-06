# IComputedDecoratedVariable

定义@Computed状态变量的接口

**继承/实现关系：** IComputedDecoratedVariable extends [IDecoratedReadableVariable<T>](IDecoratedReadableVariable<T>)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IComputedDecoratedVariable<T> extends IDecoratedReadableVariable<T>--><!--Device-unnamed-export declare interface IComputedDecoratedVariable<T> extends IDecoratedReadableVariable<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resetOnReuse

```TypeScript
resetOnReuse(): void
```

ComponentV2被重用时重置Computed变量。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IComputedDecoratedVariable-resetOnReuse(): void--><!--Device-IComputedDecoratedVariable-resetOnReuse(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOwner

```TypeScript
setOwner(owner: IVariableOwner): void
```

设置状态变量的所有者，用于检测所在自定义组件是否冻结

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IComputedDecoratedVariable-setOwner(owner: IVariableOwner): void--><!--Device-IComputedDecoratedVariable-setOwner(owner: IVariableOwner): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 状态变量的所有者 |

