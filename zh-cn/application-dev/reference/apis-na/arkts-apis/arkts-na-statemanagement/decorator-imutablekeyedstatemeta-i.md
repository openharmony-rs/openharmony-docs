# IMutableKeyedStateMeta

Define mutable state meta interface with key.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IMutableKeyedStateMeta--><!--Device-unnamed-export declare interface IMutableKeyedStateMeta-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addRef

```TypeScript
addRef(key: string): void
```

Collect the dependancy for UI component with state variable based on given key

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMutableKeyedStateMeta-addRef(key: string): void--><!--Device-IMutableKeyedStateMeta-addRef(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 |  |

## addRef

```TypeScript
addRef(index: int): void
```

Collect the dependancy for UI component with state variable based on given key

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMutableKeyedStateMeta-addRef(index: int): void--><!--Device-IMutableKeyedStateMeta-addRef(index: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 |  |

## fireChange

```TypeScript
fireChange(key: string): void
```

Notify UI component with given key to update when state variable is changed

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMutableKeyedStateMeta-fireChange(key: string): void--><!--Device-IMutableKeyedStateMeta-fireChange(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 |  |

## fireChange

```TypeScript
fireChange(index: int): void
```

Notify UI component with given key to update when state variable is changed

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMutableKeyedStateMeta-fireChange(index: int): void--><!--Device-IMutableKeyedStateMeta-fireChange(index: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 |  |

